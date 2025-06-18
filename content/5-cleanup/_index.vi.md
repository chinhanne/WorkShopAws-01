+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

#### Xóa EC2 instance

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click chọn **OperationalExcellence-Monitor-Instance**.
  + Click **Instance state**.
  + Click **Terminate instance**, sau đó click **Terminate** để xác nhận.
{{% notice note %}}
 Nếu bạn đã tạo Key Pair riêng, có thể vào “Key Pairs” (menu trái) và xóa nếu không còn dùng.
{{% /notice %}}

2. Truy cập [giao diện quản trị dịch vụ IAM](https://console.aws.amazon.com/iamv2/home#/home)
  + Click **Roles**.
  + Tại ô tìm kiếm , điền **LambdaOpExRole** và **EC2CloudWatchAgentRole**.
  + Click chọn **LambdaOpExRole** và **EC2CloudWatchAgentRole**.
  + Click **Delete**, sau đó điền tên role **LambdaOpExRole** và **EC2CloudWatchAgentRole** và click **Delete** để xóa role.
  

#### Xóa VPC 

1. Truy cập vào [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Click **Your VPCs**.
  + Chọn vpc chúng ta đã tạo cho bài thực hành **Vpc-workShop**.
  + Click **Actions**.
  + Click **Delete VPC**.

2. Tại ô confirm, điền **delete** để xác nhận, click **Delete** để thực hiện xóa **Lab VPC** và các tài nguyên liên quan.

#### Xóa Security Group
1. Truy cập vào [giao diện quản trị dịch vụ VPC](https://console.aws.amazon.com/vpc/home)
  + Menu trái chọn Security Groups.

  + Tìm security group **WorkShopSecurity**.

  + Nếu không còn gắn với instance nào → bấm Actions > Delete security group.

#### Xóa CloudWatch Alarm
1. Truy cập vào [giao diện quản trị dịch vụ CloudWatch](https://console.aws.amazon.com/cloudwatch/home)

  + Vào CloudWatch Console → Menu trái chọn Alarms > All alarms.

  + Tìm alarm HighCPUUtilization-Alert.

  + Chọn alarm → Actions > Delete.

#### Xóa SNS Topic và Subscriptions
1. Truy cập vào [giao diện quản trị dịch vụ Simple Notification Service](https://console.aws.amazon.com/sns/v3/home)

  + Menu trái chọn Topics, tìm OperationalExcellence-Alerts.

  + Chọn topic → bấm Delete.

  + Nếu chưa tự động bị xóa, bạn cũng có thể:

  + Vào Subscriptions → Chọn các subscription liên quan → Delete.

#### Xóa Lambda Function 
1. Truy cập vào [giao diện quản trị dịch vụ Simple Notification Service](https://console.aws.amazon.com/lambda/home)

  + Tìm function OperationalExcellence-AlertHandler.

  + Chọn → Bấm Actions > Delete function.

#### Xóa CLoudFormation
1. Truy cập vào [giao diện quản trị dịch vụ Simple Notification Service](https://console.aws.amazon.com/cloudformation/home)

  + Chọn Stack **CloudFormationWorkShop**.

  + Click Delete

  + Xác nhận xóa khi popup hiện ra

{{% notice note %}}
Stack sẽ có trạng thái DELETE_IN_PROGRESS và 
khi hoàn tất sẽ chuyển sang DELETE_COMPLETE
{{% /notice %}}
