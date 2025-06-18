---
title : "Mở rộng với CloudFormation Template"
date: 2025-05-25 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---


## Phần 2: Mở rộng với CloudFormation Template
- Sau khi đã hiểu rõ cách cấu hình thủ công các thành phần như EC2, CloudWatch Alarm, SNS và Lambda, phần này sẽ giúp bạn nâng cấp hệ thống lên một mức độ chuyên nghiệp hơn với Infrastructure as Code (IaC).

- Thay vì thực hiện thủ công từng bước, ta sử dụng AWS CloudFormation để tự động triển khai toàn bộ hạ tầng với chỉ một cú click hoặc lệnh duy nhất.

### Lợi ích mang lại:
  - Tự động hóa toàn bộ quá trình cấu hình và triển khai.

  - Đảm bảo tính nhất quán, tránh lỗi do thao tác thủ công.

  - Dễ dàng kiểm soát và version hóa hạ tầng như code.

  - Nhanh chóng nhân bản hệ thống sang nhiều môi trường (dev, test, prod...).

  - Template được cung cấp sẽ thiết lập đầy đủ:

  - Hạ tầng mạng và bảo mật.

  - EC2 Auto Scaling + Load Balancer.

  - Hệ thống cảnh báo qua CloudWatch + SNS.

  - Ghi log, giám sát, xử lý sự kiện tự động bằng Lambda & EventBridge.

  - Quản lý vận hành với AWS Systems Manager và OpsCenter.

## Nội dung:
 - [Chuẩn bị môi trường và triển khai với CloudFormation](2.1-createcloudformation/)

