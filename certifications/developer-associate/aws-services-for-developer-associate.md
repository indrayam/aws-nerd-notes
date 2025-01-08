# Notes on AWS Services for Developer Associate

## Management and Governance
- AWS Auto Scaling: Scale multiple resources to meet demand
- AWS CloudFormation: Create and manage resources with templates. Think, IaC
- AWS CloudTrail: Track and monitor activities by users, roles, or AWS services
- Amazon CloudWatch: Monitor resources and applications
- AWS Compute Optimizer: Recommends optimal AWS compute resources for your workloads. It can help you reduce costs and improve performance, by using machine learning to analyze your historical utilization metrics
- AWS Config: Track and evaluate configuration changes. Provides detailed view of the resources associated with your AWS account, including how they are configured, how they are related to one another, and how the configurations and their relationships have changed over time.
- AWS Control Tower: Service that enables you to enforce and manage governance rules for security, operations, and compliance at scale across all your organizations and accounts in the AWS Cloud
- AWS Health Dashboard: Service Health shows the current and historical status of all AWS services. Health Dashboard personalizes the view of the service events, showing only the ones that affect your AWS account or organization.
- AWS Launch Wizard: Easily size, configure, and deploy third-party applications on AWS
- AWS License Manager: Track and manage software licenses across multiple AWS Regions. License Manager reduces the risk of licensing overages and penalties with inventory tracking that is tied directly to AWS resources.
- AWS Management Console: Web-based user interface comprising multiple AWS service consoles
- AWS Organizations: Central governance and management across AWS accounts
- AWS Resource Groups and Tag Editor: See your resources across the AWS Regions in your AWS account
- AWS Service Catalog: Enables IT administrators to create, manage, and distribute portfolios of approved products to end users, who can then access the products they need in a personalized portal
- AWS Systems Manager: Helps you centrally view, manage, and operate nodes at scale in AWS, on-premises, and multicloud environments. An integrated console experience consolidates tools to help you complete common node tasks across AWS accounts and Regions.
- AWS Trusted Advisor: Trusted Advisor draws upon best practices learned from serving hundreds of thousands of AWS customers. Trusted Advisor inspects your AWS environment, and then makes recommendations when opportunities exist to save money, improve system availability and performance, or help close security gaps. If you have a Basic or Developer Support plan, you can use the Trusted Advisor console to access all checks in the Service Limits category and six checks in the Security category. If you have a Business, Enterprise On-Ramp, or Enterprise Support plan, you can use the Trusted Advisor console and the AWS Trusted Advisor API to access all Trusted Advisor checks.
- AWS Well-Architected Tool: Review your workloads against current Amazon Web Services architectural best practices. The AWS Well-Architected Tool measures the workload and provides recommendations on how to improve your architecture.

