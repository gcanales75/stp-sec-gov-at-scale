+++ 
title = "Task 8: Deploy Lab application" 
chapter = false 
weight = 8 
+++



The deployment, services and ingress configuration files are in the ```eks-lab-app/``` folder, please doble click on each of them to review their content.

- service.yaml
- deployment.yaml
- ingress.yaml

1. Open ```deployment.yaml``` file from the left panel, you will notice the Deployment's ```spec.template.spec.image``` field will be set from the ```$ECR_REPO_URI``` environment variable we set before. This will reference the docker image we created before.

	We will use ```envsubst```, which is preinstalled in Cloud9 to pass the container registry URI environment variable to the ```deployment.yaml``` file

1. Change directory to the application's path

	```
	cd ~/environment/stpEksLabRepo/eks-lab-app/
	```

1. Create the kubernetes service:

	```
	kubectl apply -f service.yaml
	```

1. Create kubernetes deployment:

	```
	envsubst < deployment.yaml | kubectl apply -f -
	```

1. Create kuberntes ingress:

	```
	kubectl apply -f ingress.yaml
	```

1. You can see "development" namespace pods, service, deployment and replica sets with the below command

	```
	kubectl get all
	```

1. To verify the ingress status and Application Load Balancer URL, run the below command:

	```
	kubectl get ingress
	```

1. Copy the Application Load Balancer URL from the command output (under ADDRESS column) and paste it in a browser to confirm the correct deployment. It could take 2-3 minutes to fully deploy.

	Please note that your browser shows the Kubernetes pod ID

	<img src="../readmeFiles/skitch.20.png" alt="drawing" width="600"/>

1. If you run the below command you could see this pod ID listed:

	```
	kubectl get pods
	```

If you reload your browser a few times you could see the ALB redirecting traffic to the different pods in your Kubernetes deployment.

