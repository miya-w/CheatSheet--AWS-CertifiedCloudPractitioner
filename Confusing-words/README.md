# AWS-confusing word

## AWS Artifact
### AWS Artifact
AWS Artifact is your go-to, central resource for compliance-related information that matters to your organization. It provides on-demand access to AWS’ security and compliance reports and select online agreements. Reports available in AWS Artifact include our Service Organization Control (SOC) reports, Payment Card Industry (PCI) reports, and certifications from accreditation bodies across geographies and compliance verticals that validate the implementation and operating effectiveness of AWS security controls. It is not a service, it's a no-cost, self-service portal for on-demand access to AWS’ compliance reports.
Incorrect options:
### AWS Trusted Advisor -
 AWS Trusted Advisor is an online tool that provides you real-time guidance to help you provision your resources following AWS best practices. Whether establishing new workflows, developing applications, or as part of ongoing improvement, recommendations provided by Trusted Advisor regularly help keep your solutions provisioned optimally.
AWS Secrets Manager - AWS Secrets Manager helps you protect secrets needed to access your applications, services, and IT resources. The service enables you to easily rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle. Users and applications retrieve secrets with a call to AWS Secrets Manager APIs, eliminating the need to hardcode sensitive information in plain text.

### AWS Cost & Usage Report (AWS CUR) 
 The AWS Cost & Usage Report (AWS CUR) contains the most comprehensive set of cost and usage data available. You can use AWS Cost & Usage Report (AWS CUR) to publish your AWS billing reports to an Amazon Simple Storage Service (Amazon S3) bucket that you own. You can receive reports that break down your costs by the hour or month, by product or product resource, or by tags that you define yourself. AWS updates the report in your bucket once a day in comma-separated value (CSV) format.
Reference:

### AWS Artifact vs. AWS CodeArtifact

### AWS Artifact: 
Focuses on compliance and regulatory documentation, giving you access to reports and agreements for meeting industry standards.
### AWS CodeArtifact 
Focuses on software package management and version control, allowing developers to manage dependencies and share packages across teams.


* Amazon Inspector: Focuses on security and vulnerability assessments, not resource utilization.
* Amazon CloudWatch: Monitors performance metrics and logs but does not directly recommend cost-optimization measures like identifying underutilized EBS volumes.
* AWS Config: Tracks configuration changes and helps with compliance but does not specifically analyze EBS volumes for utilization.

### ECS  ECR Fargate

When to Use Each Service:

**ECS (Elastic Container Service)**
Use ECS when you need to manage and orchestrate containerized applications, handling tasks like load balancing, scaling, and scheduling multiple containers.
It’s ideal for microservices architectures or any containerized app that needs high availability and scaling.
ECS can run on both EC2 (if you want to manage the infrastructure yourself) or Fargate (if you want AWS to manage the infrastructure).

**ECR (Elastic Container Registry)**
Use ECR whenever you are working with Docker containers and need a secure and scalable place to store, manage, and version your container images.
ECR is ideal for teams deploying containerized applications regularly, especially when those applications run on AWS services like ECS or Fargate.

**Fargate**
Use Fargate when you don’t want to manage the underlying infrastructure (EC2 instances) for your containers. It’s best for running containers serverlessly with automatic scaling and without worrying about provisioning servers.
Ideal for startups, small teams, or applications with unpredictable or varying traffic, where you don’t want to deal with server management but still need a scalable solution.

—————————————
### VPC Gateway Endpoint  vs.  interface endpoint

![endpoints](https://github.com/miya-w/CheatSheet--AWS-CertifiedCloudPractitioner/blob/main/Confusing-words/images/aws-vpc-endpoints.png)
AWS VPC Endpoints Explained

 Endpoints allow you to connect to AWS Services using a private network instead of the public www network
 This gives you enhanced security and lower latency to access AWS services

There are two main types of VPC Endpoints:

1.VPC Endpoint Gateway: S3 & DynamoDB 
2.VPC Endpoint Interface: the rest 


- **VPC Gateway Endpoint**
    - secure access to AWS services like **S3** and **DynamoDB** from your VPC, a VPC Gateway Endpoint is the most secure and efficient choice.
    - VPC Endpoints allow secure and private connections to S3 without traversing the public internet.

- **Interface Endpoints (AWS PrivateLink)**
    - A VPC Interface Endpoint provides a private connection between your VPC and supported A wide range of AWS services, such as Amazon S3, Amazon DynamoDB, Amazon SNS, or AWS services hosted by others (e.g., third-party SaaS providers).

| **Feature**            | **Interface Endpoint**                   | **Gateway Endpoint**                |
|------------------------|-----------------------------------------|-------------------------------------|
| **Connectivity**       | ENI in your subnet (private IP)          | Gateway entry in the route table    |
| **Services Supported** | Most AWS services, third-party SaaS      | Amazon S3, DynamoDB                 |
| **Cost**               | Charges for data transfer and hourly     | Free                                |
| **Network Type**       | Operates over AWS PrivateLink            | Operates over the VPC route table   |

### on-premise connection gateway

- **AWS Storage Gateway**
	- Bridge between *on-premise* data and *cloud data* in S3 
	- Hybrid storage service to allow on- premises to seamlessly use the AWS Cloud 
	- Use cases: disaster recovery, backup & restore, tiered storage 
    - 
- **AWS Transit Gateway**
    - centralized network management and interconnectivity across multiple VPCs or hybrid on-premises environments
---
### Lambda

- **API Gateway**
    - Expose Lambda functions as HTTP API


——

## AWS OpsHub  vs. AWS Outpost


AWS OpsHub:
* Purpose: AWS OpsHub is a graphical user interface (GUI) that simplifies the management of AWS Snow Family devices (such as AWS Snowball and AWS Snowcone)


AWS Outposts:
* Purpose: AWS Outposts is a fully managed service that extends AWS infrastructure, services, APIs, and tools to virtually any on-premises facility. It allows customers to run AWS services locally on-premises while still having access to the full suite of AWS tools and integration with the AWS cloud.

