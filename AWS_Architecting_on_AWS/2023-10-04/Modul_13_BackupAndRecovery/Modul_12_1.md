

![](image/Pasted%20image%2020231004135923.png)



![](image/Pasted%20image%2020231004140016.png)


![](image/Pasted%20image%2020231004140038.png)



# 1 Disaster Planning



![](image/Pasted%20image%2020231004140120.png)



![](image/Pasted%20image%2020231004140135.png)


![](image/Pasted%20image%2020231004140318.png)


Fault tolerance: even if a problem happens, you will still continue. Users are not going to.  因为 资源部署在了其他 azs 




![](image/Pasted%20image%2020231004140619.png)


![](image/Pasted%20image%2020231004140732.png)


RTO: the time, from  disaster happens , to the timeout the application is available again 

RPO:  
So the the shorter the RPO is, the more frequent the backups must taken

上一次备份为 5 hours 前,  但是我们想把数据恢复成 30mins 前 的状态


![](image/Pasted%20image%2020231004141119.png)




![](image/Pasted%20image%2020231004141145.png)





![](image/Pasted%20image%2020231004141327.png)



![](image/Pasted%20image%2020231004141419.png)




![](image/Pasted%20image%2020231004141515.png)



![](image/Pasted%20image%2020231004141553.png)




# 2 AWS Backup 



![](image/Pasted%20image%2020231004141634.png)



![](image/Pasted%20image%2020231004141645.png)



![](image/Pasted%20image%2020231004141719.png)


![](image/Pasted%20image%2020231004141810.png)



aws backup ist integrated with aws organization 


# 3 Recovery strategies 

![](image/Pasted%20image%2020231004141911.png)


![](image/Pasted%20image%2020231004141948.png)


![](image/Pasted%20image%2020231004142019.png)


-----


![](image/Pasted%20image%2020231004142132.png)


![](image/Pasted%20image%2020231004142319.png)



----

![](image/Pasted%20image%2020231004142402.png)


build a complete copy with in at low capacity 


![](image/Pasted%20image%2020231004142516.png)


DR: DIaster recovery 

![](image/Pasted%20image%2020231004142725.png)




# 4 
# 5 #
![](image/Pasted%20image%2020231004142814.png)



b

![](image/Pasted%20image%2020231004142824.png)


---

b


![](image/Pasted%20image%2020231004142911.png)






-----


a c e 

worng d: no read replicas 



![](image/Pasted%20image%2020231004142924.png)



-------

b

![](image/Pasted%20image%2020231004143053.png)

1 highly availbe
2 minize rto 

-----











