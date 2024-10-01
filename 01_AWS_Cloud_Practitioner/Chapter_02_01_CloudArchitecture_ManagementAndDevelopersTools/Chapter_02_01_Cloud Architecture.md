# 1 Cloud Architecture Terminologies

Solutions Architect 
A role in a technical organization that architects a technical solution using multiple systems via researching, documentation, experimentation.


Cloud Architect
A solutions architect that is focused solely on architecting technical solutions using cloud services.
A cloud architect needs to understand the following terms and factor them into their design architecture based on the business requirements.
-   **Availability** - Your ability to ensure service remains available e.g. **Highly Available (HA)**
-   **Scalability** - Your ability to grow rapidly or unimpeded
-   **Elasticity** - Your ability to shrink and grow to meet the demand
-   **Fault Tolerance** - Your ability to prevent a failure
-   **Disaster Recovery** - Your ability to recover from a failure e.g. **High Durable (DR)**

A Solutions Architect needs to always consider the following business factors:
-   (Security) How secure is this solution?
-   (Cost) How much is this going to cost?


![](image/Pasted%20image%2020230331154517.png)


## 1.1 High Availability

High Availability: 
Your ability for your service to remain available by ensuring there is no single point of failure and/or ensure a certain level of performance
使用不同的 instance which located in 不同的 availbility zone 

How can you achieve High Availability: 
Running your workload across multiple **Availability Zones** ensures that if 1 or 2 AZs become unavailable your service/applications remain available.

How can High Availability be implemented on AWS:
Using Elastic Load Balancer would assist in implementing High Availability

Elastic Load Balancer ​
A load balancer allows you to evenly distribute traffic to multiple servers in one or more data center. If a data center or server becomes unavailable (unhealthy) the load balancer will route the traffic to only available data centers with servers.​

![](image/Pasted%20image%2020230331155950.png)


### 1.1.1 High Availability 例子

1 
EC2 中 
对于某个EC2 中 , 他和 某个 load balancer 关联上了, 这时候就要设置 相关的  High Availability

- 打开 Elastic Beanstalk 这个服务 
    -  建议个 新的 environment , 选择 high availabilty 
    - ![](image/Pasted%20image%2020230331183217.png)


2 RDS 
新建一个 database 

![](image/Pasted%20image%2020230331183455.png)

如下图, 可以选择 multi-az 
![](image/Pasted%20image%2020230331183410.png)

## 1.2 High Scalability

What is High Scalability?
Your ability to increase your capacity based on the increasing demand of traffic, memory and computing power

How is High Scalability defined?
    Vertical Scaling is known as Scaling Up (When Upgrade to a bigger server)
    Horizontal Scaling is known as Scaling Out (When Add more servers of the same size)


Vertical Scaling (Scaling up): Upgrade to a bigger server 
Horizonal Scaling (Scaling Out): Add more servers of the same size

![](image/Pasted%20image%2020230331172546.png)

## 1.3 High Elasticity
The ability to automatically increase or decrease your capacity based on the current demand of traffic memory and computing power 

Elasticity 只专注于 自动的 Horizonal Scaling out or In (remove or Add more servers of the same size)
Vertical Scaling 难以实现 of traditional architecture
相关的 aws 服务 为 auto scaling Groups, ASG

![](image/Pasted%20image%2020230331173117.png)

What is High Elasticity?
Your ability to automatically increase or decrease your capacity based on the current demand of traffic, memory and computing power

How is Elasticity achieved?
Elasticity relies on **Horizontal Scaling**. **Vertical Scaling** is generally hard for traditional architecture so you’ll usually only see horizontal scaling described with **Elasticity**.
**Scaling Out** — Add more servers of the same size
**Scaling In** — Removing more servers of the same size

How can Elasticity be implemented in AWS?
[**Auto Scaling Groups (ASG)**](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html) - are an AWS feature that will automatically add or remove servers based on scaling rules you define.


## 1.4 Highly Fault Tolerance

What is Highly Fault Tolerant?
The ability for your service to ensure there is no single point of failure. Preventing the chance of failure
The Ability that shift traffic to a redundant system in the the primary system fails 

What is a Fail-over?
Fail-overs are when you have a plan to shift traffic to a redundant system in case the primary system fails

