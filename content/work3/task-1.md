+++ 
title = "Task 1: Create a DMS subnet group" 
chapter = false 
weight = 1 
+++

1. From the AWS console, navigate to the **AWS Database Migration Service** service (Service *search box* -> DMS)
	
1. From your left panel, click on **Subnet groups**

1. Click **Create subnet group**

1. Update the **Subnet group configuration** with the below parameters

	| Key | Value  |
	|---|---|
	|  Name  | UnicornSubnetGroup  |
	|  Description | Unicorn replication instance subnet group |
	|  VPV | vpc-xxxxxxxxxxxx - VPC-Lab-Datawarehouse |

1. In the **Add subnet** panel, select *private-subnet-1* and *private-subnet-2*

	<img src="../images/dms-subnet-group-1.png" alt="drawing" width="700"/>

1. Click **Create subnet group**