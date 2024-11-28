# acloud.guru: AWS Certified Cloud Practitioner 2020 Notes

## Exam Blue Print
- Concepts (26%)
- Security (25%)
- Technology (33%)
- Billing & Pricing (16%)

## Cloud Concepts & Technology

### 6 Advantages of Cloud
- Trade Capital expense for Variable Expense
  + Stop spending money running and maintaining DCs
- Go global in minutes!
- Stop guessing about capacity
- Increase speed and agility
- Benefit from massive economies of scale

### Types of Cloud Computing
- IaaS (For example: EC2)
- PaaS (For example: Heroku, Lightsail, Elastic Beanstalk)
- SaaS (For example: Gmail)

### Types of Cloud Computing Deployments
- Public Cloud: AWS, Azure, GCP
- Hybrid: Mix of Public and Private
- Private (On-Premise): You manage it in your DC using Openstack or VMWare

## AWS Services - Cloud Practitioner Scope
- AWS Global Infra
- Security, Identity & Compliance
- Compute
  + EC2 
  + Lambda
- Network & Content Delivery
  + VPC
  + Route53
- Storage
  + S3
  + Glacier
- Databases
  + RDS
  + DynamoDB
- AWS Cost Management
- Migration & Transfer

## Exam Tips: Why choose an AWS Region?
- Data Sovereignty Laws
- Latency to end users
- AWS Services

## Exam Tips: Support Plans
- Basic: Free
- Developer: 
  + Starts at $29/month and scales up based on usage
  + 12-24 hour response time during local business hours for Support Cases
- Business: 
  + Starts at $100/month and scales up based on usage
  + 1 hr response time for urgent Support Cases
  + Full Access to AWS Trusted Advisor for optimizing your AWS Infrastructure
  + Access to AWS Support APIs for automating your support cases and retrieving Trusted Advisor results
- Enterprise:
  + Starts at $15,000/month and scales up based on usage
  + 15 min response time for critical Support Cases and prioritized case handling
  + Full Access to AWS Trusted Advisor for optimizing your AWS Infrastructure
  + Access to AWS Support APIs for automating your support cases and retrieving Trusted Advisor results
  + Access to Technical Account Manager (TAM) who provides proactive guidance and best practices to help plan, develop and run AWS
  + Access to Support Concierge who provides Billing and Account analysis and assistance
  + Access to Infra Event Management to support product launches, seasonal promotions/events and migrations

## Exam Tips: AWS IAM
- IAM is not tied to a specific Region. It is a Global service.
- Access AWS Platform using:
  + Console
  + CLI
  + SDK
- "root" account is the email address you used to setup your AWS account. It has FULL ADMIN privileges
- Do not use "root" account for day-to-day use. Neither should the "root" account credentials be shared with anyone
- Enable MFA for the "root" user
- Create separate account for users. Assign them tp Groups.
- Users will inherit the permissions of the Group(s) that they belong to
- To set permissions in a Group, you need to apply "Policy" to that Group.
- Policies are internally represented as JSON doc

## Exam Tips: S3, Athena, Macie
- Files in S3 can be from 0 Bytes to 5 TB
- Unlimited storage
- Files are stored in "Buckets"
- "Bucket" names is a Universal namespace.
- S3 is Object based. Object consists of:
  + Key (Name of the object)
  + Value (The file)
  + Version ID
  + Metadata
  + Subresources:
    - ACL
    - Torrent
- Data Consistency in S3
  + Read after Write Consistency for PUTS of new Object
    - Translation: If you write a new file and read it immediately afterwards, you will be able to view that data
  + Eventual Consistency for overwrite PUTS and DELETES (can take some time propogate)
    - Translation: If you update an EXISTING file or delete a file and read it immediately afterwards, you may get an older version or you may not. Basically, changes to objects can take a little bit of time to propogate
- S3 is built for 99.99% availability. However, Amazon will guarantee 99.9% availability
- S3 data durability is 11x9s.
- S3 Features:
  + Tiered Storage
    - Standard
    - S3 - Infrequently Accessed
    - S3 One Zone - Infrequently Accessed
    - S3 - Intelligent Tiering 
    - S3 Glacier (Data Archiving): Retrieval time from minutes to hours.
    - S3 Glacier Deep Archive: Absolute lowest cost where retrieval time of 12 hours is acceptable
    - S3 Outposts is a storage class to deliver object storage to on-premises AWS Outpost environments
  + Lifecycle Management
  + Versioning
  + Encryption
  + Secure your data using ACLs and Bucket Policies
    - ACLs are at File level
    - Bucket Policies control access at "Bucket" level
