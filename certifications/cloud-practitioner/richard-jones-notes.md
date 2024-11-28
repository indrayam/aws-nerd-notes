# Richard Jones: AWS Certified Cloud Practitioner Notes

## AWS Services - Overview

- AWS Global Infrastructure
  - 24 Regions (3 more coming == 27)
  - 77 Availability Zones (~9 more AZs == 86)
  - 217 PoP (205 Edge; 12 Regional Caches)
- Networking & Content Delivery
  - VPC (Virtual Private Cloud)
  - Route53
  - CloudFront
  - DirectConnect
- Compute
  - EC2 (Elastic Compute Cloud)
    - EBS (Elastic Block Store): Virtual disk that you attach to your EC2.
  - ECS (EC2 Container Service) _Not an Exam Topic_
  - Elastic Beanstalk
  - Lambda _Not an Exam Topic_
  - Lightsail _Not an Exam Topic_
- Storage
  - S3 (Simple Storage Service): Object storage.
  - Glacier
  - EFS (Elastic File Service): File storage. Shared. Think NFS!
  - Storage Gateway
- Databases
  - RDS (MySQL, Postgres, MariaDB, Oracle, MS SQLServer, Aurora): Relational Database
  - DynamoDB: NoSQL database.
  - Redshift: Data Warehouse solution
  - Elasticache: K/V store. Caching solution. Think Redis!
- Messaging
  - SNS (Simple Notification Service): App2App and App2Person integration
  - SQS (Simple Query Service): Decouple your application by introducing async processing
  - SES (Simple Email Service): Sending and receiving emails
- Security & Identity
  - IAM (Identity and Access Management) _Comes up in all exams_
  - Inspector: Agent you install on each VM that inspects security posture of the VM
  - Certificate Manager: Think Lets Encrypt.
  - Directory Service
  - WAF (Web Application Firewall): App level firewall protection (Cross-site scripting, SQL injection etc.)
  - Artifacts: Compliance Reports/Documents
- Management Tools
  - Cloud Formation: Turn your infrastructure provisioning effort from imperative scripts to declarative scripts. Infra as Code.
  - CloudWatch: Monitor performance of things like EC2 (Disk Utilization, RAM Utilization etc.)
  - Cloud Trail: Auditing changes to your AWS environment
  - Opsworks: Chef based Config Management
  - Config: Audit + setup alerts
  - Service Catalog: For larger enterprises. Build out what they authorize to be used
  - Trusted Advisor: Give tips on your setup. Example: Cost optimization
- Desktop & App Streaming
  - Workspaces: Think VDI. Streaming desktop to users
  - AppStream 2.0: Streaming desktop "app(s)" to users

## Cloud Computing Basics

- Cloud Computing
  - On demand, self-service
  - elastic
  - metered pricing
- Service Models
  - IaaS
  - PaaS
  - SaaS
- Deployment Models
  - Private
  - Public
  - Hybrid
- What do we want from our Infra/App?
  - High Availability/Resiliency
  - Security
  - Durability
  - Performance
  - Cost-effectiveness
  - Scalability
  - Automation
- What do we want from our Process and/or Workflow?
  - Agile
  - Flexible
  - Efficient
  - Secure
- From a Business Perspective
  - Fast time to market
  - Secure, reliable data center
  - Opex over CapEx
  - No long-term commitments
  - Immediate scalability
  - Easier Cost Allocation
