这个 Modul 的overview 

![](image/Pasted%20image%2020231002084512.png)

# 1 amazon web services 

![](image/Pasted%20image%2020231002084604.png)

![](image/Pasted%20image%2020231002084756.png)

orchestrate services in a huge IT environment
The white commercialize those services


## 1.1 benefit of aws 

![](image/Pasted%20image%2020231002084954.png)

scaleability 
avaialbilty 
you pay only  when you use: 被称作 OpEx model operational 

## 1.2 我们学什么

![](image/Pasted%20image%2020231002085535.png)

# 2 AWS Infrasturcture 

![](image/Pasted%20image%2020231002085619.png)

n virgaina has 6 data center 

- use local zones 
    - encounter the latency
    - a stretch of region closer to where the clients are
    - local zones is AWS facility, but it's not a full-fledged availability zone or a full-fledged pledge
- Edge Locations
    - so edge locations are meant to have caching of data and some accelerated services 
- AWS data centers
    - ![](image/Pasted%20image%2020231002090434.png)
- AZ availility zones 
    - ![](image/Pasted%20image%2020231002090453.png)
    - high availabailty: one region is broken. the data in another region is still in use 
    - 
- Region
    - ![](image/Pasted%20image%2020231002090847.png)
    - prone to the latency 
    - upload through the nearest AW point of presence and then it gets carried over the WS backbone
        - aws point of presence: a rack for cache ,  but it's not a full region or a full availability zone 
- local zones
    - ![](image/Pasted%20image%2020231002091537.png)
- edge location
        - ![](image/Pasted%20image%2020231002091706.png)
    - aws local zons vs edge location 
        - AWS Local Zones address low-latency requirements in specific geographic areas, Edge Locations optimize content delivery and network performance**, and Outposts provide a hybrid cloud solution for on-premises environments with AWS services
        - ![](image/Pasted%20image%2020231002091847.png)

## 2.1 factors that impact region selection 

![](image/Pasted%20image%2020231002091149.png)

Governance : regulatory constraints, some regulations . in the government that allow or not allowed 



