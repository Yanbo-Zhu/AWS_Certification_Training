
Security
12:25:44 Defense-In-Depth
12:27:24 CIA Triad
12:28:59 Vulnerabilities
12:29:57 Encryption
12:30:45 Cyphers
12:31:51 Cryptographic Keys
12:33:05 Hashing and Salting
12:34:56 Digital Signatures and Signing
12:36:38 In-Transit vs At-Rest Encryption
12:37:51 Compliance Programs
12:41:57 AWS Compliance Programs Follow Along
12:42:40 Pen Testing
12:43:51 Pen Testing Follow Along
12:44:40 AWS Artifact
12:45:21 AWS Artifact Follow Along
12:47:31 AWS Inspector
12:48:36 DDoS
12:49:59 AWS Shield
12:52:30 AWS Guard Duty
12:54:08 AWS Guard Duty Follow Along
12:56:40 Amazon Macie
12:57:49 AWS VPN
12:59:00 AWS WAF
13:00:29 AWS WAF Follow Along
13:03:19 Hardware Security Module
13:05:49 AWS KMS
13:07:05 AWS KMS Follow Along
13:09:19 CloudHSM

# 1 Defense-In-Depth: 7 layer of Security 
12:25:44 Defense-In-Depth
[Azure Essentials: Defense in depth security](https://www.youtube.com/watch?v=OTGMi0ksjXY)



![](image/Pasted%20image%2020230522144542.png)

1. Data
access to business and customer data, and encryption to protect data.

2. Application 
applications are secure and free of security vulnerabilities.

3. Compute
Access to virtual machines (ports, on-premise, cloud)

4. Network
limit communication between resources using segmentation and access controls.

5. Perimeter  周边;周围;边缘
distributed denial  拒绝给予 of service (DDoS) protection to filter large-scale attacks before they can cause a denial of service for users.

6. Identity and access
controlling access to infrastructure and change control.

7. Physical
limiting access to a data center to only authorized personnel.

# 2 基础概念

## 2.1 Confidentiality, Integrity, and Availability (CIA) triad 三个一组
12:27:24 CIA Triad


**The CIA triad**
The CIA triad was first mentioned in a **NIST publication from 1977**.
There have been efforts to expand and modernize or suggest alternatives to CIA triad:
-   (1998) Six Atomic Elements of Information eg. confidentiality, possession, integrity, authenticity, availability, and utility
-   (2004) NIST Engineering Principles for Information Technology Security — 33 security principles

Confidentiality 机密性, Integrity 正值 完整, and Availability (CIA) triad is a model describing the foundation of security principles and their trade-off relationship.

**Confidentiality** 加密
confidentiality is a component of privacy that implements to protect our data from unauthorized viewers.
In practice, this can be using cryptographic keys to encrypt our data and using keys to encrypt our keys (envelope encryption)

**Integrity** 准去性 
maintaining and assuring the accuracy and completeness of data over its entire lifecycle.
In Practice utilizing ACID-compliant databases for valid transactions. Utilizing tamper-evident or tamper-proof Hardware security modules. (HSM)

**Availability** 可用性
information needs to be made be available when needed In Practice: High Availability, Mitigating DDoS, Decryption access

## 2.2 Vulnerabilities
12:28:59 Vulnerabilities

a hole or a weakness in the application, which can be a design flaw or an implementation bug, that allows an attacker to cause harm to the stakeholders of an application

![](image/Pasted%20image%2020230522223715.png)

-   Allowing Domains or Accounts to Expire
-   Buffer Overflow
-   Business logic vulnerability
-   CRLF Injection
-   CSV Injection
-   Catch NullPointerException
-   Covert storage channel
-   Deserialization of untrusted data
-   Directory Restriction Error
-   Doubly freeing memory
-   Empty String Password
-   Expression Language Injection
-   Full Trust CLR Verification issue
-   Heartbleed Bug
-   Improper Data Validation
-   Improper pointer subtraction
-   Information exposure through query strings
-   Injection problem
-   Insecure Compiler Optimization
-   Insecure Randomness

---

-   Insecure Temporary File
-   Insecure Third Party Domain Access
-   Insecure Transport
-   Insufficient Entropy
-   Insufficient Session-ID Length
-   Least Privilege Violation
-   Memory leak
-   Missing Error Handling
-   Missing XML Validation
-   Multiple admin levels
-   Null Dereference
-   OWASP .NET Vulnerability Research
-   Overly Permissive Regular Expression
-   PHP File Inclusion
-   PHP Object Injection
-   PRNG Seed Error
-   Password Management Hardcoded Password
-   Password Plaintext Storage
-   Poor Logging Practice
-   Portability Flaw

---

-   Privacy Violation
-   Process Control
-   Return Inside Finally Block
-   Session Variable Overloading
-   String Termination Error
-   Unchecked Error Condition
-   Unchecked Return Value Missing Check against Null
-   Undefined Behavior
-   Unreleased Resource
-   Unrestricted File Upload
-   Unsafe JNI
-   Unsafe Mobile Code
-   Unsafe function call from a signal handler
-   Unsafe use of Reflection
-   Use of Obsolete Methods
-   Use of hard-coded password
-   Using a broken or risky cryptographic algorithm
-   Using freed memory
-   Vulnerability template
-   XML External Entity (XXE) Processing

## 2.3 Encryption
12:29:57 Encryption

**What is cryptography?**
The practice and study of techniques for secure communication in the presence of third parties called adversaries

**What is encryption?**
The process of encoding (scrabbling) information **using a key** and a **cypher** to store sensitive data in an unintelligible format as a means of protection. An encryption takes in plaintext and produces **ciphertext**.

例子
The enigma machine was used during WW2. A different key for each day was used to set the position of the rotors. It relied on simple cypher substitution.

## 2.4 Cyphers  
12:30:45 Cyphers

[Key (cryptography)](https://en.wikipedia.org/wiki/Key_(cryptography))
[Codebook](https://en.wikipedia.org/wiki/Codebook)

**What is a cypher?** 密码索引书
An algorithm that performs encryption or decryption. Cipher is synonymous with “code”

**What is ciphertext**
Ciphertext is the result of encryption performed on plaintext via an algorithm

例子
A **codebook** is a type of document used for gathering and storing cryptography codes

![](image/Pasted%20image%2020230522223941.png)

## 2.5 Cryptographic Keys
密码写的

[Key (cryptography)](https://en.wikipedia.org/wiki/Key_(cryptography))
12:31:51 Cryptographic Keys

**What is a cryptographic key?**
A key is a variable used in conjunction with an encryption algorithm in order to encrypt or decrypt data.

**What is symmetric encryption?**
The same key is used for encoding and decoding. eg **Advanced Encryption Standard (AES)**

**What is asymmetric encryption?**
Two keys are used. One to encode and one to decode eg. **Rivest–Shamir–Adleman (RSA)**


![](image/Pasted%20image%2020230522224104.png)


## 2.6 Hashing and Salting
12:33:05 Hashing and Salting
[Key (cryptography)](https://en.wikipedia.org/wiki/Key_(cryptography))

**What is hashing function?**
A function that accepts arbitrary size value and maps it to a fixed-size data structure. Hashing can reduce the size of the store value.
Hashing is a **one-way process** and is **deterministic**
==A deterministic function always returns the same output for the same input.

**Hashing Passwords**
- ==Hashing functions are used to store passwords in the database so that a password does not reside in a plaintext format.
- ==To authenticate a user, when a user inputs their password, it is hashed, and the hash is compared to the store hashed. If they match then the user has successfully logged in.  
    - in this case , we never need to know, waht the key looks llike orginally 
- Popular hashing functions are **MD5, SHA256, and Bcrypt**
- If an attacker knows what function you are using and stole your database, they could enumerate a dictionary of passwords to determine the password.

**Salting Passwords**
A salt is a random string not known to the attacker that the hash function accepts to mitigate the deterministic nature of hashing functions

## 2.7 Digital Signatures and Signing (SSH key)
12:34:56 Digital Signatures and Signing

![](image/Pasted%20image%2020230522224616.png)

**What is a digital signature?**
A mathematical scheme for verifying the authenticity of digital messages or documents.

A Digital signature gives us **tamper-evidence**.
-   Did someone mess (modify) the data?
-   Is this data is not from the expected sender?

There are three algorithms for digital signatures:
-   **Key generation** – generates a public and private key.
-   **Signing** – the process of generating a digital signature with a **private key** and inputted message  (priavte key for signing)
-   **Signing verification** – verify the authenticity of the message with a **public key** (for verifing )

SSH uses a public and private key to authorize remote access into a remote machine e.g. Virtual Machine. It is common to use RSA
ssh-keygen is a **well-known command** to generate a public and private key

**What is Code Signing?**
When you use a digital signature to ensure **computer code** has not been tampered


## 2.8 In-Transit vs At-Rest Encryption
12:36:38 In-Transit vs At-Rest Encryption

[Transport Layer Security](https://en.wikipedia.org/wiki/Transport_Layer_Security)

**Encryption In-Transit**
Data that is secure when moving between locations
Algorithms: **TLS, SSL**

**Encryption At-Rest**
Data that is secure when residing on storage or within a database
Algorithms: **AES, RSA**

**Transport Layer Security (TLS)**
An encryption protocol for data integrity between two or more communicating computer applications.
TLS 1.0, 1.1 are deprecated. **TLS 1.2** and **1.3** is the current best practice

**Secure Sockets Layers (SSL)**
An encryption protocol for data integrity between two or more communicating computer application
SSL 1.0, 2.0 and 3.0 are deprecated

# 3 Common Compliance programs
12:37:51 Compliance Programs
12:41:57 AWS Compliance Programs Follow Along

[Compliance resource center](https://cloud.google.com/security/compliance)
[Compliance offerings](https://cloud.google.com/security/compliance/offerings)
[What’s The Difference Between SOC 1, SOC 2, and SOC 3?](https://kirkpatrickprice.com/video/soc-1-vs-soc-2-vs-soc-3)

**Compliance Programs**
A set of internal policies and procedures of a company to comply with laws, rules, and regulations or to uphold the business reputation.

**Health Insurance Portability and Accountability Act** of 1996) is United States legislation that provides data privacy and security provisions for safeguarding medical information.

**The Payment Card Industry Data Security Standard** (PCI DSS)
When you want to sell things online and you need to handle credit card information.


两个比较重要: HIPAA and PCI DSS

![](image/Pasted%20image%2020230313182802.png)

![](image/Pasted%20image%2020230313182845.png)

https://aws.amazon.com/compliance/programs/


---

![](image/Pasted%20image%2020230522225142.png)

​**International Organization for Standardization (ISO) / International Electrotechnical Commission​**
ISO/IEC 27001 — control implementation guidance​
ISO/IEC 27017 — enhanced focus on cloud security​
ISO/IEC 27018 — protection of personal data in the cloud. eg. PII​
ISO/IEC 27701 — Privacy Information Management System (PIMS) framework​
-   outlines controls and processes to manage data privacy and protect PII.​

​**System and Organization Controls (SOC)​​**
SOC 1 — 18 standard and report on the effectiveness of internal controls (SSAE) at a service organization ​
-   relevant to their client’s internal control over financial reporting (ICFR).​
SOC 2 — evaluates internal controls, policies, and procedures that directly relate to the security of a system at a service organization​
SOC 3 — A report based on the Trust Services Criteria that can be freely distributed​

​**Payment Card Industry Data Security Standard (PCI DSS)​**
a set of security standards designed to ensure that ALL companies that accept, process, store or transmit credit card information maintain a secure environment.​

​**Federal Information Processing Standard (FIPS) 140-2​​**
US and Canadian government standard that specifies the security requirements for cryptographic modules that protect sensitive information.​

---

![](image/Pasted%20image%2020230522225156.png)

​**Personal Health Information Protection Act (PHIPA)​​**
An Ontario provincial law (Canada) that regulates patient Protected Health Information​

​**​Health Insurance Portability and Accountability Act (HIPAA)​**.​
US federal law that regulates patient Protected Health Information​

​**Cloud Security Alliance (CSA) STAR Certification​​**
Independent third-party assessment of a cloud provider's security posture​

---

![](image/Pasted%20image%2020230522225248.png)

​**Federal Risk and Authorization Management Program (FedRAMP)​​**
US government standardized approach to security authorizations for Cloud Service Offerings​

​**Criminal Justice Information Services (CJIS)​​**
Any US state or local agency that wants to access the FBI's CJIS database is required to adhere to the CJIS Security Policy. ​

​**​General Data Protection Regulation (GDPR)​​**
A European privacy law. Imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU) or collect and analyze data tied to EU residents. ​


## 3.1 AWS Compliance programs

![](image/Pasted%20image%2020230522225408.png)

# 4 Penetration Testing

[Penetration Testing](https://aws.amazon.com/security/penetration-testing/)

PenTesting: An authorized simulated cyberattack on a computer system, performed to evaluate the security of the system.

Pen Testing **is allowed** to be performed on AWS!
在 AWS 上 , man can perform Pentesting on machince , 只需要 付费给aws , 他帮你做 penTesting , 比如说 perform Dos, Ddos 

![](image/Pasted%20image%2020230314193721.png)


**Permitted Services**
-   Amazon EC2 instances
-   NAT Gateways
-   Elastic Load Balancers
-   Amazon RDS
-   Amazon CloudFront
-   Amazon Aurora
-   Amazon API Gateways
-   AWS Lambda and Lambda Edge functions
-   Amazon Lightsail resources
-   Amazon Elastic Beanstalk environments

**Prohibited Activities**
-   DNS zone walking via Amazon Route 53 Hosted Zones
-   Subject to the **DDoS Simulation Testing policy**
    -   Denial of Service (DoS)
    -   Distributed Denial of Service (DDoS)
    -   Simulated DoS, Simulated DDoS
-   Port flooding
-   Protocol flooding
-   Request flooding (login request flooding, API request flooding)

For **Other Simulated Events** you will need to submit a request to AWS. A reply could take up to 7 days.


![](image/Pasted%20image%2020230522225912.png)

# 5 AWS Artifact (self-serve portal for on-demand access to AWS compliance reports)
[AWS Artifact](https://aws.amazon.com/artifact/)
AWS Artifact is a self-serve portal for on-demand access to AWS compliance reports

Aws artifact 就是 产生一个 pdf , 查看这个 pdf 去 determiner whether 你要用的 aws meets a compliance ? 
prove aws meets a compliance  via a very long checklist and the rules whithin a compliance programm 

![](image/Pasted%20image%2020230522230043.png)

如何 产生这个 报告 
made a services in order to generate out the report that shoes that they are compliant
- chonasse a package or aritfact , generate out a PDF , then check the PDF 
- 产生的pdf 只能用 adobe arcobat 打开, mac 的 preview 都不能将他打开. Other PDF readers are nor supported. 

Choose your report
View the PDF
Download the Excel



## 5.1 AWS Artifact Follow Along

![](image/Pasted%20image%2020230313184541.png)

![](image/Pasted%20image%2020230522231853.png)

![](image/Pasted%20image%2020230313184826.png)


pdf 中 是藏有 附件的 
![](image/Pasted%20image%2020230313185117.png)

![](image/Pasted%20image%2020230522232011.png)

得到 xcel 
![](image/Pasted%20image%2020230522232046.png)

# 6 Amazon Inspector
[Amazon Inspector](https://aws.amazon.com/inspector/)

Hardening : The act of eliminating as many security risks as possible 
AWs Inspector runs a security benchmark against specific EC2 instances. 
具体措施 就是 安装 aws agent on the ec2 instances and Run an assessment on target host oder network 

**What is Hardening?**
The act of eliminating as many **security** risks as possible. Hardening is common for Virtual Machines where you run a collection of security checks known as a security benchmark


AWS Inspector 
AWS Inspector runs a **security benchmark** against specific EC2 instances.
You can run a variety of security benchmarks.

Can perform both **Network** and **Host** Assessments
-   Install the AWS agent on your EC2 instances.
-   Run an assessment for your assessment target.
-   Review your findings and remediate security issues.

One very popular benchmark you can run is by CIS which has **699 checks!**


![](image/Pasted%20image%2020230314192225.png)


# 7 DDos (Distributed Denial of Service) 
12:48:36 DDoS
[AWS Shield](https://aws.amazon.com/shield/)

What is a DDoS (Distributed Denial of Service) Attack?

A malicious attempt to disrupt normal traffic by flooding a website with large amounts of fake traffic.
A  managed DDoS protection service that  safeguards applications running on AWS

![](image/Pasted%20image%2020230522232459.png)

# 8 AWS Shield  (对抗 DDos 攻击)
[Getting Started with AWS Shield](https://aws.amazon.com/shield/getting-started/)

AWS Shield is a **managed** DDoS (Distributed Denial of Service) protection service that safeguards applications running on AWS

When you route your traffic through **Route 53** or **CloudFront** you are using **AWS Shield Standard**
AWS Shield 是 在默认情况下 对所有的 aws Customer 免费打开的 
在Route53 和 CloudFront 中使用 aws shield Standard 
![](image/Pasted%20image%2020230522232557.png)


Protects you against **Layer 3 and 4** and 7 attacks
- 7 Application layer   
- 4 Transport layer
-   3 Network layer 
![](image/Pasted%20image%2020230314193003.png)

---

两个版本: 收费版和免费版 
![](image/Pasted%20image%2020230314193259.png)

![](image/Pasted%20image%2020230522232745.png)

![](image/Pasted%20image%2020230314193507.png)

Both plans (Shield Standard and Shield Advanced) integrate with AWS Web Application Firewall (WAF) to give you Layer 7 (Application) protection

1 **Shield Standard FREE**
**protection against most common DDoS attacks**
-   access to tools and best practices to build a DDoS resilient architecture.
-   Automatically available on all AWS services.


2 **Shield Advanced** *3000 USD / Year
**additional protection against larger and more sophisticated attacks**

Available On
-   Amazon Route 53
-   Amazon CloudFront
-   Elastic Load Balancing
-   AWS Global Accelerator
-   Elastic IP (Amazon EC1 and Network Load Balancer)

Notable Features
-   Visibility and Reporting on Layer 3,4 and 7
    -   7 Application
    -   4 Transport
    -   3 Network
-   Access to Team and Support (with Business or Enterprise Support)
-   DDoS Cost Protection
-   Comes with SLA





# 9 Amazon Guard Duty

12:52:30 AWS Guard Duty
12:54:08 AWS Guard Duty Follow Along

监控 你的行为. 利用分析 log 的方法 去 得出你有没有 threat detection. It uses machine learning to analyze the following 80 plus logs so you have cloud trail  logs, your VPC flow logs and your DNS logs. 
r然后通过 CloudWatch Event 来通知你 

![](image/Pasted%20image%2020230522233002.png)

![](image/Pasted%20image%2020230314195103.png)

**What is IDS/IPS?**
IDS/IPS, those stands for intrusion detection systems and intrusion protection system.
A device or software application that monitors a network or systems for malicious activity or policy violations.

**Guard Duty** 
Gaurd Duty detects if some one is attempting to gain access to your aws account or resources
is a **threat detection service** that continuously monitors for malicious, suspicious activity and unauthorized behavior. It uses Machine Learning to analyze the following AWS logs:
-   CloudTrail Logs
-   VPC Flow Logs
-   DNS logs

It will alert you of **Findings** which you can automate an incident response via CloudWatch Events or with 3rd Party Services
![](image/Pasted%20image%2020230314195518.png)

## 9.1 GuardDuty Follow Along

![](image/Pasted%20image%2020230522233210.png)

# 10 Amazon Macie (ML Aws 探测 S3 data access)
[Amazon Macie](https://aws.amazon.com/macie/)

Macie  =  may see

用 mahcine learning 的方法 探测 你存在 s3 中的内容 有没有 敏感的, 没有加密的内容
Macie is a fully managed service that continuously monitors **S3 data access** activity for anomalies, and generates detailed alerts when it detects the risk of unauthorized access or inadvertent data leaks.
Macie works by using Machine Learning to Analyze your CloudTrail logs
Amazon Macie is a data security and data privacy service that uses machine learning (ML) and pattern matching to discover and protect your sensitive data.

![](image/Pasted%20image%2020230314225252.png)

Example:  you put data in your s3 bucket. And that data can be it could be sensitive data, such  as credit card numbers, or personally identify identifiable information, or it could be health  record information. And so what Amazon Macy does,  using the power of machine learning, and also  analyzing your cloud trail logs, it's going to   detect that sense of data and whether that data  has a risk of being compromised or exposed.   
so if you put a file full of credit cards in plain  text, and you upload it to your s3 bucket, Amazon  is gonna say, Hey, we found some credit cards, and  it's plain text, you should probably encrypt this and and archive it and make sure  nobody has access to it. 

Macie has a variety of alerts
-   Anonymized Access
-   Config Compliance
-   Credential Loss
-   Data Compliance
-   File Hosting
-   Identity Enumeration
-   Information Loss
-   Location Anomaly
-   Open Permissions
-   Privilege Escalation
-   Ransomware
-   Service Disruption
-   Suspicious Access

Macy 的功能 
==macie has a variety  of alerts. And this kind of gives you an idea,   the kind of things that can detect
- ransomware: someone trying to lock you out your data and make you pay for it 
- privilege escalation:  for someone  trying to get access to stuff that they're not supposed to, 
- Identity enumeration:  somebody  that is trying to enumerate over the list of stuff that you have to figure out what they can  steal 
- information loss: if you've lost data,   credit credentials loss. So if you have stored  credentials there, and they were lost. 

==macie will identify  your most at-risk users, which could lead to  a compromise. 
- if you have someone on  your team, and you know, they're just having very  poor practices and access to sensitive files very  often, they're going to rank it based on this.  These badges,
- it's funny because you think bronze would be the worst user, but Platinum  is actually the worst user. So the nicer the badge   is the worse this user is. You got to give them  that attention. 



# 11 AWS VPN

AWS VPN lets you establish a secure and private tunnel from your network or device to the AWS global network. 

- Aws Site to Site VPN (我估计我们用的就是这种 )
    - securely connect on premises networks, or a branch office to your  AWS VPC.
    - E.g. connect on-premises network or branch office site to VPC
- AWs Client VPN
    - Securely connect users to AWS, or on  premise networks.
    - some employees, and  they have laptops, and they're, or they're working  from home, and you want them to connect them to  the ADA
- **What is IPSec?**
    - Internet Protocol Security (IPsec) is a secure network protocol suite that authenticates and encrypts the packets of data to provide secure encrypted communication between two computers over an Internet Protocol network. It is used in virtual private networks (VPNs)


# 12 AWS WAF (Web Application Firewall)
[Amazon Inspector](https://aws.amazon.com/inspector/)

12:59:00 AWS WAF
13:00:29 AWS WAF Follow Along

AWS **Web Application Firewall (WAF)** protect your web applications from common web exploits

==Write your own **rules** to ALLOW or DENY traffic based on the contents of HTTP requests
Use a ruleset from a trusted AWS Security Partner in the AWS WAF Rules Marketplace
WAF can be attached to either **CloudFront** or an **Application Load Balancer**

保护 web applications. 
Write your won Rules: Use a ruleset from a trusted aws security Partner in the aws WAF Rules Marketplace 
WAF 需要 atteched to AWSCloud Front or AWS Application Load Balancer

![](image/Pasted%20image%2020230314192236.png)

Protect web applications from attacks covered in the **OWASP Top 10** most dangerous attacks:
1.  Injection
2.  Broken Authentication
3.  Sensitive data exposure
4.  XML External Entities (XXE)
5.  Broken Access control
6.  Security misconfigurations
7.  Cross-Site Scripting (XSS)
8.  Insecure Deserialization
9.  Using Components with known vulnerabilities
10.  Insufficient logging and monitoring

## 12.1 AWS WAF FOllow along 

![](image/Pasted%20image%2020230523000228.png)

create new WAF ACL rule
![](image/Pasted%20image%2020230523000257.png)

![](image/Pasted%20image%2020230523000339.png)

这个新造的 acl 是 rule 某些 ip addresse 可以通过 , 正常进入到 aws acoount 中 
![](image/Pasted%20image%2020230523000438.png)

# 13 Hardware Security Module
13:03:19 Hardware Security Module
[Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/)

- A **Hardware Security Module (HSM)**.
    - ==It's a piece of hardware designed to store encryption keys.
    - ==HSM holds keys in memory and never writes them to disk.
- **Federal Information Processing Standard (FIPS)**
    - US and Canadian government standard that specifies the security requirements for cryptographic modules that protect sensitive information. 
- HSM’s that are **multi-tenant** is **FIPS 140-2 Level 2 Compliant**
    - (multiple customers virtually isolated on an HSM)
    - eg.  use this **FIPS 140-2 Level 2 Compliant** for *AWS KMS*
- HSM’s that are **single-tenant** are **FIPS 140-2 Level 3 Compliant**
    - (single customer on a dedicated HSM)
    - eg. use this **FIPS 140-2 Level 3 Compliant** for *AWS CloudHSM*


# 14 AWS KMS (Key Management Service)
13:05:49 AWS KMS
13:07:05 AWS KMS Follow Along
[AWS Key Management Service (KMS)](https://aws.amazon.com/kms/)

KMS is  a managed service that makes it easy for you to   create and control encryption keys used to encrypt  your data. 

- KMS is it's a multi tenant  HSM. 
    - HSM stands for hardware security module and this is a piece of hardware that's at the AWS  data center. I mean, there's lots of them. But   this piece of hardware is specifically designed  for storing keys within memory. So they're never  written to disk. And that piece of hardware is  extremely secure.  非常安全, 因为 这些 key 不写到硬盘里面去, 而是 写到 hardware 中 
    - It's multi tenant in the sense  that there's other customers that are utilizing  that same piece of hardware, and you all are   virtually isolated from each other via software.   customers 使用同一个 key. 但是他们是  virtually isolated from each other via software
- many AWS services integrate with kms  to encrypt your data with a simple checkbox. 
    - So in this screenshot here, we have RDS where we're  enabling encryption, and that is using kms. Okay,  so a lot of services have that checkbox, and  then you just choose the key from kms. 
    - ![](image/Pasted%20image%2020230314200156.png)
- KMS uses envelope encryption. 
    - 把 key 装到 一个 envelope 中 就看不出来了

**Envelope Encryption**
When you encrypt your data, your data is protected, but you have to protect your encryption key.
When you encrypt your data key with a master key as an additional layer of security.
[KMS Master Key] encrypts → [Envelope Data Key] encrypts → [Data]

![](image/Pasted%20image%2020230314200318.png)

## 14.1 AWS KMS Follow Along 


![](image/Pasted%20image%2020230523001244.png)


Create new key 
![](image/Pasted%20image%2020230523001258.png)

![](image/Pasted%20image%2020230523001323.png)

![](image/Pasted%20image%2020230523001348.png)


在生成 新的 EC2 instance 的时候, 选择 用那个key

![](image/Pasted%20image%2020230523001449.png)

# 15 CloudHSM
13:09:19 CloudHSM

CloudHSM is a single-tenant HSM as a service that automates hardware provisioning, software patching, high availability, and backups.

![](image/Pasted%20image%2020230523001520.png)

AWS CloudHSM enables you to generate and use your encryption keys on FIPS 140-2 Level 3 validated hardware.

Built on Open HSM industry standards to integrate with:
-   PKCS#11
-   Java Cryptography Extensions (JCE)
-   Microsoft CryptoNG (CNG) libraries

You can also transfer your keys to other commercial HSM solutions to make it easy for you to migrate keys on or off of AWS.
Configure AWS KMS to use AWS CloudHSM cluster as a custom key store rather than the default KMS key store.
AWS CloudHSM 比 KMS 贵. KMS 是免费的 或者 1 美元 per key
什么时候要 用AWS CloudHSM; 你是 企业级的, 并且 要  use your encryption keys on FIPS 140-2 Level 3 compliant 