- AWS Cloud Value Proposition
  - On-demand resources (..get what you need, when you need it)
  - Pay as you go (..use what you need)
  - No long term commitments (..feel free to throw things away if you don't need it)
  - Highly automated (repeatable infrastructures)
  - Managed Services (with inherent high-availability, security, durability)

## AWS Global Infrastructure

- AWS Global Infra
  - Regions ~27, Availability Zones ~86, Local Zones ~2, WaveLength Zones ~5, Edge Locations ~205, Regional Edge Caches ~12, Outposts
  - Regions:
    - US West: Oregon, N. California, GovCloud (US-West)
    - US East: Ohio, N. Virgina, GovCloud (US-East)
    - Canada (Central)
    - South America: Sao Paulo
    - Europe: Spain (NEW), Ireland, London, Paris, Milan, Frankfurt, Stockholm
    - Middle East: Bahrain
    - Africa: Cape Town
    - Asia Pacific: Mumbai, Hong Kong, Seoul, Tokyo, Japan (New), Singapore, Indonesia (New), Sydney
    - Mainland China: Beijing, Ningxia
  - Choosing a Region
    - Available Services and Features
    - Cost of Services
    - Latency, Proximity to Users
    - Disaster Recovery
    - Security & Compliance
  - Availability Zones:
    - Each AZ is at least one, sometimes 2 or more, DCs very close to each other
    - AZs are connected with private fiber
  - Edge Locations
    - These locations power AWS CDN (CloudFront) and DNS (Route53) services

## AWS Networking

- Networking using VPC
  - Logically isolated network. It cannot connect to other VPC or outside world without configuration
  - Created per account, per Region
  - Embrace the idea of multiple VPCs for your App Architecture
  - One VPC spans one single Region. Translation: One VPC can use "all" AZs within one Region
  - VPCs can peer with one another. However, in order for that to happen, the CIDR block for the two VPCs trying to peer should not have overlapping IP addresses
  - VPCs allow us to create Internet and VPN Gateways
  - VPCs provide numerous security mechanisms: Security Groups etc.
  - There is a soft limit of 5 VPCs per Region, per Account. However, you can request to have that be increased
- Subnets in VPC
  - Divide VPCs into Subnets
  - Subnets are tied 1:1 with AZs
  - For example, if the VPC CIDR is set to 10.2.0.0/16, by definition it has a total of ~65k addresses it can work (read, subnet) with. If we the region has 3 AZs and we decided to create 3 subnets, one for each AZ, we could create the following subnets:
    - 10.2.0.0/24 can have a maximum of 2^8 - 2 = 254 Hosts in the Subnet
      Network IP: 10.2.0.0/24
      Broadcast IP: 10.2.0.255/24
      Usable IP Addresses: 10.2.0.1 to 10.2.0.254
    - 10.2.1.0/24 can have a maximum of 2^8 - 2 = 254 Hosts in the Subnet
      Network IP: 10.2.1.0/24
      Broadcast IP: 10.2.1.255/24
      Usable IP Addresses: 10.2.1.1 to 10.2.1.254
    - 10.2.2.0/28 can have a maximum of 2^4 - 2 = 14 Hosts in the Subnet
      Network IP: 10.2.2.0/28
      Broadcast IP: 10.2.2.15/28
      Usable IP Addresses: 10.2.2.1 to 10.2.2.14
  - Let's take a Three-Tier Architecture which includes:
    - Public LB Tier
    - Private App Tier
    - Private DB Tier
  - Each tier should have Internet Access, High Availability, Fault Tolerance along with Isolation & Security
  - In such a case, you will end up with potentially 9 unique subnets, 3 for each tier and each tier replicated across 3 AZs
  - For example, if the VPC CIDR is set to 10.2.0.0/16, we could create 9 Subnets, using the following 32 subnets (bit of an overkill) by using /21:
    - 10.2.0.0/21 can have a maximum of 2^11 - 2 = 2046 Hosts in the Subnet
      Network IP: 10.2.0.0
      Broadcast IP: 10.2.7.255
      Usable IP Addresses: 10.2.0.1 to 10.2.7.254
    - 10.2.8.0/21 can have a maximum of 2^11 - 2 = 2044 Hosts in the Subnet
      Network IP: 10.2.8.0
      Broadcast IP: 10.2.15.255
      Usable IP Addresses: 10.2.8.1 to 10.2.15.254
    - 10.2.16.0/21 can have a maximum of 2^11 - 2 = 2044 Hosts in the Subnet
      Network IP: 10.2.16.0
      Broadcast IP: 10.2.23.255
      Usable IP Addresses: 10.2.16.1 to 10.2.23.254
    - 10.2.24.0/21 can have a maximum of 2^11 - 2 = 2044 Hosts in the Subnet
      Network IP: 10.2.24.0
      Broadcast IP: 10.2.31.255
      Usable IP Addresses: 10.2.24.1 to 10.2.31.254
    - ...plus 28 more subnets like this
  - Subnets enable
    - Security via Isolation
    - Because subnets allow us to use multiple AZ, it enables High-Availability
    - Fault Tolerance
    - Performance: In order to achieve the lowest latency and best packet per sec performance, all of the machines would need to be in the same subnet in the same AZ. So, sometimes, you may have to compromise on HA for sake of Performance or vice versa

* Routing & Firewalls
  - In any given VPC, the way traffic flows from it to anywhere else is by way of Routing. In other words, routing is the first line of defense. A firewall of sorts. Why? Because without a route, packets are just not going to flow anywhere. We can whitelist IPs to define where traffic is allowed to flow.
  - If you want hosts in a subnet inside a VPC to talk to the internet, first you create and attach an Internet Gateway (igw-1) to the VPC
  - Then create a Route Table with a definition like the following:
    10.2.0.0/16 => local
    0.0.0.0/0 => igw-1
  - Once you have created a Route Table, you attach the Route Table to the Subnet. By doing this, you enable bi-directional communication to and from the Internet. By doing this, you have technically made the Subnet a "public" subnet. Basically, a subnet is "public" if it has to and from Internet access
  - Network Access Control Lists are firewalls of the subnet as a whole.
  - Security Groups are firewalls at the individual machine level inside a subnet. Once you define Security Groups and add machines to it, "allow" rules can be created referencing the Security Groups, not the individual VMs per se
  - By default, security groups have an implicit "Deny All" rule. All your rules are really for allowing traffic on ports "explicitly"

- AWS Hardware VPN
  - Hardware enabled IPSEC encrypted VPN tunnel
  - On the Amazon side, that tunnel is powered by two physically distinct routers in two distinct facilities
  - On the customer side, it should me made HA too by running 2 routers on their side
  - VPN connectivity is really great for admin work, for low bandwidth type of transfer
- Amazon Direct Connect
  - If there is more data to be pumped between AWS VPCs and Customer premise, Amazon Direct Connect might be better
  - Customer works with a AWS Direct Connect Provider and can setup a 1 or 10 GBPS fiber connection to the Provider
  - DX Providers already have connections to AWS
  - This is definitely prefered if you need lots of bandwidth to flow between your premise and AWS

## AWS Route53

- Amazon Route 53 is Amazon's globally distributed DNS service and leverages those 200 odd edge locations.
- We can register domains since it is also a Registrar
- We can use AWS as stable, reliable and fast nameservers, thanks to the edge locations again
- It supports Public and Private DNS zones
- Automated via API
- Supports Health Checks
- Routing Methods
  - Latency based Routing
  - Geographic Routing
  - Failover Routing, when used in conjunction with Health Checks
  - Weighted Sets

## AWS CloudFront

- CloudFront
  - Create a "distribution" (web or streaming)
  - Connect the distribution to one or more "origins"
  - Configure the "behaviors" of the "distribution" by configuring it
    - To connect to the right origin (say, S3) if the request matches "/assets/\*"
    - To connect to ELB and the Target Groups behind it for everything else ("/\*")
  - Caches content at Edge Location
  - Supports static and dynamic content
  - You can customize the cache behavior
    - Set default TTL for static content
    - Set no TTL for dynamic content
  - Caching behavior can be changed on a per response basis
  - Custom DNS
  - Custom SSL
  - RTMP and HLS streaming

## AWS ELB

- ELB (Elastic Load Balancing)
  - Distributes requests/traffic
  - Spans Region, uses every AZ
  - Managed Service which is inherently secure, resilient and scalable
  - Health Check support
  - Integrates with Auto Scaling
  - Integrates with Route53
  - Offloads SSL, Customize Security Policy
  - 3 types of ELB:
    - Classic: Setup Ports to listen on, Register EC2 instance(s) and define which Port on the EC2 instance(s) to forward traffic to
    - Application Load Balancer: Setup Ports to listen on, Create Target Groups and then use Layer7 content filtering rules to route traffic ('/abc') to a specific Target Group. Allows Dynamic Port mapping so that one EC2 instance can receive traffic on different ports. Not possible with Classic LB.
    - Network Load Balancer: Setup Ports to listen on, Create Target Groups and then forward traffic to Ports on the Target Group. Why? Since NLB is a Layer3 Load Balancer. Handles very long running connections (for months) to backend Targets.

## AWS EC2

- EC2 (Elastic Cloud Compute)
  - VMs
  - Linux or Windows
  - Xen or Nitro hypervisor
  - Bare Metal is available
  - Fixed Prices based on CPU, IO, Disk and Memory
  - Default limit is 20 per account
  - Different Billing Models
    - On-demand
    - Spot Instances
    - Reserved Instances
  - Hourly fees includes license cost of operating system
  - Rack, Chassis => Intel Xeon (CPU)/Motherboard => Hypervisor (Xen or Nitro) => EC2 Instances (VM)
  - There may be that more than one tenant on a single host
  - However, a single customer could get dedicated host
  - AMI - Amazon Machine Images
- EC2 Best Practices
  - Treat them as disposable
  - "Immutable Infrastructure"
  - Logs as Streams
  - Leverage Roles that allows us to control access to other AWS services
  - Automate Deployments
  - Monitor with CloudWatch
  - Enable scaling and self-healing with Auto Scaling

## AWS Auto Scaling

- Auto Scaling
  - Replace failed instances not just in the same AZ, but across AZs in a Region
  - Change capacity according to load (read, demand)
  - Maintain fixed size fleet
  - Works hand-in-hand with CloudWatch
  - Events
    - SNS
    - Lambda
  - Usages
    - Demand-based Auto Scaling
    - Reliable Apps

## AWS Lambda

- Lambda
  - Serverless App Infrastructure
  - Use cases
    - Scheduled Tasks
    - Event Handlers
  - Pay for compute time per 1ms
  - Create functions
    - Online Editor
    - Upload Zip
  - Invoke functions
    - CLI or SDK
    - Events
    - Cron-style schedule
  - AWS Handles
    - Infrastructure
    - Deployment to necessary compute systems
    - Scaling
  - We specify
    - Runtime (Python, etc.)
    - Memory limit
    - Execution timeout

## AWS EBS

- EBS (Elastic Block Store)
  - Increase data durability of an EC2 instance
  - Used when we need higher degree of Random IO
  - Used when we need a mounted filesystem
  - Efficient protocol
  - Can be attached or detached to an EC2 in the same AZ
  - You can create snapshots from an EBS volume which is saved in S3
  - You can copy the snapshot to a different AZ and restore an EBS volume from that

## AWS S3

- S3 (Simple Storage Service)
  - Object Storage
  - Distributed K/V store
  - Buckets and Objects
  - Cluster spans Region
  - Durable to loss of 2 AZs
  - Server side Encryption (AES256)
- S3 Use Cases
  - Static HTML
  - CSS, JavaScript
  - Images
  - Audio/Video files
  - PDF, eBooks
  - Software Downloads
  - Log Collection
  - Backups (EBS Snapshots)
  - Data Lakes

## AWS Glacier

- Archival Storage
- Lower cost vs S3 or EBS
- Write archives
  - Transition to S3
  - Directly upload to S3
- Download via retrieval request
  - 3-5 hr wait
  - $ for faster retrieval
- Lifecycle Rules: Transition from S3 to Glacier using Lifecycle rules automatically
  - For example: After 30 days, archive to Glacier. After 2600 days (7 yrs), permanently delete

## AWS CloudWatch

- Why?
  - Intrumentation is key in Cloud
  - Are we over or under provisioned?
  - What is current demand/load?
  - Where are the bottlenecks - CPU, IO, etc?
  - Are any resources idle?
- CloudWatch Monitoring
  - Collects Metrics
  - Stores Metrics for 2 Weeks
  - Accessible via API
  - Unique Metrics Set per Service
  - Custom Metrics ($/metric)
- CloudWatch Logs
  - Collect logs by streaming
  - Search and filter using specific syntax
    - Create Metric Filters
      - Number of 404s
      - Bytes transfered
      - Number of Exceptions
  - Configure an agent on EC2 instance to watch file(s)
  - Any appending events can be streamed
  - Collect Route53 DNS queries
  - Default retention indefinite
  - Can archive to Amazon S3
  - Stream to Amazon ElasticSearch
  - Process with Lambda
- Usage Examples
  - EC2 Metrics
    - Default 5 min interval
    - Detailed 1 min interval ($/instance)
    - Reported by Hypervisor
  - ELB Metrics
    - Default 1 min interval
    - Requests per min, Healthy Hosts, etc.
  - DynamoDB
    - Read/Write throughput, etc.
- CloudWatch Alarms
  - Triggered based on breach of some threshold
  - Does not signal emergency

## AWS RDS

- Choice of
  - MySQL
  - SQL Server
  - Oracle
  - PostgreSQL
  - MariaDB
  - Amazon Aurora
- Reduced Operational Burden
- Team can focus on App (SQL Queries)
- Benefits
  - Read Replicas
  - Automated
    - OS & DB Installation
    - OS Patches
    - DB Engine Minor Updates
    - Backups
    - Failover
- Multi-AZ deployment
  - HA
  - Physically distinct servers
  - Automatic failover
    - Loss of Network
    - Compute failure
    - Storage failure
  - Production Best Practice
- Backups
  - Performed once per day
  - You control backup window
  - Retained up to 35 days
  - Point-in-time restore
  - All backups are deleted along with deletion of RDS instance
- Backups: Manual Snapshot
  - Performed at any time
  - Can copy to other regions
  - Retained indefinitely
- Aurora
  - Compatible with
    - MySQL 5.6
    - Postgres 9.6
  - 3-5x performance increase
  - Storage up to 64TB
    - Auto-scaled
    - 6 copies across 3 AZs
  - Up to 15 Read Replicas
  - Aurora Multi-Master
  - Aurora Serverless
- DB Migration
  - Dump and import
  - Backup/Restore
  - AWS DB Migration Service
    - Supports widely used DBs
    - Schema Conversion tool
    - Consolidate DBs
    - Heterogenous/Homegenous DBs
    - Continuous replication

## AWS DynamoDB

- NoSQL data store
- Backed by SSD
- Single-digit ms response
- Built-in security, resilience
- Replicated across numerous AZs in the Region
- No limits to storage or throughput
- Provisioned throughput (reads/sec or writes/sec)
- Can auto-scale
- Basics
  - Tables (Collections, Tables)
  - Items (Documents, Rows)
  - Attributes (Fields, Columns)
  - No joins or relationships. Translation: No foreign keys
  - Schema-less
  - Unique primary key required
  - Secondary indexes allowed
  - No table size limit
  - 400kb item size limit
    - Max document size in MongoDB is 16MB. Translation, max size of an Item (or Document or Row) in DynamoDB is only 2.5% of a MongoDB document
    - Max row size in Postgres is 1.6TB. Translation, max size of a MongoDB document is only .001% of a Postgres table
  - Item-level TTL
- Use cases
  - Operational State/History
  - Session/State Storage
  - Shopping Carts
  - Gaming Leaderboards
  - Ad impressions/clicks

## AWS Redshift

- Petabyte scale data warehouse
- Fully managed like RDS
- Fork of Postgres 8.0.2
- SQL compliant as of 8.0.2
- Connect with JDBC/ODBC
- Parallel Queries (Columnar Storage?)
- Ideal of OLAP and BI apps

## AWS Elastic Beanstalk

- Think PaaS like Heroku or Cloud Foundry
- App management platform
- Provides easy entry
- Choice of Java, .NET, Nodejs, Docker
- Simply upload our application
- Ideal for developers
- Automatically handles
  - Capacity provisioning
  - Load balancing
  - Auto scaling
  - Monitoring
  - Deployment (Rollback, Blue/Green)

## Automation in AWS

- Challenges of Manual Process
  - Slow
  - Unreliable
  - Difficult to repeat
  - Lack of documentation/versioning of steps
  - Less secure
- Benefits of Automation
  - Fast and efficient deployments
  - Reliable and consistent
  - Repeatable
  - Documentation/versioning is inherent
  - Secure!
- Tools
  - AWS
    - AWS CLI
    - AWS SDKs
    - AWS CloudFormation
    - AWS Elastic Beanstalk
    - AWS OpsWorks
  - Third Party
    - Terraform
    - Ansible

## AWS CloudFormation

- CloudFormation
  - Template-based infrastructure management
  - Declarative programming. Order of operations is handled by AWS
  - Offers access to full breadth of AWS
  - Infra as Code (stored in Git)
  - Write it once, deploy many time
  - Library for common architectures
  - No imposed model

## AWS WAF

- Layer7 Content filtering
- Support rules to block/allow/count mode
- Integrates with CloudFront
- Protects against
  - SQL Injection
  - Cross-site scripting
- Block based on
  - IP addresses
  - HTTP Headers/Body
  - URI Strings
- Rate Limiting per IP
- Managed Rules for Common Threats (OWASP: Open Web App Security Project)

## AWS Shield

- DDoS protection service
- Available for free to everyone using CloudFront or ELB
- Standard version gives us...
  - UDP Reflection
  - SYN floods
  - SSL renegotiation
  - Slow loris attacks
- Advanced version gives us...
  - Near real-time visibility
  - Integrates with WAF
  - Access to DDoS team

## AWS Shared Responsibility Model

- AWS is responsible for the Security OF the Cloud
  - Physical Security
    - Facilities/Data Centers
    - Edge Locations
    - Rack and Chassis
  - Hypervisor (Xen or Nitro)
  - Network Security
  - Storage
  - APIs
  - Managed Services
    - Databases
    - ...
- Customers is responsible for the Security IN the Cloud
  - Security of the Operating Systems we run
  - Network & Firewall configurations
  - Identity and Access
    - Credentials
    - Permissions using Least Privilege model
  - Security of our Applications
  - Security of our Data
    - S3 Buckets, if not configured correctly, can expose sensitive data
  - Encryption
    - At rest
    - In transit

## AWS IAM

- IAM
  - Authentication
  - Authorization via Policies
  - Users
  - Groups
  - Password Policy
  - MFA
- Users
  - Are created within IAM service
  - Allows them to login to Console
  - Can have long-term access keys
  - Enable per use MFA device
- Groups
  - Groups of users
  - Cannot be nested
- Credential Types
  - Master (root) Account: Email address + Password
  - IAM Users: Username + Password
  - API Access (CLI, SDK): Access Key ID + Secret Key
- Policies
  - Authorization achieved through policies
  - Written in JSON
  - Policy Types
    - Managed Policy (First class objects)
      - AWS Managed
      - Customer Managed
    - Inline Policy (Written inline for a group of users or roles)
      - Not first class objects
  - Create Policies via
    - Generator
    - Hand written (not recommended)
  - Evaluation logic of a policy
    - Defaults to Implicitly DENY
    - Looks through all the policies...
      - Look for explicit DENY
      - Look for explicit ALLOW
- Roles
  - What Not to Do
    - Never embed secrets in Code
    - Never embed secrets in Environment variables
    - Logistical issue with embedding secrets in code anyways..
    - Never share secrets with
      - Third parties
      - Hundreds of Enterprise users
      - Millions of web users (by embedding in a mobile app or web app)
  - The way to avoid all that is through Roles. How?
    - Gives access to automatically rotated temporary credentials (in as little as 15 mins)
    - Roles can be used to delegate permission to
      - EC2 instance
      - AWS Service in order for that service to perform action on our behalf
      - A user (temporarily elevate privileges)
      - Separate account
        - One of our own
        - Vendor or client
- AWS New Account First Steps
  - Enable CloudTrail
  - Create an IAM User with Admin privileges
  - Enable MFA on root account
  - Enable Cost and Usage Report
  - Log out of the root account
  - Log in as Admin user
  - Create additional users, groups, etc.
- IAM Best Practices
  - Root credentials
    - Email address + password
    - Protect at all costs
    - Do not use for day-to-day
    - Enable MFA
  - Rotate Access Keys
  - Follow principle of Least privilege
  - Monitor with CloudTrail
- AWS Organizations
  - Manage multiple AWS Accounts
  - Automate creation of AWS Accounts
  - Service Control Policies control service use
  - Consolidated Billing
    - One billing, many accounts
    - Aggregated volume pricing
    - Reserved instances can be used by all accounts!
  - Detailed Billing
    - Published to S3 bucket
    - Import into spreadsheet
    - Filter/Sort by service, tag, etc.

## AWS Assurance/Compliance

- Certifications/Attestations
  - Third-party independent auditor
- Laws/Regulation/Privacy
- Alignments/Frameworks
- Global Assurance Programs
  - Cloud Security Alliance
  - ISO 9001
  - ISO 27001
  - ISO 27017
  - ISO 27018
  - PCI DSS Level 1
  - SOC 1
  - SOC 2
  - SOC 3
- US Assurance Programs
  - FedRAMP
  - FIPS
  - FISMA
  - HIPAA
  - ITAR
  - MPAA
  - NIST 800-53
- HIPAA Compliance
  - HIPAA => Health Insurance Portability and Accountability Act
  - Designed to secure Protected Health Information (PHI)
  - AWS not "directly" certified
  - Requirements map to FedRAMP and NIST 800-53 which are more stringent than HIPAA
  - AWS provides Business Associate Addendum
- PCI DSS Compliance
  - PCI DSS => Payment Card Industry Data Security Standard)
  - Designed to protect
    - Cardholder Data (CHD)
    - Sensitive authentication Data (SAD)
  - Applies to business that store/process/transmit such data
  - AWS is PCI DSS 3.2 Level 1 compliant
  - Customers are responsible for Card Data Environment (CDE)
  - AWS provides Attestation of Compliance (AOC)
