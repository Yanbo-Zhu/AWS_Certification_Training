https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf

![](image/Pasted%20image%2020230211182450.png)

# 1 Exam Concept

1. Allocate 120 minutes (seat time, time to review instructions, show online Proctor your workspace, read and accept NDA, complete the exam, provide feedback at the end )
2. Actual exam is 90 minutes.
3. 50 scored questions and 15 unscored (too hard / too easy / unseen)
4. passing Grade: 700/1000
5. 证书 36 monthos 有效 

Domain 1: Cloud Concepts 26%   13 question 
Domain 2: Security and Compliance 25%   16-17 qiestopms
Domain 3: Technology 33%     21-22 questions
Domain 4: Billing and Pricing 16%  10-11 questions


We have:

1.  **Cloud Concepts** 28%
2.  **Security** 24%
3.  **Technology** 36%
4.  **Billing and Pricing** 12%

The largest portion of the exam is Technology at 36% and Billing and Pricing is the lowest which is funny because I find it to be the most valuable information in the entire course.

With **Cloud Concepts** we need to be able to define the AWS Cloud in its proposition, we need to be able to identify aspects of AWS Cloud Economics and list the different Cloud Architectural Principles.

For **Security** you will learn a variety of AWS Security Services and shared responsibility models.

For **Technology** you will learn all core AWS Services and other AWS Services and Global Infrastructures.

**Billing and Pricing** is how we know how much things cost and how we can save money on AWS, how to compare and contrast various pricing models for AWS, how to recognize the various account structures in relation to ASW Billing and Pricing and how to Identify Resources for Billing Support.

## 1.1 Domain 1: Cloud Concepts
1. Define the AWS Cloud and its value proposition
    1. Define the benefits of the AWS cloud including:
        1. Security
        2. Reliability
        3. High Availability
        4. Elasticity
        5. Agility
        6. Pay-as-you go pricing
        7. Scalability
        8. Global Reach
        9. Economy of scale
    2. Explain how the AWS cloud allows users to focus on business value
        1. Shifting technical resources to revenue-generating activities as opposed to managing infrastructure
2. Identify aspects of AWS Cloud economics
    1. Define items that would be part of a Total Cost of Ownership proposal
        1. Understand the role of operational expenses (OpEx)
        2. Understand the role of capital expenses (CapEx)
        3. Understand labor costs associated with on-premises operations
        4. Understand the impact of software licensing costs when moving to the cloud
    2. Identify which operations will reduce costs by moving to the cloud
        1. Right-sized infrastructure
        2. Benefits of automation
        3. Reduce compliance scope (for example, reporting)
        4. Managed services (for example, RDS, ECS, EKS, DynamoDB)
3. Explain the different cloud architecture design principles
    1. Explain the design principles
        1. Design for failure
        2. Decouple components versus monolithic architecture
        3. Implement elasticity in the cloud versus on-premises
        4. Think parallel

## 1.2 Domain 2: Security and Compliance
1. Define the AWS shared responsibility model
    1. Recognize the elements of the Shared Responsibility Model
    2. Describe the customer’s responsibly on AWS
        1. Describe how the customer’s responsibilities may shift depending on the service used (for example with RDS, Lambda, or EC2)
    3. Describe AWS responsibilities
2. Define AWS Cloud security and compliance concepts
    1. Identify where to find AWS compliance information
        1. Locations of lists of recognized available compliance controls (for example, HIPPA, SOCs)
        2. Recognize that compliance requirements vary among AWS services
    2. At a high level, describe how customers achieve compliance on AWS
        1. Identify different encryption options on AWS (for example, In transit, At rest)
    3. Describe who enables encryption on AWS for a given service
    4. Recognize there are services that will aid in auditing and reporting
        1. Recognize that logs exist for auditing and monitoring (do not have to understand the logs)
        2. Define Amazon CloudWatch, AWS Config, and AWS CloudTrail
    5. Explain the concept of least privileged access
