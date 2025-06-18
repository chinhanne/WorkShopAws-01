---
title: "Setting Up an Alerting and Event Handling System with CloudWatch Alarm, SNS, and Lambda"
date: 2025-05-25
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

### What is CloudWatch?

Amazon CloudWatch is a monitoring service for AWS resources and applications. It allows you to:

- Collect and display system metrics (CPU, memory, disk I/O…).
- Store and analyze logs.
- Set alarms when metrics exceed predefined thresholds.
- Trigger automatic actions via SNS, Lambda, or other AWS services.

---

### Configuration Objectives

#### CloudWatch Alarm

- Monitor the **CPUUtilization** metric of an EC2 instance.
- Trigger an alarm when CPU exceeds 80% for 2 consecutive minutes.
- Enable early detection of performance issues for timely intervention.

#### SNS Topic + Email Subscription

- Create a notification channel using **SNS Topic**.
- Send real-time alerts via **email** when the alarm is triggered.
- Ensure administrators are promptly informed.

#### Lambda Function to Handle Alerts

- Automatically receive alerts from SNS.
- Create an **OpsItem** in Systems Manager to log the event.
- Send more detailed and human-readable alerts to recipients.
- Automate incident response following **Operational Excellence** standards.


### Prerequisite Knowledge

| Component                           | Description                                                                 |
|-------------------------------------|-----------------------------------------------------------------------------|
| **Metric**                          | System metrics collected by CloudWatch (CPU, Memory, Network…)             |
| **Alarm**                           | A configured alert to monitor metrics and send notifications               |
| **SNS (Simple Notification Service)** | Sends notifications to email, SMS, Lambda, etc.                            |
| **Subscription**                    | Destination to receive SNS alerts (email, SQS, HTTP endpoint…)             |
| **Lambda**                          | Serverless function to handle SNS events for fast and flexible responses   |
| **SSM OpsItem**                     | Incident record in Systems Manager for tracking and post-analysis          |


### Contents

- [Create a CloudWatch Alarm](2.2.1-createcloudwatch/)
- [Create a Lambda Function to Handle Alerts](2.2.2-createlambda/)