- S3 Charges
  + Storage Size on a per Gig basis
  + Storage Management Pricing 
  + Number of Requests
  + Data Transfer Pricing
  + Transfer Acceleration
    - Takes advantage of CloudFront's globally distributed edge locations
    - When a user uploads a file to a Bucket with Transfer Acceleration enabled, content is uploaded to the nearest Edge location and then is "beamed" to the actual S3 bucket in the appropriate Region using Amazon's Networking backbone as opposed to traversing over the public Internet
  + Cross Region Replication
    - File gets replicated automatically to another Region
- S3 is Object based, not Block based. So, not suitable for installing OS.
- S3 buckets can be viewed globally. However, when you upload it, you do upload it to a Region. Or at least you can
- Btw, you can change Storage Class and Encryption settings of your object on-the-fly
- Access Control
  + Bucket Policies (All files inside the Bucket)
  + Object Policies (Individual files)
  + IAM Policies to Users & Groups
- You can use S3 to host static websites, but not dynamic sites. For example, sites running on Wordpress.
- S3 scales automatically to meet your demand. Many enterprises put static websites on S3 when they think there is going to be a large number of requests.
- Athena is an interactive query service which enables you to analyze and query data located in S3 using SQL
  - Serverless
  - Pay per query/per TB scanned
  - No ETL required
  - Works directly on data stored in S3
  - Used for
    + Log files stored in S3 etc..
- PII => Personally Identifiable Information. Basically, data exploited by criminals and used in identity theft or financial fraud
  + SSN, Home address, Email address
  + Passport Number, Drivers License Number
  + Date of birth, phone number, bank account, credit card number
- Macie is a security service that uses Machine Learning and NLP to discover, classify, and protect sensitive data stored in S3
  + Uses AI to recognize if your S3 objects contain PII stuff
  + Dashboard, reporting and alerts
  + Works directly with data stored in S3
  + Can also analyze CloudTrail logs
  + Great for PCI-DSS and preventing ID theft

## Exam Tips: CloudFront
- AWS CDN
- CDN is a system of distributed servers that deliver webpages and other web content to a user based on:
  + geographical location of the user
  + the origin of the web page
  + content delivery server
- Terminology
  + Distribution - Collection of Edge Locations
  + Edge Location - This is the location where content will be cached. This is separate from AWS Region/AZs
  + Origin - This is the origin (or source) of all files that the CDN will distribute. This can be an S3 bucket, an EC2 instance, an Elastic Load Balancer or Route53
- Objects are cached for TTL seconds. By default TTL is 48 hrs (86440 secs)
- 2 Types of Distributions
  + Web Distribution (for Website Streaming)
  + RTMP Distribution (for Media Streaming)
- Edge Locations are not just for READ only. You can write to them as well, as we saw with Transfer Acceleration property of an S3 object
- You can clear your cached objects, but you will be charged

## Exam Tips: EC2
- Virtual server(s) in the cloud!
- Pricing Model
  + On-demand. Pay by the sec. 
    - No upfront payment or long-term commitment
    - Good for short-term, spike, or unpredictable workloads that cannot be interrupted
    - Apps being developed or tested on EC2 for the first time
  + Reserved. Provides you with a capacity reservation and at a heavy discount. Contract terms are 1 year or 3 years.
    - Apps with steady state or predictable usage
    - Users willing to make upfront payments to reduce their total computing costs even further
    - Apps with unique capacity needs that they would rather reserve beforehand
    - Types
      - Standard (75%)
      - Convertible Reserved Instances (54%)
      - Scheduled Reserved Instances: This allows you to match your capacity reservation to a predictable recurring schedule that only requires a fraction of the day, week or month
  + Spot. Enables you to bid for the server
    - Apps with flexible start or end time
    - Apps that are only feasible at very low compute prices (like genomics etc.)
    - Users with urgent computing needs for large amounts of additional capacity. Only if the spot price is below on-demand instance.
  + Dedicated Hosts. Physical EC2 server dedicated for your use. Dedicated hosts can help you reduce costs by allowing you to use your existing server-bound licenses. Quite rare.
    - Useful for regulatory requirements that may NOT support multi-tenant virtualization
    - Great for hosting software which DOES NOT support multi-tenancy or cloud deployments
    - Can be purchased on-demand (hourly)