## Security, Identity, and Compliance
- AWS Artifact: On-demand access to AWS compliance reports
- AWS Audit Manager: Continuously audit your AWS usage to simplify how you manage risk and compliance with regulations and industry standards.
- AWS Certificate Manager (ACM): Provision, manage, and deploy SSL/TLS certificates
- AWS Private Certificate Authority: Create private certificates to identify resources and protect data
- AWS CloudHSM: Hardware-based key storage for regulatory compliance. An HSM is a dedicated hardware device designed to securely store and manage cryptographic keys, perform encryption/decryption, and ensure tamper-resistant cryptographic operations. HSM = Hardware Security Module. 
- Amazon Cognito: Handles user authentication and authorization for your web and mobile apps.
- Amazon Detective: Analyze, investigate, and quickly identify the root cause of security findings or suspicious activities. Detective automatically collects log data from your AWS resources and uses machine learning, statistical analysis, and graph theory to help you visualize and conduct faster and more efficient security investigations.
- AWS Directory Service: Set up and run Microsoft Active Directory with AWS services
- AWS Firewall Manager: AWS Firewall Manager simplifies your AWS WAF administration and maintenance tasks across multiple accounts and resources. With AWS Firewall Manager, you set up your firewall rules just once. The service automatically applies your rules across your accounts and resources, even as you add new resources
- Amazon GuardDuty: Continuous security monitoring service. Helps identify unexpected and potentially unauthorized or malicious activity in your AWS environment
- AWS Identity and Access Management (IAM):  Restricting Access to Cloud Resources
- AWS IAM Identity Center (AWS Single Sign-On): Manage single sign-on access to AWS accounts and apps
- Amazon Inspector: Continuous security vulnerability assessment service that helps improve the security and compliance of your AWS resources. Automatically assesses resources for vulnerabilities or deviations from best practices, and then produces a detailed list of security findings prioritized by level of severity
- AWS Key Management Service (AWS KMS): An encryption and key management service scaled for the cloud. AWS KMS keys and functionality are used by other AWS services, and you can use them to protect data in your own applications that use AWS.
- Amazon Macie: Fully managed data security and data privacy service. Macie uses machine learning and pattern matching to help you discover, monitor, and protect your sensitive data in Amazon S3.
- AWS Network Firewall: Stateful, managed, network firewall and intrusion detection and prevention service for your virtual private cloud (VPC) that you create in Amazon Virtual Private Cloud (Amazon VPC)
- AWS Resource Access Manager (AWS RAM): Use AWS Resource Access Manager (AWS RAM) to share resources you create in one AWS account with other accounts.
- AWS Secrets Manager: Rotate, manage, and retrieve secrets
- AWS Security Hub: Comprehensive view of the security and compliance state of your AWS resources. It collects security data from across AWS accounts and services, and helps you analyze your security trends to identify and prioritize the security issues across your AWS environment.
- AWS Shield: Protection against DDoS attacks using AWS Shield Standard and AWS Shield Advanced. AWS Shield Standard is automatically included at no extra cost beyond what you already pay for AWS WAF and your other AWS services. For added protection against DDoS attacks, AWS offers AWS Shield Advanced.
- AWS Web Application Firewall (WAF): Filter malicious web traffic

## Networking and Content Delivery
- Amazon API Gateway: Enables you to create and deploy your own REST and WebSocket APIs at any scale. You can create robust, secure, and scalable APIs that access Amazon Web Services or other web services, as well as data that's stored in the AWS Cloud. You can create APIs to use in your own client applications, or you can make your APIs available to third-party app developers.
- Amazon CloudFront: Global content delivery network
- AWS Direct Connect: AWS Direct Connect establishes a dedicated network connection between your on-premises network and AWS.
- AWS Global Accelerator: AWS Global Accelerator is a network layer service in which you create accelerators to improve the security, availability, and performance of your applications for local and global users.
- Amazon Route 53: Highly available and scalable Domain Name System (DNS) web service
- Amazon VPC: Isolated cloud resources. Provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you've defined and is isolated from other networks by default.
- AWS VPN: Establishes a secure and private tunnel from your network or device to the AWS Cloud.

## Cloud Financial Management
- AWS Billing Conductor: **Custom billing service for AWS Marketplace Channel Partners** (Partners) and organizations that have chargeback requirements.
- AWS Budgets: Track and **take action on your AWS costs and usage**
- AWS Cost and Usage Report: Cost Explorer provides you with Cost and usage reports. Examples of default cost and usage reports include: **Daily costs, Monthly costs by linked account, Monthly costs by service etc.**
- AWS Cost Explorer: Tool to **view and analyze your costs and usage**
- AWS Marketplace: Online store where you can **buy or sell software that runs on Amazon Web Services**

