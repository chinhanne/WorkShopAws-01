---
title : "Tạo Security groups"
date: 2025-05-25 
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

#### Tạo Security groups

1. Click **Security groups**.
  + Click **Create security group**.

![VPC](/images/2.prerequisite/009_createsecurity.png)

2. Trong **Create security group**.
   + **Security group name** đặt tên tùy chỉnh (Ví dụ: **WorkShopSecurity**)
   + **Description** đặt mô tả tùy chỉnh (Ví dụ: **Security group for Work Shop**)
   + **VPC** chọn VPC vừa tạo **"Vpc-workShop-vpc"**

![VPC](/images/2.prerequisite/010_createsecurity.png)

3. Xác định **Inbound rules** 
    - Chọn **Add rule**
    - Cấu hình truy cập SSH
      - **Type**: Chọn SSH
      - **Source**: Chọn **My IP** (tự động sử dụng địa chỉ IPv4 công khai hiện tại của bạn) hoặc **Anywhere** (0.0.0.0/0)

    - Chọn **Add rule** tiếp tục
    - Cấu hình truy cập ICMP:
      - **Type**: Chọn **All ICMP - IPv4**
      - **Source**: Chọn **Anywhere** (0.0.0.0/0)

    - Chọn **Add rule** tiếp tục
    - Cấu hình truy cập HTTP:
      - **Type**: Chọn **HTTP**
      - **Source**: Chọn **Anywhere** (0.0.0.0/0)

![VPC](/images/2.prerequisite/011_createsecuritygroup.png)

4. Xác định **Outound rules** 
    - Theo mặc định, tất cả lưu lượng truy cập đi đều được phép
    - Chọn Create security group
      
![VPC](/images/2.prerequisite/012_createsecurity.png)

5. Tạo thành công

![VPC](/images/2.prerequisite/013_createsecuritygroup.png)

