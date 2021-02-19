+++ 
title = "Task 1: Prepare your Cloud9 environment" 
chapter = false 
weight = 1 
+++

The first steps in this lab will require you to prepare your Cloud9 workspace with the proper IAM permissions attaching an instance role to it.

1. Go to the EC2 console. Service *search box* > EC2

	<img src="../readmeFiles/service-ec2-1.png" alt="drawing" width="600"/>
	
1. In the EC2 dashboard, click on “Instances”:

	<img src="../readmeFiles/clickoninstances.png" alt="drawing" width="700"/>

1. Mark the checkbox next to the Cloud9 workspace instance:

	<img src="../readmeFiles/click-on-cloud9-instance.png" alt="drawing" width="400"/>

1. Attach an IAM instance role the Cloud9 instance. Click  on **Actions** > **Security** > **Modify IAM Role**

	<img src="../readmeFiles/change-iam-role.png" alt="drawing" width="350"/>

1. Select the IAM Role

	1. Click on the small triangule to display the options

	1. Click on **Cloud9InstanceProfile**

	<img src="../readmeFiles/set-cloud9-instance-profile.png" alt="drawing" width="600"/>

1. Click on **Save**

1. Most of the lab's activity will be performed using the **Cloud9** service. Let’s open our Cloud9 workspace. Go to the Cloud9 service. Service *search box* > Cloud9

1. Open your Cloud9 IDE

	<img src="../readmeFiles/skitch.7.png" alt="drawing" width="500"/>

1. You need to disable the temporary Cloud9 credentials to use the IAM instance profile permissions (follow the steps described in below image).

	1. Click on **Preferences**

	1. Click on **AWS Settings**

	1. Disable **AWS managed temporary credentials**

		**(MAKE SURE THE SWITCH HAS TURNED TO RED)**

	1. Close “Preferences” window

	<img src="../readmeFiles/disable-creds.png" alt="drawing" width="1000"/>

1. Close the bottom panel

	<img src="../readmeFiles/skitch.9.png" alt="drawing" width="800"/>

1. Close the *Welcome* and *AWS Toolkit - Quick Start* tabs

	<img src="../readmeFiles/close-windows.png" alt="drawing" width="700"/>

1. Open a new terminal window

	<img src="../readmeFiles/skitch.11.png" alt="drawing" width="500"/>

1. You will execute a shell script that will prepare your Cloud9 environment to perform you lab tasks. Run the below commands to execute the script:

```sh
cd stpEksLabRepo/
chmod +x ./ekssetup.sh 
./ekssetup.sh
```

Wait a minute to complete the script execution