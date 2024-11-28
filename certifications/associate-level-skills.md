# Associate Level AWS Skills

## 1. AWS and/or Architecture Concepts
- Well Architected Framework
- Shared Responsibility Model
- HTTP Protocol

## 2. Identity & Access
+ AWS IAM
  + IAM policies and roles
  + Cross account access
  + Multi-factor authentication (MFA)
  + API calls
  + IAM Roles with EC2 (instance profiles)
  + Access keys vs roles
  + IAM best practices
  + Federation
+ AWS Organizations

## 3. Networking
+ VPC
+ Elastic Load Balancing (ELB)
+ Route53
+ CloudFront
  + Viewer vs origin protocol policies
  + Lambda@Edge use cases
  + Invalidate cache
  + Signed URLs / cookies
+ Amazon API Gateway
  + Lambda / IAM / Cognito authorizers
  + Invalidation of cache
  + Integration types: proxy vs custom / AWS vs HTTP
  + Caching
  + Import / export OpenAPI Swagger specifications
  + Stage variables
  + Performance metrics
+ AWS App Mesh
+ AWS Transit Gateway
+ AWS Global Accelerator

## 4. Compute & Containers
+ EC2
+ ASG
+ Elastic Block Store (EBS)
+ AWS Elastic Container Service (ECS)
  + Shared storage between containers
  + Single vs multi-docker environments
  + Uploading / downloading images with ECR
  + Placement strategies (e.g. spread, binpack, random etc.)
  + Port mappings
  + Defining task definitions
  + IAM Roles for Tasks
+ AWS Elastic Kubernetes Service (EKS)
+ AWS Lambda
  + Invocation types
  + Using notifications and event source mappings
  + Concurrency and throttling
  + X-Ray and Amazon SQS DLQs
  + Versions and aliases
  + Blue/green deployment
  + Packaging and deployment
  + VPC connections (with Internet/NAT GW)
  + Lambda as ELB target
  + Dependencies
  + Environment variables (inc. encrypting them)
+ AWS Fargate
+ AWS Beanstalk
  + Deployment policies and blue/green
  + .ebextensions and config file usage
  + Updating deployments
  + Worker vs web tier
  + Deployment, packaging and files, code, commands used
  + Use cases

## 5. Storage
+ Amazon Simple Secure Storage (S3)
  + Encryption – make sure you understand S3 encryption very well for the exam!
  + S3 Transfer Acceleration
  + Versioning
  + Copying data
  + Lifecycle rules
+ Amazon Elastic File System (EFS)
+ Amazon S3 Glacier & S3 Glacier Deep Archive

## 6. Database
+ RDS Aurora
+ Amazon DynamoDB
  + Scans vs queries (and the APIs, parameters you can use)
  + Local and Global Secondary indexes
  + Calculating Read Capacity Units (RCUs) and Write Capacity Units (WCUs)
  + Performance / optimization  best practices
  + Use cases (e.g. session state, key/value data store, scalability)
  + DynamoDB Streams
  + Use in serverless app with Lambda and API Gateway
  + DynamoDB Accelerator (DAX) use cases
+ Amazon ElastiCache (Redis)
  + Use cases (caching and session state)
  + In-memory data store
  + Services it sits in front of (e.g. Amazon RDS)
  + Comparison against DynamoDB DAX
  + Lazy loading vs Write Through Caching
  + Memcached vs Redis

## 7. App Integration
+ Amazon Simple Notification Service (SNS)
+ Amazon Simple Queue Service (SQS)
  + Standard queues, FIFO, DLQ, delay queue
  + Decoupling applications use cases
  + Event source mapping to Lambda
  + Visibility timeout
  + Short polling vs long polling
+ AWS Step Functions
  + Step Functions state machines
  + Using to coordinate multiple Lambda function invocations

## 8. Analytics
+ Amazon Kinesis
+ Apache EMR
+ Amazon RedShift

## 9. Developer Tools
+ CodeStar
+ Cloud9
+ CodeCommit
+ CodeBuild
+ CodeArtifact
+ AWS Elastic Container Registry (ECR)
+ CodeDeploy
+ CodePipeline
  + Know how each tool fits into the CI/CD pipeline
  + Various files used such as appspec.yml, buildspec.yml etc.
  + Process for packaging and deployment
  + Deployment types with CodeDeploy including different destination services (e.g. Lambda, ECS, EC2)
  + Manual approvals with CodePipeline
+ AWS AppConfig
+ AWS XRay
  + X-Ray daemon, installing and configuring
  + Lambda with X-Ray
  + Use cases / benefits
  + Inclusion in Elastic Beanstalk environment
  + Annotations vs segments vs subsegments vs metadata
  + API calls
  + Port used (UDP 2000)

## 10. Security 
+ AWS Certificate Manager
+ AWS Secrets Manager
+ AWS Key Management Service (KMS)

## 11. Management
+ CloudWatch
  + Monitoring application logs
  + Trigger scheduled Lambda invocation
  + CloudWatch Lambda Insights **NEW**
  + Custom metrics
  + Metric resolution
+ CloudTrail
+ AWS Systems Manager
+ CloudFormation
  + CloudFormation template anatomy (e.g. mappings, outputs, parameters, etc.)
  + Packaging and deployment including commands used
  + AWS Serverless Application Model (SAM)
+ Resource Groups & Tag Editor
+ Trusted Advisor
+ Control Tower
+ Personal Health Dashboard

## 12. Cost Management
+ AWS Cost Explorer
+ AWS Budgets

## 13. Miscellaneous
+ Cognito
  + User pools vs Identity pools
  + Unauthenticated identities
  + AWS Cognito Sync
  + Using MFA with Cognito
  + Web identity federation
+ Athena
+ Macie