- Achieving Compliance
  - Customer works towards compliance
  - AWS provides necessary documentation
  - Know who is responsible
    - AWS for physical controls
    - Customer for logical controls
  - Know the controls you inherit
  - Know the services in scope
  - Speak with your Account Manager
- Key AWS Services for Auditing & Compliance
  - AWS Artifact
  - AWS Service Catalog
  - AWS CloudTrail
  - AWS Config

## AWS Config

- Resource Inventory
- Configuration History
- Change notifications
- Use pre-made or custom rules to determine compliance against rules
- Enables
  - Compliance auditing
  - Security Analysis
  - Change tracking
  - Ops troubleshooting

## AWS Service Catalog

- Manage catalog of approved IT services
- Achieve consistent governance
- Customer defines
  - Portfolios
  - Products
    - Defined as CloudFormation templates

## AWS Artifact

- Access reports/details of
  - ~2500 security controls
  - On-demand access to AWS security and compliance documents
  - Demonstrate security and compliance of your AWS environments
  - Example: SOC and PCI reports

## AWS CloudTrail

- Records all calls made to AWS APIs
- Turn it on either for a single region or all regions. As part of that, you configure S3 bucket
- Delivers log files to S3 bucket
- Includes
  - Identity
  - Source IP
  - Request/Response details