3. Identify AWS access management capabilities
    1. Understand the purpose of User and Identity Management
        1. Access keys and password policies (rotation, complexity)
        2. Multi-Factor Authentication (MFA)
        3. AWS Identity and Access Management (IAM)
            1. Groups/users
            2. Roles
            3. Policies, managed policies compared to custom policies
        4. Tasks that require use of root accounts
        5. Protection of root accounts
4. Identify resources for security support
    1. Recognize there are different network security capabilities
        1. Native AWS services (for example, security groups, Network ACLs, AWS WAF)
        2. 3rd party security products from the AWS Marketplace
    2. Recognize there is documentation and where to find it (for example, best practices, whitepapers, official documents)
        1. AWS Knowledge Center, Security Center, security forum, and security blogs
        2. Partner Systems Integrators
    3. Know that security checks are a component of AWS Trusted Advisor

## 1.3 Domain 3: Technology
1. Define methods of deploying and operating in the AWS Cloud
    1. Identify at a high level different ways of provisioning and operating in the AWS cloud
        1. Programmatic access, APIs, SDKs, AWS Management Console, CLI, Infrastructure as
    2. Code
        1. Identify different types of cloud deployment models
            1. All in with cloud/cloud native
            2. Hybrid
            3. On-premises
        2. Identify connectivity options
            1. VPN
            2. AWS Direct Connect
            3. Public internet
2. Define the AWS global infrastructure
    1. Describe the relationships among Regions, Availability Zones, and Edge Locations
    2. Describe how to achieve high availability through the use of multiple Availability Zones
        1. Recall that high availability is achieved by using multiple Availability Zones
        2. Recognize that Availability Zones do not share single points of failure
    3. Describe when to consider the use of multiple AWS Regions
        1. Disaster recovery/business continuity
        2. Low latency for end-users
        3. Data sovereignty
    4. Describe at a high level the benefits of Edge Locations
        1. Amazon CloudFront
        2. AWS Global Accelerator
3. Identify the core AWS services
    1. Describe the categories of services on AWS (compute, storage, network, database)
    2. Identify AWS compute services
        1. Recognize there are different compute families
        2. Recognize the different services that provide compute (for example, AWS Lambda compared to Amazon Elastic Container Service (Amazon ECS), or Amazon EC2, etc.)
        3. Recognize that elasticity is achieved through Auto Scaling
        4. Identify the purpose of load balancers
    3. Identify different AWS storage services
        1. Describe Amazon S3
        2. Describe Amazon Elastic Block Store (Amazon EBS)
        3. Describe Amazon S3 Glacier
        4. Describe AWS Snowball
        5. Describe Amazon Elastic File System (Amazon EFS)
        6. Describe AWS Storage Gateway
    4. Identify AWS networking services
        1. Identify VPC
        2. Identify security groups
        3. Identify the purpose of Amazon Route 53
        4. Identify VPN, AWS Direct Connect
    5. Identify different AWS database services
        1. Install databases on Amazon EC2 compared to AWS managed databases
        2. Identify Amazon RDS
        3. Identify Amazon DynamoDB
        4. Identify Amazon Redshift
4. Identify resources for technology support
    1. Recognize there is documentation (best practices, whitepapers, AWS Knowledge Center, forums, blogs)
    2. Identify the various levels and scope of AWS support
        1. AWS Abuse
        2. AWS support cases
        3. Premium support
        4. Technical Account Managers
    3. Recognize there is a partner network (marketplace, third-party) including Independent Software Vendors and System Integrators
    4. Identify sources of AWS technical assistance and knowledge including professional services, solution architects, training and certification, and the Amazon Partner Network
    5. Identify the benefits of using AWS Trusted Advisor


## 1.4 Domain 4: Billing and Pricing
1. Compare and contrast the various pricing models for AWS (for example, On-Demand Instances, Reserved Instances, and Spot Instance pricing)
    1. Identify scenarios/best fit for On-Demand Instance pricing
    2. Identify scenarios/best fit for Reserved-Instance pricing
        1. Describe Reserved-Instances flexibility
        2. Describe Reserved-Instances behavior in AWS Organizations
    3. Identify scenarios/best fit for Spot Instance pricing
