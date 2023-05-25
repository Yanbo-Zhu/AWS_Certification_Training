
# 1 Organizations and Accounts
9:16:09 Organizations and Accounts

![](image/Pasted%20image%2020230515182704.png)

-   [**Organizations**](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org.html) allow the creation of new AWS accounts. Centrally manage billing, control access, compliance, security, and share resources across your AWS accounts.
-   [**Root Account User**](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html) is a single sign-in identity that has complete access to all AWS services and resources in an account. Each account has a Root Account User
-   [**Organization Units**](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_ous.html) are a group of AWS accounts within an organization which can also contain other organizational units - creating a hierarchy
-   [**Service Control Policies**](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html) give central control over the allowed permissions for all accounts in your organization, helping to ensure your accounts stay within your organization’s guidelines.

AWS Organizations must be turned on, once turned it cannot be turned off.
You can create as many AWS Accounts as you like, one account will be the Master/Root Account
AWS Account is not the same as a User Account

**Key Points:**
-   In AWS you can have more than one account managed through a single account using Organizations
-   Organizations allow you to setup consolidated billing where 1 account pays the AWS bill for all
-   The payer account is the root level account in an Organization
-   You can create isolated AWS accounts for different teams under the payer account - and place them inside Organizational Units (OU)
-   The separation of accounts into OUs allows you to set customized permission boundaries on the accounts using Service Control Policies (SCPs)

# 2 AWS Control Tower 服务
9:18:48 AWS Control Tower