- Does not record the following. For these, you could use CloudWatch.
  - Operating system logs
  - Database queries
  - App logs

## AWS KMS

- Managed Service
- Create/Manage encryption keys
- Integrates with services that offer encryption services
  - S3
  - EBS
  - RDS
  - Glacier
  - SQS
- Multi-tenant software backed by HSMs

## AWS CloudHSM

- If we want a dedicated/singleton enviornment for keys...
- Single-tenant Hardware Security Module
- FIPS 140-2 Level 3 validated
- On-demand, no upfront costs
- Can enable:
  - SSL offloading
  - Private key storage
  - Transparent data encryption

## Vulnerability and Penetration Testing in AWS

- Permission is required!
- Must request permission using "root" account
- Identify the instances to be tested
- Specify start and end date and time
- AWS does NOT permit testing of
  - m1.small
  - t1.micro
  - t2.nano
- AWS permits testing of
  - EC2
  - RDS
  - Aurora
  - CloudFront
  - API Gateway
  - Lambda
  - Lightsail
  - DNS Zone Walking

## Billing & Pricing

- Cardinal Rule: Remember "What you pay for" and not just "What you Pay"
- EC2 On-demand Pricing
  - No long-term commitments
  - Transform large fixed costs to lower, variable costs
  - Fees include OS license
  - Per hour billed hour forward (Windows)
  - Per sec minimum of 60 secs
