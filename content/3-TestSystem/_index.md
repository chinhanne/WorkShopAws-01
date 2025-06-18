---
title : "System Testing"
date: 2025-05-25 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

1. **SSH into the EC2 instance**
```bash
ssh -i your-key.pem ec2-user@your-instance-ip
```

![VPC](/images/2.prerequisite/063_testsystem.png)

2. **Run a stress test**
```bash
# Generate 100% CPU load for 5 minutes
sudo stress --cpu 2 --timeout 300s

# Or use the yes command
yes > /dev/null &
yes > /dev/null &
```
![VPC](/images/2.prerequisite/064_testsystem.png)

3. **CloudWatch Console**
   - Observe the CPU metrics spike
   - Alarm transitions to the "In Alarm" state

![VPC](/images/2.prerequisite/065_cloudwatch.png)
![VPC](/images/2.prerequisite/066_cloudwatch.png)

4. **Check Email**
   - Receive the original alert email from CloudWatch
   - Receive the processed alert email sent by the Lambda function

![VPC](/images/2.prerequisite/068_checkmail.png)
![VPC](/images/2.prerequisite/067_cloudwatch.png)

5. **Clean up test**
```bash
# Stop stress processes
sudo pkill stress
# Or kill yes processes
sudo pkill yes
```