## Compute
- AWS Batch: Run **batch jobs** at any scale. Think cloud native version of Broadcom's Dollar Universe.
- Amazon EC2: Create and run virtual servers in the cloud
- AWS Elastic Beanstalk: Run and manage web apps. Basically, an Application Platform-as-a-service (APaaS)
- Amazon Lightsail: Launch projects, quickly: instances (virtual private servers), managed databases, object storage, load balancers, content delivery network (CDN) distributions
- AWS Local Zones: **Extension of an AWS Region** that places compute, storage, and other AWS services closer to end-users and on-premises data centers for applications requiring low latency or local data residency.
- AWS Outposts: **Run AWS infrastructure on-premises**. A fully managed service that brings AWS infrastructure, services, and tools to your on-premises environment. Delivered as a physical hardware rack installed in your data center.
- AWS Wavelength: **Deliver ultra-low latency applications for 5G devices**. Wavelength deploys standard AWS compute and storage services to the edge of telecommunication carriers' 5G networks. Developers can extend an Amazon Virtual Private Cloud (VPC) to one or more Wavelength Zones, and then use AWS resources like Amazon Elastic Compute Cloud (EC2) instances to run applications that require ultra-low latency and a connection to AWS services in the Region.

## Containers
- Amazon Elastic Container Registry (Amazon ECR): Easily store, manage, and deploy container images
- Amazon Elastic Container Service (Amazon ECS): Highly secure, reliable, and scalable way to run containers
- Amazon Elastic Kubernetes Service (Amazon EKS): Run Kubernetes on AWS without operating your own Kubernetes clusters

## Serverless
- AWS Fargate: Serverless compute for containers
- AWS Lambda: Run code without provisioning or managing servers.

## Storage
- AWS Backup: Managed backup service that makes it easy to centralize and automate the backup of data across AWS services in the cloud as well as on premises.
- Amazon Elastic Block Store (Amazon EBS): Scalable, high-performance block-storage resources that you can use with your Amazon EC2 instances.
- Amazon Elastic File System (Amazon EFS): Serverless, elastic, set-and-forget file system that automatically grows and shrinks as you add and remove files with no need for management or provisioning
- AWS Elastic Disaster Recovery: Minimizes downtime and data loss with fast, reliable recovery of on-premises and cloud-based applications using affordable storage, minimal compute, and point-in-time recovery.
- Amazon FSx: Launch, run, and scale feature-rich, high-performance file systems in the cloud. Choose between four widely-used file systems: Lustre, NetApp ONTAP, OpenZFS, and Windows File Server.
- Amazon S3: Object storage built to retrieve any amount of data from anywhere
- Amazon S3 Glacier: Low-cost archive storage in the AWS Cloud
- AWS Storage Gateway: Connects an on-premises software appliance with cloud-based storage to provide seamless and secure integration between your on-premises IT environment and the AWS storage infrastructure in the AWS Cloud.

## Database
- Amazon Aurora: High performance managed relational database engine
- Amazon DynamoDB: Managed NoSQL database
- ElastiCache: Primarily an in-memory caching service. Supports Memcache and Redis.
- Amazon MemoryDB for Redis: Redis-compatible, **durable**, in-memory database service
- Amazon Neptune: Managed graph database service
- Amazon RDS: Managed relational database service. Supports many commercial and open-source options

## Application Integration
[Source: Amazon SQS, Amazon SNS, or Amazon EventBridge? ](https://docs.aws.amazon.com/decision-guides/latest/sns-or-sqs-or-eventbridge/sns-or-sqs-or-eventbridge.html?icmpid=docs_homepage_decision_guides)
- Amazon EventBridge: Serverless event bus that connects applications, services, and SaaS tools, allowing you to build event-driven architectures by routing events between sources and targets. Google Pub/Sub or Azure Event Grid are competitors in cloud space. On-premises competitors would be Tibco EMS, Kafka, RabbitMQ.
- Amazon Simple Notification Service (Amazon SNS): **Pub-sub messaging service** to send notifications to multiple subscribers (e.g., emails, SMS, HTTP endpoints, or AWS services) in real-time.
- Amazon Simple Queue Service (Amazon SQS): **Managed message queues for decoupling components in distributed systems.** Common use case is when we need reliable, ordered message delivery between producers and consumers (e.g., task queues, buffering).
- AWS Step Functions: Serverless **workflow orchestration service** that lets you coordinate tasks and services using visual workflows, handling retries, parallelization, and error handling automatically. AWS Step Functions is conceptually closer to the Camunda Universal Process Orchestrator as both 1) focus on workflow orchestration, 2) manage state transitions between steps in a workflow, and 3) Provide built-in support for retries, error handling, and timeouts. The difference is Step Functions is **primarily a solution for AWS services** and is optimized for **short-lived, serverless workflows** vs. Camunda focuses on business process management (BPM), including human tasks and external systems. It can also handle **long-running, stateful workflows** that span days, weeks, or more.