- EC2 Reserved Instances
  - Up to 75% discount vs. On-demand
  - Provide capacity reservation
  - 1 to 3 yr term
  - Attributes of the instance
    - Instance type
    - Platform
    - Tenancy
    - AZ (optional)
  - Reserved Instance Types
    - Standard RIs
      - Up to 75% off on-demand
      - Best for steady-state usage
    - Convertible RIs
      - Can change attributes of the instance
      - Also good for steady-state usage
      - Discount is not that high (~54%)
    - Scheduled RIs
      - Available during time window
      - Best for predictable, recurring schedule
- EC2 Spot Pricing
  - Gain discounts on spare capacity
  - Save up to 90% discount vs On-demand
  - Price
    - Set by instance type + AZ
    - Determined by supply/demand
  - Spot instances can be interrupted
  - Great for
    - Flexible start and end times
    - Development/test environments
  - Use cases:
    - Image rendering
    - Video transcoding
    - Analytics
    - Machine Learning
  - Integrated with
    - ASG
    - ECS
    - EMR
    - CloudFormation
- AWS Lambda Pricing
  - Charged per GB per 100ms
  - Charged per 1M request
  - Free Tier
    - 1M requests/month
    - 400 GB-secs/month
  - Additional charges:
    - Bandwidth
    - S3
