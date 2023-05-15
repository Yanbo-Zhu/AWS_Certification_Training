# 1 AWS Organizations and Accounts

一个组织里面有 root account user 
若干个  Organization Units, 每个 unit 就是一个 aws accounts 
每个 Unit 具有 不同的 Permission, 能够使用的 aws service 也不同  
Services Control Polices  集中管控 这些  permiisions 


![](image/Pasted%20image%2020230308225805.png)



## 1.1 例子

对应的 aws 服务:  

### 1.1.1 Identity and Access Management (IAM ) -> Aws Organization :Organization Activity 
只有 root Account  才有这个权利 
![](image/Pasted%20image%2020230308230553.png)

### 1.1.2 AWS Organizations 
只有 root Account users 才有这个权利 
通过 这个 创立一个 新的 aws organizations 

![](image/Pasted%20image%2020230308230801.png)

![](image/Pasted%20image%2020230308230814.png)


2.1 Accounts 界面 
star 星标的 代表他为 root account 
![](image/Pasted%20image%2020230308231035.png)

![](image/Pasted%20image%2020230308231133.png) 

可以用来去 create new account 
![](image/Pasted%20image%2020230308231907.png)

 
delete aws acoount  per Root account
![](image/Pasted%20image%2020230308235146.png)

delete aws acount 在这个 aws non root account 自己的界面上 
![](image/Pasted%20image%2020230308235529.png)
![](image/Pasted%20image%2020230308235536.png)

2.2 Organize Accounts 界面 
如果你是 root aacounts  下, 就可以利用这个界面去 创造 organizational Unit 
![](image/Pasted%20image%2020230308231642.png)

![](image/Pasted%20image%2020230308231736.png)


将一个 accout 挪到 某个 Organizational units

![](image/Pasted%20image%2020230308232326.png)


2.3 Policies 界面 
![](image/Pasted%20image%2020230308232510.png)

create new policy allowEC2
![](image/Pasted%20image%2020230308234646.png)
![](image/Pasted%20image%2020230308234657.png)
![](image/Pasted%20image%2020230308234722.png)
![](image/Pasted%20image%2020230308234734.png)

Authorize  permission with a Organizational Unit through assign Policy (通过 attach button, 另外还有 deattch 操作  )
![](image/Pasted%20image%2020230308234836.png)
![](image/Pasted%20image%2020230308234845.png)



# 2 AWS Networking

![](image/Pasted%20image%2020230312212008.png)

Public Subnet ist gernerally accessible to the internet. Private Subnet ist not accessible to the internet 
Availability Zone ist just a data center for your where your are going to launch your aws resources. A Availability Zone ist a specific region 

# 3 Database Services

![](image/Pasted%20image%2020230312213745.png)

Redshift: columnar Db,  It reads via columns, not row. It readlly good to read huge data, like  , where you need to generate repots, analytics, like a bussiness intelligence tool 
ElastiCache: storing Cahce, Caching databases 

# 4 Provisioning Services

Provisioning: The Allocation or creation of resources and services to a customer . A easy way to set up a bunch of aws resources for you or your servers in a automaed way 
![](image/Pasted%20image%2020230312215236.png)

- Elastic Beanstalk: 
    - Deploying Web applications , where you don't have to think about the underlying infrastructure. 
    - Only upload you code, upload it to Elastic Beanstalk , choose the container you want to use wiht the language of choice 
    - Like Heroku 技术 is a services not for aws 
- OpsWork
    - help you with the configuration of your instances, using Chef or Puppet
    - using Ruby to define the recipes. In Recipes , it finds the setup thins on you actual server 
    - Through OpsWorks, It has concepts layers. you can define serval tier layers , like appluication layer, database layer , networking layer 
- CloudFormation: 
    - Powerfull provisioning tool. 
    -  compared to  Ops work, OpsWork has some limiatation. But Cloudformation can do anything pretty much in aws. It's most flexible option 
    - in a yaml or json file, you definde hallo aws resources that you want to provision and how you want to configure them . Then upload this yaml file into CloudFormationa then , it set everything up for you in one go 
-  AWS QucikStart
    - A Provisioing tool
    - These are just pre mad packlage (其实就是 cloudformation templates ). They are created by AWS or with AWS third party providers through the apn Network 
    - Example: 你想设置 ml, you got to ml Category. There are bunch of premad configured cloudformation templated. Then you lauch one . 
- AWS Marketplace
    - You can using markepalce to buy managed EC2 instance. 这个是被别人已经调制好的.  你可以按月 subscription 

# 5 Computing Services

![](image/Pasted%20image%2020230313084201.png) 

- EC2
    - Every Services unter the hood is using EC2
- Lamda
    - you just upload the function. You don't have to think about the servers.  
