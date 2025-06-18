+++
title = "Clean Up Resources"
date = 2021
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

We will follow the steps below to delete the resources created during this hands-on lab.

#### Delete EC2 Instance

1. Go to the [EC2 management console](https://console.aws.amazon.com/ec2/v2/home)  
   + Click **Instances**  
   + Select **OperationalExcellence-Monitor-Instance**  
   + Click **Instance state**  
   + Click **Terminate instance**, then click **Terminate** to confirm  
{{% notice note %}}
If you created a custom Key Pair, you may go to “Key Pairs” (on the left menu) and delete it if no longer needed.
{{% /notice %}}

2. Go to the [IAM management console](https://console.aws.amazon.com/iamv2/home#/home)  
   + Click **Roles**  
   + In the search box, enter **LambdaOpExRole** and **EC2CloudWatchAgentRole**  
   + Select **LambdaOpExRole** and **EC2CloudWatchAgentRole**  
   + Click **Delete**, then type the role names (**LambdaOpExRole** and **EC2CloudWatchAgentRole**) and click **Delete** to confirm  

#### Delete VPC

1. Go to the [VPC management console](https://console.aws.amazon.com/vpc/home)  
   + Click **Your VPCs**  
   + Select the VPC created for this lab: **Vpc-workShop**  
   + Click **Actions**  
   + Click **Delete VPC**

2. In the confirmation field, type **delete** to confirm, then click **Delete** to remove the **Lab VPC** and all associated resources

#### Delete Security Group
1. Go to the [VPC management console](https://console.aws.amazon.com/vpc/home)  
   + On the left menu, select **Security Groups**  
   + Search for the security group **WorkShopSecurity**  
   + If it’s no longer attached to any instance → click **Actions > Delete security group**

#### Delete CloudWatch Alarm
1. Go to the [CloudWatch management console](https://console.aws.amazon.com/cloudwatch/home)  
   + In the CloudWatch Console → On the left menu, select **Alarms > All alarms**  
   + Find the alarm **HighCPUUtilization-Alert**  
   + Select the alarm → **Actions > Delete**

#### Delete SNS Topic and Subscriptions
1. Go to the [Simple Notification Service (SNS) console](https://console.aws.amazon.com/sns/v3/home)  
   + On the left menu, select **Topics**, search for **OperationalExcellence-Alerts**  
   + Select the topic → click **Delete**  
   + If it is not automatically removed, you can also:  
     + Go to **Subscriptions** → Select related subscriptions → **Delete**

#### Delete Lambda Function
1. Go to the [Lambda management console](https://console.aws.amazon.com/lambda/home)  
   + Search for the function **OperationalExcellence-AlertHandler**  
   + Select it → click **Actions > Delete function**

#### Delete CloudFormation Stack
1. Go to the [CloudFormation management console](https://console.aws.amazon.com/cloudformation/home)  
   + Select the stack **CloudFormationWorkShop**  
   + Click **Delete**  
   + Confirm the deletion when prompted  

{{% notice note %}}
The stack status will show **DELETE_IN_PROGRESS**, and once completed, it will change to **DELETE_COMPLETE**
{{% /notice %}}
