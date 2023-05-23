
11:13:28 TCO and Migration

# 1 Total Cost of Ownership (TCO)
11:14:33 Total Cost of Ownership (TCO)

用来算钱的 migrate from on-premise  to cloud 
TCO is a **financial estimate** intended to help buyers and owners determine the direct and indirect costs of a product or service.
Creating a TCO report is useful when your company **is looking to migrate from on-premise to cloud**.

![](image/Pasted%20image%2020230522000518.png)

---

**According to research stated by Garter:**

“cloud services can initially be more expensive than running on-premises data centers. [However, it also proves that] cloud services can become cost-effective over time if organizations learn to use and operate them more efficiently”

Example of a 2,500 Virtual Machines (VMs) moved to Amazon EC2

![](image/Pasted%20image%2020230522000546.png)

---



**CAPEX**  Capital expenditure
On-Premise

Software License Fees
-   Implementation
-   Configuration
-   Training![](image/Pasted%20image%2020230522094153.png)
-   Physical Security
-   Hardware
-   IT Personal
-   Maintenance

AWS's Responsibility


**OPEX**   Operational Expenditure
AWS (75% Savings)

Subscription Fees
-   Implementation
-   Configuration
-   Training

# 2 CAPEX vs OPEX
11:17:40 CAPEX vs OPEX

主要的区别
- Operational Expenditure 不用再考虑 upfront of equipment

## 2.1 Capital Expenditure (CAPEX)

Spending money upfront on physical infrastructure deducting that expense from your tax bill over time.
-   Server Costs (computers)
-   Storage Costs (hard drives)
-   Network Costs (Routers, Cables, Switches)
-   Backup and Archive Costs
-   Disaster Recovery Costs
-   Datacenter Costs (Rent, Cooling, Physical Security)
-   Technical Personal

With **Capital Expenses**, you have to guess upfront what you plan to spend

## 2.2 Operational Expenditure (OPEX)

The costs associated with an on-premises data center that has shifted the cost to the service provider. The customer only has to be concerned with non-physical costs.
-   Leasing Software and Customizing features
-   Training Employees in Cloud Services
-   Paying for Cloud Support
-   Billing based on cloud metrics eg.
    -   compute usage
    -   storage usage

With **Operational Expenses** you can try a product or service without investing in equipment

# 3 Shifting-IT Personnel
11:19:07 Shifting-IT Personnel

A company is considering migrating its workloads from on-premise to the cloud to take advantage of the savings. There is a concern among the staff that there will be mass layoffs. Does cloud make IT Personnel redundant?

**Shifting your IT Team**
-   A company needs IT personnel during the migration phase
-   A company can transition some roles to new cloud roles:
    -   Networking to Cloud Networking
-   A company may decide to take a Hybrid approach so they’ll always need to have a traditional IT team and a Cloud IT Team
-   A company can change employees activities from **Managing Infrastructure to Revenue Generating**

# 4 AWS Pricing Calculator
11:20:43 AWS Pricing Calculator

The AWS Pricing Calculator is a free cost estimate tool that can be used within your web browser without the need for an AWS Account to estimate the cost of various AWS services.

The AWS Pricing Calculator contains 100+ services that you can configure for a cost estimate.
To calculate the Total Cost of Ownership an organization needs to compare their existing cost against the AWS costs and so the AWS Pricing Calculator can be used to determine that cost.
You can export your final estimate to a CSV.

calculator.aws

![](image/Pasted%20image%2020230522095716.png)

11:21:45 AWS Pricing Calculator Follow Along



# 5 Migration Evaluator
11:24:14 Migration Evaluator

