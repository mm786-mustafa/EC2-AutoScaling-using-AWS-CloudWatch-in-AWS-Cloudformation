# EC2-AutoScaling-using-AWS-CloudWatch-in-AWS-Cloudformation
# WordPress Deployment on AWS using CloudFormation

This project provides an AWS CloudFormation template to deploy a **highly available WordPress website** using EC2 and RDS within a custom VPC. The infrastructure includes:

- Custom VPC with public and private subnets
- Internet Gateway and NAT Gateway
- Public and private route tables
- EC2 instances via Launch Template and Auto Scaling Group
- Application Load Balancer (ALB)
- RDS (MySQL) instance
- Security Groups
- CloudWatch Alarms for auto-scaling based on CPU usage

## 🚀 Features

- Fully parameterized for different environments (dev, testing, production)
- Auto Scaling EC2 instances hosting WordPress
- Highly available subnets across Availability Zones
- Secure communication between EC2 and RDS
- CloudWatch alarms for intelligent scaling
- UserData for automatic WordPress installation on EC2

## 🗂️ Template Structure

- **Parameters**: Customize VPC, Subnets, RDS, EC2 instance types, ALB, and more.
- **Mappings**: Define AMIs and instance types per environment.
- **Resources**:
  - Network setup (VPC, Subnets, Gateways, Route Tables)
  - EC2 Launch Template with UserData to install WordPress
  - RDS MySQL instance
  - ALB with Target Group and Listener
  - Auto Scaling Group
  - CloudWatch Alarms for scaling
- **Outputs**:
  - ALB DNS Name
  - RDS Endpoint Address

## 🧰 Prerequisites

Before launching this stack:

- An existing **EC2 Key Pair**
- AWS CLI or AWS Management Console access
- IAM permissions to create all mentioned AWS resources

## ⚙️ Deployment

You can deploy the stack using the AWS CLI:

```bash
aws cloudformation create-stack \
  --stack-name wordpress-ec2-rds \
  --template-body file://template.yaml \
  --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM

