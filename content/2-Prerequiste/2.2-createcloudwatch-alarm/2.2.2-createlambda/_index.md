---
title: "Create a Lambda Function to Handle Notifications"
date: 2025-05-25  
weight: 1  
chapter: false  
pre: " <b> 2.2.2 </b> "  
---

1. **Open IAM Console**  
   - Go to **Roles** > **Create role**

![VPC](/images/2.prerequisite/014_createrole.png)

   - **Trusted entity**: AWS service - Lambda  
   - Click **Next** to continue

![VPC](/images/2.prerequisite/047_createrolelambda.png)

   - **Permissions**:  
     - `AWSLambdaBasicExecutionRole`  
   - Click **Next** to continue

![VPC](/images/2.prerequisite/048_createrolelambda.png)
![VPC](/images/2.prerequisite/049_createrolelambda.png)

   - **Role name**: `LambdaOpExRole`  
   - **Description**: Allows lambda function to call AWS services on your behalf  
   - Review configuration settings  
   - Click **Create role**

![VPC](/images/2.prerequisite/050_createrolelambda.png)
![VPC](/images/2.prerequisite/051_createrolelambda.png)

2. **Search for "Lambda" in the search bar**  
   - Select **Lambda**

![VPC](/images/2.prerequisite/052_createlambda.png)

   - Go to **Functions > Create function**

![VPC](/images/2.prerequisite/053_createlambda.png)

   - **Function name**: `OperationalExcellence-AlertHandler`  
   - **Runtime**: Python 3.13  
   - **Execution role**: Use existing role (created in step 1)

![VPC](/images/2.prerequisite/054_createlambda.png)

   - Click **Create function**

![VPC](/images/2.prerequisite/055_createlambda.png)

   - **Successfully created**

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

4. **Deploy the function**

![VPC](/images/2.prerequisite/058_deploylambda.png)

5. **Connect Lambda to SNS**
   - Search for **Simple Notification Service** in the search bar  
   - Select the **Topic** you created

![VPC](/images/2.prerequisite/059_connectlambda+sns.png)

   - **In the SNS Topic**
     - Click **Create subscription**
     - **Protocol**: AWS Lambda
     - **Endpoint**: Select the Lambda function you just created
     - Click **Create subscription**

![VPC](/images/2.prerequisite/060_connectlambda+sns.png)
![VPC](/images/2.prerequisite/061_connectlambda+sns.png)

   - **Create subscription**

![VPC](/images/2.prerequisite/062_connectlambda+sns.png)

{{% notice note %}}
**Grant SNS permission to invoke the Lambda function**

- Go to your **Lambda function**
- Select the **Configuration** tab > **Permissions**
- A **Resource-based policy** will be automatically added to allow SNS to invoke the Lambda function
{{% /notice %}}
