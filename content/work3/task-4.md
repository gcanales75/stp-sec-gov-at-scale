+++ 
title = "Task 4: Create a DMS migration task" 
chapter = false 
weight = 4 
+++

1. Now we are going to create a Task to migrate your data. Click on **Database migration tasks**

	<img src="../images/create-migratioon-task.png" alt="drawing" width="250"/>

1. Click **Create task**

1. Update the **Task configuration** with the below parameters:

	| Key | Value  |
	|---|---|
	| Task identifier  | Oracle-to-Redshift  |
	| Replication instance | teamawesome-replication-instance |
	| Source databse endpoint | oracledw |
	| Target databse endpoint | redshift |
	| Migration type | Migrate Existing Data |

1. In the below **Task settings** section, for the Target table preparation mode, select **Do Nothing** (Note: We don’t need this step, as we have already used the Schema Conversion Tool to convert the schema to Redshift)

1. Under the **Table Mappings** section, click on **Add new selection rule**

	<img src="../images/add-selection-rule.png" alt="drawing" width="700"/>

1. In the selection rule configuration, for **Schema**, select **Enter a schema**, and for the **Schema name** type `TICKITDWH`

1. Finally, click the **Create Task** button at the bottom of the page.

1. This will return you to the DMS Task Listing—you should see your task change status from **Creating** to **Load complete**. This task will take a couple of minutes.

1. Once the task has finished, click on the task identifier

	<img src="../images/dms-1.png" alt="drawing" width="600"/>

1. Click on the **Table statistics** tab to see the tables and rows migrated from Oracle to Redshift

	<img src="../images/dms-2.png" alt="drawing" width="800"/>