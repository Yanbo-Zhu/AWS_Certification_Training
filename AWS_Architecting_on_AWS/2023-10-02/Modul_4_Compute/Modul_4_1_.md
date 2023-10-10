
![](image/Pasted%20image%2020231002143219.png)

![](image/Pasted%20image%2020231002143318.png)


# 1 Business requests 

![](image/Pasted%20image%2020231002143328.png)


# 2 Compute service 

![](image/Pasted%20image%2020231002143804.png)


![](image/Pasted%20image%2020231002143439.png)


# 3 ec2 instance 

![](image/Pasted%20image%2020231002143501.png)


Vituralization: 


EC2 instance is a virtual machine on a physical host in AWS


![](image/Pasted%20image%2020231002143822.png)


Consider the following options: 
• Name and tags – How should your instance be identified? 
• Application and operating system (OS) image – What will you start running? 
• Instance type and size – What technical requirements do you have? 
• Authentication and key pair – How do you plan to connect to the instance? 
• Network settings and security – What virtual private cloud (VPC), subnet, and security groups will you use? 
• Configure storage – What type of block storage is best for your use case? 
• Placement and tenancy – Where should you run your EC2 instances? 
• Scripts and metadata – What can you do to automate your launch



![](image/Pasted%20image%2020231002143923.png)

![](image/Pasted%20image%2020231002144004.png)


![](image/Pasted%20image%2020231002144219.png)



![](image/Pasted%20image%2020231002144319.png)

g ist gravition.   That's a specific hardware or CPU that integrates is used

![](image/Pasted%20image%2020231002144433.png)



the new generation in the same family 价格越便宜 
![](image/Pasted%20image%2020231002144611.png)


![](image/Pasted%20image%2020231002144651.png)



![](image/Pasted%20image%2020231002144745.png)


租期；租用

![](image/Pasted%20image%2020231002144917.png)

shared tenancy: 只占用  physical host 某个instance, 别人可以使用同个 host 的其他的 instance 
dedicated instance: physical host 全部占用 , 空出来的时候, 别人也是用得了
dedicated host : physical host 全部占用 , 空出来 别人也是用不了


## 3.1 Placement groups and use cases 

![](image/Pasted%20image%2020231002145208.png)

![](image/Pasted%20image%2020231002145743.png)

![](image/Pasted%20image%2020231002145923.png)


# 4 Storage for EC2 instances 

![](image/Pasted%20image%2020231002150106.png)


### 4.1.1 ebs 

![](image/Pasted%20image%2020231002150116.png)

![](image/Pasted%20image%2020231002150407.png)

block based storage : Storing the files and something like that in in blocks instead of making changes and so on is suitable for this kind of storage
Block storage is technology that controls data storage and storage devices. It takes any data, like a file or database entry, and divides it into blocks of equal sizes. The block storage system then stores the data block on underlying physical storage in a manner that is optimized for fast access and retrieval


primary : root volumes. ebs backed 

ebs voLumes and instance have to be in the same the AZ 

connection and kommunication between instanc and ebs volumens : via iops 
I can detach a ebs olumen and re tach it to another instance




![](image/Pasted%20image%2020231002150749.png)

burstable 是个重要的特性 

![](image/Pasted%20image%2020231002150910.png)

![](image/Pasted%20image%2020231002150923.png)

### 4.1.2 Instance store volumes

![](image/Pasted%20image%2020231002151005.png)

IOPS是一个用于电脑存储设备性能测试的量测方式，可以视为是每秒的读写次数。和其他性能测试一様，存储设备制造商提出的IOPS不保证就是实际应用下的性能。  

instance stops, store volumne 会被 会被自动删除
但是 Instance store volumes 的 iops 比 ebs  高


又想 保持 告诉访问, 又想数据不损失 怎么办: 
使用  distributed architecture. replicate my data across multiple instances  . aws replicate the data across AZs 
aws  使用 NoSQL. Dynamo DB. because it is unlimited scaling


### 4.1.3 Amazon EC2 purchase options 

![](image/Pasted%20image%2020231002151810.png)


![](image/Pasted%20image%2020231002152041.png)

ec2 instance saving plans
- only use ec2instance
- only on a fix region 

compute saving plans
- any region 
- lambda , storage 都可用



![](image/Pasted%20image%2020231002152158.png)

![](image/Pasted%20image%2020231002152657.png)

instantaneous 
stingy  吝啬 

ec2 spot instance: 
- 谁出钱多, 就马上把你的instance 给抢了. 
用 Spot fleet 出价 : 
- m5 c3 i2 这几个 instance type  我的最高价是 xx. 



