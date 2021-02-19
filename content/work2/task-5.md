+++ 
title = "Task 5: EKS Cluster authentication" 
chapter = false 
weight = 5 
+++

1. First, we need to setup some additional enviroment variables:

	```
	echo "export AWS_REGION=us-east-2" | tee -a ~/.bash_profile
	aws configure set default.region us-east-2
	```

1. To start working with your EKS cluster is has to be in ```ACTIVE``` state. To look at the status of our cluster run the below command:

	```
	aws eks describe-cluster --name eks-lab-cluster --query 'cluster.status' --output text
	```

	If the Cluster is in ```ACTIVE``` state, please proceed with the following steps, otherwise wait a few more minutes.

1. Once the Cluster is in ```ACTIVE``` state, we need to update kubeconfig file for EKS cluster authentication, please run the below commands to set proper  permissions to edit the file:

	```
	cd ~/environment/stpEksLabRepo/
	sudo chown -R $USER:$USER /home/ec2-user/.kube/
	```

	If you see this output: `chown: cannot access ‘/home/ec2-user/.kube/’: No such file or directory`
	Please wait two more minutes to finish the deployment.

1. To create the Kubernetes `config` file, you will need the cluster’s certificate authority data, the cluster URL and the cluster name, we will again use environment variables. Run the below commands to add them:

	```
	export CERTIFICATE_AUTHORITY=`aws eks describe-cluster --name eks-lab-cluster --query 'cluster.certificateAuthority' --output text`
	export CLUSTER_ENDPOINT=`aws eks describe-cluster --name eks-lab-cluster --query 'cluster.endpoint' --output text`
	export CLUSTER_NAME=`aws eks describe-cluster --name eks-lab-cluster --query 'cluster.name' --output text`
	```

	With those variables we will create a EKS Cluster ```config``` file, take a look at the file named ```config-source``` which is in the lab's working directory. We will use this file as a template.

1. Run this command to create the ```config``` file and make the variables substitution with the actual cluster information:

	```
	envsubst < "config-source" > "config"
	```

1. Copy the just created kubeconfig file to your kubernetes environment

	```
	cp ~/environment/stpEksLabRepo/config /home/ec2-user/.kube/config
	```

1. Confirm your session with the EKS Cluster is authenticated

	```
	kubectl get svc
	```

	You must see something a similar output:

	<img src="../readmeFiles/skitch.19.png" alt="drawing" width="500"/>

Reference: <a href="https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html" target="_blank">https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html</a>