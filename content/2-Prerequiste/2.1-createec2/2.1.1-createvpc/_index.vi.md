---
title : "Tạo VPC "
date: 2025-05-25 
weight : 1 
chapter : false
pre : " <b> 2.1.1 </b> "
---


#### Tạo VPC **Lab VPC**
1. Truy cập [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Click **Your VPC**.
  + Click **Create VPC**.

![VPC](/images/2.prerequisite/001_createvpc.png)

2. Tại trang **Create VPC**.
  + Tại mục **Resources to create** chọn : **VPC and more**.
  + Tại mục **Name tag** điền **Vpc-workShop**.
  + Tại mục **IPv4 CIDR** điền : **10.0.0.0/16**.


![VPC](/images/2.prerequisite/002_createvpc.png)
  + Tại mục **VPC endpoints** chọn : **None**.
![VPC](/images/2.prerequisite/003-createvpc.png)
  + Click **Create VPC**.
![VPC](/images/2.prerequisite/004_createvpc.png)

3. Sau khi tạo VPC Tại **Subnets**.
![VPC](/images/2.prerequisite/006_createsubnet.png)

+ Chọn **Vpc-workShop-subnet-public1-ap-southeast-1a**
+ Chọn **Action**
+ Chọn **Edit subnet settings**
![VPC](/images/2.prerequisite/007_editsubnet.png)

+ Trong **Edit subnet settings**
+ Check vào ô  **Enable auto-assign public IPv4 address**
+ Chọn **Save** để lưu lại


![VPC](/images/2.prerequisite/008_editsubnet.png)