[AWS Landing Zone](https://aws.amazon.com/solutions/implementations/aws-landing-zone/)
[AWS Control Tower features](https://aws.amazon.com/controltower/features/)

AWS Control Tower helps **Enterprises** quickly set-up a secure, **AWS multi-account** . 帮助建设 多 aws account architecture 
Provides you with a **baseline environment** to get started with a **multi-account architecture**
**AWS Control Tower** is the replacement for retired **AWS Landing Zones**

**Landing Zone**
A landing zone is a baseline environment following well-architected and best practices to start launching production ready workloads.
-   AWS SSO enabled, Centralized logging for AWS CloudTrail, cross-account security auditing

**Account Factory**
-   automates provisioning of new accounts in your organization
-   standardize the provisioning of new accounts with pre-approved account configurations
-   configure your account factory with pre-approved network configuration and region selections
-   enable self-service for your builders to configure and provision new accounts using AWS Service Catalog
    -  AWS Service Catalog preapproved workflow 
    - AWS Service Catalog allows organizations to create and manage catalogs of IT services that are approved for use on AWS. These IT services can include everything from virtual machine images, servers, software, and databases to complete multi-tier application architectures.
    - AWS Service catalog is kind of predefined(by admin) CloudFormation template.

**Guardrails**
pre-packaged governance rules for security, operations, and compliance that customers can select and apply enterprise-wide or to specific groups of accounts


# 3 AWS Config
9:20:50 AWS Config

**What is Change management?**
Change management in the context of Cloud Infrastructure is when we have a formal process to:
-   monitor changes
-   enforce changes
-   Remediate changes 矫正；补救；治疗

**What is Compliance-as-code (CaC)?**
Compliance as code is when we utilize programming to automate the monitoring, enforcing, and remediating changes to stay compliant with compliance programs or expected configuration.

**What is AWS Config?**
**AWS Config** is a **Compliance-as-Code** framework that allows us to manage change in your AWS accounts on a per-region basis.
用代码 的形式 产生 Compliance (需要遵守的条款).  然后 用这些 条款 去 监控 aws aacounts 中的 changes 有没有违反某某些条款 

![](image/Pasted%20image%2020230515184322.png)

When should you use AWS Config?
-   I want this **resource** to stay **configured** in a **specific way** for **compliance**. 
-   I want to **keep track** of configuration **changes** to resources.
-   I want a **list of all resources** within a region.
-   I want to use **analyze potential security** weaknesses, you need detailed historical information.

## 3.1 AWS Config Follow Along
9:22:29 AWS Config Follow Along

![](image/Pasted%20image%2020230515185453.png)

产生新的 AWS Config
![](image/Pasted%20image%2020230515190656.png)

产生新的 Rules 
![](image/Pasted%20image%2020230515190929.png)

manage remediation of a rule: 
就是 这个 rule 没有被 complied, 那这时候 可以怎么 修改 这个 rule 
![](image/Pasted%20image%2020230515191008.png)

Conformance packs  一致性 
Conformance packs is a Collection of aws Config rules and remediation actions that can be deployed and monitored as a single entity in your aws account 

![](image/Pasted%20image%2020230520193903.png)

Resource -> Resource Inventory -> Resource timeline
看 某个 rule, 他的改变轨迹.  比如, 什么时候complied, 先是是否 compliant

![](image/Pasted%20image%2020230520194455.png)

![](image/Pasted%20image%2020230520194508.png)

# 4 AWS Quick Starts
9:30:15 AWS Quick Starts

[Amazon EC2 Reserved Instances](https://aws.amazon.com/ec2/pricing/reserved-instances/)
[Amazon EC2 Reserved Instances Pricing](https://aws.amazon.com/ec2/pricing/reserved-instances/pricing/)
[Amazon EC2 Reserved Instance Marketplace](https://aws.amazon.com/ec2/purchasing-options/reserved-instances/marketplace/)
[AWS Quick Starts FAQ](https://aws.amazon.com/quickstart/faq/)

**AWS Quick Starts** are **Prebuilt templates** by AWS and AWS Partners to **help deploy a wide range of stacks**
Reduce hundreds of manual procedures into just a few steps

A Quick Start is composed of **3** parts
1.  A reference architecture for the deployment
2.  AWS CloudFormation templates that automate and configure the deployment
3.  A deployment guide explaining the architecture and implementation in detail

Most Quick Start reference deployments enable you to spin up a fully functional architecture in less than an hour!


## 4.1 AWS QuickStarts Follow Along
9:31:04 AWS QuickStarts Follow Along

Serverless Bot Framework
![](image/Pasted%20image%2020230520194958.png)

![](image/Pasted%20image%2020230520195007.png)

![](image/Pasted%20image%2020230520195021.png)

template

![](image/Pasted%20image%2020230520195107.png)

# 5 Tagging
9:33:37 Tagging

[What is the AWS Management Console?](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-are-resource-groups.html)

**A tag** is a **key and value pair** that you can assign to AWS resources.

![](image/Pasted%20image%2020230520200405.png)

Tags allow you to organize your resources in the following ways:
-   **Resource management**
    -   specific workloads, environments eg. Developer Environments
-   **Cost management and optimization**
    -   Cost tracking, Budgets, Alerts
-   **Operations management**
    -   Business commitments and SLA operations eg. Mission-Critical Services
-   **Security**
    -   Classification of data and security impact 
-   **Governance and regulatory compliance**
-   **Automation**
-   **Workload optimization**

**Tag Examples**
Dept = Finance  
Status = Approved  
Team = Compliance  
Environment = Production  
Project = Enterprise  
Location = Canada

## 5.1 Tag Name Follow Along
9:34:43 Tag Name Follow Along

![](image/Pasted%20image%2020230520200520.png)



# 6 Resource Groups
9:35:48 Resource Groups

[What is the AWS Management Console?](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/what-are-resource-groups.html)

**Resource Groups** are a collection of resources that share one or more **tags**
Helps you organize and consolidate information based on your project and the resources that you use.

Resource Groups can display details about a group of resource based on
-   Metrics
-   Alarms
-   Configuration Settings

At any time you can modify the settings of your resource groups to change what resources appear.
tag can be used in IAM policy 

Resource Groups appears in the **Global Console Header** and Under **Systems Manager**
![](image/Pasted%20image%2020230520200754.png)

## 6.1 Tag polices 

Tag polices  helps you to standarise the tag on resource groups or on you account 
attch the tag in to the entrie organization 

## 6.2 Resource Groups Follow Along
9:36:38 Resource Groups Follow Along

现在 s3 中创造一些 resource with specifice tag
![](image/Pasted%20image%2020230520201233.png)

在 aws resource groups 中 创造一个 新的 resource group 
![](image/Pasted%20image%2020230520201316.png)

![](image/Pasted%20image%2020230520201422.png)

![](image/Pasted%20image%2020230520201439.png)

resource group works with IAM policy 
![](image/Pasted%20image%2020230520201507.png)


# 7 Business Centric Services
9:42:25 Business Centric Services

一些办公软件 在 aws 中的对应的 services 

[**Amazon Connect**](https://aws.amazon.com/connect/) - `Call center` as a self-service 
- cloud-based contact center service that makes it easy for any business to deliver better customer service at lower cost.

[**WorkSpaces**](https://aws.amazon.com/workspaces/) - `Virtual Remote Desktops` 
- a fully managed, secure cloud desktop service. You can use Amazon WorkSpaces to provision either Windows or Linux desktops in just a few minutes and quickly scale to provide thousands of desktops to workers across the globe.

[**WorkDocs**](https://aws.amazon.com/workdocs/?amazon-workdocs-whats-new.sort-by=item.additionalFields.postDateTime&amazon-workdocs-whats-new.sort-order=desc) 
- a content creation and collaboration service. Easily create, edit, and share content saved centrally in AWS

[**Chime**](https://aws.amazon.com/chime/?chime-blog-posts.sort-by=item.additionalFields.createdDate&chime-blog-posts.sort-order=desc) 
- AWS platform for `online meetings, video conferencing`, and business calling which elastically scales to meet your capacity needs.

[**WorkMail**](https://aws.amazon.com/workmail/) 
- Managed `business email`, contacts, and calendar service with support for existing desktop and mobile email client applications

[**Pinpoint**](https://aws.amazon.com/pinpoint/) 
- Marketing campaign management system you can `use for sending targeted email`, SMS, push notifications, and voice messages.

[**SES**](https://aws.amazon.com/ses/) 
- Simple Email Service- A cloud based email sending service designed fro marketers and application developers to `send marketing, notifications, and emails.`

[**QuickSight**](https://aws.amazon.com/quicksight/) 
- A Business Intelligence (BI) service. Connect multiple datasource and quickly visualize data in the form of graphs with little to no programming knowledge.