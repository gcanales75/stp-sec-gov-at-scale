+++ 
title = "Task 2: Create a QuickSight analysis" 
chapter = false 
weight = 2 
+++

1. Click on **Go to Amazon QuickSight**

	<img src="../images/quicksight-2.png" alt="drawing" width="500"/>

1. Close the **Welcome to QuickSight** window

1. Click on **New analysis**

1. Click **New dataset**

1. Click on the **Athena** data source 

	<img src="../images/athena-dataset.png" alt="drawing" width="400"/>
	
1. Enter the name for your data source, there is a preconfigured Athena database called `teamawesome-merch-sales`

	<img src="../images/athena-dataset-quicksight.png" alt="drawing" width="500"/>

1. Click **Create data source**

1. In the **Choose your table** window, select "**teamawesome-merch-sales**" as the database, and select the table with this prefix```merchandise_sales_xxxxxxx```

	<img src="../images/quicksight-database-schema.png" alt="drawing" width="500"/>

1. Click **Select**

1. In the next window, leave defaults and click **Visualize**

	<img src="../images/visualize.png" alt="drawing" width="500"/>