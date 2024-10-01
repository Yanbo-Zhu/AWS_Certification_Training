
# 1 Zero Trust security Model
8:08:09 Zero-Trust Model

The Zero Trust model operates on the principle of “trust no one, verify everything.”
Malicious actors being able to by-pass conventional access controls demonstrates traditional security measures are no longer sufficient
In the Zero Trust Model Identity becomes the primary security perimeter.

What is the Primary Security Perimeter 视野计?
The primary or new security perimeter defines the first line of defense and its security controls that protect a company’s cloud resources and assets

- Network-Centric: (Old-Way)
    - treat the network as boundary 
    - traditional security-focused on firewalls and VPNs since there were few employees or workstations outside the office or they were in specific remote offices.
- Identity-Centric: (New-Way)
    - Bring-your-own-device, remote workstations are much more common, we can’t trust if the employee is in a secure location, we have identity-based security controls like MFA, or providing provisional access based on the level of risk from where, when, and what a user wants to access.

Identity-Centric does not replace but augments Network-Centric Security

# 2 Zero-Trust on AWS
8:09:55 Zero-Trust on AWS

![](image/Pasted%20image%2020230514183249.png)

**Identity Security Controls** you can implement on AWS to meet the Zero Trust Model

**AWS Identity and Access Management (IAM)**  -> **Your AWS Resources**
-   IAM Policies
-   Permission Boundaries
-   Service Control Policies (Organization-wide Policies)
-   IAM Policy Conditions
    -   aws:SourceIp – Restrict on IP Address
    -   aws:RequestedRegion – Restrict on Region
    -   aws:MultiFactorAuthPresent – Restrict if MFA is turned off
    -   aws:CurrentTime – Restrict access based on time of day

AWS does not have ready-to-use identity controls that are intelligent, which is why AWS is considered to not have a true Zero Trust offering for customers, and third-party services need to be used.

A collection of AWS Services can be setup to intelligent-ish detection of identity concerns but requires expert knowledge: 
**AWS CloudTrail**: Tracks all API calls
**Amazon GuardDuty**: Detects suspicious or malicious activity based on CloudTrail and other logs
**Amazon Detective**: Used to analyze, investigate and quickly identify security issues (can ingest findings from Guard Duty)

# 3 Zero-Trust on AWS with Third-Parties#
8:13:17 Zero-Trust on AWS with Third-Parties

AWS does technically implement a Zero Trust Model but **does not** allow for intelligent identity security controls.

For example:
Azure Active Directory has Real-time and calculated risk detection based on more data points than AWS eg:
-   Device and Application
-   Time of Day
-   Location
-   MFA turned on
-   What is being accessed

And the security controls, verifications, or logic restriction is much more robust.

---

![](image/Pasted%20image%2020230514184024.png)

Third-Party Identity solutions -> **AWS Single Sign-On (SSO)** -> **Your AWS Resources**
Those Third-Party Identity solutions have more intelligent security controls for real-time detection.
-   Azure Active Directory (Azure AD)
-   Google BeyondCorp
-   JumpCloud

# 4 Directory Service
8:15:00 Directory Service

