# AWS Certified Cloud Practitioner CLF-C02
![aws-import-services](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-import-services.png)
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
17. [Other](#other)


# cloud-computing
| Global Services                | Region-scoped Services                        |
|--------------------------------|-----------------------------------------------|
| Identity and Access Management (IAM) | Amazon EC2 (Infrastructure as a Service) |
| Route 53 (DNS service)         | Elastic Beanstalk (Platform as a Service)     |
| CloudFront (Content Delivery Network) | Lambda (Function as a Service)         |
| WAF (Web Application Firewall) | Rekognition (Software as a Service)           |
- [AWS Services by Region](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)

Cloud Computing can be broadly divided into three types: 
1. Infrastructure as a Service (IaaS), ex. AWS EC2 
2. Platform as a Service (PaaS), ex. AWS Elastic Beanstalk
3. Software as a Service (SaaS). ex. Lambda
- [Types of Cloud Computing](https://aws.amazon.com/types-of-cloud-computing/)

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
### Communicate with EC2

| Method                  | Description                                           |
|-------------------------|-------------------------------------------------------|
| SSH                     | Start a terminal into your EC2 instance (port 22) (Mac, Linux, Windows>=10)     |
| EC2 Instance Connect     | Connect to your EC2 instance within your browser (Mac, Linux, Windows)    |
| PuTTY                   | Use PuTTY (a free SSH client) to securely connect to your EC2 instance on Windows, using the private key (port 22)(Windows only) |



### EC2 Instance Storage – Summary  
#### amazon-ec2-instance-storage
| EC2 Instance Storage – Summary                             | Description                                                        |
|------------------------------------------------------------|--------------------------------------------------------------------|
| EBS volumes  EBS (Elastic Block Store)                     | 1. Network drives attached to one EC2 instance at a time              |
|                                                            | 2. It’s locked to an Availability Zone (AZ)                                 |
|                                                            | 3. Can use EBS Snapshots for backups / transferring EBS volumes across AZ |
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

Summary of Time-Based EC2 Pricing:
- On-Demand: Billed by the **second** or hour (with a **minimum of 60 seconds**).
- Reserved Instances: Pay upfront or per hour based on 1- or 3-year commitments.
- Spot Instances: Billed by the second or hour, depending on availability and duration of use.
- Savings Plans: Commitment-based billing (1 or 3 years), but offers flexible billing across compute services.
- Dedicated Hosts: Billed by the **hour** for a physical server.



# Elastic Load Balancing & Auto Scaling Groups Section

### elastic-load-balancing--auto-scaling-group

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

### Load balancers offered by AWS:
- Application Load Balancer (HTTP / HTTPS only) – Layer 7
- Network Load Balancer (ultra-high performance, allows for TCP) – Layer 4
- Gateway Load Balancer – Layer 3
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-ec2-load-balancer.png)

![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-EBS-EFS.png)
### compare EBS and EFS
| Service                               | Type                | Characteristics                                                                                                                                                        |
|---------------------------------------|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Amazon EFS (Elastic File System)       | Network File System | - (ex. Google Drive share) <br/> - Ideal for applications that require shared file storage with multiple EC2 instances. <br/> - Automatically replicates data across multiple Availability Zones (AZs) within a region, ensuring high durability and availability. |
| Amazon EBS (Elastic Block Store)       | Block Storage       | - (ex. your own disk) <br/> - Best suited for single EC2 instance storage, functioning like a hard drive attached to a single instance. <br/> - Data is automatically replicated within the same Availability Zone for durability. Snapshots can be used for backups and are stored in S3, providing added durability across regions. |

- Question 12
Which of the following is best-suited for load-balancing HTTP and HTTPS traffic?

- ()AWS Auto Scaling
- ()Network Load Balancer
- ()Your answer is correct
- ()Application Load Balancer
- ()System Load Balancer

- answer:Application Load Balancer
[Back to the top](#table-of-contents)

# S3
![s3](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1178.jpg)
![avail-durable](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-s3-ava-dura.jpg)
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



###  S3 Price table

| **Storage Class**                               | **Storage Cost (per GB/month)**                           | **Retrieval Cost (per GB)**            | **Retrieval Speed**         |
|------------------------------------------------|---------------------------------------------------------|---------------------------------------|----------------------------|
| S3 Standard                                    | $0.023 (first 50 TB), $0.022 (next 450 TB), $0.021 (over 500 TB) | Free                                  | Immediate                  |
| S3 Intelligent-Tiering (Frequent Access)       | $0.023                                                  | Varies                                | Immediate or standard      |
| S3 Intelligent-Tiering (Infrequent Access)     | $0.0125                                                 | Varies                                | Immediate or standard      |
| S3 Standard-IA                                 | $0.0125                                                 | $0.01                                 | Immediate                  |
| S3 One Zone-IA                                 | $0.01                                                   | $0.01                                 | Immediate                  |
| S3 Glacier Instant Retrieval                   | $0.004                                                  | $0.03                                 | Instant                    |
| S3 Glacier Flexible Retrieval                  | $0.0036                                                 | $0.01 - $0.03                         | Minutes to hours           |
| S3 Glacier Deep Archive                        | $0.00099                                                | $0.02 (Bulk), $0.10 (Standard)         | Hours (up to 12 hours)     |

Question 10

A photo sharing web application wants to store thumbnails of user-uploaded images on Amazon Simple Storage Service (Amazon S3). The thumbnails are rarely used but need to be immediately accessible from the web application. The thumbnails can be regenerated easily if they are lost. Which is the most cost-effective way to store these thumbnails on Amazon Simple Storage Service (Amazon S3)?

- Use Amazon S3 Standard to store the thumbnails- 
- Use Amazon S3 Glacier Flexible Retrieval to store the thumbnails
- Use Amazon S3 Standard-Infrequent Access (S3 Standard-IA) to store the thumbnails
- Use Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA) to store the thumbnails

Correct answer
Use Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA) to store the thumbnails


