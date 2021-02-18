+++ 
title = "Task 9: Deploy CloudWatch Container Insights" 
chapter = false 
weight = 9
+++

CloudWatch Container Insights collect, aggregate, and summarize metrics and logs from your containerized applications and microservices. Container Insights is available for Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS), and Kubernetes platforms on Amazon EC2.

The first step is to add a required IAM Policy (CloudWatchAgentServerPolicy) to your EKS compute (EC2) Nodes attached role policy.

1. Run the below commands to add the IAM policy to the EKS instance role:

	```
	export instanceId=`aws ec2 describe-instances --filters Name=instance-type,Values=t3.medium --query "Reservations[0].Instances[*].InstanceId" --output text`
	export instanceProfileArn=`aws ec2 describe-instances --instance-ids $instanceId --query 'Reservations[*].Instances[*].IamInstanceProfile.Arn' --output text`
	export instanceProfileName=`echo $instanceProfileArn | awk -F/ '{print $NF}'`
	export roleName=`aws iam get-instance-profile --instance-profile-name $instanceProfileName --query "InstanceProfile.Roles[*].RoleName" --output text`
	aws iam attach-role-policy --role-name $roleName --policy-arn arn:aws:iam::aws:policy/CloudWatchAgentServerPolicy
	```

	Reference: 
<a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Container-Insights-prerequisites.html" target="_blank">https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Container-Insights-prerequisites.html</a>

1. Run this commands to deploy Container Insights on your Amazon EKS Cluster:

	```
	export CLUSTER_NAME=`aws eks describe-cluster --name eks-lab-cluster --query 'cluster.name' --output text`
	curl https://raw.githubusercontent.com/aws-samples/amazon-cloudwatch-container-insights/latest/k8s-deployment-manifest-templates/deployment-mode/daemonset/container-insights-monitoring/quickstart/cwagent-fluentd-quickstart.yaml | sed "s/{{cluster_name}}/$CLUSTER_NAME/;s/{{region_name}}/us-east-2/" | kubectl apply -f -
	```

	NOTE: CloudWatch Container Insights may take up to 5 minutes to fully deploy, so you can view data. Please wait before proceeding to the following steps

1. Now access CloudWatch service returning to the AWS console tab in your browser. Service *search box* > CloudWatch

1. On your console left panel, select "Container Insights"

	<img src="../readmeFiles/picture5.png" alt="drawing" width="150"/>

	You may notice a IAM permission error, please ignore the warning and continue with the following step
	
1. Click on **View your container map**

	<img src="../readmeFiles/picture6.png" alt="drawing" width="500"/>
	
1. You will see a map of you Kubernetes environment. Click on **lab-app-deployment**

	<img src="../readmeFiles/picture7.png" alt="drawing" width="200"/>

In the far right of your screen, click on **View dashboard**

You will see the pod performance dashboard and container performance information. Feel free to explore the different options inside Container Insights

Reference: 
<a href="https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Container-Insights-setup-EKS-quickstart.html" target="_blank">https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Container-Insights-setup-EKS-quickstart.html</a>

**LAB END**

### References

Introduction to Kubernetes - AWS Workshop - 
<a href="https://eksworkshop.com/010_introduction" target="_blank">https://eksworkshop.com/010_introduction</a>

Creating an Amazon EKS cluster with eksctl -
<a href="https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html" target="_blank">https://docs.aws.amazon.com/eks/latest/userguide/create-cluster.html</a>

Create a kubeconfig for Amazon EKS - 
<a href="https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html" target="_blank">https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html</a>

Kubernetes cheat sheet - 
<a href="https://kubernetes.io/docs/reference/kubectl/cheatsheet/" target="_blank">https://kubernetes.io/docs/reference/kubectl/cheatsheet/</a>
