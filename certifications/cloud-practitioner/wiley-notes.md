# Wiley Flash Cards

- What is the best source of accurate, up-to-date information on the costs of AWS services?
  + Amazon’s online documentation, where the URL will usually follow this format: aws.amazon.com/<service-name>/pricing/
- Some EC2 instance types come with data volumes that are physically connected to the instance’s physical host. What are these
  + EC2 instance store volumes
- Which S3 service class will provide greater data availability: S3 Standard-IA or S3 One Zone-IA? 
  + S3 Standard-IA, offering 99.9 percent availability against 99.5 percent for S3 One Zone-IA
- You know you’ve got an EC2 instance running, but it doesn’t show up in the AWS Management Console on the EC2 page. What could the problem be?
  + The Region currently selected in the console is not the same Region where your instance is running.
- What type of IAM entity is assumed by processes (rather than people) to gain authorized access to AWS resources?
  + Role
- Which AWS service lets you set a desired account-wide configuration profile and regularly audit your account settings to ensure you’re in compliance?
  + AWS Config
- What, in terms of AWS deployments, is a “multitiered” environment?
  + Any deployment that includes multiple classes of resources. Combining front-end EC2 web servers, an RDS database instance, and an Elastic Load Balancer would be a common example.
- Which RDS instance class will be most cost-effective for nonproduction testing requirements where you don’t need consistent high performance?
  + The Burstable Performance instance class
- Which of these is not a category of checks offered by AWS Trusted Advisor: Cost Optimization, Performance, Security, Fault Tolerance, or Connectivity?
  + Connectivity
- Which AWS service identifies insecure, inefficient, or wasteful configurations on your account?
  + AWS Trusted Advisor
- True/False: You can use the AWS Console Mobile Application to manage Simple Storage Service (S3) buckets.
  + True
- When you’re provisioning an EC2 instance, which parameter controls the hardware features your instance will be given?
  + Instance Type
- True/False: An AWS Region consists of two or more Availability Zones that connect to each other over the public internet.
  + False: AZs within a single Region are connected directly over a low-latency network.
- What are the two primary elements that allow cloud providers like AWS to provide many low consumption costs for customers?
  + Virtualization and Operational scale
- _______________ is a scalable service that converts media files to formats that better fit your application’s target usage.
  + AWS Elastic Transcoder
- How can you optimize your S3 storage costs and performance by automating the transfer of data between storage classes?
  + By enabling Lifecycle Management
- Is it possible to directly connect local data archives that expect a tape backup interface with S3-based buckets?
  + Yes, using an AWS Storage Gateway appliance
- What is an effective way to ensure that the resources running in a busy AWS account are easy to identify and administrate?
  + Apply resource tags consistently
- How does AWS describe the integration of third-party authentication services with IAM authorization tools?
  + Federation (Identity Providers)
- How much would Business support cost for an account that consumed $60,000 dollars in a given month?
  + $4200
- You can closely analyze the way your account resources are being consumed and how much they’re costing by using which AWS service?
  + AWS Cost & Usage Reports