[About Google Cloud Directory Sync](https://support.google.com/a/answer/106368?hl=en)

A directory service maps the **names of network resources to their network addresses**.

A directory service is shared information infrastructure for **locating, managing, administering, and organizing** resources:
-   Volumes
-   Folders
-   Files
-   Printers
-   Users
-   Groups
-   Devices
-   Telephone numbers
-   other objects

A directory service is a critical component of a network operating system
A directory server (name server) is a server that provides a directory service

<mark>Each resource on the network is considered an object by the directory server. Information about a particular resource is stored as a collection of attributes associated with that resource or object</mark>

Well-known directory services:
-   Domain Name Service (DNS)
    -   the directory service for **the internet**
-   **Microsoft Active Directory**
    -   Azure Active Directory
-   Apache Directory Server
-   Oracle Internet Directory (OID)
-   OpenLDAP
-   Cloud Identity
-   JumpCloud

# 5 Active Directory
8:16:18 Active Directory

[The Difference Between Active Directory and LDAP](https://www.varonis.com/blog/the-difference-between-active-directory-and-ldap/)

Microsoft introduced **Active Directory** Domain Services in **Windows 2000** to give organizations the ability to manage multiple on-premises infrastructure components and systems using a single identity per user.


Archecture Diagramm 
![](image/Pasted%20image%2020230514185103.png)

# 6 Identity Providers (idPs)
8:17:28 Identity Providers

[Identity provider](https://en.wikipedia.org/wiki/Identity_provider)

[Oauth](https://en.wikipedia.org/wiki/Oauth)

[Identity provider (SAML)](https://en.wikipedia.org/wiki/Identity_provider_(SAML))

[What’s the Difference Between OAuth, OpenID Connect, and SAML?](https://www.okta.com/identity-101/whats-the-difference-between-oauth-openid-connect-and-saml/)

[What's the difference between OpenID and OAuth?](https://stackoverflow.com/questions/1087031/whats-the-difference-between-openid-and-oauth)


**Identity Provider (IdP)** is a system entity that creates, maintains, and manages identity information for principals and also provides authentication services to applications within a **federation** or distributed network.

A trusted provider of your user identity that lets you use to authenticate to access other services.​
Identity Providers could be: **Facebook, Amazon, Google, Twitter, Github, LinkedIn**​

**Federated联合的  identity** is a method of linking a user's identity across multiple separate identity management systems​

**Federated identity** 的产品
- **OpenID​**
    - open standard and decentralized authentication protocol. Eg be able to login into a different social media platform using a Google or Facebook account​
    - OpenID is about providing who are you​_
- **OAuth2.0​**
    - industry-standard protocol for authorization
    - OAuth doesn’t share password data but instead uses authorization tokens to prove an identity between consumers and service providers.​
    - Oauth is about granting access to functionality​_
- **SAML​**
    - Security Assertion Markup Language is an open standard for exchanging authentication and authorization between an identity provider and a service provider.​
    - An important use case for SAML is **Single-Sign-On via web browser**.​


# 7 Single-Sign-On
8:19:38 Single-Sign-On

[About Google Cloud Directory Sync](https://support.google.com/a/answer/106368?hl=en)

**Single sign-on (SSO)** is an authentication scheme that **allows a user to log in with a single ID and password to different systems and software**.​
SSO allows IT departments to administrator a single identity that can access many machines and cloud services.​
Login for SSO is **seamless**, where once a user is logged​ into their primary directory, as soon as they utilize this software, they are presented with a login screen​

![](image/Pasted%20image%2020230514191027.png)

# 8 LDAP
8:20:26 LDAP

[Office 365: Single Sign-on vs. Same Sign-on](https://corebts.com/blog/office-365-single-sign-on-vs-same-sign-on/)
[What Is LDAP & How Does It Work?](https://www.okta.com/identity-101/what-is-ldap/)
[Difference Between SSO and LDAP](http://www.differencebetween.net/technology/protocols-formats/difference-between-sso-and-ldap/)
[SAML SSO vs. LDAP — Which Protocol Is Right for You?](https://www.sailpoint.com/identity-library/saml-sso-vs-ldap/)

**Lightweight Directory Access Protocol (LDAP)** is an open, vendor-neutral, industry **standard application protocol for accessing and maintaining distributed directory information services** over an Internet Protocol (IP) network.​

A common use of LDAP is to provide a central place to store usernames and passwords​
LDAP enables for **same-sign on**. The same sign-on allows the same userID and password to be used for multiple applications, but they have to enter it in every time they want to login.​

**Why use LDAP when SSO is more convenient?​**
Most SSO systems are using LDAP.​
LDAP was not designed natively to work with web applications.​
Some systems only support integration with LDAP and not SSO​

![](image/Pasted%20image%2020230514191421.png)


# 9 Multi-Factor-Authentication#
8:21:32 Multi-Factor-Authentication

A security control where after you fill in your username/email and password **you have to use a second device** such as a phone to confirm that it's you logging in.

MFA **protects** against people who have stolen your password.
MFA is an option in most cloud providers and even social media websites such as Facebook.

# 10 Security Keys
8:22:26 Security Keys

[Alliance Overview](https://fidoalliance.org/overview/)
[FIDO Alliance Specifications Overview](https://fidoalliance.org/specifications/)

A secondary device is used as the second step in the authentication process to gain access to a device, workstation, or application.
**A popular brand of security key is a Yubikey**
![](image/Pasted%20image%2020230514191807.png)


-   Works out of the box with Gmail, Facebook, and hundreds more
-   Supports **FIDO2**/WebAuthn, U2F
-   Waterproof and crush resistant
-   USB-A and NFC dual connectors on a single key

--- 

A security key can resemble a memory stick. When your finger makes contact with a button of exposed metal on the device, it will generate And autofill a security token.

![](image/Pasted%20image%2020230514191826.png)

# 11 AWS IAM Identity and Access Management 
8:23:43 AWS IAM

AWS Identity and Access Management (IAM ) you can create and manage AWS users and groups, and use permissions to allow and deny their access to AWS resources.

- **IAM Policies**
    - JSON documents that grant permissions for a specific user, group, or role to access services. Policies are attached to **IAM Identities**
- **IAM Permission**
    - The API actions that can or cannot be performed. They are represented in the IAM Policy document

**IAM Identities**
- **IAM Users**
    - End users who log into the console or interact with AWS resources programmatically or via clicking UI interfaces
- **IAM Groups**
    - Group up your Users so they all share permission levels of the group eg. Administrators, Developers, Auditors
- **IAM Roles**
    - Roles grant AWS resources permissions to specific AWS API actions Associate policies to a Role and then assign it to an AWS resource

Access Analyzer helps you identify the resources in your organization and accounts, such as Amazon S3 buckets or IAM roles, shared with an external entity. This lets you identify unintended access to your resources and data, which is a security risk.

## 11.1 Anatomy of an IAM Policy
8:25:05 Anatomy 组成结构 of an IAM Policy

IAM Policies are written in JSON, and contain the permissions which determine what API actions are allowed or denied.

![](image/Pasted%20image%2020230514193031.png)

- Version policy language version.
    - 2012-10-17 is the latest version.
- Statement 
    - container for the policy element you are allowed to have multiples
- Sid (optional) 
    - a way of labeling your statements.
- Effect 
    - Set whether the policy will Allow or Deny
- Action 
    - list of actions that the policy allows or denies
- Principal 
    - account, user, role, or federated user to which you would like to allow or deny access
- Resource 
    - the resource to which the action(s) applies
- Condition (optional) 
    - circumstances under which the policy grants permission


## 11.2 IAM Policies Follow Along
8:27:07 IAM Policies Follow Along

modify IAM role of a EC2 Instance
![](image/Pasted%20image%2020230514202241.png)


# 12 Principle-of-Least-Privilege
8:46:57 Principle-of-Least-Privilege

[Principle of least privilege](https://en.wikipedia.org/wiki/Principle_of_least_privilege)
[Using adaptive authentication](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-user-pool-settings-adaptive-authentication.html)
[ConsoleMe: A Central Control Plane for AWS Permissions and Access](https://netflixtechblog.com/consoleme-a-central-control-plane-for-aws-permissions-and-access-fd09afdd60a8)


**Principle of Least Privilege (PoLP)** is the computer security concept of providing a user, role, or application the least amount of permissions to perform an operation or action.

**Just-Enough-Access (JEA)**: Permitting only the exact actions for the identity to perform a task
**Just-In-Time (JIT)**: Permitting the smallest length of duration an identity can use permissions

**Risk-based adaptive policies**
Each attempt to access a resource generates a risk score of how likely the request is to be from a compromised source. The risk score could be based on many factors e.g. device, user location, IP address what service is being accessed, and when.
AWS at the time of this recording does not have Risk-based adaptative policies built into IAM

**ConsoleMe** is an open-source Netflix project to self-serve short-lived IAM policies so an end-user can access AWS resources while enforcing JEA and JIT
[https://github.com/Netflix/consoleme](https://github.com/Netflix/consoleme)

# 13 AWS Account Root User
8:49:12 AWS Account Root User

[AWS account root user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html)

**AWS Account** – the account which holds all your AWS resources
**AWS Account** – **Root User** – a special account with full access that cannot be deleted
**AWS Account** – **User** – a user for common tasks that are assigned permissions

![](image/Pasted%20image%2020230514200745.png)

AWS Account Root User is a special user who is created at the time of AWS account creation:
-   The Root User account uses an Email and Password to log in
    -   A regular user has to provide the Account ID / Alias, Username, and Password
-   The Root User account can not be deleted
-   The Root User account has full permissions to the account and its permissions *cannot be limited.
    -   You cannot use IAM policies to explicitly deny the root user access to resources.
    -   You can only use an AWS Organizations service control policy (SCP) to limit the permissions of the root user
-   There can only be one Root user per AWS account
-   The root user is instead for very specific and specialized tasks that are infrequently or rarely performed
    -   An AWS Root Account should not be used for daily or common tasks
-   It's strongly recommended to never use Root User Access Keys
-   It's strongly recommended to turn on MFA for the Root User

Administrative Tasks **that only the Root User can perform**:
-   **Change your account settings**.
    -   includes the account name, email address, root user password, and root user access keys.
    -   Other account settings, such as contact information, payment currency preference, and Regions, do not require root user credentials.
-   Restore IAM user permissions.
    -   If the only IAM administrator accidentally revokes their own permissions, you can sign in as the root user to edit policies and restore those permissions.
-   Activate IAM access to the Billing and Cost Management console.
-   View certain tax invoices
-   **Close your AWS account**.
-   **Change or Cancel AWS Support plan**
-   Register as a seller in the Reserved Instance Marketplace.
-   Enable MFA Delete on an S3 Bucket.
-   Edit or delete an Amazon S3 bucket policy that includes an invalid VPC ID or VPC endpoint ID.
-   Sign up for GovCloud.

# 14 SSO
8:52:31 AWS SSO

[Introducing AWS Single Sign-On](https://aws.amazon.com/blogs/security/introducing-aws-single-sign-on/)
[AWS Single Sign-On](https://aws.amazon.com/single-sign-on/)

**AWS Single Sign-On (AWS SSO)** is where you create or connect, your workforce identities in AWS **once** and manage access centrally across your AWS organization.

**Choose your Identity Source**
-   AWS SSO
-   Active Directory
-   SAML 2.0 IdP

**Managed User Permissions Centrally**
-   AWS Account
-   AWS Applications
-   SAML Applications

**Uses get Single Click Access**

![](image/Pasted%20image%2020230514201311.png)