## Machine Learning
- Amazon Comprehend: Natural language processing (NLP) service that uses AI to analyze text, extracting insights like sentiment, key phrases, entities, and topics.
- Amazon Kendra: Search service, powered by machine learning, that helps users to search unstructured text using natural language.
- Amazon Lex: Build voice and text chatbots
- Amazon Polly: Turn text into life-like speech
- Amazon Rekognition: Analyze image and video
- Amazon SageMaker: Build, train, and deploy machine learning models at scale
- Amazon Textract: Extract text and data from documents. Think OCR.
- Amazon Transcribe: Automatic speech recognition
- Amazon Translate: Natural and fluent language translation

## Developer Tools
- AWS AppConfig: Service for managing and deploying application configurations dynamically, allowing you to safely update settings without redeploying your application. Think Feature flags, centralized configurations, etc.
- AWS CLI: Tool to manage AWS services using commands in a terminal, enabling automation of tasks like resource provisioning, configuration, and management.
- AWS Cloud9: Cloud-based IDE that you use to write, run, and debug code.
- AWS CloudShell: Command line access to AWS resources and tools directly from a browser
- AWS CodeArtifact: Managed artifact repository for securely storing, sharing, and managing software dependencies like npm, Maven, PyPI, and NuGet
- AWS CodeBuild: Managed build service that compiles code, runs tests, and produces software packages ready for deployment.
- AWS CodeCommit: Managed source control service for hosting secure, private Git
- AWS CodeDeploy: Managed service for automating application deployments to EC2, on-premises servers, Lambda, or ECS
- AWS CodePipeline: Marries CodeCommit, CodeBuild, and CodeDeploy under one roof to create a CI/CD pipeline
- AWS X-Ray: Helps developers analyze the behavior of their distributed applications by providing request tracing, exception collection, and profiling capabilities.

## End User Computing
- Amazon AppStream 2.0: Stream desktop applications securely to a browser. Basically, a managed, secure application streaming service that lets you stream desktop applications to users without rewriting applications.
- Amazon WorkSpaces: Virtual desktops in the cloud
- Amazon WorkSpaces Web: Users can access their Windows WorkSpaces and DCV (Desktop Cloud Virtualization) Linux WorkSpaces from any location using a web browser. 

## Frontend Web and Mobile
- AWS Amplify: Platform for building, deploying, and hosting full-stack web and mobile apps, with tools for backend services, CI/CD, and frontend hosting.
- AWS AppSync: Managed service for building GraphQL APIs, enabling real-time data queries, synchronization, and offline support for web and mobile apps.
- AWS Device Farm: Farms of thousands of distinct mobile devices, in real hardware, that you can rent screen time on. Test Android, iOS, and web apps on real devices in the AWS Cloud

## Internet of Things (IoT)
- AWS IoT Core: Provides secure, bi-directional communication for Internet-connected devices (such as sensors, actuators, embedded devices, wireless devices, and smart appliances) to connect to the AWS Cloud over MQTT, HTTPS, and LoRaWAN.
- AWS IoT Greengrass: Service for running local compute, messaging, and data processing on IoT devices, enabling edge computing with offline capabilities.

