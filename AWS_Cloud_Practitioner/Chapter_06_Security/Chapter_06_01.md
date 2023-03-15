
# 1 Shared Responsibility Model

![](image/Pasted%20image%2020230313180031.png)

- Customer's responsibilities  
    - secure the data
        - if you don not turn on monitoring services to monitor sensitive data. It's your fault
    - Configuration
        - if you mis conifguration or dont use the 相应的 aws service to keep them in screct 

![](image/Pasted%20image%2020230313180552.png)


# 2 AWS Compliance programs

Compliance programs: A set of internal policies and procedures of a company to comply with laws, rules  and regulations or to uphold business reputation,  

两个比较重要: HIPAA and PCI DSS

![](image/Pasted%20image%2020230313182802.png)

![](image/Pasted%20image%2020230313182845.png)

https://aws.amazon.com/compliance/programs/

# 3 AWS Artifact

Aws artifact 就是 产生一个 pdf , 查看这个 pdf 去 determiner whether 你要用的 aws meets a compliance ? 
prove aws meets a compliance  via a very long checklist and the rules whithin a compliance programm 

如何 产生这个 报告 
made a services in order to generate out the report that shoes that they are compliant
- chonasse a package or aritfact , generate out a PDF , then check the PDF 
- 产生的pdf 只能用 adobe arcobat 打开, mac 的 preview 都不能将他打开. Other PDF readers are nor supported. 

## 3.1 AWS Artifact Follow Along

![](image/Pasted%20image%2020230313184541.png)

![](image/Pasted%20image%2020230313184826.png)

![](image/Pasted%20image%2020230313185117.png)

# 4 Amazon Inspector

Hardening : The act of eliminating as many security risks as possible 
AWs Inspector runs a security benchmark against specific EC2 instances. 
具体措施 就是 安装 aws agent on the ec2 instances and Run an assessment on target host oder network 

![](image/Pasted%20image%2020230314192225.png)

# 5 AWS WAF (Web Application Firewall)

保护 web applications. 
买 Rules: Use a ruleset from a trusted aws security Partner in the aws WAF Rules Marketplace 
WAF 需要 atteched to AWSCloud Front or AWS Application Load Balancer

![](image/Pasted%20image%2020230314192236.png)

# 6 AWS Shield
A  managed DDoS protection service that  safeguards applications running on AWS
AWS Shield 是 在默认情况下 对所有的 aws Customer 免费打开的 
在Route53 和 CloudFront 中使用 aws shield Standard 

![](image/Pasted%20image%2020230314193003.png)

两个版本: 收费版和免费版 
![](image/Pasted%20image%2020230314193259.png)

![](image/Pasted%20image%2020230314193507.png)

# 7 Penetration Testing

PenTesting: An It's  an authorized simulated cyber attack on a computer  system performed to evaluate the security of the  system
在 AWS 上 , man can perform Pentesting on machince , 只需要 付费给aws , 他帮你做 penTesting , 比如说 perform Dos, Ddos 

![](image/Pasted%20image%2020230314193721.png)

# 8 Amazon Guard Duty
Gaurd Duty detects if some one is attempting to gain access to your aws account or resources
guard duty is a threat  detection service that continuously monitors for   malicious suspicious activity and unauthorized  behavior. 
监控 你的行为. 利用分析 log 的方法 去 得出你有没有 threat detection. It uses machine learning to analyze the following 80 plus logs so you have cloud trail  logs, your VPC flow logs and your DNS logs. 

IDS/IPS, those stands for intrusion detection systems and intrusion protection system.

![](image/Pasted%20image%2020230314195103.png)

![](image/Pasted%20image%2020230314195518.png)

# 9 Key Management Service (KMS)

It is  a managed service that makes it easy for you to   create and control encryption keys used to encrypt  your data. 

- KMS is it's a multi tenant  HSM. 
    - HSM stands for hardware security module and this is a piece of hardware that's at the AWS  data center. I mean, there's lots of them. But   this piece of hardware is specifically designed  for storing keys within memory. So they're never  written to disk. And that piece of hardware is  extremely secure.  非常安全, 因为 这些 key 不写到硬盘里面去, 而是 写到 hardware 中 
    - It's multi tenant in the sense  that there's other customers that are utilizing  that same piece of hardware, and you all are   virtually isolated from each other via software.   customers 使用同一个 key. 但是他们是  virtually isolated from each other via software
- many Eva services integrate with kms  to encrypt your data with a simple checkbox. 
    - So in this screenshot here, we have RDS where we're  enabling encryption, and that is using kms. Okay,  so a lot of services have that checkbox, and  then you just choose the key from kms. 
    - ![](image/Pasted%20image%2020230314200156.png)
- KMS uses envelope encryption. 
    - 把 key 装到 一个 envelope 中 就看不出来了
    - ![](image/Pasted%20image%2020230314200318.png)


# 10 Amazon Macie

Macie  =  may see
用 mahcine learning 的方法 探测 你存在 s3 中的内容 有没有 敏感的, 没有加密的内容

- MACIE is a fully managed service that continuously  monitors s3 data access activity for anomalies,  and generates detailed alerts when it detects  risks of unauthorized access or inadvertently data leaks. 
- Amazon may see it, 

Example:  you put data in your s3 bucket. And that data can be it could be sensitive data, such  as credit card numbers, or personally identify identifiable information, or it could be health  record information. And so what Amazon Macy does,  using the power of machine learning, and also  analyzing your cloud trail logs, it's going to   detect that sense of data and whether that data  has a risk of being compromised or exposed.   
so if you put a file full of credit cards in plain  text, and you upload it to your s3 bucket, Amazon  is gonna say, Hey, we found some credit cards, and  it's plain text, you should probably encrypt this and and archive it and make sure  nobody has access to it. 

Macy has a variety  of alerts. And this kind of gives you an idea,   the kind of things that can detect
- ransomware: someone trying to lock you out your data and make you pay for it 
- privilege escalation:  for someone  trying to get access to stuff that they're not supposed to, 
- Identity enumeration:  somebody  that is trying to enumerate over the list of stuff that you have to figure out what they can  steal 
- information loss: if you've lost data,   credit credentials loss. So if you have stored  credentials there, and they were lost. 


macie will identify   your most at-risk users, which could lead to  a compromise. 
- if you have someone on  your team, and you know, they're just having very  poor practices and access to sensitive files very  often, they're going to rank it based on this.  These badges,
- it's funny because you think bronze would be the worst user, but Platinum  is actually the worst user. So the nicer the badge   is the worse this user is. You got to give them  that attention. 


![](image/Pasted%20image%2020230314225252.png)

# 11 Security Groups vs NACLs



# 12 AWS VPN