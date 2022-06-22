+++ 
title = "Task 1: Create a Service Catalog product and portfolio" 
chapter = false 
weight = 1 
+++

1. Login to your AWS console using the instructions provided by the instructor

1. Go to Services *search box* > Service Catalog

	<img src="../images/lookup-service.png" alt="drawing" width="600"/>

1. From the left pane, under **Administration**, click on **Product list**

	<img src="../images/sc-products.png" alt="drawing" width="250"/>

1. To create our *product*, we will use a simple CloudFormation template which include the following services:

	<img src="../images/secgov-sc.png" alt="drawing" width="700"/>

1. Click <img src="../images/upload-product.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="alt text" width="120"/>

1. In **Product Name** type: `my-awesome-product`

1. In **Owner** type your name or an alias

1. In **Version details** select **Use a CloudFormation template**

1. In **Use a CloudFormation template** text box, copy and paste the following URL:

	```
	https://ee-assets-prod-us-east-1.s3.us-east-1.amazonaws.com/modules/6dc73ef66a2d4cf79e247e72cfa4006d/v1/CF-service-catalog-deploy.json
	```
	
	Note: This CloudFormation template describes the resources and configurations that will be created as part of the Service Catalog product deployment
	
1. In **Version title**, type `v1`

1. Click <img src="../images/click-create-product.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="120"/>

1. You must see this message

	<img src="../images/success-product.png" alt="drawing" width="300"/>

1. Now you need to create a *Portfolio* to share with your end users and add your newly created *Product*

1. From the left pane, click on **Portfolios**

1. Click on <img src="../images/create-portfolio.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="110"/>

1. In **Portfolio Name**, type `my-awesome-portfolio`

1. In **Owner**, type your name or alias

1. Click on <img src="../images/click-create.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="60"/>

1. Click on the newly created Portfolio

1. Now you will add the *Product* to the *Portfolio*, click on the **Products** tab

1. Click on <img src="../images/add-product.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="120"/>

1. Select your *Product*

	<img src="../images/select-product.png" alt="drawing" width="400"/>

1. Click on <img src="../images/add-product-2.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="170"/>

1. Your *Product* has been added to your *Portfolio*, now you need to add users to consume your *Product*

1. Click on the **Groups, roles, and users** tab

1. Click on <img src="../images/add-group.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="155"/>

1. Select the **DeveloperGroup**, which as been pre-created in the lab environment

	<img src="../images/select-group.png" alt="drawing" width="380"/>

1. Click on <img src="../images/add-access.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="85"/>

1. In the next steps you will provide the IAM permissions to the *Portfolio* so it could have all the required permissions to deploy all the services described in your *Product*, you will do this by creating a **Constraint** and assign it an **IAM Role**. Click on the **Constraints** tab.

1. Click on <img src="../images/create-constraint.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="110"/>

1. You will see the **Create constraint** configuration

1. In **Product**, select your *Product*

1. In **Constraint type**, select **Launch**

1. Scroll down to the **Launch constraint** section

1. In **Method**, select **Select IAM role**

1. In **IAM role**, select **Sc-launchConstraint-role** from the displayed options

1. Click on <img src="../images/click-create.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="60"/>

	Note: This IAM role has been pre-created in this lab environment, feel free to navigate to Services > IAM >Roles > Sc-launchConstraint-role to see the **Permissions policies** attached