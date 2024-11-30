# AWS Live Projects

AWS projects should be performed using 
- AWS Console (*ClickOps*)
- AWS CLI (*Automation 1.0*)
- Terraform (*Infrastructure as Code IaC*)

## Network Setup
1. Setup SEAZ Organization
  - Production (current) Account
  - Playground Account
  - Configure Brahma Permission Set for users across all accounts
  - Configure PowerUse Permission Set for a user per account
2. **1x1:** 1 EC2 instance in 1 AZ that is Internet accessible
  - VPC
  - us-east-2 Region in a single AZ
  - 1 Public subnet 
  - 1 Route Table
  - 1 Internet Gateway
  - 1 EC2 Instance using Ubuntu 24.04 AMI
  - Attach ec2-ssm iam instance profile to the EC2 instance
3. **2x1:** 2 EC2 instances across 1 AZ, 1 is Internet accessible and the other is in the Private Subnet
  - VPC
  - us-east-2 Region in a single AZ
  - 1 Public subnet 
  - 1 Private subnet
  - 1 Route Table for each subnet
  - 1 Internet Gateway
  - 1 NAT Gateway in the public subnet for the EC2 instance(s) in the private subnet
  - 2 EC2 Instance using Ubuntu 24.04 AMI, one in each subnet
  - 1 Security Group for each subnet
  - Attach ec2-ssm iam instance profile to each EC2 instance
4. **4x2:** 4 EC2 instances across 2 AZs, 2 are Internet accessible and 2 are in private subnets
  - VPC
  - us-east-2 Region across 2 AZs
  - 2 Public subnets, one in each AZ
  - 2 Private Subnets, one in each AZ
  - 2 Route Table, one for EC2 instances in Public subnet and one for EC2 instance(s) in Private subnets
  - 1 Internet Gateway
  - 2 NAT Gateway for the EC2 instances, one in each AZ for the Private subnet
  - 4 EC2 Instances using Ubuntu 24.04 AMI, one in each of the subnets
  - 1 Security Group per EC2 instance
  - Attach ec2-ssm iam instance profile to each EC2 instance

## Nginx Setup as Web Server/Reverse Proxy

1. Nginx with SSL termination using **1x1**
  - Setup nginx as a web server on public subnets with SSL termination
2. Reverse Proxy with SSL termination using **2x1**
  - Setup nginx as reverse proxy (layer 7) on public subnet with SSL termination
  - Setup nginx as Web Server (HTTP only) on the private subnet 
3. Use ALB and Target Group using **4x2**
  - Setup multiple nginx as Web Servers (HTTP only) on the private subnets
4. Use Route53 and AWS Certificate Manager (ACM)

## Wordpress Setup
1. Wordpress using **1x1**
2. Wordpress using **1x1** connecting to a Managed RDS
3. Wordpress using **4x2** connecting to a Managed RDS

## Static Hugo Website Setup

[Source: How to deploy a Hugo site to S3 in 2024](https://www.jeromethibaud.com/en/blog/deploy-hugo-site-to-s3/)
- S3 bucket with appropriate settings and replicated across 2 regions
- Set it up as a Web site
- Use CloudFront as a CDN and SSL termination
- Use ACM for SSL Certs
- Use Route53 for DNS

## Python App(s) Setup

- "Hello FastAPI/Flask" with Managed RDS and/or DynamoDB and/or ElastiCache **1x1**
- "Hello FastAPI/Flask" with Managed RDS or DynamoDB and/or ElastiCache **2x1**
- "Hello FastAPI/Flask" with Managed RDS or DynamoDB and/or ElastiCache **4x2**
- ECS/Fargate cluster(s) as Compute
- EKS Cluster(s) as Compute

## Refernces

## Build Modern Apps in AWS

[Source](./building-apps-in-aws.md)

### DevHub Setup

- IAM
- EC2
  - VPC
  - Subnet
  - Security Groups
  - Route Tables
  - Internet Gateway
  - NAT Gateway
- Route53
  - Hosted Zones
  - Traffic Policy
- ACM
- ALB
  - Target Groups
- Classic ELB
  - Target Groups
- EKS
- RDS
- S3
- CloudWatch