- EC2 Instance Types
  + ARM-based => A (scale out workloads such as web servers)
  + General purpose => T (Lowest Cost, Small Web Servers/DB), M (App Servers)
  + Field Programmable Gate Array (FPGA) => F
  + Graphics Intensive, Machine Learning, Bitcoin Mining etc. => G, P (GPU)
  + Compute Optimized => C
  + Memory Optimized => R, X (SAP Hana, Spark)
  + Disk IO Throughput => I, H
  + Dense Storage => D (Fileservers, Hadoop)
  + High Compute Capacity & High Memory Footprint => Z
  + Bare Metal => U
- EC2 Instance Types - Mnemonic
  + F = FPGA
  + I = IOPS
  + G = Graphics
  + H = High-Disk throughput
  + T = Cheap (think, t2.micro)
  + D = Density
  + R = RAM
  + M = Main choice for general purpose apps
  + C = Compute
  + P = Pix (Graphics)
  + X = Xtreme Memory
  + Z = Xtreme Memory and CPU
  + A = ARM based workloads
  + U = Bare Metal
Stands for, "FIGHT DR MCPXZ in AUstin"
- EBS
  + Virtual hard disks
  + EC2 instance needs to be in the same AZ as EBS for it to be able to mount the EBS volume
  + SSD Types
    - GP2 (General Purpose): Balances price and performance for a wide variety of workloads
    - Provisioned IOPS SSD  (IO1, IO2): Highest-performance SSD volume for mission-critical low-latency or high-throughput workloads
  + Magnetic Types
    - Throughput Optimized HDD (ST1, ST2): Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
    - Cold HDD (SC1): Lowest cost HDD volume designed for less frequently accessed workloads (File Servers)
- If the Spot instance is terminated by Amazon EC2, you will NOT be charged for the partial hour of usage. However, if you terminate the instance yourself, you will be charged for the hour in which the instance ran
- Linux access via SSH (Port 22)
- Windows access via RDP (Port 3389)
- Security Groups == Firewall around a single EC2 instance
- /32 means this IP only

## Exam Tips: AWS CLI
- You can interact with AWS using
  + Console
  + CLI
  + SDKs
- Roles are much more secure than using access key id and secret access keys. They're also easier to manage.
- Roles are universal, not tied to a Region
- Roles can be assigned to many AWS resources. For example: EC2

## Exam Tips: Load Balancers
- Load Balancers come in 3 flavors
  + HTTP/HTTPS: Layer 7 aware
  + TCP: Extreme performance, static IP
  + Classic: Test & Dev. Keeping costs low.

## Exam Tips: Database
- Database Types based on Queries:
  + OLTP is Online Transaction Processing
  + OLAP is Online Analytics Processing
- RDS (OLTP) types
  + MS SQL Server
  + Oracle
  + MySQL
  + PostgreSQL
  + MariaDB
  + Amazon Aurora
  + 2 Key Features
    + Multi-AZ: For Disaster Recovery
    + Read Replicas: For High Performance
- Non-relational (NoSQL) databases
  + DynamoDB
    + Collection = Table
    + Document = Items
    + Key/Value Pairs = Attributes
    + Columns in the database can vary. This will not affect other documents in the database
  + ElastiCache
    + In-memory, distributed caching layer
    + Used to cache stuff that is requested frequently, but does not change very much
    + K/V based
    + Supports the following open-source in-memory engines:
      - Memcached and 
      - Redis
- Data Warehousing is for OLAP. Used for Business Intelligence by Business Leaders to run reports over a large, but connected, data set. To support this style of querying, they are architected differently both at data and infra layer. 
  + AWS Redshift (OLAP)

## Exam Tips: Route53
- DNS service
- It is a global service, like IAM
- You can use it to direct traffic all around the world!

## Exam Tips: Elastic Beanstalk
- AWS PaaS
- As a developer you bring your code. EB does the rest
  + Get Elastic IP
  + EC 2 instances with right software
  + ...
- Elastic Beanstalk is limited in what it can provision and is not very programmable 

