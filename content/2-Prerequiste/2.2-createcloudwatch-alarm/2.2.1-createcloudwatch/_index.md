---
title: "Create CloudWatch Alarm"
date: 2025-05-25
weight: 1
chapter: false
pre: " <b> 2.2.1 </b> "
---

1. Go to the [CloudWatch management console](https://console.aws.amazon.com/cloudwatch/home)  
![VPC](/images/2.prerequisite/030_searchcloudwatch.png)

2. Click **All alarms** to create a new alarm  
   + Click **Create alarm**

![VPC](/images/2.prerequisite/031_createalarm.png)

   + Click **Select metric**

![VPC](/images/2.prerequisite/032_createAlarm.png)

   + Choose the instance you just created  
   + Select the metric **CPUUtilization**  
   + Click **Select metric**

![VPC](/images/2.prerequisite/033_createalarm.png)

![VPC](/images/2.prerequisite/034_createalarm.png)

3. Configure **Conditions**:  
   - **Threshold type**: Static  
   - **Condition**: Greater than threshold  
   - **Threshold value**: 80  
   - **Period**: 1 minute  
   - **Evaluation periods**: 2  

![VPC](/images/2.prerequisite/035_createalarm.png)
![VPC](/images/2.prerequisite/036_createalarm.png)

   - Click **Next** to continue

4. Configure **Notification**:  
   - Choose **In alarm**  
   - Select **Select an existing SNS topic**  
   - Under **Send a notification to**, choose the previously created SNS topic (if you don’t have one, create a new topic)

![VPC](/images/2.prerequisite/037_createalarm.png)

5. Create an **SNS Topic**:  
   - In the search bar, type **Simple Notification Service**  
   - Go to **Topics > Create topic**

![VPC](/images/2.prerequisite/038_createtopic.png)

   - **Type**: Standard  
   - **Name**: `OperationalExcellence-Alerts`  
   - **Display name**: `OpEx Alerts`  
   - Click **Create topic**

![VPC](/images/2.prerequisite/040_createtopic.png)

   - After successfully creating the topic:  
     - Go to the newly created topic  
     - Click **Create subscription**  
     - **Protocol**: Email  
     - **Endpoint**: Enter your email address  
     - Click **Create subscription**

   - **Confirm Subscription**:  
     - Check your email and click the confirmation link  
     - Verify that the subscription status is "Confirmed"

![VPC](/images/2.prerequisite/041_createsubcription.png)
![VPC](/images/2.prerequisite/042_createsubcription.png)
![VPC](/images/2.prerequisite/043_createsubcription.png)

6. Continue configuring **Notification**:  
   - Under **Send a notification to**, select the created SNS topic: **OperationalExcellence-Alerts**  
   - Click **Next** to continue  

![VPC](/images/2.prerequisite/044_createalarm.png)

7. In **Step 3: Name the Alarm**  
   - Example: **HighCPUUtilization-Alert**  
   - Click **Next** to continue  

![VPC](/images/2.prerequisite/045_createalarm.png)

8. Review your configuration before creating the alarm  

![VPC](/images/2.prerequisite/046_createalarm.png)

