---
title: "Create an EC2 Instance"
date: 2025-05-25
weight: 4
chapter: false
pre: " <b> 2.1.4 </b> "
---

1. Go to the [EC2 Management Console](https://console.aws.amazon.com/ec2/v2/home)  
  + Click **Instances**  
  + Click **Launch instances**  

![EC2](/images/2.prerequisite/020_createec2.png)


2. On the **Step 1: Choose an Amazon Machine Image (AMI)** page:  
  + Name your EC2 Instance: **OperationalExcellence-Monitor-Instance**  
  + Click **Select** next to the **Amazon Linux 2023 AMI**

![EC2](/images/2.prerequisite/021_createec2.png)

3. On the **Step 2: Choose an Instance Type** page:  
  + Select instance type **t2.micro**  
  + Under **Key pair**, choose an existing key pair  
  + If you don’t have one, click **Create new key pair**

![EC2](/images/2.prerequisite/022_createec2.png)
![EC2](/images/2.prerequisite/028_createkeypair.png)

4. Under **Network settings**, click **Edit** to configure:  
  + Select **Select existing security group**

![EC2](/images/2.prerequisite/createec2+.png)

  + For **VPC**, choose the existing VPC: **Vpc-workShop-vpc**  
  + Then select the subnet: **subnet-public1-ap-southeast-1a**  
  + Choose the Security Group: **WorkShopSecurity**

![EC2](/images/2.prerequisite/023_createec2.png)

5. In the **Advanced details** section:  
  + Click to select the role **EC2CloudWatchAgentRole** for the **IAM instance profile**

![EC2](/images/2.prerequisite/024_createec2.png)

  + Under **User data**, paste the following script:
  ```bash
   #!/bin/bash
   yum update -y
   yum install -y amazon-cloudwatch-agent stress httpd
   systemctl start httpd
   systemctl enable httpd
   echo "<h1>Operational Excellence Demo Server</h1>" > /var/www/html/index.html
  ```
  + Click **Launch instance** to create the instance

  + Purpose: Install a web server, monitoring agent, and create a demo web page accessible via HTTP.

![EC2](/images/2.prerequisite/025_createec2.png)

{{% notice note %}}
Please wait a few minutes until the EC2 instance is fully created before proceeding to the next step.
{{% /notice %}}

6. **Successfully created**

![EC2](/images/2.prerequisite/026_createec2.png)

7. Click on the newly created instance to view its details  
   + Copy the **Public IPv4 address**  
   + Click **Connect** to test the connection

![EC2](/images/2.prerequisite/027_createec2.png)

8. Open the **terminal**

{{% notice note %}}
Make sure you are in the directory where the key pair file is stored.
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
Remember to replace "key-pair.pem" with the correct path to the .pem file you downloaded when creating the key pair.
{{% /notice %}}

![EC2](/images/2.prerequisite/029_Connecttestec2.png)