[Back to the top](#table-of-contents)

### AWS Snow Family
- Highly-secure, portable devices to collect and process data at the
edge, and migrate data into and out of AWS

| AWS Snow Family Device   | Use Case                                                                                                 | Storage Capacity                       | Features                                                                                                 | Size                         |
|--------------------------|----------------------------------------------------------------------------------------------------------|----------------------------------------|----------------------------------------------------------------------------------------------------------|------------------------------|
| **AWS Snowcone**          | Small, portable, rugged device for edge computing, data collection, and data transfer in limited space, power, or connectivity environments. | 8 TB of usable storage                 | Supports local computing with AWS IoT Greengrass or Amazon EC2 instances for edge processing and data transfer to AWS. | Lightweight (weighs about 4.5 pounds), making it easy to transport. |
| **AWS Snowball Edge**     | Larger capacity device for petabyte-scale data transfer and edge computing in disconnected or edge environments. | Up to 80 TB of usable storage per device | - **Storage Optimized**: Primarily used for data storage and migration. <br> - **Compute Optimized**: Equipped for high-performance computing at the edge. | - |
| **AWS Snowmobile**        | A massive-scale data transfer service designed to move extremely large datasets (exabytes) to AWS.         | Up to 100 petabytes (PB) per Snowmobile | Snowmobile is a ruggedized shipping container pulled by a semi-truck, ideal for migrating large data centers or large-scale archives to AWS. | - |


#### AWS OpsHub
• Historically, to use Snow Family devices, you needed a CLI (Command Line Interface tool)
• Today, you can use AWS OpsHub (a software you install on your computer / laptop) to manage your Snow Family Device


# Databases & Analytics Summary in AWS
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/IMG_1179.jpg)
### databases--analytics

| **Service**                         | **Category**                              | **Key Features**                                                                                                    | **Use Case**                                                                                                         |
|-------------------------------------|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **RDS (Relational Database Service)** | Relational Database - OLTP (SQL)          | Managed relational databases (MySQL, PostgreSQL, MariaDB, Oracle, SQL Server). Automates backups, patching, scaling. | Traditional relational databases for transaction-heavy applications (OLTP) like e-commerce, finance, or CRM systems. |
| **Aurora**                          | Relational Database - OLTP (SQL)          | Compatible with MySQL and PostgreSQL, highly available, auto-scaling, designed for high performance and durability.  | Applications needing high throughput, scalability, and reliability. Suitable for both OLTP and analytics workloads.  |
| **Redshift**                        | Data Warehouse - OLAP (SQL)               | Managed, scalable data warehouse supporting SQL queries. Massively Parallel Processing (MPP), columnar storage, integrates with BI tools. | Large-scale data analytics and business intelligence workloads, designed for fast querying and reporting over massive datasets. |
| **DocumentDB**                      | NoSQL Document Database (JSON)            | Managed database service compatible with MongoDB, designed for JSON data, supports high scalability and availability. | Applications that require a NoSQL database with flexible schema and document storage, e.g., content management systems or mobile apps. |
| **Neptune**                         | Graph Database                            | Fully managed graph database supporting Gremlin (property graph) and SPARQL (RDF) query languages. Highly scalable and available. | Applications dealing with highly connected data like social networks, recommendation engines, fraud detection, and knowledge graphs. |
| **Athena**                          | Serverless Query Engine (SQL)             | Serverless service that allows SQL querying directly over data stored in Amazon S3. No need for infrastructure setup. | Ad-hoc querying, data analysis, or reporting on large datasets stored in S3 without setting up databases or clusters. |

- Online Analytical Processing (OLAP) involve querying and analyzing large datasets, often for business intelligence (BI), reporting, and data analytics.

| **Category**                     | **Service**                                                                                   |
|----------------------------------|-----------------------------------------------------------------------------------------------|
| In-memory Database               | ElastiCache                                                                                   |
| Key/Value Database               | DynamoDB (serverless) & DAX (cache for DynamoDB)                                              |
| Warehouse - OLAP                 | Redshift (SQL)                                                                                |
| Hadoop Cluster                   | EMR                                                                                           |
| QuickSight                       | Dashboards on your data (serverless)                                                          |
| Amazon QLDB                      | Financial Transactions Ledger (immutable journal, cryptographically verifiable)               |
| Amazon Managed Blockchain        | Managed Hyperledger Fabric & Ethereum blockchains                                             |
| Glue                             | Managed ETL (Extract Transform Load) and Data Catalog service                                 |
| Database Migration               | DMS                                                                                           |
| Timestream                       | Time-series database                                                                          |

- Which AWS service can be used to provision resources to run big data workloads on Hadoop clusters?

### Comparison of Storage in AWS
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-storage-type-1.png)
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-storage-type-2.png)
| Service                         | Type                         | Characteristics                                                                                                                                       |
|---------------------------------|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| EBS (Elastic Block Store)       | Block Storage                | - EBS volumes can only be attached to EC2 instances, and they act as the disk for those instances. <br/> - Data persists even after the EC2 instance is stopped or terminated. <br/> - Backed up by creating snapshots, which are stored in S3. |
| EC2 Instance Store              | Block Storage                | - Temporary storage that is physically attached to the host machine. <br/> - Data is lost when the EC2 instance is stopped or terminated. <br/> - High I/O performance due to proximity to the instance. <br/> - No additional cost; included with the instance. |
| EFS (Elastic File System)       | File Storage                 | - Fully managed, scalable file storage that can be mounted to multiple EC2 instances simultaneously. <br/> - Automatically scales as files are added or removed. <br/> - Provides shared access to files with strong consistency and durability. |
| S3 (Simple Storage Service)     | Object Storage               | - S3 is used for storing and retrieving any amount of data (backups, images, videos), at any time, from anywhere. <br/> - Highly durable and scalable, ideal for big data storage, backups, and static website hosting. |
| RDS (Relational Database Service) | Managed Relational Database  | - RDS is a managed service for running relational databases such as MySQL, PostgreSQL, and Oracle. <br/> - Provides automatic backups, patching, scaling, and high availability. |