- Elastic Beanstalk
    - Elastic Beanstalk will setup to s3, sns, cloudwatch , RDS, load balancers, etc. 
    - Elastic Beanstalk allows you to setup the developer environments
    - Elastic Beanstalk doesn't really for production use. 
    - Example: you have a web application in Ruby Code, You just upload your code to Elastic Beanstalk. Elastic Beanstalk will run the Code for you 
- AWS Batch 
    - Example: run EC2 scheduled plan , for you usring spot pricing so that you can save the money 

# 6 Storage Services

![](image/Pasted%20image%2020230313123029.png)

- S3: hard drive im Could, unlimied space 
- S3 Glacier: 
    - inexpensive. Waitung一阵子 to acces thos files. There ist a retreival cost. 
    - Good for enterprises who have lots of sensitive data 
    - storage it the archiving and long-term backup
- Storage Gateway
    - hybird solution for on prem to cloud for storage 
    - A extension of your on premise storage into cloud . 就是文件还保存在本地 电脑中, 但是能够 在cloud 中看见 
    - use storage gateway as a backup solution for you local storage. You would just back it up onto S3
- EFS andEBS
    - Ebs can only be attached to only one EC2 instances . 但是 EFS can be sttached to multiple Ec2  instances 
- Snowball
    - a Way that can move a lots of data form on Premise into aws 
    - 通过手动上传 到 s3 太慢了.  
    - if you order a snowball, then they will send. it's basically a computer in the form  of a suitcase with a lot of hard drives in it. And   what you're going to do is you're going to quickly  load your data onto that snowball, and then it's  going to be delivered to AWS directly into s3. it happens just to be like a snowball with additional  features, and more storage so that it actually can also process data as it's being inserted into the  snowball.
    - It's basically like a data center on wheels.  So AWS will drive it to your on premise, location,   and you're going to basically just hook up to  that, and you're going to move all of your data  onto there, and then it's going to be driven back  to AWS and then loaded into s3. 

# 7 Business Centric Services

![](image/Pasted%20image%2020230313134048.png)f

- Amazon Connect 
    - you can accept inbound, inbound  calls and dial outbound, you can record your calls and then store them into s3. 
    - So maybe you could  then run them for analysis maybe through Amazon comprehend or something like that. And you can  also set up workflows within Amazon Connect. So if you want to route a call based on a set of rules,  you can definitely do that there. 
- Workspaces
    - 可以登录 server via your aws account 
    - boils down to  being a virtual Remote Desktop. So secure managed services for provisioning either Windows or Linux desktops in just a few minutes, which quickly scales up to 1000s of desktops.
    - So you just would  have bring your own license and you'd be able to spin up a Windows 10 server that you can now log  in from the convenience of your AWS account. 
- Pinpoint and SES
    - Pinpoint:  is for marketing campaign  management system. And this can send emails  
    - SES is more for like when you are building your web application, and you want to send out emails from that application. So let's say you had someone who registered on your platform, and you want to send them a confirmation email, you send them out through ses. 
    - SES and SNS: SES supports HTML emails. So there's another service called  SNS, which also can send emails, but that can only send plain text. So that's SES is more  designed for marketers because it has that HTML  

# 8 Enterprise Integration
就是将你的 on premise 的东西 和 aws 技术, 造一个 hybrid 系统

![](image/Pasted%20image%2020230313172105.png)

- Direct Connect
    - It's a really good way of having low  latency and a dedicated connection
    - 

# 9 Logging Services

![](image/Pasted%20image%2020230313172125.png)

CloudTrail
CloudWatch

- CloudWatch
    - CloudWatch logs is just a durable storage solution for your logs. And so logs could be performance data about your database services, such as CPU utilization, memory, or network in, you could also store your application logs here. 
    - Example1: So if you are running Ruby on Rails, you could send the logs there or nginx. Just as that as well.
    - Example2: 通过 lambda 产生很多 console logs, 然后把pass 这些 console logs to cloud watch. let's say you're using lambda, you would, you can put within your  functions, a lot of console log calls. And so that would then pass that on to cloud watch. And that is just in itself, application logs for lambdas.  
- CloudWatch Metrics
    - Cloud watch metrics ist like a variable to monitor 
    - CloudWatch Metrics turns the data from Cloudwatch logs into a graph 
- CloudWatch Events
    - when you  have logged data, or you can trigger based off of a metric, or other other kinds of rules. 
    - Example: you might use cloudwatch events for is, every hour, you want  to take a snapshot of your elastic block store,  like the volume that is attached to your  server, you can do that with cloudwatch events,  
- CloudWatch Alarms
    - so you would specify a threshold and when that  threshold is breached, that alarm gets triggered, and then it would send you an email or a  text message however you specify, okay,   then you have cloud watch dashboards. And this  just creates visualizations based off of metrics.  
- CloudWatch Dashboard
    - build graph based on CloudWatch Metrics
    - You cloud represent a lot of data at a glance


