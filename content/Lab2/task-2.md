+++ 
title = "Task 2: Create EKS Cluster" 
chapter = false 
weight = 2 
+++

We will use ekctl to create an EKS Cluster in your lab account, with this command will be also create a dedicated VPC for your cluster

**eksctl** Documentation

<a href="https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html" target="_blank">https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html</a>

<a href="https://eksctl.io/introduction/" target="_blank">https://eksctl.io/introduction/</a>

Create EKS cluster.

1. Copy all the below lines and paste them on the Cloud9 console and hit ```ENTER```

```
eksctl create cluster \
--name eks-lab-cluster \
--region us-east-2 \
--nodegroup-name worknodes-1 \
--node-type t3.medium \
--nodes 3 \
--nodes-min 1 \
--nodes-max 4 \
--managed
```

This command will create a EKS Cluster, including the EKS control plane and 3 worker nodes that will be managed by the control plane.

Cluster creation will take ~15 minutes, continue with the lab's following steps.