How can Fault Tolerance be achieved?
A common example is having a copy (secondary) of your database where all ongoing changes are synced. The Secondary is not in-use until a failover occurs and it becomes the primary database.

How can Fault Tolerance be implemented using AWS?
RDS Multi-AZ - is when you run a duplicate standby database in another Availability Zone in case your primary database fails.

相关的 服务 :  RDS Multi-AZ 

![](image/Pasted%20image%2020230331173425.png)

## 1.5 High Durability

Your ability to recover from a disaster and to prevent the loss of data solutions that recover from a disaster is known as Disaster Recovery (DR)

Questions you should be asking about your Disaster Recovery procedures:
    Do you have a backup?
    How fast can you restore that backup?
    Does your backup still work?
    How do you ensure current live data is not corrupt?

相关的 aws 服务: CloudEndure Disaster Recovery
CloudEndure Disaster Recovery continuously replicates your machines into a low-cost staging area in your target AWS account and preferred Region enabling fast and reliable recovery in case of IT data center failures. 
 ![](image/Pasted%20image%2020230331173803.png)

## 1.6 Disaster Recovery
### 1.6.1 Business Continuity Plan  (BCP) 
A BCP is a document that outlines how a business will continue operating during an unplanned disruption in services

- RPO Recovery Point Objective 
    - The maximum acceptable amount of data loss  after an unplanned data-loss incident, expressed as an amount of time 
        - How much data are you will to lose 
    - The maximum acceptable amount of data loss since the last data revovery point
    - the objective determines what is considered an acceptable loss of data between the last recovery point and the interruption of service and is defined by the organization
- RTO Recovery Time Objective 
    - The maximum amount of downtime your bussiness can tolerate whithout inccuringa asignificant financial loss 
        -  How much time are you willing to go down 
    - The acceptable delay between the interruption of service and restoration of service. 
    - This Objective determine what is considered an acceptable time window when service is unavailable and is defined by the organization

![](image/Pasted%20image%2020230331174436.png)

### 1.6.2 Disaster Recovery Options
Multiple options for recovery that trade cost vs time to recover

从左往右
- cost 越来越大
- revover 需要的的时间 越来越小
![](image/Pasted%20image%2020230331180028.png)

1 **Backup & Restore**
RPO/RTO (Hours)
You back up your data and restore it to new infrastructure
-   Lower priority use cases
-   Restore data after the event
-   Deploy resources after the event
-   Cost $

2 **Pilot Light**
RPO/RTO (10 mins)
Data is replicated to another region with minimal services running
-   Less stringent RTO & RPO
-   Core Services
-   Start & scale resources after the event
-   Cost

3 **Warm Standby**
RPO/RTO (Minutes)
Scaled-down copy of your infrastructure running ready to scale up
-   Business Critical Services
-   Scale resources after the event
-   Cost 

4 **Multi-site Active/active**
RPO/RTO (Real-time)
Scaled up copy of your infrastructure in another region
-   Zero downtime
-   Near-zero loss
-   Cost 



### 1.6.3 RTO Visualized

- RTO Recovery Time Objective 
    - The maximun amount of downtime your bussiness can tolerate whithout inccuringa asignificant financial loss 
    - The maximum acceptable delay between the interruption of service and restoration of service. 
    - This Objective determine what is considered an acceptable time window when service is unavailable and is defined by the organization
    - How much time are you willing to go down 


- Length of serive interruption 就是  time after the service interruption happens
![](image/Pasted%20image%2020230331180509.png)



### 1.6.4 RPO Visualized

- RPO Recovery Point Objective 
    - The maximum acceptable amount of data loss  after an unplanned data-loss incident, expressed as an amount of time 
        - How much data are you will to lose 
    - The maximum acceptable amount of data loss since the last data revovery point
    - the objective determines what is considered an acceptable loss of data between the last recovery point and the interruption of service and is defined by the organization

![](image/Pasted%20image%2020230331181324.png)

## 1.7 Architectural diagram examples (如何画图)

Download aws architectural  icon:  https://aws.amazon.com/architecture/icons/
![](image/Pasted%20image%2020230331182111.png)

![](image/Pasted%20image%2020230331182704.png)