## Migration and Transfer
- AWS Application Discovery Service: AWS Application Discovery Service helps systems integrators quickly and reliably plan application migration projects by automatically identifying applications running in on-premises data centers, their associated dependencies, and their performance profile.
- AWS Application Migration Service: AWS Application Migration Service (MGN) is a highly automated lift-and-shift solution that simplifies and expedites migration to AWS
- AWS Database Migration Service (AWS DMS): AWS Database Migration Service (AWS DMS) is a web service you can use to migrate data from your database that is on-premises, on an Amazon Relational Database Service (Amazon RDS) DB instance, or in a database on an Amazon Elastic Compute Cloud (Amazon EC2) instance to a database on an AWS service. You can also migrate a database from an AWS service to an on-premises database. You can migrate between source and target endpoints that use the same database engine, such as from an Oracle database to an Oracle database. You can also migrate between source and target endpoints that use different database engines, such as from an Oracle database to a PostgreSQL database.
- AWS Migration Hub: Provides a single location to track migration tasks across multiple AWS tools and partner solutions. With Migration Hub, you can choose the AWS and partner migration tools that best fit your needs while providing visibility into the status of your migration projects.
- AWS Schema Conversion Tool (AWS SCT): AWS Schema Conversion Tool makes heterogeneous database migrations easy by automatically converting the source database schema and a majority of the custom code to a format compatible with the target database. The custom code that the tool converts includes views, stored procedures, and functions. 
- AWS Snow Family: AWS Snowball is a petabyte-scale data transport service that uses secure devices to transfer large amounts of data into and out of the AWS Cloud
- AWS Transfer Family: AWS Transfer Family is a managed service for securely transferring files to and from AWS using standard protocols like SFTP, FTPS, and FTP.

## Analytics
- Amazon Athena: Interactive query service to **analyze data directly in S3 using standard SQL**
- AWS Data Exchange: Helps AWS customers easily share and manage data entitlements from other organizations at scale. It simplifies **finding and licensing datasets, such as financial, healthcare, or weather data, and integrates them seamlessly into your AWS environment for analysis.**
- Amazon EMR: **Hosted Hadoop Framework. EMR = Elastic Map Reduce**. Cloud service for processing and analyzing large datasets using big data frameworks like Apache Hadoop and Spark, with the scalability, flexibility, and cost-efficiency of AWS.
- AWS Glue: **ETL Tool**. Like Informatica. Serverless data integration service that helps you prepare, transform, and move data for analytics, using tools like ETL, data cataloging, and workflows.
- Amazon Kinesis: Platform for **real-time data streaming**, allowing you to collect, process, and analyze data from sources like logs, IoT devices, or social media in real time
- Amazon MSK: **Managed Kafka. MSK = Managed Streaming for Apache Kafka.**
- Amazon OpenSearch Service: **OpenSearch = Open-source fork of Elasticsearch and Kibana.** Managed service for searching, visualizing, and analyzing data in real-time, using the OpenSearch and Elasticsearch engines.
- Amazon QuickSight: Think Power BI, Tableau, and Business Objects. **Business intelligence (BI) service** that lets you create interactive dashboards and visualizations from your data. 
- Amazon Redshift: Fully Managed **cloud data warehouse** that lets you analyze large datasets quickly using SQL and BI tools. Cloud Data Warehouse competitors would be Snowflake, Google Big Query, and Azure Synapse Analytics. On-Prem and hybrid solution providers in this space include Oracle Exadata, and Teradata. Open-source and Managed versions include Apache Hive and Greenplum (VMWare)
- AWS Lake Formation: Build and Manage **data lakes on Amazon S3**
- AWS Glue Data Catalog: Provides **metadata management and discovery for data stored in the data lake**. Acts as the metadata layer for services like Lake Formation, Athena, and Redshift

## Customer Engagement
- AWS Activate for Startups: AWS's flagship startup program. From the earliest stages, the AWS Activate program provides startups with cloud credits, technical support, business mentorship, and more
- AWS IQ: Find AWS Certified third-party experts for on-demand project work
- AWS Managed Services (AMS): AMS acts as an extension of your IT team, handling AWS infrastructure operations so you can focus on innovation. It helps companies operate AWS more efficiently and securely. 
- AWS Support: AWS Support provides support for users of Amazon Web Services. AWS Support offers five support plans: Basic, Developer, Business, Enterprise On-Ramp, and Enterprise.

## Business Applications
- Amazon Connect: Omnichannel cloud contact center
- Amazon Simple Email Service (Amazon SES): High-scale inbound and outbound email

