# AWS-Project
✅ Solution Overview
This solution deploys a web application on Amazon EC2 instances, distributed across multiple Availability Zones using an Application Load Balancer (ALB) to provide scalability and high availability. The Auto Scaling Group (ASG) ensures elasticity by automatically adjusting the number of EC2 instances based on demand.

🎯 Learning Objectives
Design a fault-tolerant, scalable architecture on AWS.

Use Elastic Load Balancing and Auto Scaling for high availability.

Understand private and public subnet use cases in secure VPC designs.

Monitor application performance with Amazon CloudWatch.

🏗️ Architecture Diagram
![Ahmed Farag](https://github.com/user-attachments/assets/578beaa8-5c71-4d9d-b80d-1b00ac88ad6e)





📌 Public vs Private Subnets
Component	Subnet Type	Purpose
Application Load Balancer (ALB)	Public	Accepts traffic from the internet.
EC2 Instances (Web Server)	Private	Behind ALB for security.

🖥️ AWS Services Used
Amazon VPC (with Public & Private Subnets)

Amazon EC2

Elastic Load Balancing (ALB)

Auto Scaling Groups (ASG)

IAM Roles

Amazon CloudWatch and SNS 

⚙️ Customizing the Solution
📋 Prerequisites
AWS Account

AWS CLI installed & configured

Web Browser for AWS Management Console


🚀 Deployment Steps

1️⃣ Create Networking
Create VPC

Create 2 Public Subnets (e.g., 10.0.1.0/24, 10.0.2.0/24)

Create 2 Private Subnets (e.g., 10.0.11.0/24, 10.0.12.0/24)

Attach Internet Gateway (IGW) to VPC

Create Route Tables with appropriate routes 

2️⃣ Launch Application Load Balancer (ALB)
Type: Application Load Balancer

Associate with Public Subnets

Configure Target Group → Points to EC2 instances (ASG-managed)

3️⃣ Create Auto Scaling Group (ASG)
Launch Template → Amazon Linux/Ubuntu

User Data script → Use scripts/install_web_server.sh

Attach to ALB Target Group

Configure Scaling Policies

4️⃣  Configure IAM & Security Groups
ALB → Allow HTTP (80) from 0.0.0.0/0

EC2 → Allow HTTP (80) from ALB Security Group

RDS → Allow MySQL (3306) from EC2 Security Group

6️⃣ Configure Monitoring 
Setup CloudWatch alarms for CPU utilization or instance health

Setup SNS to receive email alerts
