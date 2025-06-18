---
title : "Chuẩn bị môi trường và triển khai với CloudFormation"
date: 2025-05-25 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---


1. Truy cập [giao diện quản trị dịch vụ  Cloudformation](https://console.aws.amazon.com/cloudformation/home)
  - Chọn **Create stack**

![VPC](/images/2.prerequisite/069_cloudformation.png)

  - Trong **Step 1:**
    - [Tải về file CloudFormation template](/files/LabTempletNew.yaml)
    - Chọn **Choose an existing  template > Upload a template file**
    - Chọn file template mẫu vừa tải 
    - Chọn Next

![VPC](/images/2.prerequisite/070_cloudformation.png)

  - **Stack name:** `CloudFormationWorkShop`
  - Chọn **Key-pair** đã tạo tại bước "2.1.4"
  - Địa chỉ **email** mà bạn muốn nhận thông báo 
  - Chọn **Next**

![VPC](/images/2.prerequisite/072_cloudformation.png)
![VPC](/images/2.prerequisite/073_cloudformation.png)

  - Chọn **I acknowledge that AWS CloudFormation might create IAM resources**
  - Chọn **Next**

![VPC](/images/2.prerequisite/074_cloudformation.png)

  - Chọn **Submit**

![VPC](/images/2.prerequisite/075_cloudformation.png)

{{% notice note %}}
**Đợi khoảng 5 phút cho CloudFormation chuyển sang trạng thái CREATE_COMPLETE**
{{% /notice %}}
![VPC](/images/2.prerequisite/076_cloudformation.png)
![VPC](/images/2.prerequisite/078_cloudformation.png)

  - Chọn vào link **ALBEndpoint** để mở URL ALB.

  - Trang web mở ra là ứng dụng web đang chạy qua Load Balancer.

  2. **Access Load Balancer**
```bash
# Get ALB DNS name from stack outputs
aws cloudformation describe-stacks \
    --stack-name operational-excellence-lab \
    --query 'Stacks[0].Outputs[?OutputKey==`ALBEndpoint`].OutputValue' \
    --output text
```
3. **Generate Load**
```bash
# Use hey tool for load testing
hey -n 10000 -c 50 http://your-alb-dns-name/

# Or Apache Bench
ab -n 10000 -c 50 http://your-alb-dns-name/
```

![VPC](/images/2.prerequisite/081_cloudformation.png)
![VPC](/images/2.prerequisite/082_cloudformation.png)

  - Khi kiểm tra xong bạn có thể vào **Logs group, activity history, resources, ...** để xem.

![VPC](/images/2.prerequisite/083_activity.png)
![VPC](/images/2.prerequisite/84-logsgroup.png)
![VPC](/images/2.prerequisite/85-resources.png)
