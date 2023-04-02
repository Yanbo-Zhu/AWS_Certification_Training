# 1 Cloud Architecture Terminologies

Solutions Architect 
Cloud Architect
    -Avaiablity
    -Scalability
    -Elasticity
    -Fault Tolerance
    - Disaster Recovery 

![](image/Pasted%20image%2020230331154517.png)


## 1.1 High Availability

High Availability: to remain available by ensuring there ist no single point of failure and/or ensure a certain level of performance 
使用不同的 instance which located in 不同的 availbility zone 

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

Vertical Scaling (Scaling up): Upgrade to a bigger server 
Horizonal Scaling (Scaling Out): Add more servers of the same size

![](image/Pasted%20image%2020230331172546.png)

## 1.3 High Elasticity
The ability to automatically increase or decrease your capacity based on the current demand of traffic memory and computing power 

Elasticity 只专注于 自动的 Horizonal Scaling out or In (remove or Add more servers of the same size)
Vertical Scaling 难以实现 of traditional architecture
相关的 aws 服务 为 auto scaling Groups, ASG

![](image/Pasted%20image%2020230331173117.png)


## 1.4 Highly Fault Tolerance
The Ability for you service to ensure there is no single point of failure 
The Ability that shift traffic to a redundant system in the the primary system fails 
相关的 服务 :  RDS Multi-AZ 

![](image/Pasted%20image%2020230331173425.png)

## 1.5 High Durability

The ability to recover from a disaster  , to prevent the loss of data solution
Disaster Recovery (DR)
相关的 aws 服务: CloudEndure Disaster Recovery 

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


