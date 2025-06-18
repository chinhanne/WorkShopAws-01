---
title : "Tạo Cloudwatch Alarm "
date: 2025-05-25 
weight : 1 
chapter : false
pre : " <b> 2.2.1 </b> "
---


1. Truy cập [giao diện quản trị dịch vụ  Cloudwatch](https://console.aws.amazon.com/cloudwatch/home)
![VPC](/images/2.prerequisite/030_searchcloudwatch.png)

2. Chọn **All alarm** để tạo một alarm 
  + Chọn **Create alarm**

![VPC](/images/2.prerequisite/031_createalarm.png)

  + Chọn **Select metric**

![VPC](/images/2.prerequisite/032_createAlarm.png)

  + Chọn instance vừa tạo
  + Chọn metric **CPUUtilization**
  + Click **Select metric**

![VPC](/images/2.prerequisite/033_createalarm.png)

![VPC](/images/2.prerequisite/034_createalarm.png)

3. Cấu hình **Conditions:**
   - **Threshold type**: Static
   - **Condition**: Greater than threshold
   - **Threshold value**: 80
   - **Period**: 1 minute
   - **Evaluation periods**: 2

![VPC](/images/2.prerequisite/035_createalarm.png)
![VPC](/images/2.prerequisite/036_createalarm.png)

  - Click **Next** để tiếp tục

4. Cấu hình **Notification**
  - Chọn **In alarm**
  - Chọn **Select an existing SNS topic**
  - Tại **Send a notification to** chọn SNS đã tạo (nếu chưa có thì tạo mới SNS)

![VPC](/images/2.prerequisite/037_createalarm.png)

5. Tạo **SNS Topic**
  - Tìm trên thanh tìm kiếm từ khóa **Simple Notification Service**
  - Chọn **Topics > Create topic**

![VPC](/images/2.prerequisite/038_createtopic.png)

  - **Type**: Standard
  - **Name**: `OperationalExcellence-Alerts`
  - **Display name**: `OpEx Alerts`
  - Chọn **Create topic**

![VPC](/images/2.prerequisite/040_createtopic.png)

  - Tạo **thành công**
  - Tiếp tục **Trong topic vừa tạo**
    - Chọn **Create subscription**
    - **Protocol**: Email
    - **Endpoint**: Nhập email address của bạn
    - Chọn **Create subscription**

  - **Confirm Subscription**
    - Kiểm tra email và chọn vào link xác nhận
    - Verify subscription status: "Confirmed"

![VPC](/images/2.prerequisite/041_createsubcription.png)
![VPC](/images/2.prerequisite/042_createsubcription.png)
![VPC](/images/2.prerequisite/043_createsubcription.png)

6. Tiếp tục cấu hình **Notification**
  - Tại **Send a notification to** chọn SNS đã tạo **OperationalExcellence-Alerts**
  - Chọn **Next** để tiếp tục

![VPC](/images/2.prerequisite/044_createalarm.png)

7. Trong **Step 3: Đặt tên cho Alarm**
  - Ví dụ: **HighCPUUtilization-Alert**
  - Chọn **Next** để tiếp tục

![VPC](/images/2.prerequisite/045_createalarm.png)

8. Xem chi tiết cấu hình trước khi tạo mới alarm

![VPC](/images/2.prerequisite/046_createalarm.png)



