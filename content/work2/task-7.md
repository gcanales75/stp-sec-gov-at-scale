+++ 
title = "Task 7: Set a new Kubernetes namespace for our lab application" 
chapter = false 
weight = 7 
+++

A Kubernetes namespace provides the scope for Pods, Services, and Deployments in the cluster. We will create a new context for the kubectl client to work in a dedicated namespace.

1. We will execute file ```labNamespace.sh``` which is also in the lab's working directory.

	```sh
	cd ~/environment/stpEksLabRepo/
	chmod +x ./labNamespace.sh
	./labNamespace.sh
	```

1. Verify your kubectl client is working on your dedicated environment, execute the following command:

	```
	kubectl config current-context
	```

	You must see this output:

	<img src="../readmeFiles/picture3.png" alt="drawing" width="600"/>

From now on, all requests we make to the Kubernetes cluster from the command line are scoped to the `containers-lab` namespace.
