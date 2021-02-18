+++ 
title = "Task 3: Create a Task Definition" 
chapter = false 
weight = 3 
+++


A task is a collection of one or more containers that is the smallest deployable unit of your application. A task definition is a JSON document that serves as the blueprint for ECS to know how to deploy and run your tasks.
The console makes it easier to create this definition by exposing all the parameters graphically. In addition, the console creates two dependencies:

- The Amazon CloudWatch log group to store the aggregated logs from the task
- The task execution IAM role that gives Fargate the permissions to run the task

1. In the left navigation pane, choose **Task Definitions**, then click on **Create new task definition**.
 
 	<img src="../images/Picture8.png" alt="drawing" width="500"/>
 
1. Under **Select launch type compatibility**, choose **FARGATE**, click on **Next step**.
 
	<img src="../images/Picture9.png" alt="drawing" width="700"/>
 
1. For Task Definition Name, enter `Fargate-td-[your-name]`. You could use your name or some alias. Please remove the brackets "[ ]".

1. You don't need a select **Task Role** for this task.

1. Under **Task size**, for **Task memory (GB)**, choose `0.5 GB`. For **Task CPU (vCPU)**, choose `0.25 vCPU`.

1. Under **Container Definitions**, click on **Add container**

1. For **Container name** enter `Fargate-image`.

1. For **Image**, paste the image URI you copied in *Task 2*.

1. For **Port mappings** type `80` into Container port.

1. Click on **Add**.

	You will see a warninig "*Failed to retrieve App Mesh information*", you can ignore the warning and proceed with the next step.

1. Scroll to the button of the page and click on **Create**

	<img src="../images/Picture14.png" alt="drawing" width="700"/>