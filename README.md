# AWS Certified Cloud Practitioner CLF-C02

# table-of-contents
1. [Cloud Computing](#cloud-computing)
2. [AWS IAM Identity & Access Management](#aws-iam-identity-access-management)
3. [Amazon EC2](#amazon-ec2)
4. [Amazon EC2 Instance Storage](#amazon-ec2-instance-storage)
5. [Elastic Load Balancing & Auto Scaling Group](#elastic-load-balancing--auto-scaling-group)
6. [Amazon S3](#amazon-s3)
7. [Databases & Analytics](#databases--analytics)
8. [Other Compute Services, Lambda](#other-compute-services)
9. [Deploying & Managing Infrastructure at Scale](#deploying--managing-infrastructure-at-scale)
10. [Global Infrastructure](#global-infrastructure)
11. [Cloud Integration](#cloud-integration)
12. [Cloud Monitoring](#cloud-monitoring)
13. [Amazon VPC](#amazon-vpc)
14. [Security & Compliance](#security--compliance)
15. [Machine Learning](#machine-learning)
16. [Account Management, Billing, & Support](#account-management-billing--support)


# cloud-computing
| Global Services                | Region-scoped Services                        |
|--------------------------------|-----------------------------------------------|
| Identity and Access Management (IAM) | Amazon EC2 (Infrastructure as a Service) |
| Route 53 (DNS service)         | Elastic Beanstalk (Platform as a Service)     |
| CloudFront (Content Delivery Network) | Lambda (Function as a Service)         |
| WAF (Web Application Firewall) | Rekognition (Software as a Service)           |
- [AWS Services by Region](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)
[Back to the top](#table-of-contents)

# AWS IAM Identity & Access Management
### aws-iam-identity--access-management

| Item          | Description                                                      |
|---------------|------------------------------------------------------------------|
| Users         | Mapped to a physical user, has a password for AWS Console        |
| Groups        | Contains users only                                              |
| Policies      | JSON document that outlines permissions for users or groups      |
| Roles         | Used for EC2 instances or AWS services                            |
| Security      | MFA(Multi Factor Authentication) + Password Policy               |
| Access Keys   | Access AWS using the CLI or SDK                                  |
| Audit         | IAM Credential Reports(**Account level**) & IAM Access Advisor(**user level**)                      |

### Access AWS
| Item                 | Description                                                             |
|----------------------|-------------------------------------------------------------------------|
| AWS CLI              | (Command Line Interface) Manage your AWS services using the command line |
| AWS SDK              | (Software Developer Kit) Manage your AWS services using a programming language(ex. python) |
| AWS Management Console | Web-based user interface to manage AWS services                       |


[Back to the top](#table-of-contents)
# EC2
### amazon-ec2
![ec2](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1175.PNG)

| EC2 Section – Summary                                      | Description                                                        |
|------------------------------------------------------------|--------------------------------------------------------------------|
| EC2 Instance                                               | AMI (OS) + Instance Size (CPU + RAM) + Storage + Security Groups + EC2 User Data |
| Security Groups                                            | Firewall attached to the EC2 instance                              |
| EC2 User Data                                              | Script launched at the first start of an instance                  |
| EC2 Instance Role                                          | Link to IAM roles                                                  |
| Purchasing Options                                         | On-Demand, Spot, Reserved (Standard + Convertible), Dedicated Host, Dedicated Instance |

### Communicate with EC2
| Method                  | Description                                           |
|-------------------------|-------------------------------------------------------|
| SSH                     | Start a terminal into our EC2 Instances (port 22)     |
| EC2 Instance connect    | Connect to your EC2 instance within your browser      |



### EC2 Instance Storage – Summary  
| EC2 Instance Storage – Summary                             | Description                                                        |
|------------------------------------------------------------|--------------------------------------------------------------------|
| EBS volumes  EBS (Elastic Block Store)                     | Network drives attached to one EC2 instance at a time              |
|                                                            | Mapped to an Availability Zone                                     |
|                                                            | Can use EBS Snapshots for backups / transferring EBS volumes across AZ |
| AMI(Amazon machine image)                                  | Create ready-to-use EC2 instances with our customizations          |
| EC2 Image Builder                                          | Automatically build, test, and distribute AMIs                     |
| EC2 Instance Store                                         | High-performance hardware disk attached to our EC2 instance        |
|                                                            | Lost if our instance is stopped / terminated                       |
| EFS(Elastic File System)                                   |Manage NFS(Network file system), can be attached to 100s of instances in a region |
| EFS-IA                                                     | Cost-optimized storage class for infrequently accessed files       |
| FSx for Windows                                            | Network File System for Windows servers                            |
| FSx for Lustre                                             | High Performance Computing Linux file system                       |

[Back to the top](#table-of-contents)

| EC2 Instances Purchasing Options                          | Description                                                                                                    | Example                                                                                         |
|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| EC2 On Demand                                             | Has the highest cost but no upfront payment                                                                    | Like coming and staying in a resort whenever we like, we pay the full price                    |
|                                                           | No long-term commitment                                                                                        |                                                                                                 |
|                                                           | Recommended for short-term and uninterrupted workloads, where you can't predict how the application will behave |                                                                                                 |
| EC2 Reserved Instances (1 & 3 years)                      | Up to 72% discount compared to On-demand                                                                       | Like planning ahead and if we plan to stay for a long time, we may get a good discount          |
|                                                           | Recommended for steady-state usage applications (think database)                                               |                                                                                                 |
|                                                           | You can buy and sell in the Reserved Instance Marketplace                                                      |                                                                                                 |
|                                                           | Convertible Reserved Instance:                                                                                 |                                                                                                 |
|                                                           | Can change the EC2 instance type, instance family, OS, scope and tenancy                                       |                                                                                                 |
|                                                           | Up to 66% discount                                                                                             |                                                                                                 |
| EC2 Savings Plans (1 & 3 years)                           | Get a discount based on long-term usage (up to 72% - same as RIs)                                              | Pay a certain amount per hour for a certain period and stay in any room type (e.g., King, Suite, Sea View, ...) |
|                                                           | Commit to a certain type of usage ($10/hour for 1 or 3 years)                                                  |                                                                                                 |
|                                                           | Usage beyond EC2 Savings Plans is billed at the On-Demand price                                                |                                                                                                 |
|                                                           | Locked to a specific instance family & AWS region (e.g., M5 in us-east-1)                                      |                                                                                                 |
|                                                           | Flexible across:                                                                                               |                                                                                                 |
|                                                           | Instance Size (e.g., m5.xlarge, m5.2xlarge)                                                                    |                                                                                                 |
|                                                           | OS (e.g., Linux, Windows)                                                                                      |                                                                                                 |
|                                                           | Tenancy (Host, Dedicated, Default)                                                                             |                                                                                                 |
| EC2 Spot Instances                                         | Can get a discount of up to 90% compared to On-demand                                                          | The hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms. You can get kicked out at any time |
|                                                           | The MOST cost-efficient instances in AWS                                                                       |                                                                                                 |
|                                                           | Can lose instances (less reliable)                                                                             |                                                                                                 |
| EC2 Dedicated Hosts                                        | Book an entire physical server, control instance placement                                                     | We book an entire building of the resort                                                        |
|                                                           | The most expensive option                                                                                      |                                                                                                 |
|                                                           | Ideal for companies with strong regulatory or compliance needs                                                 |                                                                                                 |
| EC2 Dedicated Instances                                    | Instances run on hardware that’s dedicated to you                                                              |                                                                                                 |
|                                                           | May share hardware with other instances in the same account                                                    |                                                                                                 |
| Capacity Reservations                                      | Reserve capacity in a specific AZ for any duration                                                             | You book a room for a period with full price even if you don’t stay in it                       |


# Elastic Load Balancing & Auto Scaling Groups Section
#### elastic-load-balancing-auto-scaling-group

| Scaling Type         | Description                                                      |
|----------------------|------------------------------------------------------------------|
| **Vertical Scaling** | Increase instance size (= scale up / down)                       |
|                      | • From: t2.nano - 0.5G of RAM, 1 vCPU                            |
| **Horizontal Scaling**| Increase number of instances (= scale out / in)                  |
|                      | • Auto Scaling Group                                             |
|                      | • Load Balancer                                                  |
| **High Availability**| Run instances for the same application across multi AZ           |
|                      | • Auto Scaling Group multi AZ                                    |
|                      | • Load Balancer multi AZ                                         |

### Scalability, Elasticity 
| Concept              | Description                                                                                      |
|----------------------|--------------------------------------------------------------------------------------------------|
| **Scalability**      | Ability to accommodate a larger load by making the hardware stronger (scale up), or by adding nodes (scale out).|
|                      | • Increase instance size (scale up).                                                             |
|                      | • Increase number of instances (scale out).                                                      |
| **Elasticity**       | Once a system is scalable, elasticity means that there will be some “auto-scaling” so that the system can scale based on the load.|
|                      | • This is “cloud-friendly”: pay-per-use, match demand, optimize costs.                           |



| ELB & ASG – Summary                                        | Description                                                        |
|------------------------------------------------------------|--------------------------------------------------------------------|
| High Availability vs Scalability                           | Vertical and horizontal scalability, Elasticity, and Agility in the Cloud |
| ***Elastic Load Balancers(ELB)***                          | Distribute traffic across backend EC2 instances, can be Multi-AZ |
|                                                            | Supports health checks                                             |
|                                                            | 4 types: Classic (old), Application (HTTP – L7), Network (TCP – L4), Gateway (L3) |
| ***Auto Scaling Groups(ASG)***                             | Implement Elasticity for your application, across multiple AZ |
|                                                            | Scale EC2 instances based on the demand on your system, replace unhealthy instances |
|                                                            | Integrated with the ELB                                            |

[Back to the top](#table-of-contents)

# S3
![s3](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1178.jpg)
### amazon-s3
| Amazon S3 – Summary                                       | Description                                                                 |
|-----------------------------------------------------------|-----------------------------------------------------------------------------|
| Buckets vs Objects                                        | Global unique name, tied to a region                                        |
| S3 security                                               | IAM policy, S3 Bucket Policy (public access), S3 Encryption                 |
| S3 Websites                                               | Host a static website on Amazon S3                                          |
| S3 Versioning                                             | Multiple versions for files, prevent accidental deletes                     |
| S3 Replication                                            | Same-region or cross-region, must enable versioning                         |
| S3 Storage Classes                                        | Standard, IA, 1Z-IA, Intelligent, Glacier (Instant, Flexible, Deep)         |
| Snow Family                                               | Import data onto S3 through a physical device, edge computing               |
| OpsHub                                                    | Desktop application to manage Snow Family devices                           |
| Storage Gateway                                           | Hybrid solution to extend on-premises storage to S3                         |

## Performance across the S3 storage classes
| Feature                          | S3 Standard          | S3 Intelligent-Tiering*      | S3 Express One Zone** | S3 Standard-IA                  | S3 One Zone-IA**           | S3 Glacier Instant Retrieval     | S3 Glacier Flexible Retrieval*** | S3 Glacier Deep Archive***       |
|----------------------------------|----------------------|------------------------------|-----------------------|----------------------------------|----------------------------|----------------------------------|----------------------------------|----------------------------------|
| **Use cases**                    | General purpose storage for frequently accessed data | Automatic cost savings for data with unknown or changing access patterns | High performance storage for your most frequently accessed data | Infrequently accessed data that needs millisecond access | Re-creatable infrequently accessed data | Long-lived data that is accessed a few times per year with instant retrievals | Backup and archive data that is rarely accessed and low cost | Archive data that is very rarely accessed and very low cost |
| **First byte latency**           | milliseconds         | milliseconds                  | single-digit milliseconds | milliseconds                    | milliseconds               | milliseconds                    | minutes or hours                 | hours                            |
| **Durability**                   | 99.999999999% (11 nines) | 99.999999999% (11 nines)     | 99.999999999% (11 nines) | 99.999999999% (11 nines)        | 99.999999999% (11 nines)   | 99.999999999% (11 nines)        | 99.999999999% (11 nines)        | 99.999999999% (11 nines)        |
| **Designed for availability**    | 99.99%               | 99.9%                         | 99.95%                  | 99.9%                           | 99.5%                      | 99.9%                           | 99.99%                          | 99.99%                          |
| **Availability SLA**             | 99.9%                | 99%                           | 99.9%                   | 99%                             | 99%                        | 99%                             | 99.9%                            | 99.9%                            |
| **Availability Zones**           | ≥3                   | ≥3                            | 1                        | ≥3                              | 1                          | ≥3                              | ≥3                              | ≥3                               |
| **Minimum storage duration charge** | N/A               | N/A                           | 1 hour                   | 30 days                         | 30 days                    | 90 days                         | 90 days                         | 180 days                        |
| **Retrieval charge**             | N/A                  | N/A                           | N/A                      | per GB retrieved               | per GB retrieved           | per GB retrieved               | per GB retrieved               | per GB retrieved               |
| **Lifecycle transitions**        | Yes                  | Yes                           | No                       | Yes                             | Yes                        | Yes                             | Yes                             | Yes                              |
[Back to the top](#table-of-contents)

# Databases & Analytics Summary in AWS
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1179.jpg)
### databases--analytics

| **Category**                     | **Service**                                                                                   |
|----------------------------------|-----------------------------------------------------------------------------------------------|
| Relational Databases - OLTP      | RDS & Aurora (SQL)                                                                            |
| Differences                      | Multi-AZ, Read Replicas, Multi-Region                                                         |
| In-memory Database               | ElastiCache                                                                                   |
| Key/Value Database               | DynamoDB (serverless) & DAX (cache for DynamoDB)                                              |
| Warehouse - OLAP                 | Redshift (SQL)                                                                                |
| Hadoop Cluster                   | EMR                                                                                           |
| Athena                           | Query data on Amazon S3 (serverless & SQL)                                                    |
| QuickSight                       | Dashboards on your data (serverless)                                                          |
| DocumentDB                       | “Aurora for MongoDB” (JSON – NoSQL database)                                                  |
| Amazon QLDB                      | Financial Transactions Ledger (immutable journal, cryptographically verifiable)               |
| Amazon Managed Blockchain        | Managed Hyperledger Fabric & Ethereum blockchains                                             |
| Glue                             | Managed ETL (Extract Transform Load) and Data Catalog service                                 |
| Database Migration               | DMS                                                                                           |
| Neptune                          | Graph database                                                                                |
| Timestream                       | Time-series database                                                                          |

[Back to the top](#table-of-contents)

# Other Compute Services, Lambda
### other-compute-services
| **Feature**                | **Details**                                                      |
|----------------------------|------------------------------------------------------------------|
| Docker                     | Container technology to run applications                         |
| ECS                        | Run Docker containers on EC2 instances                           |
| Fargate                    | Run Docker containers without provisioning the infrastructure     |
|                            | Serverless offering (no EC2 instances)                           |
| ECR                        | Private Docker Images Repository                                 |
| Batch                      | Run batch jobs on AWS across managed EC2 instances               |
| Lightsail                  | Predictable & low pricing for simple application & DB stacks     |

### Lambda 
| **Feature**                        | **Details**                                               |
|------------------------------------|-----------------------------------------------------------|
| Lambda                             | Serverless, Function as a Service, seamless scaling, reactive |
| Lambda Billing                     | By the time run x by the RAM provisioned                  |
|                                    | By the number of invocations                              |
| Language Support                   | Many programming languages except (arbitrary) Docker      |
| Invocation Time                    | Up to 15 minutes                                          |
| Use Cases                          | Create Thumbnails for images uploaded onto S3             |
|                                    | Run a Serverless cron job                                 |
| API Gateway                        | Expose Lambda functions as HTTP API                       |

[Back to the top](#table-of-contents)

# Deploying & Managing Infrastructure at Scale
### deploying--managing-infrastructure-at-scale

| Service           | Description                                                                                           |
|-------------------|-------------------------------------------------------------------------------------------------------|
| CloudFormation    | (like you write a npm to install all the package)Infrastructure as Code, works with almost all of AWS resources. Repeat across Regions & Accounts.     |
| Beanstalk         | Platform as a Service (PaaS), limited to certain programming languages or Docker. Deploy code consistently with a known architecture: ex, ALB + EC2 + RDS. |
| CodeDeploy        | Deploy & upgrade any application onto servers.                                                        |
| Systems Manager   | Patch, configure, and run commands at scale.                                                          |

### Developer Services
| Service       | Description                                                                         |
|---------------|-------------------------------------------------------------------------------------|
| CodeCommit    | Store code in private git repository (version controlled)                           |
| CodeBuild     | Build & test code in AWS                                                            |
| CodeDeploy    | Deploy code onto servers                                                            |
| CodePipeline  | Orchestration of pipeline (from code to build to deploy)                            |
| CodeArtifact  | Store software packages / dependencies on AWS (Work with managed tools, NPM, yarn )                                     |
| CodeStar      | Unified view for allowing developers to do CICD and code                            |
| Cloud9        | Cloud IDE (Integrated Development Environment) with collaboration features          |
| AWS CDK       | Define your cloud infrastructure using a programming language                       |

[Back to the top](#table-of-contents)

# Global Infrastructure- Global Applications in AWS
### global-infrastructure 
- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
- global application is an application deployed in multiple geographies
-  could be Regions and / or Edge Locations
1. Decreased Latency 
2. Disaster Recovery (DR)
3. Attack protection
| Category                      | Description**                                      |
|-----------------------------------|------------------------------------------------------|
| Regions                       | For deploying applications and infrastructure        |
| Availability Zones            | Made of multiple data centers                        |
| Edge Locations (Points of Presence) | For content delivery as close as possible to users   |

### Route 53 Routing Policies
1. SIMPLE ROUTING POLICY
2. WEIGHTED ROUTING POLICY
3. LATENCY ROUTING POLICY
4. FAILOVER ROUTING POLICY (Disaster Recovery)
| Service                    | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| Route 53                   | Global Managed DNS (Domain Name System): Great to route users to the closest deployment with least latency. Great for disaster recovery strategies |
| CloudFront                 | Global Content Delivery Network (CDN): Replicate part of your application to AWS Edge Locations – decrease latency. Cache common requests – improved user experience and decreased latency |
| S3 Transfer Acceleration   | Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region                     |
| AWS Global Accelerator     | Improve global application availability and performance using the AWS global network |

- edge Location
A site that CloudFront uses to cache copies of your content for faster delivery to users at any location.

| Feature                     | **CloudFront**                                                                 | **S3 Cross Region Replication**                                               |
|---------------------------------|--------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| **Network Type**                | Global Edge network                                                            | Must be setup for each region you want replication to happen                  |
| **Content Caching**             | Files are cached for a TTL (Time-to-Live, maybe a day)                         | Files are updated in near real-time                                           |
| **Content Type**                | Great for static content that must be available everywhere                     | Great for dynamic content that needs to be available at low-latency in few regions |
| **Access**                      | Read and write                                                                 | Read only                                                                     |


| Service          | Description                                                                                  |
|------------------|----------------------------------------------------------------------------------------------|
| AWS Outposts     | Deploy Outposts Racks in your own Data Centers to extend AWS services                        |
| AWS WaveLength   | Brings AWS services to the edge of the 5G networks – Ultra-low latency applications          |
| AWS Local Zones  | Bring AWS resources (compute, database, storage, ...) closer to your users – Good for latency-sensitive applications |


[Back to the top](#table-of-contents)

 # Cloud Integration
 ### cloud-integration
 | Service     | Description                                                                                                            |
|-------------|------------------------------------------------------------------------------------------------------------------------|
| SQS         | Queue service in AWS. Multiple producers, messages are kept up to 14 days. Multiple consumers share the read and delete messages when done. Used to decouple applications in AWS. |
| SNS         | Notification service in AWS. Subscribers: Email, Lambda, SQS, HTTP, Mobile... Multiple subscribers, send all messages to all of them. No message retention. |
| Kinesis     | Real-time data streaming, persistence, and analysis.                                                                  |
| Amazon MQ   | Managed message broker for ActiveMQ and RabbitMQ in the cloud (MQTT, AMQP.. protocols).                               |

[Back to the top](#table-of-contents)


# Cloud Monitoring
### cloud-monitoring
![cloud-watch](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1180.jpg)

| Service                     | Description                                                                                                              |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------|
| CloudWatch                  | Metrics: Monitor the performance of AWS services and billing metrics. Alarms: Automate notification, perform EC2 action, notify to SNS based on metric. Logs: Collect log files from EC2 instances, servers, Lambda functions... Events (or EventBridge): React to events in AWS, or trigger a rule on a schedule. |
| CloudTrail                  | Audit API calls made within your AWS account. CloudTrail Insights: Automated analysis of your CloudTrail Events.          |
| X-Ray                       | Trace requests made through your distributed applications.                                                                |
| AWS Health Dashboard        | Status of all AWS services across all regions.                                                                            |
| AWS Account Health Dashboard| AWS events that impact your infrastructure.                                                                               |
| Amazon CodeGuru             | Automated code reviews and application performance recommendations.                                                       |

[Back to the top](#table-of-contents)

# Amazon VPC
### amazon-vpc
![vpc](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1174.jpg)

| Topic                      | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| VPC                        | Virtual Private Cloud                                                       |
| Subnets                    | Tied to an AZ, network partition of the VPC                                  |
| Internet Gateway           | At the VPC level, provides Internet Access                                   |
| NAT Gateway / Instances    | Provide internet access to private subnets                                   |
| NACL                       | Stateless, subnet rules for inbound and outbound                             |
| Security Groups            | Stateful, operate at the EC2 instance level or ENI                           |
| VPC Peering                | Connect two VPCs with non-overlapping IP ranges, non-transitive              |
| Elastic IP                 | Fixed public IPv4, ongoing cost if not in use                                |
| VPC Endpoints              | Provide private access to AWS Services within VPC                            |
| PrivateLink                | Privately connect to a service in a 3rd party VPC                            |
| VPC Flow Logs              | Network traffic logs                                                         |
| Site to Site VPN           | VPN over public internet between on-premises DC and AWS                      |
| Client VPN                 | OpenVPN connection from your computer into your VPC                          |
| Direct Connect             | Direct private connection to AWS                                             |
| Transit Gateway            | Connect thousands of VPCs and on-premises networks together                  |

-  VPN stands for Virtual Private Network. It is a service that enables you to securely connect your on-premises network or a remote device (such as a laptop or mobile device) to your AWS Virtual Private Cloud (VPC) over an encrypted connection via the public internet.
[Back to the top](#table-of-contents)




[Security & Compliance](#security--compliance)




[Machine Learning](#machine-learning)