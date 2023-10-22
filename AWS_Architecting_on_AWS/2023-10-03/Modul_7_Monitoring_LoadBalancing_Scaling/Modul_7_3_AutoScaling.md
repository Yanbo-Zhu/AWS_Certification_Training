

The operations manager asks, “How can we dynamically increase and decrease capacity to meet changing demand?”
Your operations team needs to compare auto scaling features to determine best practices.


![](image/Pasted%20image%2020231003133603.png)

ssl offloading
ssl certizeiter are uploaded into alb . 所以 target 段 不在需要 ssl zertificate 
需要重听 


![](image/Pasted%20image%2020231003133500.png)


AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. Using AWS Auto Scaling, you can set up application scaling for multiple resources across multiple services in minutes.
The service provides a simple, powerful user interface that you can use to build scaling plans for resources. For example, these resources might include EC2 instances, Spot Fleets, and other compute and database services. AWS Auto Scaling makes scaling simple with recommendations for you to optimize performance and costs, or to balance between them.
AWS Auto Scaling provides application scaling for multiple resources such as Amazon EC2, Amazon DynamoDB, Amazon Aurora, and many more across multiple services  in short intervals



# 1 ec2 auto scaling 

![](image/Pasted%20image%2020231003133658.png)


Elasticity: Scaling in and out

![](image/Pasted%20image%2020231003133809.png)

![](image/Pasted%20image%2020231003133841.png)


![](image/Pasted%20image%2020231003133915.png)




![](image/Pasted%20image%2020231003133944.png)



![](image/Pasted%20image%2020231003134015.png)



![](image/Pasted%20image%2020231003134051.png)



![](image/Pasted%20image%2020231003134101.png)

## 1.1 Invoke auto Scaling 

![](image/Pasted%20image%2020231003134150.png)

health status check: 比如说 cpu 使用率过高 

![](image/Pasted%20image%2020231003134233.png)



![](image/Pasted%20image%2020231003134256.png)


## 1.2 ##


![](image/Pasted%20image%2020231003134347.png)



# 2 #


![](image/Pasted%20image%2020231003134450.png)




# 3 #

a

![](image/Pasted%20image%2020231003134510.png)


----

b 因为 只有这样 才能应对 unpredictable traffic 


![](image/Pasted%20image%2020231003134529.png)




----

b

![](image/Pasted%20image%2020231003134644.png)



---


c d 

![](image/Pasted%20image%2020231003134717.png)



----
a 不对 用 cloud watch 
b 是对的 
c 不对 因为 有application
d 是对的 
e 用 cloud watch 

![](image/Pasted%20image%2020231003134801.png)



----


# 4 Lab4


![](image/Pasted%20image%2020231003140836.png)


![](image/Pasted%20image%2020231003134936.png)


![](image/Pasted%20image%2020231003135010.png)


![](image/Pasted%20image%2020231003135022.png)



![](image/Pasted%20image%2020231003135050.png)
































