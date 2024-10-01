这一个章节主要进行一些  不同服务之间的对比 

13:10:59 Know Your Initialisms
13:13:42 AWS Config AWS AppConfig
13:14:39 SNS vs SQS
13:16:16 SNS vs SES vs PinPoint vs Workmail
13:19:18 Amazon Inspector vs AWS Trusted Advisor
13:20:18 Connect Named Services
13:21:26 Elastic Transcoder vs MediaConvert
13:22:27 AWS Artifact vs Amazon Inspector
13:23:13 ELB Variants

# 1 Similar names in AWS

![](image/Pasted%20image%2020230316185240.png)

- CloudFormation
    - it is used for provisioning lots of resources on  AWS.
- CloudWatch
    - CloudWatch Events: can base on could Watch Metrics oder Cloud logs


# 2 Know Your Initialisms 一些缩写
13:10:59 Know Your Initialisms

-   IAM Identity and Access Management
-   S3 Simple Storage Service
-   SWF Simple Workflow Service
-   SNS Simple Notification Service
-   SQS Simple Queue Service
-   SES Simple Email Service
-   SSM Simple Systems Manager
-   RDS Relational Database Service
-   VPC Virtual Private Cloud
-   VPN Virtual Private Network
-   CFN CloudFormation
-   WAF Web Application Firewall
-   MQ Amazon ActiveMQ
-   ASG Auto Scaling Groups
-   TAM Technical Account Manager

---

-   ELB Elastic Load Balancer
-   ALB Application Load Balancer
-   NLB Network Load Balancer
-   GWLB Gateway Load Balancer
-   CLB Classic Load Balancer
-   EC2 Elastic Cloud Compute
-   ECS Elastic Container Service
-   ECR Elastic Container Repository
-   EBS Elastic Block Storage
-   EFS Elastic File Storage
-   EMR Elastic MapReduce
-   EB Elastic Beanstalk
-   ES Elasticsearch
-   EKS Elastic Kubernetes Service
-   MSK Managed Kafka Service

---

-   RAM AWS Resource Manager
-   ACM Amazon Certificate Manager
-   PoLP Principle of Least Privilege
-   IoT Internet of Things
-   RI Reserved Instances

# 3 AWS Config and AWS AppConfig
13:13:42 AWS Config AWS AppConfig

AWS Config
AWS Config is a governance tool for Compliance 管理 as Code (CoC).
You can create rules that will check to see if resources are configured the way you expect them to be.
If a resource drifts from the expected configuration you are notified or AWS Config can auto-remediate (correct) the configuration back to the expected state

AWS AppConfig
AWS App Config is used to automate the process of deploying application configuration variable changes to your web application (s).
You can write a validator to ensure the changed variable will not break your web-app
You can monitor deployments and automate integrations to catch errors or rollback.


# 4 SNS vs SQS


- 共同点 
    - have somethings to do with messaging, The Both Connect Apps via Messages
    - ist used for application Integration

SNS: **Simple Notifications Service**
- Pass Along Messages eg. PubSub
- Send notifications to **subscribers** of **topics** via multiple protocols. eg, HTTP, **Email**, SQS, SMS
- SNS is generally used for sending **plain text emails** which are triggered via other AWS Services. The best example of this is billing alarms.
- Can retry sending in case of failure for **HTTPS**
- 应用场景: Really good for webhooks, simple internal emails, triggering Lambda functions

SQS **Simple Queue Service**
- Queue Up Messages, Guaranteed Delivery
- Places messages into a **queue**. Applications pull queue using **AWS SDK**
- XX
    - Can retain a message for up to 14 days
    -   Can send them in sequential order or in parallel
    -   Can ensure only one message is sent
    -   Can ensure messages are delivered at least once
- 应用场景 Really good for delayed tasks, queueing up emails


![](image/Pasted%20image%2020230317093220.png)

|Thema |Simple Notifications Service (SNS)| Simple Queue Services |
|--|--|--|
|发送信息是否等待 |using PubSub, Publisher Subscriber messaging model . It passes allongs messages | massaging message, but it is queuing up message |
|确保信息是否收到|just pass message| if can get the guaranteed of delievery|
|email 的格式|just plain text emails, it cannot do HTML emails|| 


# 5 SNS vs SES vs PinPoint vs Workmail
13:16:16 SNS vs SES vs PinPoint vs Workmail

![](image/Pasted%20image%2020230317175053.png)

共同点
- the all send emails 

- SNS: Simple Notification Service (Practical and Internal Emails)
    -  It is really intended for  practical use cases and internal use cases when  it comes to sending emails.
    - with  SNS you can send notifications to subscribers  of topics via multiple protocols, so we're not  just limited to email, but we have HTTP email,  SMS and we can also do lambdas
    - sending *plain text emails* ( best example: billing alarms)
- SES: Simple Email Services (Transactional Emails )
    - 更专业的 email services
    - can send *html emails* and also plain text email 
    -  can create Email Templates
    - Custom domain name email 
    - monitor your email reputation
- **Amazon PinPoint**   ( Promotional Emails) 
    - Emails for marketing
    -   Create email campaigns
    -   Segment your contacts
    -   Create customer journeys via emails
    -   A/B emailing testing
- **Amazon Workmail** (Email Web Client)
    - Similar to Gmail and Outlook. 
    - 应用场景: Create company emails, read, write and send emails from a Web Client within AWS Management Console

# 6 Amazon Inspector vs AWS Trusted Advisor

相同之处
- **Both are** **security tools** **and they both perform audits** 
- both of these services  have a security component involved
- both are security tools and they both perfrom audits

