

![](image/Pasted%20image%2020231003132018.png)


# 1 ELB 

![](image/Pasted%20image%2020231003132153.png)



![](image/Pasted%20image%2020231003132335.png)



Gateway load balancer:  more secutriry only 
其他两个 loadbalacer : normal workload 


----


![](image/Pasted%20image%2020231003132600.png) 



![](image/Pasted%20image%2020231003132645.png)


ssl: for network \
https: for a loader blanace 

什么事 SSL offloading ? 

preserve source ip address: 因为某些国家 要 阻挡 某个货架的访问 
redirects: to another websites


![](image/Pasted%20image%2020231003132905.png)



![](image/Pasted%20image%2020231003133117.png)


s


static ip addresse: fix the ip address that used in alb 

![](image/Pasted%20image%2020231003133208.png)



![](image/Pasted%20image%2020231003133258.png)





ssl offloading

ssl certizeiter are uploaded into alb . 所以 target 段 不在需要 ssl zertificate 
需要重听 


![](image/Pasted%20image%2020231003133500.png)







