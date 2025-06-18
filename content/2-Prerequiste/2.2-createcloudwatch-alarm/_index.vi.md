---
title : "Thiết lập hệ thống cảnh báo và xử lý sự kiện bằng CloudWatch Alarm, SNS và Lambda"
date: 2025-05-25 
weight : 2 
chapter : false
pre : " <b> 2.2 </b> "
---

### CloudWatch là gì?

Amazon CloudWatch là dịch vụ giám sát tài nguyên AWS và ứng dụng. Cho phép:

- Thu thập và hiển thị các chỉ số hệ thống (CPU, bộ nhớ, disk I/O…).
- Lưu trữ, phân tích logs.
- Thiết lập cảnh báo khi vượt ngưỡng định trước (Alarm).
- Kích hoạt hành động tự động qua SNS, Lambda, hoặc các dịch vụ AWS khác.

---

### Mục tiêu của phần cấu hình

#### CloudWatch Alarm

- Theo dõi chỉ số **CPUUtilization** của EC2 instance.
- Cảnh báo khi CPU vượt 80% trong vòng 2 phút.
- Giúp phát hiện sớm các vấn đề về hiệu suất để can thiệp kịp thời.

#### SNS Topic + Email Subscription

- Tạo kênh thông báo qua **SNS Topic**.
- Gửi cảnh báo tức thời qua **email** khi Alarm kích hoạt.
- Đảm bảo người quản trị nhận thông tin kịp thời.

#### Lambda Function xử lý cảnh báo

- Tự động nhận thông báo từ SNS.
- Tạo **OpsItem** trong Systems Manager để ghi nhận sự kiện.
- Gửi cảnh báo chi tiết và dễ hiểu hơn đến người nhận.
- Giúp **tự động hóa quy trình xử lý sự cố** theo chuẩn "Operational Excellence".

---

### Kiến thức nền cần có

| Thành phần                            | Ý nghĩa                                                                 |
|--------------------------------------|-------------------------------------------------------------------------|
| **Metric**                           | Chỉ số hệ thống được CloudWatch thu thập (CPU, Memory, Network…)       |
| **Alarm**                            | Cảnh báo được cấu hình để theo dõi metric và gửi thông báo              |
| **SNS (Simple Notification Service)**| Gửi thông báo đến email, SMS, Lambda…                                   |
| **Subscription**                     | Địa chỉ nhận cảnh báo từ SNS (email, SQS, HTTP endpoint…)              |
| **Lambda**                           | Hàm serverless xử lý sự kiện từ SNS, giúp phản ứng nhanh và linh hoạt |
| **SSM OpsItem**                      | Mục ghi nhận sự cố trong Systems Manager để theo dõi, phân tích sau này |

---

### Nội dung

- [Tạo CloudWatch Alarm](2.2.1-createcloudwatch/)
- [Tạo Lambda Function xử lý thông báo](2.2.2-createlambda/)


