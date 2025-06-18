---
title : "Chuẩn bị VPC và EC2 Instance"
date: 2025-05-25 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

Trong bước này, chúng ta sẽ cần tạo một VPC có 2 subnet public / private. Sau đó tạo 1 EC2 OperationalExcellence-Monitor-Instance nằm trong public subnet.
Tổng quan kiến trúc sau khi các bạn hoàn tất bước này sẽ như sau:

![VPC](/images/arc-05.png)

Để tìm hiểu cách tạo các EC2 instance và VPC với public/private subnet các bạn có thể tham khảo bài lab :
  - [Giới thiệu về Amazon EC2](https://000004.awsstudygroup.com/vi/)
  - [Làm việc với Amazon VPC](https://000003.awsstudygroup.com/vi/) 


### Nội dung
  - [Tạo VPC](2.1.1-createvpc/)
  - [Tạo Security groups](2.1.2-createsecuritygroup/)
  - [Tạo IAM role](2.1.3-createiamrole/)
  - [Tạo EC2 Instance](2.1.4-createec2/)

