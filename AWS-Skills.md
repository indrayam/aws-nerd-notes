# AWS Skills

## Skills @ 10,000k ft.

- Infrastructure
  - Ubuntu, Amazon Linux
  - Kubernetes, Containers
  - AWS Networking, Networking Services (DNS)
  - Terraform, Ansible
  - GitHub, GitHub Actions
- Programming
  - Python (go, rust, java, javascript)
  - Postgres, MongoDB, DuckDB
  - Kafka, RabbitMQ
- AI
  - Machine Learning
  - Deep Learning
  - Large Language Models
- Command-Line Tinkerer

## Core AWS Building Blocks and Services

- Security, Identity, and Compliance
  - IAM - Restricting Access to Cloud Resources
  - IAM Identity Center: Manage single sign-on access to AWS accounts and apps
  - Certificate Manger (ACM): Provision, manage, and deploy SSL/TLS certificates
  - GuardDuty: Continuous security monitoring service. Helps identify unexpected and potentially unauthorized or malicious activity in your AWS environment. Builds Machine learning model using VPC Flow logs, DNS traffic, etc. (ENABLE)
  - Inspector: Continuous security vulnerability assessment service that helps improve the security and compliance of your AWS resources. Automatically assesses resources for vulnerabilities or deviations from best practices, and then produces a detailed list of security findings prioritized by level of severity. Scanning for SW vulnerabilities or Networking configs on EC2 (OPTIONALLY ENABLE)
  - WAF: ilter malicious web traffic
  - Shield: Protection against DDoS attacks using AWS Shield Standard and AWS Shield Advanced.
  - Security Hub: Comprehensive view of the security and compliance state of your AWS resources.
  - Secrets Manager: Securely encrypt, store, retrieve, and rotate (or manage) credentials for your databases and other services. Instead of hardcoding credentials in your apps, you can make calls to Secrets Manager to retrieve your credentials whenever needed. 
  - Key Management Service (KMS): An encryption and key management service scaled for the cloud. AWS KMS keys and functionality are used by other AWS services
- Networking & Content Delivery
  - VPC => Isolated cloud resources. Provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you've defined and is isolated from other networks by default.
    - Subnets
    - Route Tables
    - Internet Gateway
    - Egress-Only Internet Gateways
    - Endpoints: for Private Subnet Access
    - Endpoint Services
    - NAT Gateways
    - Network ACLs
    - VPC Lattice: With VPC Lattice, developers work at the service level, invoking APIs via logical service names, while the platform takes care of the underlying networking, routing, security, and scaling—even within a single VPC
    - Site-to-Site VPN Connections: By default, instances that you launch into an Amazon VPC can't communicate with your own (remote) network. You can enable access to your remote network from your VPC by creating an AWS Site-to-Site VPN (Site-to-Site VPN) connection, and configuring routing to pass traffic through the connection.
    - Virtual Private Gateways: A virtual private gateway is the VPN concentrator on the Amazon side of the site-to-site VPN connection.
    - Transit Gateways: Amazon VPC Transit Gateways is a network transit hub used to interconnect virtual private clouds (VPCs) and on-premises networks.
  - Route53: Highly available and scalable Domain Name System (DNS) web service
  - CloudFront: Global content delivery network
  - API Gateway: Create and deploy your own REST and WebSocket APIs at any scale
- Compute
  - EC2: Create and run virtual servers in the cloud
    - AMI
    - Snapshots
    - Security Groups
    - Elastic IPs
    - Key Pairs
    - Network Interfaces
  - ELB: Load Balancers
    - Target Groups
  - Lambda: Executing Functions
- Containers
  - ECS: Highly secure, reliable, and scalable way to run containers
    - Fargate (or EC2) based
  - EKS: Run Kubernetes on AWS without operating your own Kubernetes clusters
    - Fargate (or EC2) based
  - ECR: Easily store, manage, and deploy container images
  - App Runner: Use App Runner for simple, managed container deployments with minimal setup.
- Storage
  - S3: Object storage built to retrieve any amount of data from anywhere
  - Glacier: Low-cost archive storage in the AWS Cloud
  - EBS: Elastic Block Storage for Virtual Machines
  - EFS: Serverless, elastic, set-and-forget file system that automatically grows and shrinks as you add and remove files with no need for management or provisioning
