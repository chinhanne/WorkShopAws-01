---
title: "Create VPC"
date: 2025-05-25
weight: 1
chapter: false
pre: " <b> 2.1.1 </b> "
---

#### Create VPC **Lab VPC**

1. Go to the [VPC Management Console](https://console.aws.amazon.com/vpc/home)  
   + Click **Your VPCs**.  
   + Click **Create VPC**.  

![VPC](/images/2.prerequisite/001_createvpc.png)

2. On the **Create VPC** page:  
   + Under **Resources to create**, select: **VPC and more**.  
   + In **Name tag**, enter: **Vpc-workShop**.  
   + In **IPv4 CIDR**, enter: **10.0.0.0/16**.  

![VPC](/images/2.prerequisite/002_createvpc.png)

   + Under **VPC endpoints**, choose: **None**.  

![VPC](/images/2.prerequisite/003-createvpc.png)

   + Click **Create VPC**.  

![VPC](/images/2.prerequisite/004_createvpc.png)

3. After creating the VPC, go to **Subnets**:  

![VPC](/images/2.prerequisite/006_createsubnet.png)  

+ Select **Vpc-workShop-subnet-public1-ap-southeast-1a**  
+ Click **Actions**  
+ Click **Edit subnet settings**  

![VPC](/images/2.prerequisite/007_editsubnet.png)

+ In the **Edit subnet settings** screen:  
+ Check the box **Enable auto-assign public IPv4 address**  
+ Click **Save** to apply the changes  

![VPC](/images/2.prerequisite/008_editsubnet.png)