## Exam Tips: CloudFormation
- Infrastrcuture as Code offering from AWS
- Declarative model of defining infrastructure
- Dependencies is handled by CloudFormation
- Service itself is free, but not the resources that it provisions

## Exam Tips: AWS Snowball
- PB-scale transport solution
- Uses secure appliances to transfer large amounts of data into and out of the AWS Cloud

## Exam Tips: Architecting for the Cloud - Best Practices
- Traditional vs Cloud Computing
  + IT Assets as Programmable/Provisioned Resources
  + Global, Available and Scalable Capacity
  + Higher Level (App) Managed Services  
  + Built-in Security
  + Architecting for Cost
  + Operations on AWS
- Design Principles: Scalability
  + Scale up: Add more compute, memory etc.
  + Scale Out: More common, more scalable
    - Stateless Apps
      + Stateless Components
      + Stateful Components
    - Distribute Load to Multiple Nodes
    - Implement Session Affinity
    - Implement Distributed Processing
- Design Principles: Disposable Resources instead of Fixed Servers
  + Instantiating Compute Resources
    - Boostrapping
    - Golden Images
    - Containers
    - Hybrids
  + Infrastructure as Code
    - CloudFormation
+ Design Principles: Automation
  + Serverless Management and Deployment
  + Infrastructure Management and Deployment
    - Auto Scaling
    - AWS Elastic Beanstalk
    - EC2 Auto Recovery
  + Alarms and Events
    - Amazon CloudWatch Events
    - Amazon CloudWatch Alarms
    - AWS Lambda Scheduled Events
    - AWS WAF Security Automations
+ Design Principles: Loose Coupling
  - Well defined Interfaces
    + API Gateway
  - Service Discovery 
    + DNS
  - Asynchronous Integration
    + Events-based vs Synchronous API based
  - Distributed Systems Best Practice
    + Graceful Failure in Practice
    + Automatic notification if things fail
+ Design Principles: Services, not Servers
  - Managed Services
  - Serverless Architectures
+ Design Principles: Databases
  - Relational Databases (Aurora)
    + Scalability
    + High-Availability (Multi-AZ)
    + Anti-Patterns:
      = If you do not need joins or complex transactions, use NoSQL technologies
  - NoSQL Databases (DynamoDB)
    + Scalability with auto-scalability
    + High-Availability (Multi-AZ)
    + Anti-Patterns:
      - If you need joins or complex transactions, use RDBMS
      - If you have large binary files, use S3
  - Data Warehouse (Redshift) 
    + Scalability
    + High-Availability (Multi-AZ)
    + Anti-Patterns:
      - Not meant for OLTP
  - Search 
    + Cloud Search
    + Amazon ElasticSearch
    + Scalability with auto-scalability
    + High-Availability (Multi-AZ)
  - Graph Database
    + Amazon Neptune    
    + Scalability with auto-scalability
    + High-Availability (Multi-AZ)
  - Data Lakes
    + Architectural approach where you store massive amounts of data in a central location
    + Readily available to be analyzed, categorized, processed and consumed by diverse groups within your org
    + Data can be stored as-is. Translation: you DO NOT have to convert it to a pre-defined schema
    + This unstructured nature of Data Lake also means that you DO NOT need to know the questions to ask beforehand
    + S3 is a good place to create Data Lakes
    + Athena is a good tool to then query the data
+ Design Principles: Remove Single Points of Failure
  - Introduce Redundancy
  - Introduce a mechanism to Detect Failure
  - Durable Data Storage
  - Automate Multi-Data Center Resilience
  - Fault Isolation and Traditional Horizontal Scaling
  - Sharding
+ Design Principles: Design for Cost
  - Right Sizing
  - Elasticity
  - Take advantage of the variety of Purchasing Options
+ Design Principles: Caching
  - Application Caching (ElastiCache)
  - Edge Caching (CDN)
+ Design Principles: Security
  - Use AWS Features for Defense in Depth
  - Shared Responsibility with AWS
  - Reduce Privileged Access
  - Security as Code
  - Real-time Auditing

## Exam Tips: AWS Global Services
+ AWS Global Services
  - IAM
  - AWS Organizations
  - Route53
  - CloudFront
  - SNS
  - SES (Not available in all regions)
  - Tag Editor
+ Some Services Give Global Views, but are Regional
  - S3

