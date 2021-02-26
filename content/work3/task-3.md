+++ 
title = "Task 3: Create DMS endpoints" 
chapter = false 
weight = 3 
+++

1. We will now create the Oracle DW connection endpoint. From the left panel, click on **Endpoints**

	<img src="../images/click-endpoints.png" alt="drawing" width="300"/>

1. Click **Create endpoint**

1. For Endpoint type, select **Source endpoint**

1. For **Endpoint configuration**, update the information according with the below parameters:

	| Key | Value  |
	|---|---|
	| Endpoint identifier  | OracleDW  |
	| Source engine | oracle |
	| Access to endpoint database | Provide access information manually |
	| Server name | [ *Oracle DW private IP* ] |
	| Port | 1521 |
	| Secure Socket Layer (SSL) mode | none |
	| User name | TICKITDWH |
	| Password | tickit#2020$dw |
	| SID/Service name | xe |

1. Click **Create endpoint**

1. Now we will create the Redshift connection endpoint. Click on **Create endpoint**

1. For Endpoint type, select **Target endpoint**

1. For **Endpoint configuration**, update the information according with the below parameters:

	| Key | Value  |
	|---|---|
	| Endpoint identifier  | Redshift  |
	| Target engine | Amazon Redshift |
	| Access to endpoint database | Provide access information manually |
	| Server name | [ *Redshift cluster endpoint* ] |
	| Port | 5439 |
	| Secure Socket Layer (SSL) mode | none |
	| User name | awsuser |
	| Password | PsoBigData01 |
	| Database name | psobigdata |
	
1. Click **Create endpoint**