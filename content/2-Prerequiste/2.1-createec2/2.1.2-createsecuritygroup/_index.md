---
title: "Create Security Groups"
date: 2025-05-25
weight: 2
chapter: false
pre: " <b> 2.1.2 </b> "
---

#### Create Security Groups

1. Click **Security groups**.  
   + Click **Create security group**.  

![VPC](/images/2.prerequisite/009_createsecurity.png)

2. In the **Create security group** page:  
   + **Security group name**: Enter a custom name (e.g., **WorkShopSecurity**)  
   + **Description**: Enter a custom description (e.g., **Security group for Work Shop**)  
   + **VPC**: Select the VPC you just created (e.g., **"Vpc-workShop-vpc"**)  

![VPC](/images/2.prerequisite/010_createsecurity.png)

3. Define **Inbound rules**:  
   - Click **Add rule**  
   - Configure SSH access:  
     - **Type**: Select **SSH**  
     - **Source**: Select **My IP** (automatically uses your current public IPv4 address) or **Anywhere** (0.0.0.0/0)

   - Click **Add rule** again  
   - Configure ICMP access:  
     - **Type**: Select **All ICMP - IPv4**  
     - **Source**: Select **Anywhere** (0.0.0.0/0)

   - Click **Add rule** again  
   - Configure HTTP access:  
     - **Type**: Select **HTTP**  
     - **Source**: Select **Anywhere** (0.0.0.0/0)

![VPC](/images/2.prerequisite/011_createsecuritygroup.png)

4. Define **Outbound rules**:  
   - By default, all outbound traffic is allowed  
   - Click **Create security group**  

![VPC](/images/2.prerequisite/012_createsecurity.png)

5. Successfully created  

![VPC](/images/2.prerequisite/013_createsecuritygroup.png)