- Data Transfer Pricing
  - Inbound generally free
  - S3 to CloudFront is free
  - Outbound to internet. Also, applies cross-region traffic
    - $/GB/month
    - Tiered pricing
      - 10/40/100 TB increments
  - Cross-AZ traffic $/GB/month
  - VPC peering $/GB/month
- RDS Pricing
  - Price determined by
    - Instance type
    - Database Engine (license)
    - Reserved Instance discount
  - Multiple AZ deployment 2X $
  - Storage
    - Pay for EBS volume $/GB/month
    - $/provisioned IOPS/month
- DynamoDB Pricing. Remember, DynamoDB automatically adds 10 GB to the storage when certain threshold is reached
  - Charged for "provisioned" throughput. Note, "provisioned" means you pay for not what you consume, but what you configure
    - $/Write capacity unit
    - $/Read capacity unit
  - Charged for storage consumed
- EBS Pricing
  - $/GB/month of "provisioned" storage. Again, you pay for what you provisioned, not what you use.
    - General purpose SSD
    - Provisioned IOPS storage
    - Magnetic Volumes
  - Additional costs for
    - $/provisioned IOPS
    - EBS snapshots to S3
- S3 Pricing
  - $/GB/month of "consumed" storage. You pay for what you consume. No pre-provisioning required.
  - Additional costs for requests
    - PUT, COPY, POST, LIST $/1000
    - GET $/1000
  - Storage classes
    - Frequent
    - Infrequent (Cheaper, but on-demand)
    - Glacier (Cheapest, not on-demand)

