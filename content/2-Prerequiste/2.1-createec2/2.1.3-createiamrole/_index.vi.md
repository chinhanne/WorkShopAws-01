---
title : "Tạo IAM role"
date: 2025-05-25 
weight : 3
chapter : false
pre : " <b> 2.1.3 </b> "
---

#### Tạo IAM role

1. Truy cập vào AWS Management Console:
   - Tìm kiếm "IAM" trong thanh tìm kiếm
   - Click vào "Roles" để mở dashboard

![VPC](/images/2.prerequisite/createrole.png)

   - Chọn **Create Role** để tạo role mới

![VPC](/images/2.prerequisite/014_createrole.png)

   - Chọn **AWS Service** 
   - Trong "Use case" chọn **EC2**
   - Chọn **Next** để tiếp tục
![VPC](/images/2.prerequisite/015_createrole.png)

   - Tìm kiếm "CloudWatchAgentServerPolicy" và chọn vào quyền **CloudWatchAgentServerPolicy**
   - **Next** để tiếp tục

![VPC](/images/2.prerequisite/016_createrole.png)

   - Đặt tên cho role **EC2CloudWatchAgentRole**
   - Xem lại các thông tin
   - Chọn **Create role** để tạo role

![VPC](/images/2.prerequisite/017_createrole.png)
![VPC](/images/2.prerequisite/018_createrole.png)

   - Trở lại "Dashboard" chọn **Roles**
   - Tìm kiếm "EC2CloudWatchAgentRole" (Nếu có thì đã tạo thành công)
![VPC](/images/2.prerequisite/019_createrole.png)

