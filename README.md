# AWS Certified Cloud Practitioner CLF-C02

# table-of-contents
1. [Cloud Computing](#cloud-computing)
2. [AWS IAM Identity & Access Management](#aws-iam-identity--access-management)
3. [Amazon EC2](#amazon-ec2)
4. [Amazon EC2 Instance Storage](#amazon-ec2-instance-storage)
5. [Elastic Load Balancing & Auto Scaling Group](#elastic-load-balancing--auto-scaling-group)
6. [Amazon S3](#amazon-s3)
7. [Databases & Analytics](#databases--analytics)
8. [Other Compute Services](#other-compute-services)
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
# aws-iam-identity--access-management

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
| AWS SDK              | (Software Developer Kit) Manage your AWS services using a programming language |
| AWS Management Console | Web-based user interface to manage AWS services                       |


[Back to the top](#table-of-contents)

# amazon-ec2
| EC2 Section – Summary                                      | Description                                                        |
|------------------------------------------------------------|--------------------------------------------------------------------|
| EC2 Instance                                               | AMI (OS) + Instance Size (CPU + RAM) + Storage + Security Groups + EC2 User Data |
| Security Groups                                            | Firewall attached to the EC2 instance                              |
| EC2 User Data                                              | Script launched at the first start of an instance                  |
| EC2 Instance Role                                          | Link to IAM roles                                                  |
| Purchasing Options                                         | On-Demand, Spot, Reserved (Standard + Convertible), Dedicated Host, Dedicated Instance |

### Communicate with EC2
| SSH                      | Start a terminal into our EC2 Instances (port 22)    |
|--------------------------|------------------------------------------------------|
| EC2 Instance connect     | Connect to your EC2 instance within your browser     |


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



# elastic-load-balancing--auto-scaling-group
### Elastic Load Balancing & Auto Scaling Groups Section
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

