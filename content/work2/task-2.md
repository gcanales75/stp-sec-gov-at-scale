+++ 
title = "Task 2. Create an AWS Config rule with automated remediation" 
chapter = false 
weight = 2 
+++

In this task you will create a new Config rule that will check whether your EC2 instances are of the specified instance types and apply a remediation action in case of rule non compliant status.

1. In your left panel, click on **Rules**

	<img src="../images/config-rules.png" alt="drawing" width="200"/>

1. Click on <img src="../images/add-rule-2.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. In the **AWS Manager Rules** search box, type: `desired-instance-type`

1. Select the managed rule and click <img src="../images/next-1.png" alt="drawing" width="50"/>

	<img src="../images/select-rule.png" alt="drawing" width="520"/>
	
1. Under the Trigger section -> Scope of changes, select **Tags**. In Resources by tag, type `Compliance` as the **Tag key**, and in **Value tag** type `Prod`

	<img src="../images/config-rule-instance-2.png" alt="drawing" width="700"/>

1. In the Parameters section, type `t3.small` as the value for the Key **instanceType**

	<img src="../images/config-rule-instance-3.png" alt="drawing" width="520"/>

1. Click on <img src="../images/next-1.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="50"/>

1. Click on <img src="../images/add-rule-2.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. Your rule will start evaluating resources compliance

1. Previous to enable an automated remediation action, you need to create an IAM role and assign it to the Config rule to be able to execute the instance resize remediation action. Go to Services *search box* > IAM

1. On the left pane, click on **Roles**

1. Click on <img src="../images/create-role.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. Under **Choose a use case**, click on **Systems Manager**

1. Under **Select your use case**, select **Systems Manager**

1. Click on <img src="../images/next-permissions.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="100"/>

1. In the Filter policies search box type `AmazonEC2FullAccess`, and click the checkbox next to the policy

	<img src="../images/ec2-full.png" alt="drawing" width="1000"/>

1. Click <img src="../images/next-tags.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/>

1. Click <img src="../images/next-review.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="80"/>

1. In **Role name*** type: `config-resize-instance-role`

1. Click <img src="../images/create-role.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="75"/>

1. You will see **The role config-resize-instance-role has been created.** at the top of the screen. Click on the *role name*

1. Copy the **Role ARN** (i.e. arn:aws:iam::xxxxxxxxxxx:role/config-resize-instance-role) and paste it in a note pad, you will use it in a later step.

1. Now return to Config service. Services *search box* > Config

1. On the left pane, click on **Rules**

1. Look for the instance resize rule, and click on the rule

	<img src="../images/click-on-rule-2.png" alt="drawing" width="500"/>

1. Click <img src="../images/click-on-actions.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="70"/> and select **Manage remediation**

1. In **Select remediation method** section, select **Automatic remediation**

1. In **Remediation action details**, section, expand the drop-down menu and select **AWS-ResizeInstance**

	<img src="../images/choose-remediation-action-2.png" alt="drawing" width="800"/>
	
1. In **Resource ID parameter** select **InstanceId**

	<img src="../images/resourceid-param.png" alt="drawing" width="650"/>
	
1. In the **Parameters** section, fill the  *InstanceType* and  *AutomationAssumeRole* ** parameters 

	<img src="../images/remediation-params.png" alt="drawing" width="800"/>
	
	** Paste the role ARN you copied in step 22

1. Click <img src="../images/save-changes.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="80"/>

1. This automatic remediation action will start to evaluate EC2 resources configurations. 

1. Now you will change the instance type so you could test the remediation action you just configured. Go to the EC2 service. Services *search box* > EC2

1. On the left pane, click on **Instances**

	<img src="../images/click-on-instances.png" alt="drawing" width="200"/>

1. Look for the instance with the prefix "sc-web-" and select the checkbox next to it

	<img src="../images/select-instance.png" alt="drawing" width="370"/>

1. Click on <img src="../images/instance-state.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="100"/> and select **Stop instance** and confirm your action.

	<img src="../images/stop-instance.png" alt="drawing" width="150"/>

1. Wait a few seconds until the instance state changes to **Stopped**

1. Change the instance type:

	1. Actions
	1. Instance settings
	1. Change instance type

	<img src="../images/change-instance-type-1.png" alt="drawing" width="470"/>

1. In the **Change instance type** window, below **Instance type**, select `t3.xlarge`

	<img src="../images/change-instance-type-2.png" alt="drawing" width="650"/>

1. Click <img src="../images/click-apply.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="50"/>

1. Now start the EC2 instance, click Instance state -> Start instance

	<img src="../images/start-instance.png" alt="drawing" width="150"/>

1. Copy the instance ID, we will use it in a later step

	<img src="../images/copy-instance-id.png" alt="drawing" width="700"/>

1. This change will trigger the Config rule remediation action, it will take a couple of minutes for the rule to start changing the instance status automatically, from shutting down, to resize back to `t3.small` and finally start the instance again, so it can enter in a **compliant** state according to the rule we created. 

1. Return to Config console. Go to Services *search box* > Config

1. Now we will use another Config feature, the capacity to keep track of changes in AWS resource.

	> AWS Config records details of changes to your AWS resources to provide you with a configuration history. You can use the AWS Management Console, API, or CLI to obtain details of what a resource’s configuration looked like at any point in the past. AWS Config will also automatically deliver a configuration history file to the Amazon S3 bucket you specify.

1. From the left pane, click on **Resources**

	<img src="../images/resources.png" alt="drawing" width="170"/>

1. In the Resources section paste the EC2 instance ID into the search box, it will display the instance ID below the Resource identifier section. Click on the instance ID.

	<img src="../images/resourceid-config.png" alt="drawing" width="520"/>
	
1. Click <img src="../images/resource-timeline.png" style="border: 0; display:inline; margin: 0 2px; box-shadow: none" alt="drawing" width="100"/>

1. On the far right of the screen you will find an **Event type** filter. Display the options and select *Configuration events*, feel free to explore the events displayed, expand each one of them and explore the EC2 instance change details. After that, select *Compliance events*, explore the displayed events as well.
	
#### LAB END
