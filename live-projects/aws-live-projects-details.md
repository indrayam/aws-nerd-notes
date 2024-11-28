# AWS Live Projects

AWS projects should be performed both using AWS Console (*ClickOps*) and Terraform (*Infrastructure as Code IaC*)

1. Create a VPC with 
  - us-east-1 Region and us-east-1a AZ
  - 1 Public subnet 
  - 1 Route Table for the subnet
  - 1 Internet Gateway
  - 1 EC2 Instance using Ubuntu 24.04 AMI
  - 1 Security Group
2. Create a VPC with 
  - us-east-1 Region and us-east-1a AZ
  - 1 Public subnet and 2 Private Subnets
  - 3 Route Table for each of the subnets
  - 1 Internet Gateway
  - 1 NAT Gateway for the EC2 instances in the two Private subnets
  - 1 EC2 Instance using Ubuntu 24.04 AMI in each of the subnets
  - 1 Security Group per EC2 instance
3. Use the setup in 2 above as base and
  - Setup nginx as a web server on public subnet with SSL termination
4. Use the setup in 2 above as base and
  - Setup nginx as reverse proxy (layer 7) on public subnet with SSL termination
  - Setup nginx as Web Server (HTTP only) on any one of the private subnet 
5. Use the setup in 2 above as base and
  - Setup nginx as reverse proxy (layer 7) and load balancer on public subnet with SSL termination
  - Setup multiple nginx as Web Servers (HTTP only) on any one of the private subnet 
6. Use the setup in 2 above as base and
  - Setup nginx as reverse proxy (layer 4) on public subnet
  - Setup nginx as Web Server (HTTP only) on any one of the private subnet 
7. Use the setup in 2 above as base and
  - Setup nginx as reverse proxy (layer 4) and load balancer on public subnet
  - Setup multiple nginx as Web Servers (HTTP only) on any one of the private subnet

---

## Using EC2

- Pick a Region
- Pick 3 or more AZs to work with
- Create a VPC
- Create 6 subnets across the 3 Regions
  - 3 as public subnet
  - 3 as private subnet
- Create related EC2 artifacts
  - Key pairs
  - NAT Gateway
  - Internet Gateway
  - Security Groups
  - Network Access Control
- Instantiate 3 VMs across the 3 Public Subnets as well as 3 VMs across the 3 Private Subnets that hosts "Hello Rocket+DynamoDB" or "Hello SpringBoot+DynamoDB
- Create an ALB that fronts the 3 public VMs
- Create Route53 entry and map it to ALB
- Create a certificate using AWS Certificate Manager and use it for SSL termination

## Using ECS/Fargate

- Spin up ECS/Fargate cluster(s) that hosts "Hello Rocket+DynamoDB" or "Hello SpringBoot+DynamoDB
- Create an ALB that fronts the 3 public VMs
- Create Route53 entry and map it to ALB
- Create a certificate using AWS Certificate Manager and use it for SSL termination

## Using EKS

- Spin up EKS cluster(s) that hosts "Hello Rocket+DynamoDB" or "Hello SpringBoot+DynamoDB
- Create an ALB that fronts the 3 public VMs
- Create Route53 entry and map it to ALB
- Create a certificate using AWS Certificate Manager and use it for SSL termination

## Using Lambda

- Create a Lambda that responds to an API call
- Create a Lambda that responds to uploads in S3 bucket
- Create a Lambda that puts message(s) into SQS/SNS

## Using S3

- Create S3 buckets and review features
  - Replicates updates across regions
  - Set it up as a Web site
  - Use CloudFront as a CDN
  - Use Route53 for DNS
  - Use Certificate Manager for SSL termination

## Define CD Pipeline tools

- Use GitHub, GitHub Actions
- Use Artifactory and/or ECR
- Explore AWS Code\* tools

## Using Terraform/CloudFormation

- Automate (almost) everything using Terraform
- Automate (almost) everything using CloudFormation

## AWS Services used in DevHub

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
