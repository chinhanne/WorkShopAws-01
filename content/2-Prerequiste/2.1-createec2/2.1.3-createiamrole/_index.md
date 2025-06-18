---
title: "Create IAM Role"
date: 2025-05-25
weight: 3
chapter: false
pre: " <b> 2.1.3 </b> "
---

#### Create IAM Role

1. Go to the AWS Management Console:  
   - Search for "IAM" in the search bar  
   - Click on "Roles" to open the dashboard  

![VPC](/images/2.prerequisite/createrole.png)

   - Click **Create role** to create a new role  

![VPC](/images/2.prerequisite/014_createrole.png)

   - Select **AWS Service**  
   - In the "Use case" section, choose **EC2**  
   - Click **Next** to continue  

![VPC](/images/2.prerequisite/015_createrole.png)

   - Search for **CloudWatchAgentServerPolicy** and check the box to attach this policy  
   - Click **Next** to proceed  

![VPC](/images/2.prerequisite/016_createrole.png)

   - Name the role **EC2CloudWatchAgentRole**  
   - Review the configuration  
   - Click **Create role** to finalize the creation  

![VPC](/images/2.prerequisite/017_createrole.png)
![VPC](/images/2.prerequisite/018_createrole.png)

   - Go back to the "Dashboard" and click **Roles**  
   - Search for **EC2CloudWatchAgentRole** (If found, the role has been successfully created)  

![VPC](/images/2.prerequisite/019_createrole.png)

