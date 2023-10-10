

# 1 #


![](image/Pasted%20image%2020231004080532.png)

![](image/Pasted%20image%2020231004080633.png)


# 2 VPC endpoints 
 VPC endpoints they public by default 

![](image/Pasted%20image%2020231004080818.png)

![](image/Pasted%20image%2020231004080707.png)


sts: security token services 

![](image/Pasted%20image%2020231004081244.png)


security
- 不许给 ec2 instance iam role,  因为这样虽然可以通过 internet gateway, 但是这样 外部就可以访问他了. 危险了  

为什么不在 public subnet 中设置个 nat gateway , 因为 nat 花钱 


vpc endpoint 只能接触到 aws 内部的资源.  如果真的 要接触到 internet from private subnet, 就必须设置 nat gateway 了 


![](image/Pasted%20image%2020231004081855.png)



---------




![](image/Pasted%20image%2020231004080846.png)



![](image/Pasted%20image%2020231004082338.png)




![](image/Pasted%20image%2020231004082410.png)


![](image/Pasted%20image%2020231004082550.png)



# 3 VPC Peering 

![](image/Pasted%20image%2020231004082716.png)


![](image/Pasted%20image%2020231004082740.png)


vpc peering 不能用, 当 有ip spaces 有 overlap
![](image/Pasted%20image%2020231004083014.png)


croess-account support:  可以联机 不同 aws account 的 vpc 




---

peering connection is only one to one 

![](image/Pasted%20image%2020231004083246.png)


vpc peering go through the backbone 

![](image/Pasted%20image%2020231004083336.png)



![](image/Pasted%20image%2020231004083412.png)



![](image/Pasted%20image%2020231004083449.png)

n: nummber of vpc 

就是说 每个 vpc 的 route table 都需要自己更新 

![](image/Pasted%20image%2020231004083525.png)








# 4 Hybrid networking 

The network engineer asks, “How can we privately route traffic between our VPCs?”
The networking team team is considering options for how to network across VPCs both in a single account and across multiple accounts and AWS Regions.


![](image/Pasted%20image%2020231004083648.png)


![](image/Pasted%20image%2020231004083920.png)




IP sec:   
site to site vpn:  quick to setup , priavte  and secure 
ist ip secert 

----

direct connecti: it takes time,  high speed, private but not secure ,  and cost more
low latency, and is good for hig performace ny 


you get all the public IP address ranges across all the regions

![](image/Pasted%20image%2020231004084028.png)


---


![](image/Pasted%20image%2020231004084422.png)



![](image/Pasted%20image%2020231004084450.png)



# 5 aws transit Gateway


transit gateway 就是一个 gaint gateway 

![](image/Pasted%20image%2020231004084528.png)





![](image/Pasted%20image%2020231004084700.png)



![](image/Pasted%20image%2020231004084719.png)




![](image/Pasted%20image%2020231004084734.png)






![](image/Pasted%20image%2020231004084938.png)



![](image/Pasted%20image%2020231004084953.png)





![](image/Pasted%20image%2020231004085002.png)




![](image/Pasted%20image%2020231004085113.png)






# 6 Review 


![](image/Pasted%20image%2020231004085255.png)






# 7 #

b

![](image/Pasted%20image%2020231004085305.png)



---


![](image/Pasted%20image%2020231004085319.png)


a and c
coutomer site to aws cloud


----

![](image/Pasted%20image%2020231004085414.png)

b  and d 



----












