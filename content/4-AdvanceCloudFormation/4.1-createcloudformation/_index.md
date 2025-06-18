---
title : "Environment Setup and Deployment with CloudFormation"
date: 2025-05-25 
weight : 1 
chapter : false
pre : " <b> 4.1 </b> "
---


1. Go to the [AWS CloudFormation Management Console](https://console.aws.amazon.com/cloudformation/home)  
   - Click **Create stack**

![VPC](/images/2.prerequisite/069_cloudformation.png)

  - In **Step 1:**
    - [Download the CloudFormation template file](/files/LabTempletNew.yaml)
    - Select **Choose a template > Upload a template file**
    - Upload the template you just downloaded
    - Click **Next**

![VPC](/images/2.prerequisite/070_cloudformation.png)

 - **Stack name:** `CloudFormationWorkShop`
 - Choose the **Key Pair** created in step "2.1.4"
 - Enter the **email address** where you want to receive notifications
 - Click **Next**

![VPC](/images/2.prerequisite/072_cloudformation.png)
![VPC](/images/2.prerequisite/073_cloudformation.png)

  - Check **I acknowledge that AWS CloudFormation might create IAM resources**
  - Click **Next**

![VPC](/images/2.prerequisite/074_cloudformation.png)

  - Click **Submit**

![VPC](/images/2.prerequisite/075_cloudformation.png)

{{% notice note %}}
**Wait approximately 5 minutes for CloudFormation to change status to CREATE_COMPLETE**
{{% /notice %}}

![VPC](/images/2.prerequisite/076_cloudformation.png)
![VPC](/images/2.prerequisite/078_cloudformation.png)

  - Click on the **ALBEndpoint** link to open the ALB URL.
  - A web application should open via the Load Balancer.

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

  - Once testing is complete, you can check **Log groups, activity history, resources,** etc.

![VPC](/images/2.prerequisite/083_activity.png)
![VPC](/images/2.prerequisite/84-logsgroup.png)
![VPC](/images/2.prerequisite/85-resources.png)
