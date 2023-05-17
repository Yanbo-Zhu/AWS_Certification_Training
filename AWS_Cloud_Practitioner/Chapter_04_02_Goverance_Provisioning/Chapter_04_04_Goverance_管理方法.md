
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



# 4 AWS Quick Starts
9:30:15 AWS Quick Starts

## 4.1 AWS QuickStarts Follow Along
9:31:04 AWS QuickStarts Follow Along

# 5 Tagging
9:33:37 Tagging

## 5.1 Tag Name Follow Along
9:34:43 Tag Name Follow Along

# 6 Resource Groups
9:35:48 Resource Groups

## 6.1 Resource Groups Follow Along
9:36:38 Resource Groups Follow Along

# 7 Business Centric Services
9:42:25 Business Centric Services

