
这一个章节主要进行一些  不同服务之间的对比 

# 1 Cloud* Service

![](image/Pasted%20image%2020230316185240.png)

- CloudFormation
    - it is used for provisioning lots of resources on  AWS.
- CloudWatch
    - CloudWatch Events: can base on could Watch Metrics oder Cloud logs

# 2 *Connect Service

![](image/Pasted%20image%2020230316190231.png)


# 3 Elastic Transcoder vs Media Convert
这两种 服务 都是 用来 tanscode videos 
Aws Elemental MediaConvert has a better Integration with aws API 

![](image/Pasted%20image%2020230317092955.png)

# 4 SNS vs SQS

SNS: Simple Notification Service
SQS: Simple Queue Services

- 共同点 
    - have somethings to do with messaging 
    - ist used for application Integration

![](image/Pasted%20image%2020230317093220.png)

|Thema |Simple Notifications Service (SNS)| Simple Queue Services |
|--|--|--|
|发送信息是否等待 |using PubSub, Publisher Subscriber messaging model . It passes allongs messages | massaging message, but it is queuing up message |
|确保信息是否收到|just pass message| if can get the guaranteed of delievery|
|email 的格式|just plain text emails, it cannot do HTML emails|| 


# 5 SNS vs SES

![](image/Pasted%20image%2020230317175053.png)

- SNS: Simple Notification Service
    -  It is really intended for  practical use cases and internal use cases when  it comes to sending emails.
    - with  SNS you can send notifications to subscribers  of topics via multiple protocols, so we're not  just limited to email, but we have HTTP email,  SMS and we can also do lambdas
    - sending plain text emails ( best example: billing alarms)
- SES: Simple Email Services
    - 更专业的 email services
    - can send html emails and also plain text email 
    -  can create Email Teplates
    - Custom domain name email 
    - monitor your email reputation
- 

# 6 Inspector vs Trusted Advisor
both of these services  have a security component involved
both are security tools and they both perfrom audits

不同之处 :
inspector is really  just about A EC2 instances and and making them  secure or hardened. 
trusted advisor is all  about multiple services and security practices

![](image/Pasted%20image%2020230317172708.png)

## 6.1 Inspector

- Inspector audit a single instance or all the  instances within your region. it  would run a script, which would then run against  a security checklist, and it will come back and  report to you what checks have passed or failed.  
    - there is one very popular benchmark by the CIS,  which will do 699 checks


## 6.2 trusted advisor

- trusted advisor doesn't generate PDF report, 
    - probably is  a way to export a CSV or something. But it's not like something that is promoted with trusted  advisor. 
- trusted advisor gives you a holistic view of  recommendations across multiple service services  and best practices. 
    - it has a whole section on just security, 
    - Example: it would tell you  something like, Hey, you should really enable   MFA on your root account.


# 7 Artifact vs Inspector

Both Artifact ans Inspector compile out PDFs

![](image/Pasted%20image%2020230318144044.png)

- Artifact
    - Why enterprise trust aws. Does AWS meet specific compliance frameworks (SOC or PCI)
- AWS Inspector
    - How do we know this EC2 Instance is Secure? Prove it
    - It runs a  script that analyzes your EC two instance, and  then generates out a PDF report telling you which  security checks have passed.


# 8 ALB vs NLB vs CLB

all are loadbalancer

ALB: Applikation Loadbalancer 
NLB: Network Loadbalancer
CLB: Classic Loadbalancer 

application load balancer  and network load balancer  are specialized for their  individual use case. 

All thos Loadbalancer you can attch the amazon certification manager so you can apply ssl certificate

![](image/Pasted%20image%2020230317173623.png)


- CLB
    -  does not use target groups. 
    -  it's  intended for applications that were built with   the EC two classic network in mind,
- ALB
    - works in Application Layer
    - So prior to  this, if you needed a load bouncer for subdomain,  you'd have to launch a load bouncer for each one.  But now you with routing rules, you can route all  subdomains to the single load balancer and make  sure that it goes to the right instances that you  want to target.
    - Can attach WAF (web application firewall)
- NLB
    - works in Transport layer . thie layer is dealing with IP protocol data. So this is where  you are dealing with TCP and TLS traffic where extreme performance ist required 
    - Example:  video , games ,  real time. So think about handling  millions of requests per second will maintain  ultra low latency, . I
    - t's also optimized  for sudden and volatile traffic patterns. 




