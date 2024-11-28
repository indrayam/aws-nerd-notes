# Starting to use AWS

There are around **30** services/concepts that we will need to get our arms around.

For each, here are some things to think about...

## Cost Management (~5)

- AWS Calculators
  - _Gain expertize in AWS Simple Monthly Calculator_
  - _Gain expertize in AWS Pricing Calculator_
- AWS Cost Explorer w/ AWS Cost and Usage Reports
  - _Gain expertize so we can keep a handle on our current costs_
  - _How do we consume the Cost and Usage reports?_
- AWS Trusted Advisor

## Infrastructure (~6)

- IAM
  - _Are we manually creating the users and groups? Any chance of integrating it with Okta/Sailpoint_
  - _Standardize a few Roles_
  - _Roles definition using Policies_
- Regions
  - _Which Regions?_
    - _Data Sovereignty Laws_
    - _Latency to end users_
    - _AWS Services_
- AZs
  - _Minimum 3_
- VPC (Subnet w/ CIDRs and NACL, Security Groups, Route Table, Internet Gateway, NAT Gateway)
  - _How many VPCs for all the services?_
    - _Avoid VPC Peering costs_
  - _How many Subnets? Types - Public or Private_
  - _SCI_
- Route53
  - _Are we using it?_
- CloudFront
  - _Are we using it?_
- Certificate Manager
  - _Are we using it?_
- ELB w/ ALB or NLB
  - _ALB expertize_
  - _NLB expertize_

## Dev (~10)

- EC2 w/ EBS
  - _Use it only if others do not work_
  - _Reserved instances (Standard or Convertible)_
  - _Standardize Windows/Linux AMI_
  - _Standardize Instance Types_
  - _Default limit is 20 per account. Request increase, if not already_
  - _Default EBS specs_
  - _Do we use ASG?_
- Lambda
  - _Event Workers_
  - _Scheduled Workers_
  - _Containers based or Functions based_
  - _Lambda Layers expertize_
- EKS (Fargate)
  - _CAE replacement_
- S3/Glacier
  - _Bucket structure_
  - _Storage type standardization_
  - _Bucket and Objects Policy Standards and expertize_
  - _Encryption at rest policies_
  - _S3 Use Cases_
- DynamoDB
  - _As a Document store_
- ElastiCache
  - _As a K/V store_
- Amazon ElasticSearch
  - _As a Search engine store_
- RDS
  - _Are we using it?_
- SQS/SNS
  - _Replacing RabbitMQ_

## Ops (~4)

- Configuraton Management
  - _Terraform/Puppet_
  - _CloudFormation_
  - _AWS CLI_
- CloudWatch
  - _CloudWatch expertize_
  - _CloudWatch Logs strategy_
  - _CloudWatch Monitoring strategy_
- AWS CloudTrail
  - _Are we using it?_
- AWS Config
  - _Are we using it?_

## Security (~4)

- Trusted Advisor
- AWS WAF
  - _Are we using it?_
- AWS Shield
  - _Are we using it?_
- AWS KMS
  - _Are we using it?_
  - _CyberArk?_