## AWS Cost Management

- AWS Calculators
  - AWS Simple Monthly Calculator https://calculator.s3.amazonaws.com/index.html
  - AWS TCO Calculator is now AWS Pricing Calculator: https://calculator.aws
- AWS Cost Explorer
  - Visualizing our current costs in AWS
- AWS Cost and Usage Reports
  - Access highly detailed billing information
  - Written as a CSV file and saved to S3 bucket. Even if multiple accounts are involved
  - Ingested into Redshift or QuickSight
  - Usage for each service
  - Usage for each tag
  - Can aggregate to daily or monthly
- AWS Trusted Advisor
  - Automatically and regularly analyze our environment
  - Offers best practice recommendations
  - Cost optimization
  - Room for improvement in Performance
  - Room for improvement in Security (Think, Cisco Security Buddy)
  - Room for improvement in Fault Tolerance
  - 7 Core Checks
    - S3 Bucket Permissions
    - Security Groups (specific ports unrestricted)
    - IAM Use
    - MFA in root account
    - EBS Public Snapshots
    - RDS Public Snapshots
    - Service Limits
  - Notifications and Programmatic Access are not available until you have higher degree of Amazon Support

## AWS Support

- AWS Support Plans
  - Basic
  - Developer
  - Business
  - Enterprise
- Basic Support
  - Core Trusted Advisor Checks
  - No technical support
  - Can submit
    - Bugs
    - Feature Requests
    - Service Limit Increases
- Developer Support
  - Core Trusted Advisor Checks
  - Business Hours access to Cloud Support Associates
  - Guidance < 24 business hours
  - Impairments < 12 business hours
  - Only offers "General" guidance
- Business Support Plans
  - Full set of Trusted Advisor checks
  - 24/7 access to Cloud Support Engineers
  - Email, chat, phone
  - 1-24 hour response
  - Offers contextual guidance based on use-case
  - On a per account basis
- Enterprise Support
  - Full set of Trusted Advisor checks
  - 24/7 access to Cloud Support Engineers
  - Email, chat, phone
  - 15min to 24 hour response
  - Offers consultative review of our architecture
  - Applies to all accounts
  - Access to a Well-Architected Review
  - Access to online labs
  - Dedicated Technical Account Manager
