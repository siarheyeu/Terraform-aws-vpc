# Terraform AWS VPC

A production-ready **Terraform module** for deploying a custom VPC on AWS with public and private subnets, NAT Gateway, and security groups.

## 🎯 Purpose

This project demonstrates:

- **Terraform modularity** — reusable modules for VPC, subnets, and security groups
- **AWS networking** — VPC, public/private subnets, Internet Gateway, NAT Gateway, Route Tables
- **Security best practices** — Security Groups, no wide-open ports (except demo)
- **CI/CD** — GitHub Actions with `terraform fmt`, `validate`, and `tflint`
- **Remote state ready** — example for S3 backend (commented out)

## 📐 Architecture
Internet

│

▼

┌─────────────────────────────────────────┐

│ VPC (10.0.0.0/16) │

│ │

│ ┌─────────────────────────────────┐ │

│ │ Public Subnets (2 AZs) │ │

│ │ 10.0.1.0/24 10.0.2.0/24 │ │

│ │ (ALB, Bastion) │ │

│ └─────────────────────────────────┘ │

│ │ │

│ ▼ NAT Gateway │

│ ┌─────────────────────────────────┐ │

│ │ Private Subnets (2 AZs) │ │

│ │ 10.0.11.0/24 10.0.12.0/24 │ │

│ │ (App servers, Databases) │ │

│ └─────────────────────────────────┘ │

└─────────────────────────────────────────┘

text

## 🚀 Quick Start

### Prerequisites
- AWS CLI configured (`aws configure`)
- Terraform >= 1.5.0
- An AWS account with permissions to create VPC, EC2, IAM roles

### Deploy
bash
# Clone the repo
git clone https://github.com/your-username/terraform-aws-vpc.git
cd terraform-aws-vpc

# Copy example variables
cp terraform.tfvars.example terraform.tfvars

# Initialize and apply
terraform init
terraform plan
terraform apply