- [What's the Difference Between Block, Object, and File Storage in AWS?](https://www.youtube.com/watch?v=btcbNARavUM)


[Back to the top](#table-of-contents)

# Other Compute Services, Lambda
### other-compute-services

### How does the Docker work 
![vpc](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/docker-image.jpeg)

| **Feature**                | **Details**                                                      |
|----------------------------|------------------------------------------------------------------|
| Docker                     | Container technology to run applications                         |
| ECS Elastic Container Service | Run Docker containers on EC2 instances                           |
| ECR Elastic Container Registry| Private Docker Images Repository                                 |
| Fargate                    | Run Docker containers without provisioning the infrastructure     |
|                            | Serverless offering (no EC2 instances)                           |
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

### serverless
Serverless is a cloud computing model where you can build and run applications without managing the underlying infrastructure.
- No Server Management, Automatic Scaling,Pay-as-You-Go,Event-Driven Execution.
   - Compute: AWS Lambda, AWS Fargate
   - Storage: S3 (Simple Storage Service),DynamoDB
   - Data Processing & Analytics: Amazon Kinesis, AWS Glue
   - Machine Learning: Amazon SageMaker
   -  Messaging & Notification: Amazon SQS (Simple Queue Service),Amazon SNS (Simple Notification Service)  


- Test 3 Question 31
A startup runs its proprietary application on docker containers. As a Cloud Practitioner, which AWS service would you recommend so that the startup **can run containers and still have access** to the underlying servers?

   - ()AWS Fargate
   - ()Amazon Elastic Container Registry (Amazon ECR)
   - ()AWS Lambda
   - ()Amazon Elastic Container Service (Amazon ECS)

Correct answer: Amazon Elastic Container Service (Amazon ECS)
Explanation:
Amazon ECS is a highly scalable, high-performance container orchestration service that supports Docker containers. ECS allows users to run and manage containers on a cluster of Amazon EC2 instances, providing access to the underlying servers if needed. This is ideal for scenarios where you need control over the EC2 instances running the containers.

Incorrect options:

- AWS Fargate: It allows running containers without managing the underlying infrastructure (no access to servers), so it wouldn’t meet the requirement to have access to the underlying servers.
- Amazon Elastic Container Registry (Amazon ECR): This is a fully managed container registry to store, manage, and deploy container images but does not orchestrate or run containers.
- AWS Lambda: This is a serverless computing service that automatically runs your code in response to events, but it’s not for running Docker containers with access to underlying servers.

- Question 60 Incorrect
AWS Lambda pricing is based on which of the following criteria? (Select two)

   - ()The number of lines of code for the AWS Lambda function
   - ()The language runtime of the AWS Lambda function
   - ()Number of requests for the AWS Lambda function
   - ()The size of the deployment package for the AWS Lambda function
   - ()The time it takes for the AWS Lambda function to execute


** With AWS Lambda, you pay only for what you use. You are charged based on the number of requests for your functions and the duration, the time it takes for your code to execute.** 




[Back to the top](#table-of-contents)

# Deploying & Managing Infrastructure at Scale
### deploying--managing-infrastructure-at-scale

| Service           | Description                                                                                           |
|-------------------|-------------------------------------------------------------------------------------------------------|
| CloudFormation    | (like you write a npm to install all the package) Infrastructure as Code, works with almost all of AWS resources. Repeat across Regions & Accounts.     |
| Beanstalk         | Platform as a Service (PaaS), limited to certain programming languages or Docker. Deploy code consistently with a known architecture: ex, ALB + EC2 + RDS. |
| CodeDeploy        | Deploy & upgrade any application onto servers.                                                        |
| Systems Manager   | Helps you manage your EC2 and On-Premises systems at scale. Another Hybrid AWS service. Get **operational insights** about the state of your infrastructure. Patch, configure, and run commands at scale.  |


### CloudFormation code like
```yaml
#  CloudFormation yaml 
Parameters:
  SecurityGroupDescription:
    Description: Security Group Description
    Type: String

Resources:
  MyInstance:
    Type: AWS::EC2::Instance
    Properties:
      AvailabilityZone: us-east-1a
      ImageId: ami-a4c7edb2
      InstanceType: t2.micro
      SecurityGroups:
        - !Ref SSHSecurityGroup
        - !Ref ServerSecurityGroup

  # an elastic IP for our instance
  MyEIP:
    Type: AWS::EC2::EIP
    Properties:
      InstanceId: !Ref MyInstance

  # our EC2 security group
  SSHSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Enable SSH access via port 22
      SecurityGroupIngress:
      - CidrIp: 0.0.0.0/0
        FromPort: 22
        IpProtocol: tcp
        ToPort: 22

  # our second EC2 security group
  ServerSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: !Ref SecurityGroupDescription
      SecurityGroupIngress:
      - IpProtocol: tcp
        FromPort: 80
        ToPort: 80
        CidrIp: 0.0.0.0/0
      - IpProtocol: tcp
        FromPort: 22
        ToPort: 22
        CidrIp: 192.168.1.1/32

Outputs:
  ElasticIP:
    Description: Elastic IP Value
    Value: !Ref MyEIP
```                                                       
### Beanstalk

AWS Elastic Beanstalk is a platform-as-a-service (PaaS) offering from Amazon Web Services that allows you to deploy and manage applications in various programming languages such as Java, .NET, Node.js, Python, Ruby, Go, and Docker. With Elastic Beanstalk, you only need to upload your application code, and AWS will take care of the deployment, including creating the necessary resources like EC2 instances, S3 buckets. 
So Beanstalk does have a full monitoring suite available within the service itself. And so there's going to be a health agent on each EC2 instance within Beanstalk that is going to push metrics to CloudWatch. And then within Beanstalk you can view these metrics,
do some monitoring and so on. But it will also check for application health and will publish health events.

Key features include:

- Automatic scaling
- **Built-in monitoring with Amazon CloudWatch**
- Easy integration with other AWS services
- Support for rolling updates and environment cloning

![codePipeline](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-deploy-codePipeline.png)

### Developer Services
| Service       | Description                                                                         |
|---------------|-------------------------------------------------------------------------------------|
| CodeCommit    | Store code in private git repository (version controlled)                           |
| CodeBuild     | Build & test code in AWS                                                            |
| CodeDeploy    | Deploy code onto servers                                                            |
| CodePipeline  | Orchestration of pipeline (from code to build to deploy)                            |
| CodeArtifact  | Store software packages / dependencies on AWS (Work with managed tools, NPM, yarn )                        |
| CodeStar      | Unified view for allowing developers to do CICD and code                            |
| Cloud9        | Cloud IDE (Integrated Development Environment) with collaboration features          |
| AWS CDK       | (AWS Cloud Development Kit (CDK))Define your cloud infrastructure using a **programming language**|

### CDK (typescript)
```typescript
import * as cdk from 'aws-cdk-lib';
import { Construct } from 'constructs';
import * as s3 from 'aws-cdk-lib/aws-s3';

export class MyCdkAppStack extends cdk.Stack {
  constructor(scope: Construct, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    // Define an S3 bucket
    new s3.Bucket(this, 'MyFirstBucket', {
      versioned: true,           // Enable versioning for objects
      removalPolicy: cdk.RemovalPolicy.DESTROY,  // Automatically delete the bucket when stack is destroyed
      autoDeleteObjects: true,   // Automatically delete objects when the bucket is removed
    });
  }
}

```

[Back to the top](#table-of-contents)

# Global Infrastructure- Global Applications in AWS
### global-infrastructure 
- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
- [Regions and Availability Zones](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/?p=ngi&loc=2)
- global application is an application deployed in multiple geographies
-  could be Regions and / or Edge Locations
1. Decreased Latency 
2. Disaster Recovery (DR)
3. Attack protection

| Category                      | Description**                                      |
|-----------------------------------|------------------------------------------------------|
| Regions                       | AWS has the concept of a Region, which is a **physical location** around the world where we cluster data centers.  Each AWS Region consists of **a minimum of three**, isolated, and physically separate AZs within a geographic area.       |
| Availability Zones            | An Availability Zone (AZ) is **one or more** discrete **data centers** with redundant power, networking, and connectivity in an AWS Region.|
| Edge Locations (Points of Presence) | For content delivery as close as possible to users   |



### Route 53 Routing Policies

1. SIMPLE ROUTING POLICY
2. WEIGHTED ROUTING POLICY
3. LATENCY ROUTING POLICY
4. FAILOVER ROUTING POLICY (Disaster Recovery)

## Global Applications in AWS
- A global application is an application deployed in multiple geographies

| Global Applications Service | Description                                                                                                  |
|-----------------------------|--------------------------------------------------------------------------------------------------------------|
| Route 53                    | Global Managed DNS (Domain Name System): Routes users to the closest deployment with the least latency. Great for disaster recovery strategies. |
| CloudFront                  | Global Content Delivery Network (CDN): Replicates part of your application to AWS Edge Locations to decrease latency. Caches common requests, improving user experience and reducing latency. |
| S3 Transfer Acceleration     | Increases transfer speed by transferring files to an AWS edge location, which forwards the data to the S3 bucket in the target region. |
| AWS Global Accelerator       | Improves global application availability and performance using the AWS global network.                       |


- edge Location
A site that CloudFront uses to cache copies of your content for faster delivery to users at any location.

- Test 2 Question 47
Which AWS service helps with global application availability and performance using the AWS global network?
   - ()Elastic Load Balancing (ELB)
   - ()Amazon Route 53
   - ()AWS Global Accelerator 
   - ()Amazon CloudFront

- AWS Global Accelerator (O)
IP Routing: Handles the actual transfer of data between devices, relying on IP addresses and routers.
DNS Routing: Translates domain names into IP addresses, enabling users to access websites without knowing their IP addresses.

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

- Test3 Question 41 
A company has a static website hosted on an Amazon Simple Storage Service (Amazon S3) bucket in an AWS Region in Asia. Although most of its users are in Asia, now it wants to drive growth globally. How can it improve the global performance of its static website?

   - Use Amazon CloudFront to improve the performance of your website
   - Use AWS Web Application Firewall (AWS WAF) to improve the performance of your website
   - Use Amazon CloudFormation to improve the performance of your website
   - Use Amazon S3 Transfer Acceleration (Amazon S3TA) to improve the performance of your website

answer: Use Amazon CloudFront to improve the performance of your website
- Why not Amazon S3 Transfer Acceleration (S3TA)?
Amazon S3 Transfer Acceleration (S3TA) is designed to improve data upload and download speeds to S3 buckets by routing the data through AWS edge locations. However, it primarily benefits data transfer into and out of the S3 bucket (e.g., for users uploading large files or accessing large files from far regions).

- Test 5 Question 22
Which of the following services are provided by Amazon Route 53? (Select Two)
   - Domain registration
   - Health checks and monitoring
   - IP routing
   - Load balancing

Answer: Domain registration , Health checks and monitoring

- Test 6 Question 9
Which of the following statements are true about AWS Regions and Availability Zones (AZ)? (Select two)

- AWS calls each group of logical data centers as AWS Regions
- Traffic between Availability Zones (AZ) is not encrypted by default, but can be configured from AWS console
- An Availability Zone (AZ) is a physical location where AWS clusters the data centers
- All traffic between Availability Zones (AZ) is encrypted
- Each AWS Region consists of multiple, isolated, and physically separate Availability Zones (AZ) within a geographic area

Answer:  
1. All traffic between Availability Zones (AZ) is encrypted
2. Each AWS Region consists of multiple, isolated, and physically separate Availability Zones (AZ) within a geographic area
—
Your selection is incorrect
An Availability Zone (AZ) is a physical location where AWS clusters the data centers

In the AWS document, An Availability Zone (AZ) is **ne or more discrete data centers with redundant power, networking, and connectivity in an AWS Region** . It didn’t mention physical location. 
However, AWS has the concept of a Region, which is a **physical location** around the world where we cluster data centers.

Ex. 
Australia has two Regions : Sydney and Melbourne

Australia (Sydney) Region has Availability Zones: 3, Launched 2012
Australia (Melbourne) Region has Availability Zones: 3, Launched 2023

- [Regions and Availability Zones](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/?p=ngi&loc=2)


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
| CloudWatch                  | Metrics: Monitor the **performance of AWS services** and **billing metrics**. Alarms: Automate notification, perform EC2 action, notify to SNS based on metric. Logs: Collect log files from EC2 instances, servers, Lambda functions... Events (or EventBridge): React to events in AWS, or trigger a rule on a schedule. |
| CloudTrail                  | Audit **API calls**, **logging** made within your AWS account. CloudTrail Insights: Automated analysis of your CloudTrail Events. It captures information about the who, when, and what of actions performed on AWS services.          |
| X-Ray                       | Trace requests made through your distributed applications.                                                                |
| AWS Health Dashboard        | Status of all AWS services across all regions.                                                                            |
| AWS Account Health Dashboard| AWS events that impact your infrastructure.                                                                               |
| Amazon CodeGuru             | Automated code reviews and application performance recommendations.                                                       |

####  CloudTrail  vs. CloudWatch   
| Feature           | CloudTrail                                 | CloudWatch                               |
|-------------------|--------------------------------------------|------------------------------------------|
| Purpose           | API call tracking and auditing             | Performance and operational monitoring   |
| Data Collected    | Collects API calls made within your AWS account. This includes actions such as creating, deleting, or modifying AWS resources (e.g., creating an EC2 instance or changing S3 bucket permissions).              |  Collects metrics and log data. Metrics include things like CPU utilization of an EC2 instance, memory usage, or disk reads/writes. It can also collect custom metrics that you define for your applications and log data like error messages, request logs, and application logs.    |
| Use Case          | Auditing, compliance, forensics            | Resource monitoring, performance, alerts |
| Retention         | 90 days default (S3 for long-term)         | 15 months (metrics), logs as per retention |
| Cost              | Pay for trails and S3 storage              | Pay for metrics, alarms, and log storage |
| Scope             | AWS-wide (all regions if specified)        | Resource-specific metrics and logs       |

#### Use Cases:
CloudTrail:
- Security Auditing: Tracks who accessed or modified resources and what actions were taken.
- Compliance Monitoring: Helps ensure that your AWS account is in compliance with industry regulations by providing audit trails of actions.
- Forensics: Investigate incidents by reviewing historical activity logs and understanding who made changes and when.
CloudWatch:
- Monitoring Performance: Provides insight into the operational health and performance of your AWS resources and applications.
- Alerting: Set up alarms based on thresholds (e.g., CPU utilization above 80%) to notify you or trigger automated responses like scaling or restarting an instance.
- Log Analysis: Collect and analyze log files from applications, infrastructure, or AWS services like Lambda, API Gateway, or EC2.

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
| Client VPN                 | OpenVPN connection from your computer into your VPC                          |

### On-Premises Connection
![on-premises](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-vpc-on-premises.png)

#### On-Premises Connection
| On-Premises Connection | Details |
|------------------------|---------|
| 1. Site to Site VPN       | * Connect an on-premises VPN to AWS<br>* The connection is automatically encrypted<br>* Goes over the public internet |
| 2. Direct Connect (DX)    | * Establish a physical connection between on-premises and AWS<br>* The connection is private, secure, and fast<br>* Goes over a private network<br>* Takes at least a month to establish |
| Transit Gateway        | * For having transitive peering between thousands of VPC and on-premises, hub-and-spoke (star) connection<br>* One single Gateway to provide this functionality<br>* Works with Direct Connect Gateway, VPN connections |


-  VPN stands for Virtual Private Network. It is a service that enables you to securely connect your on-premises network or a remote device (such as a laptop or mobile device) to your AWS Virtual Private Cloud (VPC) over an encrypted connection via the public internet.

- Question 44 
A multi-national organization has a separate virtual private cloud (VPC) for each of its business units on the AWS Cloud. The organization also wants to connect its **on-premises** data center with the different virtual private clouds (VPC) for better organization-wide collaboration. Which AWS services can be combined to build the MOST efficient solution for this use-case? (Select two)
- ()AWS Storage Gateway
- ()AWS Transit Gateway
- ()AWS Direct Connect
- ()VPC peering connection
- ()Internet Gateway

Answer: AWS Transit Gateway, AWS Direct Connect

[Back to the top](#table-of-contents)

# Security & Compliance
### security--compliance

## AWS Shared Responsibility Model
![AWS-share-responbility](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-Shared%20Responsibility%20Model%20diagram.png)
- [aws-Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/)
### AWS responsibility - Security **of** the Cloud
• Protecting infrastructure (hardware, software, facilities, and networking) that runs all the AWS services
• Managed services like S3, DynamoDB, RDS, etc.
### Customer responsibility - Security **in** the Cloud
• For EC2 instance, customer is responsible for management of the guest OS (including security patches and updates), firewall & network configuration, IAM
• Encrypting application data • Shared controls:
• Patch Management, Configuration Management, Awareness & Training

![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-sectury-firewall.jpg)
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-sectury-firewall-manager.jpg)
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-secturity-architecture.png)

### Compare the Shield, WAF, Network Firewall

| Service                      | Purpose                                                   | Layer Protected                   | Key Features, Use Cases, and Integration Points                                                                                                                                                                |
|------------------------------|-----------------------------------------------------------|-----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AWS Shield                   | DDoS protection                                           | Network and Transport (Layer 3/4) | - Automatic protection against DDoS attacks <br> - Two tiers: Standard and Advanced <br> - Advanced provides near real-time attack visibility and access to AWS DDoS Response Team (DRT) <br> - Protects against large-scale DDoS attacks <br> - Basic protection for all AWS services <br> - Automatically integrated with AWS services like **CloudFront**, **Route 53**, and **Elastic Load Balancing** |
| AWS Network Firewall         | Network-level protection within VPCs (Protect your entire Amazon VPC)                    | Network (Layer 3/4)               | - Stateful traffic inspection <br> - Intrusion prevention <br> - Web filtering to block malicious traffic <br> - Fine-grained control over network traffic <br> - Enforces network policies within VPCs <br> - **Blocks or allows** specific traffic **based on IP, protocols, and ports** <br> - Provides deeper packet inspection <br> - Integrates with VPCs (Virtual Private Cloud), Transit Gateway |
| AWS WAF (Web Application Firewall) | Protects web applications from common web exploits        | Application (Layer 7)             | - Define rules to block common attack patterns like **SQL injection and XSS** <br> - Integration with CloudFront, ALB, API Gateway <br> - Managed rule groups for quick setup <br> - Protects web applications from specific threats like SQL injection and XSS <br> - Customized security rules <br> - Integrates with CloudFront (CDN), Application Load Balancer (ALB), API Gateway |



Q: If you want to protect your application from Cross Site Scripting and SQL Injection attacks will you use AWS WAF or AWS Shield or AWS Firewall?
A: AWS WAF

---

### Compare the GuardDuty, Inspector, Detective.

| **AWS Service**       | **Primary Focus**                      | **Type of Service**                         | **Analyzes**                                        | **Detects**                                        | **Integrations**                         | **Output**                                      | **Ideal For**                                                             |
|-----------------------|----------------------------------------|---------------------------------------------|-----------------------------------------------------|----------------------------------------------------|------------------------------------------|-----------------------------------------------|---------------------------------------------------------------------------|
| **AWS GuardDuty**     | Threat detection and monitoring        | Continuous monitoring                       | CloudTrail logs, VPC flow logs, DNS logs             | Threats and suspicious activities                   | Security Hub, Lambda, EventBridge        | Threat findings with severity                   | Continuous threat detection and real-time monitoring                     |
| **AWS Inspector**     | Vulnerability management               | On-demand or continuous scanning            | EC2 instances, containers (ECR)                      | Vulnerabilities and deviations from best practices  | Security Hub, Systems Manager            | Vulnerability reports and recommendations       | Ensuring infrastructure security and compliance                          |
| **AWS Detective**     | Security investigation and analysis    | Post-incident analysis and investigation    | CloudTrail logs, VPC flow logs, GuardDuty findings   | Root cause and scope of security incidents          | Security Hub, GuardDuty, Detective       | Interactive graphs and detailed investigation tools | Detailed investigations and understanding the impact of security incidents |

---
## AWS config 
| Config Feature              | Description                                                                                                         |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------|
| Purpose                     | Helps with auditing and recording compliance of your AWS resources; records configurations and changes over time.    |
| Data Storage                | Configuration data can be stored in S3 and analyzed using Athena.                                                   |
| Questions Addressed         | - Is there **unrestricted SSH access** to my security groups? <br> - Do my buckets have any **public access?** <br> - How has my **ALB configuration changed** over time? |
| Alerts                      | Can receive alerts via SNS notifications for any changes.                                                           |
| Service Scope               | AWS Config is a per-region service but can be aggregated across regions and accounts.                                |


| Task/Feature                       | Description                                                                                             |
|------------------------------------|---------------------------------------------------------------------------------------------------------|
| Shared Responsibility on AWS       | Defines the division of responsibilities between AWS and the customer                                   |
| KMS (Key Management Service)       | Encryption keys managed by AWS                                                                          |
| CloudHSM                           | (AWS provisions encryption hardware) Hardware encryption where the customer manages the encryption keys |
| ACM (AWS Certificate Manager)      | Provision, manage, and deploy SSL/TLS Certificates.                                                     |
| Config                             | Track configuration changes and compliance against rules                                                |
| Macie                              | Identify sensitive data (e.g., PII) in Amazon S3 buckets                                                |
| CloudTrail                         | Track API calls made by users within an account                                                         |
| AWS Security Hub                   | Gather security findings from multiple AWS accounts                                                     |
| AWS Abuse                          | Report AWS resources used for abusive or illegal purposes                                               |
| Root user privileges               | Includes changing account settings, closing the account, changing/canceling the support plan, or registering as a seller in the Reserved Instance Marketplace |
| IAM Access Analyzer                | Identify which resources are shared externally                                                          |
| Firewall Manager                   | Manage security rules across an Organization (WAF, Shield, etc.)                                        |

- What are SSL and TLS?
SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are cryptographic protocols designed to provide secure communication over a computer network.
- [ OSI Model 1-7 layers](https://aws.amazon.com/what-is/osi-model/)
   1. Layer 1: Physical Layer, 
   2. Layer 2: Data Link Layer, 
   3. Layer 3: Network Layer,
   4. Layer4: Transport Layer ,
   5. Layer 5: Session Layer, 
   6. Layer 6: Presentation Layer, 
   7. Layer 7: Application Layer. 
# Machine Learning
### machine-learning

| Service      | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| Rekognition  | Face detection, labeling, celebrity recognition                             |
| Transcribe   | Audio to text (e.g., subtitles)                                             |
| Polly        | Text to audio                                                               |
| Translate    | Translations                                                                |
| Lex          | Build conversational bots – chatbots                                        |
| Connect      | Cloud contact center                                                        |
| Comprehend   | Natural language processing                                                 |
| SageMaker    | Machine learning for every developer and data scientist                     |
| Forecast     | Build highly accurate forecasts                                             |
| Kendra       | ML-powered search engine                                                    |
| Personalize  | Real-time personalized recommendations                                      |
| Textract     | Detect text and data in documents                                           |

[Back to the top](#table-of-contents)

# Account Management, Billing, & Support
### account-management-billing--support
![](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-account-ou.jpg)

### AWS Organizations
• Global service, allows to manage multiple AWS accounts • The main account is the master account
• Cost Benefits:
   - Consolidated Billing across all accounts - single payment method
   - Pricing benefits from aggregated usage (volume discount for EC2, S3...) 
   - Pooling of Reserved EC2 instances for optimal savings
• API is available to **automate AWS account creation**
• Restrict account privileges using Service Control Policies (SCP)

### Account Best Practices
| Task/Feature                   | Description                                                                                           |
|--------------------------------|-------------------------------------------------------------------------------------------------------|
| Organizations                  | Operate multiple accounts using Organizations                                                         |
| SCP                            | Use SCP (service control policies) to restrict account power                                           |
| AWS Control Tower              | Easily setup multiple accounts with best-practices with AWS Control Tower                              |
| Tags & Cost Allocation Tags    | Use Tags & Cost Allocation Tags for easy management & billing                                          |
| IAM guidelines                 | MFA, least-privilege, password policy, password rotation                                               |
| Config                         | Record all resources configurations & compliance over time                                             |
| CloudFormation                 | Deploy stacks across accounts and regions                                                              |
| Trusted Advisor                | Get insights, Support Plan adapted to your needs                                                       |
| S3 or CloudWatch Logs          | Send Service Logs and Access Logs to S3 or CloudWatch Logs                                             |
| CloudTrail                     | Record API calls made within your account                                                              |
| Account is compromised         | Change the root password, delete and rotate all passwords/keys, contact the AWS support                |
| AWS Service Catalog            | Allow users to create pre-defined stacks defined by admins using AWS Service Catalog                   |

### Billing and Costing Tools 

| Billing Service            | Purpose                                                                                                         | Target Audience                                                                                                   |
|--------------------|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| **Compute Optimizer**  | Reduce costs and improve performance by recommending optimal AWS resources for your workloads.                  | AWS users looking to optimize their cloud infrastructure for performance and cost efficiency.                     |
| **Pricing Calculator** (Estimating costs in the cloud) | Helps in **estimating costs** before **launching or expanding AWS services.**                           | AWS users, especially those planning new deployments or budgeting for AWS services.                               |
| **Cost Explorer** (Tracking costs in the cloud) | Offers detailed insights and visualizations of your AWS spending patterns over time.             | AWS users who want detailed insights into their AWS spending and need to track costs over time.                   |
| **Budgets** (Monitoring against cost plans)  | Allows setting budgets and receiving alerts to ensure spending stays within predefined limits.  | AWS users who want to enforce spending limits and receive proactive alerts about their AWS costs.                 |

- AWS Cost Explorer : You can generate reports, visualize trends, and use forecasting models to **estimate future usage and spending** basing on the current useage.
- AWS Cost Explorer uses historical data, analyzes it against different Savings Plan models, and provides clear recommendations to help you choose the plan that best suits your usage patterns and can save you the most money.
- example : If your EC2 instance usage is consistent over time, AWS Cost Explorer might recommend a Compute Savings Plan with a 1-year term and "Partial Upfront" payment, showing you the exact amount of savings compared to your current pay-as-you-go costs.
- AWS Budgets : 4 types of budgets: Usage, Cost, Reservation, Savings Plans

| Billing and Costing Tools       | Summary |
|---------------------------------|---------|
| Billing Dashboard               | Provides a high-level overview + free tier dashboard |
| Cost Allocation Tags            | Tags resources to create detailed reports |
| Cost and Usage Reports          | Most comprehensive billing dataset |
| Billing Alarms                  | Set in us-east-1 – track overall and per-service billing |
| Savings Plans                   | Easy way to save based on long-term usage of AWS |
| Cost Anomaly Detection          | Detect unusual spends using Machine Learning |
| Service Quotas                  | Notifies you when you’re close to service quota threshold |

ex. AWS Compute Optimizer delivers recommendations for which of the following AWS resources?
1. Amazon EC2 instances, 
2. Amazon EC2 Auto Scaling groups, 
3. Amazon EBS volumes, 
4. AWS Lambda functions, 
5. Amazon ECS services running on Fargate.

- Question: AWS Compute Optimizer delivers recommendations for which of the following AWS resources? (Select two)

   - ()Amazon Elastic Block Store (Amazon EBS), AWS Lambda functions

   - ()Amazon Elastic Compute Cloud (Amazon EC2) instances, Amazon Elastic File System (Amazon EFS)

   - ()Amazon Elastic Compute Cloud (Amazon EC2) instances, Amazon EC2 Auto Scaling groups

   - ()Amazon Elastic File System (Amazon EFS), AWS Lambda functions

   - ()AWS Lambda functions, Amazon Simple Storage Service (Amazon S3)

A: Correct selection
Amazon Elastic Compute Cloud (Amazon EC2) instances, Amazon EC2 Auto Scaling groupsAmazon Elastic Block Store (Amazon EBS), AWS Lambda functions

- Question 52 Incorrect
An IT company is on a cost-optimization spree and wants to identify all Amazon Elastic Compute Cloud (Amazon EC2) instances that are under-utilized. Which AWS services can be used off-the-shelf to address this use-case without needing any manual configurations? (Select two)

   - ()AWS Cost & Usage Report (AWS CUR)
Correct selection
   - ()AWS Trusted Advisor
Your selection is correct
   - ()AWS Cost Explorer
   - ()AWS Budgets
Your selection is incorrect
   - ()Amazon CloudWatch

- Question 37 Incorrect
Which of the following AWS services can be used to forecast your **AWS account usage and costs**?

Your answer is incorrect
   - ()AWS Pricing Calculator
   - ()AWS Cost & Usage Report (AWS CUR)
Correct answer
   - ()AWS Cost Explorer
   - ()AWS Budgets

[Back to the top](#table-of-contents)


## other

# Well-Architected Framework: 6 Pillars 
- (OPR + 2S + C)
1. **Operational Excellence**
   - Includes the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures.

2. **Security**
   - Includes the ability to protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies.

3. **Reliability**
   - The ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues.

4. **Performance Efficiency**
   - Includes the ability to use computing resources efficiently to meet system requirements, and to maintain that efficiency as demand changes and technologies evolve.

5. **Cost Optimization**
   - Includes the ability to run systems to deliver business value at the lowest price point.

6. **Sustainability**
   - The sustainability pillar focuses on minimizing the environmental impacts of running cloud workloads.



###  AWS Basic, Developer, Business, and Enterprise support plans

| **Feature**                             | **Basic**                           | **Developer**                      | **Business**                        | **Enterprise**                        |
|-----------------------------------------|-------------------------------------|------------------------------------|--------------------------------------|----------------------------------------|
| **Pricing**                             | Free                                | $29/month (or 3% of monthly usage) | $100/month (or 10% of monthly usage) | $15,000/month (or 10% of monthly usage) |
| **24/7 Support**                        | No                                  | No                                 | Yes                                  | Yes                                    |
| **Access to Cloud Support Engineers**   | No                                  | Business Hours                     | 24/7 phone, web , and chat           | 24/7 phone, web, and chat              |
| **Response Time**                       | None                                | < 24 business hours                | < 1 hour for urgent issues           | < 15 minutes for critical issues       |
| **Support for Third-Party Software**    | No                                  | No                                 | Yes                                  | Yes                                    |
| **IAM Support**                         | No                                  | No                                 | Yes                                  | Yes                                    |
| **Trusted Advisor**                     | Core Checks (7 checks)              | Core Checks (7 checks)             | Full Checks (All checks)             | Full Checks (All checks)               |
| **Personal Health Dashboard**           | Yes                                 | Yes                                | Yes                                  | Yes                                    |
| **Architectural Guidance**              | No                                  | General Guidance                   | Contextual Guidance                  | Consultative Review                    |
| **Infrastructure Event Management**     | No                                  | No                                 | Yes (Additional fee)                 | Yes                                    |
| **Technical Account Manager (TAM)**     | No                                  | No                                 | No                                   | **Yes**                                |
| **Well-Architected Reviews**            | No                                  | No                                 | Yes                                  | Yes                                    |
| **Operations Reviews**                  | No                                  | No                                 | No                                   | Yes                                    |
| **Proactive Guidance**                  | No                                  | No                                 | No                                   | Yes                                    |
| **Training and API Support**            | No                                  | No                                 | Yes                                  | Yes                                    |
| **Access to Enterprise Concierge**      | No                                  | No                                 | No                                   | Yes                                    |

![trust-advisor](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/images/aws-trust-advisor.png)

- **AWS Trusted Advisor** is a service that provides real-time guidance to help you optimize your AWS infrastructure, improve security and performance, reduce costs, and monitor service limits. It offers best practices and checks across five categories:
- Cost Optimization
- Performance
- Security
- Fault Tolerance
- Service Limits

[Back to the top](#table-of-contents)

Resources
---
- [udemy - Ultimate AWS Certified Cloud Practitioner CLF-C02](https://www.udemy.com/course/aws-certified-cloud-practitioner-new/?couponCode=KEEPLEARNING)
- [大話AWS雲端架構：雲端應用架構圖解輕鬆學](https://readmoo.com/book/210259735000101)
- [Intro to AWS - The Most Important Services To Learn](https://www.youtube.com/watch?v=FDEpdNdFglI&list=WL&index=14&t=393s)
- [Youtube - freeCodeCamp.org - AWS Certified Cloud Practitioner Certification Course (CLF-C02) - Pass the Exam!](https://www.youtube.com/watch?v=NhDYbskXRgc&t=22481s)
