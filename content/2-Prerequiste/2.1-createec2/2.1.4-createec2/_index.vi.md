---
title : "Tạo EC2 Instance"
date: 2025-05-25 
weight : 4
chapter : false
pre : " <b> 2.1.4 </b> "
---


1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2/v2/home)
  + Click **Instances**.
  + Click **Launch instances**.
  
![EC2](/images/2.prerequisite/020_createec2.png)

2. Tại trang **Step 1: Choose an Amazon Machine Image (AMI)**.
  + Đặt tên cho EC2 Instance **OperationalExcellence-Monitor-Instance**
  + Click **Select** để lựa chọn AMI **Amazon Linux 2023 AMI**.
  
![EC2](/images/2.prerequisite/021_createec2.png)

3. Tại trang **Step 2: Choose an Instance Type**.
 + Click chọn Instance type **t2.micro**.
 + Tại "Key pair" chọn **key pair** đã tạo (Nếu chưa có bấm **Create new key pair**) .
 
![EC2](/images/2.prerequisite/022_createec2.png)
![EC2](/images/2.prerequisite/028_createkeypair.png)

4. Tại "Network settings" chọn **Edit** để cấu hình 
  + Chọn **Select existing security group**

![EC2](/images/2.prerequisite/createec2+.png)

  + Trong "VPC" chọn VPC đã tạo trước đó **Vpc-workShop-vpc**
  + Tiếp theo cọn subnet đã tạo **subnet-public1-ap-southeast-1a**
  + Click chọn Security group **WorkShopSecurity**

![EC2](/images/2.prerequisite/023_createec2.png)

5. Trong **Advanced details:**
  +  Click chọn role đã tạo **EC2CloudWatchAgentRole** cho **IAM instance profile**

![EC2](/images/2.prerequisite/024_createec2.png)

  + Tại **User data**
  ```bash
    #!/bin/bash
    yum update -y
    yum install -y amazon-cloudwatch-agent stress httpd
    systemctl start httpd
    systemctl enable httpd
    echo "<h1>Operational Excellence Demo Server</h1>" > /var/www/html/index.html
  ```
  + Click **Launch instance** để tạo 
  + Mục đích: Cài web server, cài agent giám sát, tạo trang demo khi truy cập HTTP.

![EC2](/images/2.prerequisite/025_createec2.png)

{{% notice note %}}
Bạn hãy đợi vài phút cho đến khi EC2 được tạo xong trước khi làm bước tiếp theo nhé.
 {{% /notice %}}

6. Tạo **thành công**

![EC2](/images/2.prerequisite/026_createec2.png)

7. Chọn vào instance vừa tạo để xem chi tiết
  + Sao chép **địa chỉ public ipv4** 
  + Click chọn **Connect** để kiểm tra kết nối 

![EC2](/images/2.prerequisite/027_createec2.png)

8. Mở **terminal**

{{% notice note %}}
Bạn nhớ trỏ đến thư mục hiện tại đang lưu file key-pair.
{{% /notice %}}

   ```bash
    #!/bin/bash
    chmod 400 key-pair.pem
  ```

  + **Kết nối:**

   ```bash
    #!/bin/bash
    ssh -i "key-pair.pem" ec2-user@ec2-3-0-102-240.ap-southeast-1.compute.amazonaws.com
   ``` 

{{% notice note %}}
 Nhớ thay "key-pair.pem" bằng đường dẫn đúng đến file .pem bạn đã tải về khi tạo key pair.
{{% /notice %}}

![EC2](/images/2.prerequisite/029_Connecttestec2.png)




