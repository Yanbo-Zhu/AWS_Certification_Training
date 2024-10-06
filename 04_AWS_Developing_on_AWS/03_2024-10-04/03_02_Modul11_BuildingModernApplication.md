

![](image/Pasted%20image%2020241004103220.png)




![](image/Pasted%20image%2020241004103306.png)

# 1 Archeture Diagramm  

![](image/Pasted%20image%2020241004103915.png)



![](image/Pasted%20image%2020241004104252.png)


![](image/Pasted%20image%2020241004110433.png)

icon 下载  
[https://aws.amazon.com/architecture/icons/](https://aws.amazon.com/architecture/icons/ "https://aws.amazon.com/architecture/icons/")
![](image/Pasted%20image%2020241004110506.png)





# 2 modern applications 


![](image/Pasted%20image%2020241004110338.png)


![](image/Pasted%20image%2020241004110948.png)


![](image/Pasted%20image%2020241004111014.png)



![](image/Pasted%20image%2020241004111438.png)


# 3 serverless application stack 

![](image/Pasted%20image%2020241004111723.png)

## 3.1 Fargate 的优势 


with aws Fargate , 会构建 conputing instance according the conainer in running 
paying docker instance 
这样 就不会多花钱了,   如果构建的 ec2 instance 过于大, 太花钱了, 浪费了, 

## 3.2 Orchestation through aws step fucntions 

![](image/Pasted%20image%2020241004112255.png)



![](image/Pasted%20image%2020241004112341.png)

Do it locally 

![](image/Pasted%20image%2020241004112410.png)


![](image/Pasted%20image%2020241004112432.png)


![](image/Pasted%20image%2020241004112456.png)



图形化界面来选取资源 


# 4 Application Integration: SQS


![](image/Pasted%20image%2020241004121235.png)


![](image/Pasted%20image%2020241004121736.png)



每个 komponent只用了 95% 

aviailabity of service 是打折扣的 

----

serveral threads 被产生 , 然后call backend 
这时候你需要个 queue, than backend restrivve the call from queue
![](image/Pasted%20image%2020241004122111.png)




## 4.1 Amason SQS 

### 4.1.1 Crate queue 
![](image/Pasted%20image%2020241004122708.png)


遇到 dedulipcated 的message, 
recievering side 先要和 client 核实, 然后再看 是弄两遍 , 还是只是一遍


#### 4.1.1.1 Conguration  


![](image/Pasted%20image%2020241004123537.png)


visibility timeout: 
Time that a message disappears when it's picked up from the cube and then rappears once if it is not processed successfully 


Person 1 has taken the mssage A from queue. the message is only visable for person1 for only 30s 
but then, Person1 没有处理成功这个 message  在 30s内 , 比如说因为 windows server crashed . Then after 30s,  the second persion can pick up this message again 

![](image/Pasted%20image%2020241004123722.png)


![](image/Pasted%20image%2020241004123728.png)




### 4.1.2 Order

send a message to queue 

![](image/Pasted%20image%2020241004123746.png)

![](image/Pasted%20image%2020241004123817.png)




## 4.2 Amazon SNS

![](image/Pasted%20image%2020241004125057.png)

with it, you have  a susbscrptipon to a subject with a filter 
diiferent subscribers: like email , like a queue ,  a SNS

![](image/Pasted%20image%2020241004124622.png)




![](image/Pasted%20image%2020241004124628.png)


### 4.2.1 Subscriptions 

![](image/Pasted%20image%2020241004124638.png)

Subscriptor  2 

![](image/Pasted%20image%2020241004124645.png)


Subscriptor 2: cost control 

![](image/Pasted%20image%2020241004124806.png)

Subscriptor 3 

![](image/Pasted%20image%2020241004124817.png)

Subscriptor 3

![](image/Pasted%20image%2020241004125026.png)






## 4.3 一个案例 

s3 has event bus 
一旦s3 有新的event, 然后 s3 eventbus 发布这个 event 到 sqs 上面, 然后若干个人订阅这个 event 




