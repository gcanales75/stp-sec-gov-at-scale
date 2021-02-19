+++ 
title = "Task 4: Create an ECR repository and push the Docker image" 
chapter = false 
weight = 4 
+++

Now we will create a container registry using the ECR service to store our Docker image, and then we will push the image to that repo.

1. Create an ECR repository named "containers-lab"

	```
	aws ecr create-repository --repository-name containers-lab --region us-east-2
	```

1. We will set some environment variables to help us throughout the lab. Let's export the new ECR repo URI, account number and default region in our environment variables with the below commands.

	```
	export ACCOUNT_NUMBER=`aws sts get-caller-identity --query 'Account' --output text`
	export ECR_REPO_URI=`aws ecr describe-repositories --repository-names containers-lab --region us-east-2 --query 'repositories[*].repositoryUri' --output text`
	export AWS_DEFAULT_REGION=us-east-2
	```

1. Let's test our environment variables

	```
	echo $ACCOUNT_NUMBER
	echo $ECR_REPO_URI
	```

1. Before we could push our Docker image to our ECR repo we need to authenticate. Run the below command:

	```sh
	$(aws ecr get-login --registry-ids $ACCOUNT_NUMBER --no-include-email --region us-east-2)
	```

	We must see this output: ```Login Succeeded```

1. Tag the image for identification

	```
	docker tag stp/website:latest $ECR_REPO_URI:v1
	```

1. Now push the Docker image to our ECR repo

	```
	docker push $ECR_REPO_URI:v1
	```

	You must see a similar output:

	<img src="../readmeFiles/skitch.18.png" alt="drawing" width="600"/>
