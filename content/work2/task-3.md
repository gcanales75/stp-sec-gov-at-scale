+++ 
title = "Task 3: Create Docker image" 
chapter = false 
weight = 3
+++

1. Open a new terminal window.

	<img src="../readmeFiles/skitch.14.png" alt="drawing" width="700"/>

	Now we will create the Docker image we will use in our project

1. Change directory (cd) to the Docker project working directory

	```sh
	cd stpEksLabRepo/website/
	```

1. This folder contains the website and Dockerfile source code we will use to deploy a containarized application in our EKS cluster.

	```
	cat Dockerfile
	```

1. Run this command to create the Docker image

	```
	docker build -t stp/website .
	```

1. Run the container locally

	```
	docker run -P -d -p 8080:80 stp/website
	```

	You can preview a running application in Cloud9, let's look at it:

1. Go to Preview -> Preview Running Application

	<img src="../readmeFiles/skitch.15.png" alt="drawing" width="600"/>

1. You must see the the webpage running in the right panel. You can close now the preview panel:

	<img src="../readmeFiles/local-docker.png" alt="drawing" width="900"/>

	Now you will stop the running container.

1. List the containers running

	```
	docker container ps
	```

	<img src="../readmeFiles/skitch_17.png" alt="drawing" width="800"/>

1. Please take note of the Container ID number, we will stop it in the next step.

1. Stop the container

	```
	docker container stop <CONTAINER ID>
	```