[Migration Evaluator](https://aws.amazon.com/migration-evaluator/)
[TSO Logic: Software Demo](https://www.youtube.com/watch?v=z6IshDJgWRQ)

**AWS Migration Evaluator** (formally known as TSO Logic) is an **estimating tool** used to determine an organization existing on-premise cost so it can compare it against AWS Costs for planned cloud migration

Migration Evaluator uses an **Agentless Collector** to collect data from your on-premise infrastructure to extract your on-premise costs

![](image/Pasted%20image%2020230522100058.png)

# 6 VM Import Export
11:25:00 VM Import Export

VM Import/Export allows users **to import Virtual Machine images into EC2.**

AWS has import instructions for:
-   VMWare
-   Citrix
-   Microsoft Hyper-V
-   Windows VHD from Azure
-   Linux VHD from Azure

vmware, citrix, hyper-v, vhd

---

流程
1. Prepare your Virtual Image for Upload
2. Upload your Virtual Image to S3
3. Use the AWS CLI to Import your Image It will generate an Amazon Machine Image (AMI)

![](image/Pasted%20image%2020230522100154.png)

# 7 Database Migration Service
11:25:51 Database Migration Service

[What is AWS Database Migration Service?](https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html)
[AWS Schema Conversion Tool](https://aws.amazon.com/dms/schema-conversion-tool/?nc=sn&loc=2)

**AWS Database Migration Service (DMS)** allows you to quickly and securely migrate one database to another.
DMS can be used to migrate your on-premise database to AWS.


**AWS Schema Conversion Tool** is used in many cases to automatically convert a source database schema to a target database schema.
Each migration path requires a bit of research since not all combinations of sources and targets are possible.

![](image/Pasted%20image%2020230522100318.png)


**Possible Sources Database:**
-   Oracle Database
-   Microsoft SQL
-   MySQL
-   MariaDB
-   PostgreSQL
-   MongoDB
-   SAP ASE
-   IMDB Db2
-   Azure SQL Database
-   Amazon RDS
-   Amazon S3 (database dumps)
-   Amazon Aurora
-   Amazon DocumentDB

**Possible Targets Database:**
-   Oracle Database
-   Microsoft SQL
-   MySQL
-   MariaDB
-   PostgreSQL
-   Redis
-   SAP ASE
-   Amazon Redshift
-   Amazon RDS
-   Amazon DynamoDB
-   Amazon S3
-   Amazon Aurora
-   Amazon OpenSearch Service
-   Amazon ElastiCache for Redis
-   Amazon DocumentDB
-   Amazon Neptune
-   Apache Kafka

# 8 Cloud Adoption Framework
11:28:04 Cloud Adoption Framework

[AWS Cloud Adoption Framework (AWS CAF)](https://aws.amazon.com/professional-services/CAF/)
[Introduction](https://docs.aws.amazon.com/whitepapers/latest/overview-aws-cloud-adoption-framework/introduction.html)

The AWS Cloud Adoption Framework is a whitepaper to help you plan your migration from on-premise to AWS.

At the highest level, the AWS CAF organizes guidance into **six focus areas**.
1. Business Perspective
    1. e.g. Business Managers, Finance Managers, Budget Owners, and Strategy Stakeholders.
    2. How to update the staff skills and organizational processes to optimize business value as they move ops to the cloud
2. People Perspective
    1. e.g. Human Resources, Staffing, People Managers.
    2. how to update the staff skills and organizational processes to optimize and maintain their workforce, and ensure competencies are in place at the appropriate time.
3. Governance Perspective
    1. e.g. CIO, Program Managers, Project Managers, Enterprise Architects, Business Analysts
    2. how to update the staff skills and organizational processes that are necessary to ensure business governance in the cloud, and manage and measure cloud investments to evaluate their business outcomes.
4. Platform Perspective
    1. e.g. CTO, IT Managers, Solution Architects.
    2. how to update the staff skills and organizational processes that are necessary to deliver and optimize cloud solutions and services.
5. Security Perspective
    1. e.g. CISO, IT Security Managers, IT Security Analysts.
    2. how to update the staff skills and organizational processes that are necessary to ensure that the architecture deployed in the cloud aligns to the organization’s security control requirements, resiliency, and compliance requirements.
6. Operations Perspective
    1. e.g. IT Operations Managers, IT Support Managers.
    2. how to update the staff skills and organizational processes that are necessary to ensure system health and reliability during the move of operations to the cloud and then to operate using agile, ongoing, cloud computing best practices.





