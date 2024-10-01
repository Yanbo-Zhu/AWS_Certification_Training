
# 1 Resource Groups and Tagging
给 aws resources 加上自己的设置的 tag, 这样 那些 share one or more tags 的 resources 就被铅刀同一个 resource Groups 中了 
![](image/Pasted%20image%2020230308165302.png)

## 1.1 Example: group ec2 

1 创建新的 ec2 , 在创建的时候 填入tag
![](image/Pasted%20image%2020230308170024.png)

2 create  resource groups

![](image/Pasted%20image%2020230308170117.png)

![](image/Pasted%20image%2020230308170416.png)


3 tag Editor ( 用来 manage tag)
通过这个界面 给 某个 resource group 中的所有 elements 加上一个新的 tag
![](image/Pasted%20image%2020230308170907.png)

![](image/Pasted%20image%2020230308170938.png)



=== 下面的这些都有独立的页面, 属于 aws 主 services 页面中的一员

# 2 TCO Calculator (Total Cost of ownership)
可以估算 如果你把你的系统 从 on-premise 迁移到 aws, 你能省多少钱 

![](image/Pasted%20image%2020230308162947.png)

## 2.1 TCO Calculator 的例子

![](image/Pasted%20image%2020230308163214.png)

![](image/Pasted%20image%2020230308163244.png)

![](image/Pasted%20image%2020230308163420.png)

![](image/Pasted%20image%2020230308163500.png)

# 3 AWS Landing Zone
有比较贵的 upfront cost. 
适合大企业, 不适合 中小型的 startup 
提供 baseline environment.   g给他们提供帮助, 帮助这些企业 去建设 多 aws account 的记过 

![](image/Pasted%20image%2020230308164005.png)

主页:  
![](image/Pasted%20image%2020230308164612.png)


## 3.1 AWS Solution: Multi-Account Structure 
![](image/Pasted%20image%2020230308164835.png)

## 3.2 AWS Solution: Account Vending Machine
![](image/Pasted%20image%2020230308165045.png)



# 4 AWS QuickStart
使用 quickstart temple 帮客户按照一个预定好的 template 去 deploy  一个 stock, 由若干个server 组成 
![](image/Pasted%20image%2020230308171650.png)


## 4.1 例子
![](image/Pasted%20image%2020230308171750.png)

![](image/Pasted%20image%2020230308171957.png)

![](image/Pasted%20image%2020230308172021.png)

![](image/Pasted%20image%2020230308172219.png)

![](image/Pasted%20image%2020230308172245.png)



