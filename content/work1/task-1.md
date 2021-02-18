+++ 
title = "Task 1: Create an ECS cluster" 
chapter = false 
weight = 1 
+++

An ECS cluster is a logical construct for running groups of containers known as tasks. Clusters can also be used to segregate different environments or teams from each other. In the traditional EC2 launch mode, there are specific EC2 instances associated with and managed by each ECS cluster, but this is transparent to the customer with Fargate.

Make sure that your AWS console session is using `Ohio` region.



<img src="../images/Picture2.png" alt="drawing" width="400"/>
 
1. Open the ECS console. Service *search box* > ECS
 
	![image1](../images/service-ecs.png?width=600px)

1. From the left pane choose **Clusters**, then click on **Create Cluster**.
 
	<img src="../images/Picture4.png" alt="drawing" width="500"/>

1. Choose **Networking only**, click on **Next step**.
 
	<img src="../images/Picture5.png" alt="drawing" width="500"/>
 
1. For Cluster name, enter `Fargate`. For the purpose of this Lab, there is no need to create a new VPC. 
 
	<img src="../images/Picture6.png" alt="drawing" width="500"/>
 	
1. You will get the *ECS Cluster Fargate successfully created* message

	<img src="../images/ok-cluster.png" alt="drawing" width="700"/>

	Note: In case you get this error message...
		
	<img src="../images/error-fargate.png" alt="drawing" width="700"/>
	
	... click on **Back** and in the next page click **Cancel**
	
	<img src="../images/click-cancel.png" alt="drawing" width="200"/>
	
	Repeat the instructions to create the Fargate Cluster starting from *step 2*.

	
1. Click on **View Cluster**

	Your cluster should look similar to:
 
 	<img src="../images/Picture54.png" alt="drawing" width="600"/>