不同之处 :
- inspector is really  just about A EC2 instances and and making them  secure or hardened. 
- trusted advisor is all  about multiple services and security practices
- Trusted Advisor **doesn’t generate out a PDF** report.

**Amazon Inspector**
- Inspector audit **a single instance* or all the  instances within your region. it  would run a script, which would then run against  a security checklist, and it will come back and  report to you what checks have passed or failed.  
    - there is one very popular benchmark by the CIS,  which will do 699 checks
- Audits **a single EC2 instance** that you’ve selected
- Generates a report from a long list of security checks i.e 699 checks.

**Trusted Advisor**
- Trusted Advisor **doesn’t generate out a PDF** report.
    - probably is  a way to export a CSV or something. But it's not like something that is promoted with trusted  advisor. 
- trusted advisor gives you **a holistic view** of  recommendations across multiple service services  and best practices. 
    - it has a whole section on just security, 
    - Example: it would tell you  something like, Hey, you should really enable   MFA on your root account.
    - eg. You have open ports on these security groups
- You should enable MFA on your root account when using Trusted advisor.

![](image/Pasted%20image%2020230317172708.png)


# 7 Connect Named Services
13:20:18 Connect Named Services

They all have **“Connect”** in the name but they are not related or similar in functionality

**AWS Direct Connect**
-   A Dedicated Fiber Optics Connection from your DataCenter to AWS
-   Intended for large enterprises with their own data center and they need an insanely fast and private connection directly to AWS.
-   If you need a **secure connection** you need to apply an AWS VPN connection on top of Direct Connect

**Amazon Connect**  (呼叫中心)
-   Call Center as a Service
-   Get a toll-free number, accept inbound and outbound calls, set up automated phone systems.
-   Interactive Voice System (IVS)

~~**Media Connect **~~ ( 视频 转码器)
-   ~~New Version of Elastic Transcoder, Converts Videos to Different Video Types~~
-   ~~You have 1000 videos of you and you need to transcode them into different videos format, maybe you need to apply watermarks, or insert an introduction video in front of every video~~

**AWS Elemental MediaConnect**
-   A igh-quality transport service for live video
-   Get the reliability and security of satellite and fiber combined with the flexibility, agility, and economics of IP-based networks using AWS Elemental MediaConnect

![](image/Pasted%20image%2020230316190231.png)



# 8 Elastic Transcoder vs Media Convert
13:21:26 Elastic Transcoder vs MediaConvert

这两种 服务 都是 用来 tanscode videos 
Aws Elemental MediaConvert has a better Integration with aws API 

**Elastic Transcoder**
The Old Way
Elastic Transcoder was the original transcoding service. It may have programmatic APIs or workflows not available in MediaConvert.
It exists due to legacy customers still using the platform

-   Transcodes videos to streaming formats

**AWS Elemental MediaConvert**
The New Way
MediaConvert is a more robust transcoding service that can perform various operations during transcoding.

-   Transcodes videos to streaming formats
-   Overlays images
-   Insert videos clips
-   Extracts captions data
-   Robust UI


![](image/Pasted%20image%2020230317092955.png)



# 9 AWS Artifact vs Amazon Inspector



![](image/Pasted%20image%2020230318144044.png)

Both Artifact and Inspector **compile out PDFs**

- Artifact
    - Why enterprise trust aws? Does AWS meet specific compliance frameworks (SOC or PCI) ? 
    - Generates a security report that’s based on **global compliance frameworks** such as:
        -   Service Organization Control (SOC)
        -   Payment Card Industry (PCI)
- AWS Inspector
    - How do we know this EC2 Instance is Secure? Prove it ? 
    - It runs a  script that analyzes your EC two instance, and  then generates out a PDF report telling you which  security checks have passed.
    - **Audit tool for the security of EC2 instances**

# 10 ELB Variants:  ALB vs NLB vs CLB
Elastic Load Balancer (ELB) has 4 different types of possible load balancers.
all are loadbalancer

ALB: Applikation Loadbalancer 
NLB: Network Loadbalancer
CLB: Classic Loadbalancer 
GWLB: Gateway Load Balancer 

application load balancer  and network load balancer  are specialized for their  individual use case. 

All thos Loadbalancer you can attch the amazon certification manager so you can apply ssl certificate

![](image/Pasted%20image%2020230317173623.png)

![](image/Pasted%20image%2020230522144042.png)

- CLB Classic Load Balancer 
    -  Layer 3,4 and 7 
    - does not use target groups. 
    - it's  intended for applications that were built within  the **EC two classic network** in mind,
    - Retires on Aug 15, 2022
- ALB Application Load Balancer
    - works in Application Layer Layer 7 - HTTP/S 
    - So prior to  this, if you needed a load bouncer for subdomain,  you'd have to launch a load bouncer for each one.  But now you with routing rules, you can route all  subdomains to the single load balancer and make  sure that it goes to the right instances that you  want to target.
    - Can attach WAF (web application firewall)
    -  Routing Rules:    create rules to change routing based on information found in an HTTP/S request
- NLB Network Load Balancer 
    - works in Transport layer .  Layer 3 and 4 – TCP and UDP
        - thie layer is dealing with IP protocol data. So this is where  you are dealing with TCP and TLS traffic where extreme performance ist required 
    - Example:  video , games ,  real time. So think about handling  millions of requests per second will maintain  **ultra low latency**
    - It's also optimized  for sudden and volatile traffic patterns. 
    - Optimized for **sudden and volatile traffic** patterns while using a single static IP address per Availability Zone
    - Capable of handling millions of requests per second while maintaining ultra-low latencies
- **Gateway Load Balancer (GWLB)**
    - When you need to deploy a fleet of third-party virtual appliances that support GENEVE


