---
title : "Kiểm tra hệ thống"
date: 2025-05-25 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

1. **SSH vào EC2 instance**
```bash
ssh -i your-key.pem ec2-user@your-instance-ip
```

![VPC](/images/2.prerequisite/063_testsystem.png)

2. **Chạy stress test**
```bash
# Tạo load CPU 100% trong 5 phút
sudo stress --cpu 2 --timeout 300s

# Hoặc sử dụng yes command
yes > /dev/null &
yes > /dev/null &
```
![VPC](/images/2.prerequisite/064_testsystem.png)

3. **CloudWatch Console**
   - Xem CPU metrics tăng lên
   - Alarm chuyển sang "In Alarm" state
![VPC](/images/2.prerequisite/065_cloudwatch.png)
![VPC](/images/2.prerequisite/066_cloudwatch.png)

4. **Check Email**
   - Nhận email alert gốc từ CloudWatch
   - Nhận email đã được xử lý từ Lambda

![VPC](/images/2.prerequisite/068_checkmail.png)
![VPC](/images/2.prerequisite/067_cloudwatch.png)

5. **Clean up test**
```bash
# Stop stress processes
sudo pkill stress
# Or kill yes processes
sudo pkill yes
```






