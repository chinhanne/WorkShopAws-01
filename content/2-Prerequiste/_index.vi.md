---
title : "Các bước chuẩn bị"
date: 2025-05-25 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

<!-- {{% notice info %}}
Bạn cần tạo sẵn 1 Linux instance thuộc public subnet và 1 Window instance thuộc private subnet để thực hiện bài thực hành này.
{{% /notice %}} -->
**Để triển khai hệ thống theo bài lab, người học cần chuẩn bị các thành phần cơ bản sau:**

**Nội dung cần chuẩn bị**

1. Tạo VPC riêng và các thành phần mạng cơ bản (Subnet, Route Table, Internet Gateway)

2. Tạo EC2 instance sử dụng Amazon Linux 2

3. Tạo và gán Security Group cho phép truy cập SSH (22) và HTTP (80)

4. Cài đặt Web Server và CloudWatch Agent qua User Data

5. Tạo IAM Role và gán quyền cho EC2 gửi metric/logs lên CloudWatch

**Để tìm hiểu cách tạo các EC2 instance và VPC với public/private subnet các bạn có thể tham khảo bài lab :**
  - [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Làm việc với Amazon VPC](https://000003.awsstudygroup.com/vi/)



### Nội dung
  - [Chuẩn bị VPC và EC2 Instance](2.1-createec2/)
  - [Thiết lập hệ thống cảnh báo và xử lý sự kiện bằng CloudWatch Alarm, SNS và Lambda](2.2-createcloudwatch-alarm/)

  
