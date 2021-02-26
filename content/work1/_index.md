+++
title = "Service Catalog"
date = 2021-02-17T17:04:42-06:00
weight = 2
chapter = false
pre = "<b>1. </b>"
+++

**AWS Service Catalog** enables organizations to create and manage catalogs of IT services that are approved for use on AWS. These IT services can include everything from virtual machine (VM) images, servers, software, and databases to complete multi-tier application architectures. 

You can use AWS Service Catalog to create preconfigured products that your developers can launch. In a large organization, it’s typical for a cross-functional team like a Cloud Center of Excellence (CCoE) to maintain the catalog for the organization. An AWS Service Catalog product can contain one or more AWS resources. Many customers use AWS Service Catalog to restrict access to resources, such as AWS APIs, using a launch constraint. Launch constraints allow an AWS Service Catalog end user to launch an AWS Service Catalog product without requiring elevated permissions to AWS resources.

You can centrally manage commonly deployed IT services to achieve consistent governance and meet your compliance requirements, while enabling users to deploy only the approved IT services they need. The IT services are grouped as products, and the products are organized in portfolios. 

In this lab, you will perform this activities:

* Create **AWS Service Catalog** portfolio and products
* Share a portfolio with users and groups
* Consume an **AWS Service Catalog** product from the user perspective