![](image/Pasted%20image%2020231002152733.png)



# 5 AWS Lambda

serverless computing 

![](image/Pasted%20image%2020231002152912.png)



![](image/Pasted%20image%2020231002153303.png)

lambda, take a image, create a small instance, then run function code. and then upload the result  to bucket 
怎么付钱 user change time cosuming and the momory that is has utizied. don charge the instance  

14.5s x 10G 就要付30欧元 

![](image/Pasted%20image%2020231002153631.png)

==if the cod eurns for up to 15 minutes. do not use the lambda . This case use ecs contains oder eks ==


![](image/Pasted%20image%2020231002153514.png)


![](image/Pasted%20image%2020231002153528.png)



# 6 Review 


# 7 Knowledge Check 

---
a 不对 , vpc 可以选择 


b d

![](image/Pasted%20image%2020231003080749.png)

---

a

![](image/Pasted%20image%2020231003081102.png)

---

![](image/Pasted%20image%2020231003081130.png)

cd

---



-----



# 8 Lab2 

![](image/Pasted%20image%2020231002153857.png)

Lab 2 uses a VPC across one Availability Zone with a public and private subnet. Each subnet contains a T3 EC2 instance. Separate security groups control the EC2 instances. You manage route tables separately for the public and private subnet. A NAT gateway in the public subnet receives traffic from the private subnet. An internet gateway receives traffic from the public subnet.
Review the diagram here, and then read the lab tasks on the following page

![](image/Pasted%20image%2020231002153943.png)


## 8.1 task 1 : testing connectivity to the private instance from the public instance 

加入一个 inbound rules for icmp, 因为 ping 用的是 ic,p protocol 

![](image/Pasted%20image%2020231002163107.png)


![](image/Pasted%20image%2020231002163224.png)


## 8.2 task 2: retrieving instance metadata 

![](image/Pasted%20image%2020231002163541.png)

![](image/Pasted%20image%2020231002163608.png)

```sh
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` \
&& curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/
```

得到 
```http
sh-5.2$ TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` \
&& curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    56  100    56    0     0  38808      0 --:--:-- --:--:-- --:--:-- 56000
* processing: http://169.254.169.254/latest/meta-data/
*   Trying 169.254.169.254:80...
* Connected to 169.254.169.254 (169.254.169.254) port 80
> GET /latest/meta-data/ HTTP/1.1
> Host: 169.254.169.254
> User-Agent: curl/8.2.1
> Accept: */*
> X-aws-ec2-metadata-token: AQAEAJHtU0Tt2q3W6G9KqKpejCXBm3KCiisAAXE_S8JNQyx4SA6uEw==
>
< HTTP/1.1 200 OK
< X-Aws-Ec2-Metadata-Token-Ttl-Seconds: 21600
< Content-Type: text/plain
< Accept-Ranges: none
< Last-Modified: Mon, 02 Oct 2023 14:05:18 GMT
< Content-Length: 312
< Date: Mon, 02 Oct 2023 14:32:45 GMT
< Server: EC2ws
< Connection: close
<
ami-id
ami-launch-index
ami-manifest-path
block-device-mapping/
events/
hostname
iam/
identity-credentials/
instance-action
instance-id
instance-life-cycle
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
reservation-id
security-groups
services/
* Closing connection
systemsh-5.2$
```


---

输入
```sh
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-hostname
```

```http
sh-5.2$ curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-hostname
* processing: http://169.254.169.254/latest/meta-data/public-hostname
*   Trying 169.254.169.254:80...
* Connected to 169.254.169.254 (169.254.169.254) port 80
> GET /latest/meta-data/public-hostname HTTP/1.1
> Host: 169.254.169.254
> User-Agent: curl/8.2.1
> Accept: */*
> X-aws-ec2-metadata-token: AQAEAJHtU0Tt2q3W6G9KqKpejCXBm3KCiisAAXE_S8JNQyx4SA6uEw==
>
< HTTP/1.1 200 OK
< X-Aws-Ec2-Metadata-Token-Ttl-Seconds: 21575
< Content-Type: text/plain
< Accept-Ranges: none
< Last-Modified: Mon, 02 Oct 2023 14:05:18 GMT
< Content-Length: 53
< Date: Mon, 02 Oct 2023 14:33:10 GMT
< Server: EC2ws
< Connection: close
<
* Closing connection
ec2-35-183-235-141.ca-central-1.compute.amazonaws.comsh-5.2$
```