---
title: "Preparation Steps"
date: 2025-05-25
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

**To deploy the system as described in the lab, learners need to prepare the following essential components:**

**Preparation Requirements**

1. Create a custom VPC and basic networking components (Subnet, Route Table, Internet Gateway)

2. Launch an EC2 instance using Amazon Linux 2

3. Create and assign a Security Group that allows SSH (port 22) and HTTP (port 80) access

4. Install a Web Server and CloudWatch Agent via User Data

5. Create an IAM Role and attach the necessary permissions to allow EC2 to send metrics/logs to CloudWatch

**To learn how to create EC2 instances and a VPC with public/private subnets, you can refer to the following labs:**
  - [Introduction to Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Working with Amazon VPC](https://000003.awsstudygroup.com/vi/)

### Content
  - [Preparing VPC and EC2 Instance](2.1-createec2/)
  - [Setting up alert and event response using CloudWatch Alarm, SNS, and Lambda](2.2-createcloudwatch-alarm/)