## Exam Tips: What AWS Services Can be used On-Premise
+ On-Premise Services
  - Snowball
  - Snowball Edge (Computer with Storage)
    + Install Lambda Functions On-Premise
    + Comes with Storage as well
  - Storage Gateway
    + Physical or Virtual
    + Stays on-premise, unlike Snowball
    + Data on Storage Gateway gets replicated to AWS S3
  - CodeDeploy
  - OpsWorks. Similar to Elastic Beanstalk
    + Uses Chef to deploy Apps to EC2 in AWS Code
    + Or, On-Premise Runtime
  - IoT Greengrass
    + Connects IoT device to AWS Cloud
+ Which AWS Services can be used to Deploy Apps On Premise?
  - CodeDeploy
  - OpsWorks

## Exam Tips: CloudWatch
- Monitors Performance like your Gym Coach
- CloudWatch can monitor things like
  + Compute
    - EC2 Instances
    - ASGs
    - ELB
    - Route53 Health Checks
  + Storage & Content Delivery
    - EBS Volumes
    - Storage Gateway
    - CloudFront
  + Host Level Metrics
    - CPU
    - Network
    - Disk
    - Status Check 
- So...
  + Used for monitoring performance
  + Can monitor most of AWS as well as your applications that run on AWS (# of users visting your web site)
  + CloudWatch will monitor EC2 instances every 5 mins by default
  + You can have 1 min monitoring if you turn on detailed monitoring
  + Use CloudWatch Alarms to trigger notifications 
  + CloudWatch is all about Performance!

## Exam Tips: AWS Systems Manager
- Allows you to Manage your AWS EC2 instances and on-premise Virtual Machines at scale: EC2 Fleet!
- A piece of software is installed on each VM. Behaves like Puppet
- Manage your EC2 fleet as well as virtual machines on-premise
- Run Command is used to install, patch, uninstall software
- Integrates with CloudWatch to give you a dashboard of your entire estate

## Exam Tips: AWS Pricing
- AWS Pricing Philosophy
  + Pay as you go
  + Pay for what you use
  + Pay less as you use more
  + Pay even less when you reserve capacity
- Capex vs Opex
  + Capex = Capital Expenditure. It means fixed, sunk cost
  + Opex = Operational Expenditure which is where you pay for what you use. Think utility billing!
- 5 Basic Pricing Policies
  + Pay as you go
  + Pay less per unit by using more
  + Pay even less when you reserve
  + Continue to pay less as AWS grows
  + Custom Pricing
- Pricing Models vary across Services
- That said, key principles and best practices are broadly applicable
  + 1. Understand the fundamentals of pricing
  + 2. Start early with Cost optimization
  + 3. Maximize the power of flexibility
  + 4. Use the right pricing model for the job
- 1. Fundamentals of Pricing
  + Three fundamental drivers of cost with AWS:
    - Compute
    - Storage
    - Data Outbound (data leaving your AWS environment)
- 2. Start Early with Cost Optimization
  + It is never too early to start!
  + It's easiest to put cost visibility and control mechanisms in place BEFORE the environment grows too large and complex
  + Bottom line, the earlier you start to manage your costs, the greater the likelihood that it will not hinder your business as it grows and scales
- 3. Maximize the power of flexibility
  + AWS Services are priced independently and transparently
  + Translation: You can choose the right AWS service based on both your technical needs, while keeping ROI in mind
  + It also means you pay for exactly what you need and use and no more
  + No minimum commitments or long-term contracts are required, unless you choose to save money through a reservation model
  + An elastic pricing model allows businesses to focus on their product and customers thereby driving overall business agility!
- 4. Right Pricing Model
  + On Demand
  + Dedicated Instances
  + Spot Instances
  + Reservations
- AWS Free Services
  + Identity and Access Management (IAM)
  + AWS Organizations
  + Amazon VPC
  + Auto Scaling Groups
  + AWS CloudFormation
  + Elastic Beanstalk
  + OpsWorks
  + Consolidated Billing
- Factors driving EC2 Pricing 
  + Clock Hours of Server time
  + Instance Type: Depending on the instance type, you are paying by the "second" or the "hour"
  + Pricing Model
  + Number of Instances
  + Load Balancing (NLB or ALB is more expensive than classic)
  + Detailed Monitoring
  + Elastic IP
  + Auto Scaling
  + Operating Systems and Software Packagess
  + Types
    - On-demand
    - Reserved
    - Spot
    - Dedicated Hosts
- EC2 Reserved Instances
  + The more you pay upfront...
  + ...and the longer the duration of the contract
  + The more the savings! 
  + Around ~60% to 75% savings are possible, especially for 3 year terms with all payments done upfront.
- Factors driving Lambda Pricing
  + Request Pricing
    - Free Tier: 1 million requests per month!
    - $0.20 per 1 million requests 
  + Duration Pricing
    - Duration is calculated from the time your code begins executing until it returns or otherwise terminates, rounded up to 100ms. The price depends on the amount of memory allocated to the function.
    - Free Tier: 400k GB-seconds per month! Up to 3.2 million seconds of compute time.
    - $0.00001667 for every GB-second used thereafter
  + Additional charges:
    - You incur additional charges if your Lambda function uses other AWS services or transfers data.
- Factors driving EBS Pricing
  + Volumes (per GB)
  + Snapshots (per GB)
  + Data Transfer
- Factors driving S3 Pricing
  + Storage Classes (Standard or IA or IA 1AZ or Glacier or Glacier DA or Intelligent Tiering)
  + Storage
  + Number of Requests (GET,PUT,COPY)
  + Data Transfer
- Factors driving Glacier Pricing
  + Storage
  + Data Retrieval Times
  + Retrieval Requests
- Factors driving Snowball Pricing
  + Service Fee per job
    - Snowball 50 TB: $200
    - Snowball 80 TB: $250
  + Daily Charge
    - First 10 days are free, after that it's $15 a day
  + Data Transfer
    - Data Transfer into S3 is free. 
    - Data Transfer out is not
- Factors driving RDS Pricing
  + Clock Hours of Server Timing
  + Database Characteristics (Type of DB: SQL Server etc.)
  + Database Purchase Type (Size of DB instance purchased)
  + Number of Database Instances
  + Provisioned Storage
  + Additional Storage
  + Number of Requests
  + Deployment Types
  + Data Transfer
- Factors driving DynamoDB Pricing
  + Provisioned throughput (write). One Write Capacity Unit (WCU) provides 1 write per second
  + Provisioned throughput (read). One Read Capacity Unit (RCU) provides for 2 reads per second
  + Indexed data storage 
- Factors driving CloudFront pricing
  + Traffic Distribution
  + Number of Requests
  + Data Transfer Out

## Exam Tips: AWS Budgets vs Cost Explorer
- AWS Budgets gives you the ability to set custom budgets that alert you when your costs or usage exceed (or are forecaseted to exceed) your budgeted amount
- Used to budget costs BEFORE they have been incurred
- AWS Cost Explorer lets you visualize, understand, and manage AWS costs and usage over time
- Used to explore costs AFTER they have been incurred

## Exam Tips: AWS Support Plans
- Basic
  + Cost: Free
  + No Tech Support
  + No TAM
  + Cannot open cases, although they can interact on forums
  + Case Response Times in case of Downtimes:
    - NA
- Developer
  + Cost: $29/month or 3% of monthly AWS usage
  + Tech Support only during business hours via email
  + No TAM
  + 1 person can open unlimited number of cases
  + Case Response Times in case of Downtimes:
    - General Guidance will be provided within less than 24 business hours
    - If System is impaired, guidance will be provided within less than 12 business hours
- Business
  + Cost: $100/month or
    - 10% for AWS Monthly Bill from $0 to $10k
    - 7% for AWS Monthly Bill from $10k to $80k
    - 5% for AWS Monthly Bill from $80k to $250k
    - 3% for AWS Monthly Bill above $250k
  + Tech Support includes 24x7 chat, email and phone
  + No TAM
  + Unlimited number of people can open unlimited number of cases
  + Case Response Times in case of Downtimes:
    - General Guidance will be provided within less than 24 hours
    - If System is impaired, guidance will be provided within less than 12 hours
    - If Production System is impaired, guidance will be provided within less than 4 hours
    - If Production System is down, guidance will be provided within less than 1 hour
- Enterprise
  + Cost: $15,000/month or
    - 10% for AWS Monthly Bill from $0 to $150k
    - 7% for AWS Monthly Bill from $150k to $500k
    - 5% for AWS Monthly Bill from $500k to $1M
    - 3% for AWS Monthly Bill above $1M
  + Tech Support includes 24x7 chat, email and phone
  + Includes a TAM and a Billing Concierge service
  + Unlimited number of people can open unlimited number of cases
  + Case Response Times in case of Downtimes:
    - General Guidance will be provided within less than 24 hours
    - If System is impaired, guidance will be provided within less than 12 hours
    - If Production System is impaired, guidance will be provided within less than 4 hours
    - If Production System is down, guidance will be provided within less than 1 hour
    - If Business Critical System is down, guidance will be provided within less than 15 mins

## Exam Tips: Tagging & Resource Groups
- Tags
  + Key/Value pairs attached to AWS Resources
  + Metadata (data about data)
  + Tags can sometimes be inherited
    - If a CloudFormation stack is tagged, all AWS Resources created by CloudFormation will inherit those tags
  + Tags can contain specific information 
    - For EC2, Public & Private IP address
    - For ELB, Port configurations
    - For RDS, Database Engine name
- Resource Groups 
  + They make it easy to group your AWS Resources using the tags that are assigned to them
  + Can contain information such as:
    - Name
    - Department
    - Region
    - Employee ID
- Using Resource Groups, we can apply automation across all AWS Resources that belongs to a certain group. It is using AWS Systems Manager to actually execute the automation
- Resource Groups is NOT a Global service
- Tag Editor
  + Unlike Resource Groups, Tag Editor is a Global Service
  + It allows us to discover resources that meet certain criteria related to tags
  + It also allows us to add additional tags to the resources

## Exam Tips: AWS Organizations & Consolidated Billing
- An Account Management service that enables you to consolidate multiple AWS accounts into an Organization that you can create and centrally manage
- AWS Organizations come in two flavors:
  + All features where you take advantage of Organizational Units, Policies etc.
  + AWS Organizations with just the Consolidated Billing feature
- How Consolidated Billing Works?
  + Paying Account
    Linked Accounts:
    - Test/Dev
    - Production
    - Back Office
   => Monthly Bill
    - Test/Dev = $1456
    - Production = $2400
    - Back Office = $6500
  + Paying Account is independent. It cannot access resources of the other accounts.
  + Currently there is a soft limit of 20 Linked Accounts in Consolidated Billing
  + Billing Alerts:
      - When monitoring (?) is enabled on the paying account, the Billing data for all linked accounts is included
      - You can create Billing alerts per individual account
- Advantages of Consolidated Billing
  + One bill per AWS account
  + Easy to track charges across accounts
  + Volume pricing discount! Consolidated Billing allows you to get volume discounts on **ALL** your accounts. For example:
    - S3 storage consumption across all accounts are added up before applying cost
    - Unused reserved instances for EC2 are applied across the Group
- Best Practices with AWS Organizations
  + Always enable MFA on root account
  + Always use strong & complex password for your root account
  + Paying Account should be used for billing purposes ONLY! Do not deploy resources into Billing Account. Question: In an Organizational setting, should we make root account the paying accoount?
- How to use CloudTrail with AWS Organizations
  + CloudTrail:
    - Per AWS Account and is enabled per Region
    - Can consolidate logs using S3 bucket:
      + Turn on CloudTrail in paying account
      + Create a bucket policy that allows cross-account access
      + Turn on CloudTrail in the other accounts and use the bucket in the paying account
    - Best practice is to use a separate account for Logging!

## AWS Exam Tips: AWS Quick Starts and AWS Landing Zones
- AWS Quick Start is a way of deploying environments quickly using CloudFormation templates built by AWS Solution Architects who are experts in that particular technology
- AWS Landing Zones is a solution that helps customers more quickly set up secure, multi-account AWS environment based on AWS best practices

## Exam Tips: AWS Calculators
- AWS helps you to calculate your costs using a couple of different calculators
- AWS Simple Monthly Calculator
  - Hosted on S3
  - Calculate running costs on AWS on a per month basis. Not designed to be a comparison tool
- AWS Total Cost of Ownership (TCO) Calculator. Renamed to AWS Pricing Calculator
  - Used to compare costs of running your infrastructure on premise vs in the AWS cloud
  - Can be used to generate reports that you can give to your C-level execs to make a business case to move to the cloud
  - This calculator is trying to help you understand what it is costing you on-premise or your co-lo facility
  - This calculator really helps you compare the cost difference if you were doing it on-premise vs on AWS!
- TCO Calculator Components:
  + Server Costs: 
    - Hardware: Server, Rack, Infrastructure, Power Distribution Unit (PDUs) Top-of-Rack (ToR) Switches (+Maintenance)
    - Software: OS, Virtualization License (+Maintenance)
  + Storage Costs
    - Storage Hardware: Storage, Disks, Host Bus Adapters (HBAs), SAN/FC Switches
  + Network Costs
    - Network Hardware: Core/Aggregation Switches, ISP Bandwidth
  + Labor Costs
    - Labor: Server Admin, Virtualization Admin
    - Labor: Storage Admin
    - Labor: Network Admin
  + Overhead:
    - Space
    - Power
    - Cooling

## Exam Tips: Compliance on AWS & AWS Artifact
= How do you know...
  + It is safe to build an App that accepts credit cards on AWS
  + It is safe to store Health Care information on AWS 
- Turns out, AWS goes out and gets tested by various Compliance Programs
  + PCI-DSS
  + HIPAA
  + ...
- To view these compliance reports, go to aws.amazon.com/compliance
- AWS Artifact features a comprehesive list of access-controlled documents relevant to compliance and security in the AWS cloud

## Exam Tips: Shared Responsibility Model
- What is Shared Responsibility Model?
  + While AWS manages security "of the cloud", security "in the cloud" is the responsibility of the Customer!
  + Customers retain control of what security they choose to implement to protect their own content, platform, apps, systems and networks!
  + In many ways, this is NO different than what they would do in an on-site data center.
- Visualizing Shared Responsibility Model
  + Can you, yourself do this in AWS Console or in EC2? If yes, you are likely responsible. Things like..
    - IAM Users
    - Security Groups
    - Patching EC2 instance' Operating System
    - Patching databases running on EC2 instances
  + If not, AWS is likely responsible. Things like..
    - DC Management
    - Security Cameras
    - Cabling
    - Patching
    - Patching RDS Operating System
  + Encryption is a shared responsibility
    - Customer has to turn it ON and use it CORRECTLY (like, if you are providing the Master Key)
    - AWS has to make sure it is done right

## Exam Tips: AWS WAF & AWS Shield
- WAF is Web App Firewall
- Helps your web apps from common web exploits that could affect application availability, compromise security, or consume excessive resources
- WAF works as a Layer 7 firewall and protects web apps from
  + Cross-site scripting attacks
  + SQL injection attacks
- AWS Shield is a "managed" DDoS protection service that safeguards web applications running on AWS
  + Provides always-on detection and automatic inline mitigations
  + Minimizes App downtime and latency
  + No need to engage AWS Support to benefit from DDoS protection
  + 2 Tiers
    - Standard: Automatically turned on in all AWS accounts!
    - Advanced

## Exam Tips: AWS Inspector vs AWS Trusted Advisor vs AWS CloudTrail
- AWS Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS
  + Regional Service
  + Can do Network Assessments and/or Host assessments. For Network Assessments, no AI Agent is required. However, for Host assessment, AI agent is required.
  + Amazon Inspector (AI) Agent: A software that you install on EC2 instances and reviews the configuration based on best practices
  + Assessment target: Currently, AI assessment targets can consist only of EC2 instances!!!!
  + Automatically assesses applications for vulnerabilities or anomalies
  + After performing an assessment, Amazon Inspector produces a detailed list of security findings prioritized by level of severity
  + Reviewed via Amazon Inspector Console or API
- AWS Trusted Advisor is NOT just a security thing
  + Global Service
  + Real-time guidance to help you provision your resources following the best practices
  + Provide guidance on:
    - Cost Optimization
    - Performance
    - Security
    - Fault Tolerance
  + Core Checks and Recommendations are FREE
  + Full Trusted Advisor - Companies with Business and Enterprise Support Plans ONLY
- AWS CloudTrail  
  + Think of it as CCTV :-) 
  + Increases visibility into your user and resource activity by recording **all** AWS Console actions and API calls
  + You can identify 
    - Users and Accounts that called AWS
    - Source IP address
    - When did the call occur

## Exam Tips: AWS Config
- Inventory of your AWS resources
- History of configuration changes to these reqources
- You can define rules to evaluate these configurations for compliance
- Bottom line, it used to monitor your inventory and any/all configuration changes that happen