2. Recognize the various account structures in relation to AWS billing and pricing
    1. Recognize that consolidated billing is a feature of AWS Organizations
    2. Identify how multiple accounts aid in allocating costs across departments
3. Identify resources available for billing support
    1. Identify ways to get billing support and information
        1. Cost Explorer, AWS Cost and Usage Report, Amazon QuickSight, third-party partners, and AWS Marketplace tools
        2. Open a billing support case
        3. The role of the Concierge for AWS Enterprise Support Plan customers
    2. Identify where to find pricing information on AWS services
        1. AWS Simple Monthly Calculator
        2. AWS Services product pages
        3. AWS Pricing API
    3. Recognize that alarms/alerts exist
    4. Identify how tags are used in cost allocation

# 2 tools, technologies, and concepts

## 2.1 其他

 APIs
 Cost Explorer
 AWS Cost and Usage Report
 AWS Command Line Interface (CLI)
 Elastic Load Balancers
 Amazon EC2 instance types (for example, Reserved, On-Demand, Spot)
 AWS global infrastructure (for example, AWS Regions, Availability Zones)
 Infrastructure as Code (IaC)
 Amazon Machine Images (AMIs)
 AWS Management Console
 AWS Marketplace
 AWS Professional Services
 AWS Personal Health Dashboard
 Security groups
 AWS Service Catalog
 AWS Service Health Dashboard
 Service quotas
 AWS software development kits (SDKs)
 AWS Support Center
 AWS Support tiers
 Virtual private networks (VPNs)


# 3 AWS services and features

Analytics:
 Amazon Athena
 Amazon Kinesis
 Amazon QuickSight

Application Integration:
 Amazon Simple Notification Service (Amazon SNS)
 Amazon Simple Queue Service (Amazon SQS)

Compute and Serverless:
 AWS Batch
 Amazon EC2
 AWS Elastic Beanstalk
 AWS Lambda
 Amazon Lightsail
 Amazon WorkSpaces

Containers:
 Amazon Elastic Container Service (Amazon ECS)
 Amazon Elastic Kubernetes Service (Amazon EKS)
 AWS Fargate

Database:
 Amazon Aurora
 Amazon DynamoDB
 Amazon ElastiCache
 Amazon RDS
 Amazon Redshift

Developer Tools:
 AWS CodeBuild
 AWS CodeCommit
 AWS CodeDeploy
 AWS CodePipeline
 AWS CodeStar

Customer Engagement:
 Amazon Connect

Management, Monitoring, and Governance:
 AWS Auto Scaling
 AWS Budgets
 AWS CloudFormation
 AWS CloudTrail
 Amazon CloudWatch
 AWS Config
 AWS Cost and Usage Report
 Amazon EventBridge (Amazon CloudWatch Events)
 AWS License Manager
 AWS Managed Services
 AWS Organizations
 AWS Secrets Manager
 AWS Systems Manager
 AWS Systems Manager Parameter Store
 AWS Trusted Advisor

Networking and Content Delivery:
 Amazon API Gateway
 Amazon CloudFront
 AWS Direct Connect
 Amazon Route 53
 Amazon VPC

Security, Identity, and Compliance:
 AWS Artifact
 AWS Certificate Manager (ACM)
 AWS CloudHSM
 Amazon Cognito
 Amazon Detective
 Amazon GuardDuty
 AWS Identity and Access Management (IAM)
 Amazon Inspector
 AWS License Manager
 Amazon Macie
 AWS Shield
 AWS WAF

Storage:
 AWS Backup
 Amazon Elastic Block Store (Amazon EBS)
 Amazon Elastic File System (Amazon EFS)
 Amazon S3
 Amazon S3 Glacier
 AWS Snowball Edge
 AWS Storage Gateway
