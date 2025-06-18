---
title: "Prepare VPC and EC2"
date: 2025-05-25
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

In this step, we will create a VPC with both public and private subnets. Then, we will launch an EC2 instance named **OperationalExcellence-Monitor-Instance** in the public subnet.  
The overall architecture after completing this step will look like the following:

![VPC](/images/arc-05.png)

To learn how to create EC2 instances and a VPC with public/private subnets, you can refer to the following labs:
  - [Introduction to Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Working with Amazon VPC](https://000003.awsstudygroup.com/vi/)

### Content
  - [Create VPC](2.1.1-createvpc/)
  - [Create Security Group](2.1.2-createsecuritygroup/)
  - [Create IAM Role](2.1.3-createiamrole/)
  - [Create EC2 Instance](2.1.4-createec2/)
