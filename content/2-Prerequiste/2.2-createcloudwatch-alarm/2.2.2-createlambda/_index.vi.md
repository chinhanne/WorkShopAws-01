---
title : "Tạo Lambda Function xử lý thông báo "
date: 2025-05-25 
weight : 1 
chapter : false
pre : " <b> 2.2.2 </b> "
---


1. **Mở IAM Console**
  - Vào **Roles** > **Create role**

![VPC](/images/2.prerequisite/014_createrole.png)

  - **Trusted entity**: AWS service - Lambda
  - **Next** để tiếp tục

![VPC](/images/2.prerequisite/047_createrolelambda.png)

  - **Permissions**:
     - `AWSLambdaBasicExecutionRole`
  - **Next** để tiếp tục

![VPC](/images/2.prerequisite/048_createrolelambda.png)
![VPC](/images/2.prerequisite/049_createrolelambda.png)

  - **Role name: LambdaOpExRole**
  - **Description: Allows lambda function to call AWS services on your behaft**
  - Xem lại các thông tin cấu hình 
  - **Create role** để tạo

![VPC](/images/2.prerequisite/050_createrolelambda.png)
![VPC](/images/2.prerequisite/051_createrolelambda.png)

2. Tìm từ khóa **Lambda** trên thanh tìm kiếm 
  - Chọn **Lambda**

![VPC](/images/2.prerequisite/052_createlambda.png)

  - Chọn **Functions > Create function**

![VPC](/images/2.prerequisite/053_createlambda.png)

  - **Function name**: `OperationalExcellence-AlertHandler`
  - **Runtime**: Python 3.13
  - **Execution role**: Use existing role (từ bước 1)

![VPC](/images/2.prerequisite/054_createlambda.png)

  - **Create function**

![VPC](/images/2.prerequisite/055_createlambda.png)

  - Tạo **thành công**

![VPC](/images/2.prerequisite/056_createlambda.png)

3. **Function Code**:
```python
import json
import boto3
from datetime import datetime

def lambda_handler(event, context):
    print(f"Received event: {json.dumps(event)}")
    
    sns = boto3.client('sns')
    ssm = boto3.client('ssm')
    
    try:
        # Parse SNS message
        message = event['Records'][0]['Sns']['Message']
        subject = event['Records'][0]['Sns'].get('Subject', 'AWS Alert')
        
        # Create formatted notification
        timestamp = datetime.utcnow().strftime('%Y-%m-%d %H:%M:%S UTC')
        formatted_message = f"""
==============================
AWS Operational Excellence Alert
==============================

Alert: {subject}
Time: {timestamp}
Details: {message}

==============================
For more information, check AWS Console.
==============================
        """
        
        # Create OpsCenter item for tracking
        ops_response = ssm.create_ops_item(
            Title=f"Operational Alert: {subject}",
            Description=f"Alert received at {timestamp}\n\nDetails:\n{message}",
            Source='lambda.operational-excellence',
            Category='Performance',
            Severity='2'
        )
        
        # Send enhanced notification
        enhanced_message = formatted_message + f"\nOpsItem ID: {ops_response['OpsItemId']}"
        
        sns.publish(
            TopicArn=event['Records'][0]['Sns']['TopicArn'],
            Message=enhanced_message,
            Subject=f"[OpEx] {subject}"
        )
        
        return {
            'statusCode': 200,
            'body': json.dumps('Alert processed successfully')
        }
        
    except Exception as e:
        print(f"Error: {str(e)}")
        return {
            'statusCode': 500,
            'body': json.dumps(f'Error: {str(e)}')
        }
```

![VPC](/images/2.prerequisite/057_createlambda.png)

4. **Deploy** function

![VPC](/images/2.prerequisite/058_deploylambda.png)

5. **Kết nối Lambda với SNS**
  - Tìm kiếm từ khóa **Simple Notification Service** trên thanh tìm kiếm 
  - Chọn **Topics** vừa tạo

![VPC](/images/2.prerequisite/059_connectlambda+sns.png)

  - **Trong SNS Topic**
    - **Create subscription**
    - **Protocol**: AWS Lambda
    - **Endpoint**: Chọn Lambda function vừa tạo
    - **Create subscription**

![VPC](/images/2.prerequisite/060_connectlambda+sns.png)
![VPC](/images/2.prerequisite/061_connectlambda+sns.png)
  - **Create subscription**
![VPC](/images/2.prerequisite/062_connectlambda+sns.png)
{{% notice note %}}
**Cấp quyền cho SNS invoke Lambda**

- Vào **Lambda function**
- Chọn tab **Configuration** > **Permissions**
- Một **Resource-based policy** sẽ tự động được thêm để cho phép SNS gọi Lambda
{{% /notice %}}



