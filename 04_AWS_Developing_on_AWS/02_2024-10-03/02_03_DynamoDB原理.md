
![](image/Pasted%20image%2020241003103546.png)



ralarionnal DB的缺点
when you do index maintenace or backup , latenz will increase  up from milisecond to second 
most website need the db with low latency

![](image/Pasted%20image%2020241003110019.png)


spike is casued by sales festeaval , load is increased 
to reconsile with this circumstance , you need to change the capacity dynamically , 

the instance should be destory, wenn the workload devcread 

当你需要 不管用户有多少的时候, latency 保持在一定值 , 这时候 你就需要 dynamoDB 
De always with five users per day or fifty or five million, we always want to reply less than five milliseconds.



# 1 文献 

Avinash Lakshman ist Canssadra 的创始人

![](image/Pasted%20image%2020241003110508.png)


![](image/Pasted%20image%2020241003110634.png)


![](image/Pasted%20image%2020241003110805.png)


[https://youtu.be/yvBR71D0nAQ](https://youtu.be/yvBR71D0nAQ "https://youtu.be/yvbr71d0naq")
![](image/Pasted%20image%2020241003142923.png)


![](image/Pasted%20image%2020241003143426.png)


![](image/Pasted%20image%2020241003143511.png)






----
100 -> 
401 表示 数字越来越大 需要对  DynomoDB了解比较深了再看 

DAT401 

![](image/Pasted%20image%2020241003144553.png)


![](image/Pasted%20image%2020241003144629.png)


![](image/Pasted%20image%2020241003144649.png)





# 2 下载和使用dynomoDB Locally 

![](image/Pasted%20image%2020241003143017.png)



![](image/Pasted%20image%2020241003143149.png)

![](image/Pasted%20image%2020241003143224.png)




## 2.1 noSQL Workbench


![](image/Pasted%20image%2020241003143243.png)


![](image/Pasted%20image%2020241003143310.png)

[https://youtu.be/yvBR71D0nAQ](https://youtu.be/yvBR71D0nAQ "https://youtu.be/yvbr71d0naq")


![](image/Pasted%20image%2020241003143330.png)



# 3 DynamoDB basics

> The maximum item size in DynamoDB is 400KB.

![](image/Pasted%20image%2020241003110851.png)

- DynamoDB ist serverless 


Choice of Partition Key  is very important 


![](image/Pasted%20image%2020241003112607.png)



## 3.1 eventually consistent.

DynamoDB is an eventually consistent system.

![](image/Pasted%20image%2020241003142051.png)

https://i.ibb.co/DtxrRH3/eventual-consistency.png


It takes time for rights to propagate to all the nodes.

Right. So are you then saying that somebody writes something at 9:00 in the evening and then you update at 10?
I'm obviously exaggerating the times here but let's say I write something in dynamdv at 9 like the price of the ticket of Kyle M for Amsterdam to Paris for example and it's currently €100 and then Somebody goes at E10 and updates the price to €150.

Right. And when you read at 12, you might get the price at 9. You might get a price at 11 or you might get a price of yesterday.

Let me repeat it very slowly. When you write to Dynamo DB or any other eventually consistent system, I'm obviously exaggerating here because you know why we call it eventual consistency because the system gets to final consistency eventually when we do not know.

'Cause I can get from here to Australia in 250 milliseconds but if you say hey I open a support ticket withinwsi just updated something


![](image/Pasted%20image%2020241003135810.png)

Eventually consisiten ist default 

globally distributed system  

What would be the consequences if due to the fact that is a distributed computing global distributed system? What would be the consequences if it's an eventually consistent system?
-> user maybe like a policy
-> I run it and the policy says I don't have access to S3.



![](image/Pasted%20image%2020241003135826.png)


## 3.2 S3 is not anymore


S3 was  eventually consitent for 14 year but not antmore 

https://aws.amazon.com/blogs/aws/amazon-s3-update-strong-read-after-write-consistency/


![](image/Pasted%20image%2020241003142304.png)

![](image/Pasted%20image%2020241003142358.png)




## 3.3 Cap theorem

在理论计算机科学中，CAP定理，又被称作布鲁尔定理，它指出对于一个分布式计算系统来说，不可能同时满足以下三点： 一致性 可用性 分区容错性 根据定理，分布式系统只能满足三项中的两项而不可能满足全部三项。理解CAP理论的最简单方式是想象两个节点分处分区两侧。允许至少一个节点更新状态会导致数据不一致，即丧失了C性质。 维基百科

![](image/Pasted%20image%2020241003140112.png)








# 4 如何设计 nosql table 

Queries that are more common because that determines the layout on the table.
 restrict the number of queries

根据 最常见的 query 的频率 去选择 partionkey , sortKey 



## 4.1 core princple

distributed partition should be balanced  for each partition 
Query should be distributed to partition balanced 
The combination of the you want the combination of the partition key  should be balance and the sort key to be unique 
the combination of  parationkey and sortkey  should be give you a  uniqued result, uniqued identity 查询结果 


## 4.2 Choose the right- DynamoDB-partition-key 



![](image/Pasted%20image%2020241003112115.png)



## 4.3 设计 DynamDBtable的DesignPattern

hierarchical structure
modeling Design 

![](image/Pasted%20image%2020241003144355.png)



plesae 
maybe I want to do a query to say show me only this leaf here of the tree like get me only at least of my dealers in the Netherlands.
For Amsterdam region and always do it with that magical trick of the sort key and the partition key, because we know that's the stuff that runs on the back end and I can have millions of viewers and they will always come back in five milliseconds or less. I.


![](image/Pasted%20image%2020241003144457.png)




## 4.4 例子 


1 movie 


![](image/Pasted%20image%2020241003111832.png)

2 大选选票 

Texes and Florida 作为 Partion key 
Thrump or xx 作为 Sortkey 



# 5 Create DB 


![](image/Pasted%20image%2020241003112738.png)


![](image/Pasted%20image%2020241003112815.png)


![](image/Pasted%20image%2020241003112832.png)


![](image/Pasted%20image%2020241003112839.png)


![](image/Pasted%20image%2020241003112913.png)



## 5.1 Read/write Capacity 

provisoned 
rcu: Read-copy-update

provisioned throughput exceeds 


![](image/Pasted%20image%2020241003112931.png)


![](image/Pasted%20image%2020241004084021.png)

![](image/Pasted%20image%2020241003113138.png)



![](image/Pasted%20image%2020241003113208.png)


![](image/Pasted%20image%2020241003113304.png)

### 5.1.1 provisioned mode  and on-Demand mode 

 provisioned mode 
- advantage
    - the capaticy ist reseverd for you 
    - get a rough idea how much ist cause 
- Disadvantage 
    - you has to pay even if you don't use thie capacity 

on-Demand
- advandtage 
    - you don;t need to pay if you don;t use 
    - So I would say on demand is probably certainly economically specially
- disadvantage 
    - coldstart :  And now I see that you guys connect capacity as needed, but you still taking a few minutes and my application this specific use case cannot tolerate.


#### 5.1.1.1 privioned mode 

item is vector, 每个 item 都是一个储存形式 


![](image/Pasted%20image%2020241003113410.png)


![](image/Pasted%20image%2020241003113527.png)

#### 5.1.1.2 on demand

![](image/Pasted%20image%2020241003114230.png)


![](image/Pasted%20image%2020241003113937.png)


# 6 Create Item

![](image/Pasted%20image%2020241003114600.png)


![](image/Pasted%20image%2020241003114631.png)

# 7 explore item 

![](image/Pasted%20image%2020241003114753.png)


![](image/Pasted%20image%2020241003114741.png)


![](image/Pasted%20image%2020241003114930.png)

---
add attribute 

![](image/Pasted%20image%2020241003115010.png)


![](image/Pasted%20image%2020241003115018.png)




---
返回结果 更像是一个 vector 


![](image/Pasted%20image%2020241003115201.png)




![](image/Pasted%20image%2020241003115218.png)



![](image/Pasted%20image%2020241003115304.png)


---
## 7.1 查询过程不产生延迟的原因



![](image/Pasted%20image%2020241003115519.png)

先 read all the data 不做 filtering, 谁然我们之前就定义好了 filter. 不做 filtering 才可以确保DynamoDB没有 latenz, 
read all the data , 拿出来之后, 再做 filtering 

- Cause remember the fundamental idea of this system is make sure that we never hit five milliseconds or more.
- So that's why yes, we'll do the filtering for you. But after we read all the data, it's all in the docs.

## 7.2 每个item都有自己的value, 是否redundant
But there but doesn't it affect the the rights capacity units as well?
在例子中 的DynamoDB, 每个演员 每个 movie 都要保存 review number , 会不会 过于redundant
答案是不会的, 为什么: 因为 Storage is cheap, so duplicating the data is no problem whatsoever.


![](image/Pasted%20image%2020241003115824.png)




----

![](image/Pasted%20image%2020241003115932.png)


# 8 local seconadary index, global secondary index in the main table 

local seconadary index, global secondary index 更像是一张新表 


去帮助你更好的查询, 快速的查询 

![](image/Pasted%20image%2020241003120132.png)



# 9 Free Tier 


![](image/Pasted%20image%2020241003114310.png)


![](image/Pasted%20image%2020241003114321.png)



![](image/Pasted%20image%2020241003114435.png)


![](image/Pasted%20image%2020241003140915.png)



![](image/Pasted%20image%2020241003140923.png)




# 10 clsuter 

why use clsuter 
- mirco sekuncde service 
- R CU read, WCU write  



![](image/Pasted%20image%2020241004111137.png)


一个cluster 中 有若干个 node,. 对一个 table 提供不同的 rcu wcu 值

![](image/Pasted%20image%2020241004111253.png)


