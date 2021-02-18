+++ 
title = "Task 6: ALB Ingress Controller on Amazon EKS" 
chapter = false 
weight = 6
+++

To ensure the ingress objects make use of the Application Load Balancer (ALB) service to route HTTP and HTTPS traffic to kubernetes pods within the EKS cluster, we will execute the following shell script. Feel free to explore the content of the file ```albIngressController.sh``` which is in the lab's working directory.

1. Run this commands to execute the shell script:

	```
	cd ~/environment/stpEksLabRepo/
	chmod +x ./albIngressController.sh 
	./albIngressController.sh
	```

1. Confirm that the ALB Ingress Controller is running with the following command. 

	```
	kubectl get pods -n kube-system
	```

	Expected output:

	```
	alb-ingress-controller-55b5bbcb5b-bc8q9   1/1     Running   0          56s
	```

Reference: <a href="https://docs.aws.amazon.com/eks/latest/userguide/alb-ingress.html" target="_blank">https://docs.aws.amazon.com/eks/latest/userguide/alb-ingress.html</a>
