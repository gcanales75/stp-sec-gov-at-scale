+++ 
title = "Task 5: Create an ECS service using Fargate" 
chapter = false 
weight = 5 
+++

A service in ECS using Fargate serves a similar purpose to an Auto Scaling group in EC2. It ensures that the needed number of tasks are running both for scaling as well as spreading the tasks over multiple Availability Zones for high availability. A service creates and destroys tasks as part of its role and can optionally add or remove them from an Application Load Balancer as targets as it does so.

1. Open the ECS console. Service *search box* > ECS

1. In the left navigation pane, choose **Task Definitions**.

1. Mark the check box next to the Task definition you created in *Task 3*, click on **Actions**, and then click on **Create Service**.
 
	<img src="../images/Picture48.png" alt="drawing" width="600"/>

1. For Launch Type, select `Fargate`.

1. For Service name, enter `Lab1-Fargate`.

1. For Number of tasks, enter `1`.
 
1. Click on **Next step**.

1. Choose the correct VPC (10.100.0.0/16, VPC-Lab1). Under Subnets, select `private-subnet-1` and `private-subnet-2`.

	<img src="../images/Picture49.png" alt="drawing" width="400"/>

1. For Security Groups, click **Edit**.
 
1. Choose **Select existing security group** and select the **Container-SG** security group. 

	<img src="../images/Picture50.png" alt="drawing" width="600"/>

1. Click **Save**.

1. In **Auto-assign public IP** select **DISABLED**
 
1. Under **Load balancing**, choose **Application Load Balancer** 

1. Select **Fargate-LB** in **Load Balancer Name**
 
1. Under **Container to load balance**, click on **Add to load balancer**
 
1. For **Target group name**, choose `Lab1-TG`.

	<img src="../images/Picture52.png" alt="drawing" width="500"/>

1. Click **Next step**

1. Leave defaults and click on **Next step**

1. Click on **Create Service**.

1. Click on **View Service**

	At this point, you have a running web service service using Fargate. You can now explore what you have running and how it works. You can also scale up to two tasks which will be deployed across two Availability Zones.

	In the Service page you could find details about the associated load balancer, tasks, events, metrics, and logs:
 
	Scale the service from one task to multiple tasks:

1. Click on **Update**.
 
1. For **Number of tasks**, enter `2`.
 
1. Click on **Next step**

1. Click on **Next step**

1. Click on **Next step**

1. Click on **Update Service**.

1. Click on **View Service**

1. Click on the **Tasks** tab and you will see that another task is in *Provisioning* status.
 
1. Now click on the **Details** tab, click on the Target Group `Lab1-TB` link to be redirected to the **Taget Group** configuration page. click on the **Targets** tab. You will see the IP address registered for the *Task* you just deployed spread across two different availability zones.

1. Paste on a new browser window the "DNS name" you copied at the end of Task 4, you will see the website page. 

	<img src="../images/Picture53.png" alt="drawing" width="600"/>

1. You could refresh the browser and see the **Task ID** updated, this means the the Application Load Balancer is distribuiting traffic across your **Fargate** tasks.

**LAB END**
