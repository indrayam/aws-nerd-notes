# Practice Exercises

## COURSE: Hands-On with RDS and Aurora Databases
- Create an RDS Instance
- RDS Snapshots and Backup
- Copy and Share RDS Snapshots
- Multi-AZ RDS
- Read Replicas
- Create an Aurora Cluster
- Add Serverless to a Provisioned Aurora Cluster

## COURSE: Getting Started with AWS Safari
- Setup S3
  - Lifecycle Retention Policy
- Setup CloudTrail 
  - Enable
  - Integrate it with S3 (with Lifecycle Retention Policy)
- Setup SNS Topic 
  - Send email to anand.sharma@gmail.com
- Play with GuardDuty
- Play with Inspector
- Play with IAM Access Analyzer
- Play with Cost Explorer
  - Cost Allocation Tags enablement
  - Go through your costs and slice-and-dice it
- Play with SSM
  - Run Command feature

## BOOK: AWS in a Month of Lunches
- Play with Lamp Server in a **1x1**
- Play with Wordpress in a **1x1** using local MySQL
- Play with Wordpress in a **2x1** connecting to a Managed RDS
- Play with Wordpress in a **2x1** using ASG
  - Define an AMI with your Wordpress instance connecting to Managed RDS
  - Setup a Launch Template 
  - Setup an ASG with desired value of 3, min of 2 and max of 4
  - Define a Load Balancer and Target Group that targets instances spawned by the ASG
  - Integrate the ASG with the LB/TG created in the previous step

## Personal List
- Setup AWS Organization
  - Production (current) Account
  - Playground Account
  - Configure Brahma Permission Set for users across all accounts
  - Configure PowerUse Permission Set for a user per account
- Play with VPC (Single and Multi AZs)
  - **1x1:** 1 EC2 instance in 1 AZ that is Internet accessible
    - VPC
    - us-east-2 Region in a single AZ
    - 1 Public subnet 
    - 1 Route Table
    - 1 Internet Gateway
    - 1 EC2 Instance using Ubuntu 24.04 AMI (use Launch Template)
    - Attach ec2-ssm iam instance profile to the EC2 instance
  - **2x1:** 2 EC2 instances across 1 AZ, 1 is Internet accessible and the other is in the Private Subnet
    - VPC
    - us-east-2 Region in a single AZ
    - 1 Public subnet 
    - 1 Private subnet
    - 1 Route Table for each subnet
    - 1 Internet Gateway
    - 1 NAT Gateway in the public subnet for the EC2 instance(s) in the private subnet
    - 2 EC2 Instance using Ubuntu 24.04 AMI, one in each subnet (use Launch Template)
    - 1 Security Group for each subnet
    - Attach ec2-ssm iam instance profile to each EC2 instance
  - **4x2:** 4 EC2 instances across 2 AZs, 2 are Internet accessible and 2 are in private subnets
    - VPC
    - us-east-2 Region across 2 AZs
    - 2 Public subnets, one in each AZ
    - 2 Private Subnets, one in each AZ
    - 2 Route Table, one for EC2 instances in Public subnet and one for EC2 instance(s) in Private subnets
    - 1 Internet Gateway
    - 2 NAT Gateway for the EC2 instances, one in each AZ for the Private subnet
    - 4 EC2 Instances using Ubuntu 24.04 AMI, one in each of the subnets (use Launch Template)
    - 1 Security Group per EC2 instance
    - Attach ec2-ssm iam instance profile to each EC2 instance
- Play with Nginx
  - Nginx with SSL termination using **1x1**
    - Setup nginx as a web server on public subnets with SSL termination
  - Reverse Proxy with SSL termination using **2x1**
    - Setup nginx as reverse proxy (layer 7) on public subnet with SSL termination
    - Setup nginx as Web Server (HTTP only) on the private subnet 
  - Use ALB and Target Group using **4x2**
    - Setup multiple nginx as Web Servers (HTTP only) on the private subnets
  - Use Route53 and AWS Certificate Manager (ACM)
- Play with [Hugo](https://www.jeromethibaud.com/en/blog/deploy-hugo-site-to-s3/)
  - S3 bucket with appropriate settings and replicated across 2 regions
  - Set it up as a Web site
  - Use CloudFront as a CDN and SSL termination
  - Use ACM for SSL Certs
  - Use Route53 for DNS