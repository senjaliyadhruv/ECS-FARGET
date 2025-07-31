# 🚀 ECS Fargate Deployment using Terraform

This project automates the deployment of a containerized application on **AWS ECS Fargate** using **Terraform**.  
It provisions a highly available and scalable setup with Application Load Balancer, Security Groups, IAM Roles, and ECS Fargate.

---

## ✅ Features

- AWS ECS Fargate Cluster provisioning
- ECS Task Definition with Docker image
- Application Load Balancer + Target Group
- Auto-created VPC + Public Subnets
- IAM roles for ECS Task Execution
- Security Groups for ALB and ECS
- Terraform modules for clean structure (optional)
---

## 🧱 Architecture Overview

                     🌍 Internet Users
                             │
                             ▼
                    ┌───────────────────┐
                    │ Application Load  │
                    │   Balancer (ALB)  │
                    └────────┬──────────┘
                             │
                    ┌────────▼────────┐
                    │  Target Group   │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │   ECS Fargate   │
                    │   Service +     │
                    │   Task (Docker) │
                    └─────────────────┘
                             │
                    ┌────────▼────────┐
                    │   Public Subnet │
                    └────────┬────────┘
                             │
                      ┌──────▼───────┐
                      │   VPC + IGW  │
                      └──────────────┘

---

## 📦 Use Case

This setup is ideal for:

- Running containerized applications without managing EC2
- Lightweight apps that need scalability and low ops overhead
- Quick, production-grade deployments with Load Balancer, security, and IAM
  
---

## 📁 Terraform Project Structure

---

## 🚀 How to Deploy

### 1️⃣ Prerequisites

- Terraform v1.3+
- AWS CLI configured (`aws configure`)
- Docker image already pushed to ECR (or public DockerHub image)

---

### 2️⃣ Clone and Initialize

```bash
git clone https://github.com/senjaliyadhruv/ecs-fargate-terraform.git
cd ecs-fargate-terraform
terraform init
cp terraform.tfvars.example terraform.tfvars
```
Update:

- VPC CIDRs
- Image URL
- ALB listener ports
- ECS task resources
```bash
terraform plan
terraform apply
```
---

## 🧹 Cleanup

To destroy the infrastructure and avoid AWS charges:

```bash
terraform destroy
```