- Database
  - RDS: SQL Databases
  - DynamoDB: NoSQL Database
  - ElastiCache: In-memory K/V store
  - MemoryDB for Redis: Durable Redis
- Application Integration
  - SQS: Distributed Queues w/ one consumer
  - SNS: Notification Service
  - AWS EventBridge: Serverless event bus that connects applications, services, and SaaS tools, allowing you to build event-driven architectures by routing events between sources and targets. Google Pub/Sub or Azure Event Grid are competitors in cloud space. On-premises competitors would be Tibco EMS, Kafka, RabbitMQ.
  - Step Functions: Serverless **workflow orchestration service** that lets you coordinate tasks and services using visual workflows, handling retries, parallelization, and error handling automatically. AWS Step Functions is conceptually closer to the Camunda Universal Process Orchestrator
- Management and Governance
  - AWS Organizations: Central governance and management across AWS accounts
  - Auto Scaling: Scale multiple resources to meet demand
    - Launch Templates
  - CloudWatch: Monitoring and Logging of resources and applications
    - CloudWatch Alarm
  - CloudTrail: Track and monitor activities by users, roles, or AWS services. Auditing Events (Management Events are free; Data events are not) (ENABLE)
  - Systems Manager: Helps you centrally view, manage, and operate nodes at scale in AWS, on-premises, and multicloud environments. An integrated console experience consolidates tools to help you complete common node tasks across AWS accounts and Regions.
  - AWS Config: Track and evaluate configuration changes. Provides detailed view of the resources associated with your AWS account, including how they are configured, how they are related to one another, and how the configurations and their relationships have changed over time.
  - Trusted Advisor: Trusted Advisor draws upon best practices learned from serving hundreds of thousands of AWS customers. Trusted Advisor inspects your AWS environment, and then makes recommendations when opportunities exist to save money, improve system availability and performance, or help close security gaps. If you have a Basic or Developer Support plan, you can use the Trusted Advisor console to access all checks in the Service Limits category and six checks in the Security category. If you have a Business, Enterprise On-Ramp, or Enterprise Support plan, you can use the Trusted Advisor console and the AWS Trusted Advisor API to access all Trusted Advisor checks.
  - Well-Architected Tool: Review your workloads against current Amazon Web Services architectural best practices. The AWS Well-Architected Tool measures the workload and provides recommendations on how to improve your architecture.
  - AWS Health Dashboard: Service Health shows the current and historical status of all AWS services. Health Dashboard personalizes the view of the service events, showing only the ones that affect your AWS account or organization.
  - Resource Groups & Tag Editor: See your resources across the AWS Regions in your AWS account
  - Billing and Cost Management
    - Cost Allocation Tags
- Analytics
  - RedShift: Data Warehousing
  - EMR:  Managed Hadoop Framework
  - Athena: SQL support for data in S3
  - Glue: Managed ETL service
  - Kinesis: Work with real-time streaming data
  - MSK: Managed Apache Kafka
- Machine Learning/AI
  - Foundational Blocks
    - SageMaker AI: Build, Train, and Deploy Machine Learning Models
    - Bedrock: Build and scale GenAI apps with Foundation Models (FM)
  - AI App Building Blocks
    - Lex: Build Voice and Text chatbot
    - Kendra: Enterprise search service powered by ML (includes similarity search using embeddings)
    - Comprehend: Analyze unstructured text
    - Transcribe: Speech recognition transformed into text
    - Tranlate: ML powered translation
    - Polly: Turn text into lifelike speech
    - Rekognition: Search and analyze images and video


**Note:**
[Flattened list of unique AWS Services](./scratchpad/2025-my-list-of-aws-services.md)


## Certifications

- Core
  - AWS Certified Cloud Practitioner
  - AWS Certified AI Practitioner
  - AWS Certified Solution Architect Associate
  - AWS Certified Solutions Architect Professional
  - Certified Kubernetes Administrator
- OPTIONAL
  - AWS Certified SysOps Administrator Associate
  - AWS Certified Developer Associate
  - AWS Certified Machine Learning Associate
  - Cisco Certified Networking Associate
  - AWS Certified Advanced Networking

