+++ 
title = "Task 1: Enable AWS Config" 
chapter = false 
weight = 1 
+++

1. Sign in to your Lab's AWS Console following the instructions provided

1. Make sure your selected region is **Oregon**

1. Go to Services *search box* > Config

	<img src="../images/service-config-2.png" alt="drawing" width="650"/>

1. Click <img src="../images/get-started-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. In the **Settings** page, leave defaults and click on <img src="../images/next-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="55"/>

1. In the **Rules** page, leave defaults and click on <img src="../images/next-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="55"/>

1. In the **Review** page, click on <img src="../images/confirm-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="65"/>

1. AWS Config will start, you can close the "Welcome to AWS Config" window.

1. Now we will create our first Config rule, it will check whether any security groups with inbound 0.0.0.0/0 have TCP or UDP ports accessible. The rule is NON_COMPLIANT when a security group with inbound 0.0.0.0/0 has a port accessible which is not specified in the rule parameters. In your left panel, click on **Rules**

	<img src="../images/config-rules.png" alt="drawing" width="200"/>

1. Click on <img src="../images/add-rule-2.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. In the **AWS Managed Rules** search box, type: `vpc-sg-open-only-to-authorized-ports`

1. Select the managed rule and click <img src="../images/next-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="55"/>

1. In the **Details** page, in the **Trigger** section, select **Tags** under **Scope of changes**.

1. In Resources by tag, type `Compliance` in the *Tag Key* box, and `Prod` in the *Tag value* box

	<img src="../images/resource-by-tag.png" alt="drawing" width="500"/>

1. Under **Parameters**, you will authorize only port `80` to be open to the internet

	<img src="../images/allow-port-80-1.png" alt="drawing" width="600"/>

1. Click on <img src="../images/next-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="55"/>

1. In the **Review and create** page click <img src="../images/add-rule-2.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>
	
1. Click on the Rule you just created, under **Resources in scope**, select All. after a couple of minutes you will see the a security group in **Compliant** status
	
	<img src="../images/compliant.png" alt="drawing" width="250"/>
	
	NOTE: you may need to refresh the displayed information on the rule console, click on the refresh botton <img src="../images/refresh-botton.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="30"/>
	
1. Now we will make a change on the security group inbound rule, and open port 22 to the internet, so this resource change its status to **Noncompliant**

1. Go to Services *search box* > VPC

1. On the left pane, under the **Security** section, click on **Security Groups**

1. In the Security Group search box, type `sc-web-secgroup-`, and click on the lookup result

	<img src="../images/sg-lookup-1.png" alt="drawing" width="370"/>
	
	**Note**: You will notice this **Security Group** was created as part of your **Service Catalog** application deployment

1. In the below panel, click on **Inbound rules**

	<img src="../images/click-inbound.png" alt="drawing" width="370"/>

1. Click on <img src="../images/edit-inbound.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="100"/>

1. Click on <img src="../images/add-rule-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="65"/>

1. You will edit the second rule line just added, in the inbound **Type**, select **SSH** and in **Source** select **Anywhere**

	<img src="../images/add-ssh.png" alt="drawing" width="700"/>

1. Click <img src="../images/save-rules.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. Now return to Config console. Services *search box* > Config

1. On the left pane, click on **Rules**

1. Click on the rule you previously created, after a minute the rule **Resource compliance status** will change from **Compliant** to **Noncompliant**

	NOTE: you may need to refresh the displayed information on the rule console, click on the refresh botton <img src="../images/refresh-botton.png" alt="drawing" width="30"/>

	<img src="../images/noncompliant-sg.png" alt="drawing" width="900"/>
