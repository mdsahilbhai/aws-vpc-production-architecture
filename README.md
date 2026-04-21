# AWS Production-Grade Secure VPC Architecture ☁️

**Author:** Md Sahil
**Role Target:** DevOps Engineer

## 📌 Project Overview
This project demonstrates the deployment of a highly available and secure 2-tier architecture on AWS. The setup strictly follows industry best practices 
by isolating the application in a Private Subnet while exposing only the necessary endpoints to the public internet via an Application Load Balancer (ALB).

## 🚀 Architecture Flow & Implementation
1. **Network Isolation:** Configured a custom VPC with 2 Public Subnets and 2 Private Subnets.
2. **Traffic Routing:** Deployed an Internet Gateway for public resources and a NAT Gateway for secure outbound internet access.
3. **Bastion Host (Jump Server):** Provisioned an Ubuntu EC2 instance in the public subnet. Securely transferred SSH keys using `scp` and managed permissions 
using `chmod 400`.
4. **Application Deployment:** Launched EC2 instances in the private subnets. Hosted a web server using Linux `nohup` commands to ensure persistence.
5. **Load Balancing:** Configured an Application Load Balancer in the public subnets to distribute HTTP traffic to the private instances.

## 💻 Core Linux Operations Executed
* Secure file transfer: `scp -i key.pem key.pem ubuntu@<Bastion-IP>:/home/ubuntu/`
* File permission management: `chmod 400 key.pem`
* Process management: `nohup python3 -m http.server 8000 &`