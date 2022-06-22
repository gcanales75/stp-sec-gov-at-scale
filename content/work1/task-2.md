+++ 
title = "Task 2: Deploy a Service Catalog product as an end user" 
chapter = false 
weight = 2 
+++

1. Now you will simulate logging as a member of the DeveloperGroup **IAM** group, access the Product from the Portfolio and deploy it. First you need to your lab's AWS account number, in your Console upper right corner you will see your account number, it's a 12 digit number (remove hypens) and copy it on a note pad, you will use it in a later step

	<img src="../images/acc-number.png" alt="drawing" width="400"/>
	
1. In order to login as a member of the Development team, first sign out from your current session.

	<img src="../images/sign-out.png" alt="drawing" width="220"/>
	
1. Click on **Log back in**

1. Under the **Sing in** menu, select **IAM User**

1. Type the **Account ID** (12 digits) you recorded in a previous step

1. Click **Next**

1. In **IAM user name**, type `developer1`

1. In Password, type `StpSecGovAtScale2020!`

1. Click **Sign in**

1. Make sure your selected region is **Oregon**

1. Once you have signed in the AWS Console, go to Services *search box* > Service Catalog

1. From the left pane, go to **Products**

	<img src="../images/sc-products-2.png" alt="drawing" width="250"/>

1. Select your *Product*

	<img src="../images/select-product-2.png" alt="drawing" width="400"/>

1. Click on <img src="../images/launch-product.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="100"/>

1. In the **Provisioned product name** section, you could type a product name or mark the **Generate name** checkbox

1. In the **Parameters section**, type an application name (i.e. application-[your-name-or-alias])

	**NOTE**: Do not leave blank spaces, upper case or special characters are not allowed.

1. Click on <img src="../images/launch-product.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="100"/>

1. Now the deployment of your application resources has started, it will take ~5 minutes to deploy, please wait.

1. The resources deployment will be completed once the **Event** status has changed from **Under change** to **Available**. You may need to click on the refresh botton <img src="../images/refresh-botton.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="30"/> to update the console information

1. In the **Resources** tab you will see the resources created details, feel free to navigate to the different AWS Services and review their configuration

1. Make sure to **sign out** from the *developer1* account, as we will no longer use this IAM user on *Lab 2*

	<img src="../images/dev-signout.png" alt="drawing" width="250"/>

**LAB END**