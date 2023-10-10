
![](image/Pasted%20image%2020231002124015.png)


![](image/Pasted%20image%2020231002124100.png)


![](image/Pasted%20image%2020231002124142.png)

IP address: Internet Protocol reachability between the endpoints or host and services

# 1 IP address


![](image/Pasted%20image%2020231002124415.png)

![](image/Pasted%20image%2020231002124437.png)

ip addresse
- network part:  buildung number
- host part: room number 


![](image/Pasted%20image%2020231002125016.png)

So 16 means the leftmost 16 bits  network locations. This is the network and if you want to allocate hosts

/16  : subnet mask,   这包含的 ip addresse 都是 被分配的 subnet 中的 地址 

==vpc 的要求 subnet mask 的位数 在 28 到 16 之间  ==


# 2 VPC virtual private cloud

![](image/Pasted%20image%2020231002125625.png)


## 2.1 Amazon VPC 
data center is a building which hosts servers 

![](image/Pasted%20image%2020231002125735.png)

VPC Can have submits or segments of the CIDR block. 
Vpc can cross server AZs

![](image/Pasted%20image%2020231002154237.png)

## 2.2 Subnet 

![](image/Pasted%20image%2020231002130525.png)


4 distinct subnets forma main block 

private subnets means that it is not accessible from Internet 
subnet reisdes within one avaialbility zone 


==in each subnet, the first 4 ip adrresse and the last  ip addesse is reserved ==
The first four IP addresses and the last IP address in each subnet CIDR block are not available for your use, and they cannot be assigned to a resource, such as an EC2 instance. For example, in a subnet with CIDR block `10.0.0.0/24`, the following five IP addresses are reserved:

- 10.0.0.0: Network address.
    
- 10.0.0.1: Reserved by AWS for the VPC router.
    
- 10.0.0.2: Reserved by AWS. The IP address of the DNS server is the base of the VPC network range plus two. For VPCs with multiple CIDR blocks, the IP address of the DNS server is located in the primary CIDR. We also reserve the base of each subnet range plus two for all CIDR blocks in the VPC. For more information, see [Amazon DNS server](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-dns.html#AmazonDNS).
    
- 10.0.0.3: Reserved by AWS for future use.
    
- 10.0.0.255: Network broadcast address. We do not support broadcast in a VPC, therefore we reserve this address.


### 2.2.1 Public Subnets

each public subnets hat Internet gateway and Route table 

![](image/Pasted%20image%2020231002131132.png)

Route table 中保存有 
- default gate way 0.0.0.0/0 :  指向 igw , internet gateway 
    - 0.0.0.0/0 代表, 任何在 route table 中 没有明确指出的其他的地址 
    - ![](image/Pasted%20image%2020231002131412.png)


### 2.2.2 Internet gateways 

![](image/Pasted%20image%2020231002131831.png)

NAT: network access translation , 将 ec2 instance 的 priavte ip 翻译 成 public ip, 再暴露给外面. 或者反之, 在暴露给vpv 内部
Inter gatewart 起到保护的作用 

Intergate 

### 2.2.3 route tables 
public subnet 和 private subnet 有不同的 toot table, 因为  public 的 root table 又 0.0.0.0/0 从而指向外部 
local:  all the taget within vpc  , they all talk to reach , and nobody can change it . 

![](image/Pasted%20image%2020231002132609.png)


### 2.2.4 Private subnet

private table can not ceass website directly 

![](image/Pasted%20image%2020231002132721.png)


### 2.2.5 Default Amzons vpcs 

only habe public subnets, will have a internet gateways in default 


![](image/Pasted%20image%2020231002132821.png)


once the ec2 instance is stopped, the public ip of it will be deleted . once created again, the public ip 

![](image/Pasted%20image%2020231002132946.png)


Elastic ip address: one the ex2 instance . this Elastic ip address will allocate to another instance 

![](image/Pasted%20image%2020231002133115.png)

### 2.2.6 Elastic network interface 

需要重听 

![](image/Pasted%20image%2020231002133223.png)

eni: Elastic network interface  


### 2.2.7 NAT  gateways 

NAT gateways is not in priavte sunet: beacuas in priavte sunenet ist not accessible to Intenet 



![](image/Pasted%20image%2020231002133327.png)

elastic ip 就是 public ip , exposed to 外部的访问的 

在 priavte subnet 中 route table 中加入 下面的 entry, 指向 nat gateway 
![](image/Pasted%20image%2020231002133730.png)

![](image/Pasted%20image%2020231002133851.png)

### 2.2.8 

![](image/Pasted%20image%2020231002133925.png)

## 2.3 VPC Traffic security 

### 2.3.1 ACLs

ACL ist effective on subnet level , not on instance level 

![](image/Pasted%20image%2020231002134410.png)

一旦 最小的 rule number 的 rule 适用了, 就不在检查更大的 rule number 的 rule 了 
星号的 放在最晚的检查
inbound 进入的 request
outbound, 从自己方发出的 request 

### 2.3.2 security groups 
secourtiy groups ist funtional at instance level, not subnet level 
在security groups  之前, acl 会先被 evalated 

![](image/Pasted%20image%2020231002134738.png)

stateful rules 
the response to the same traffic is allowed even if there are no rules to allow. 
so the statefulness means if 
 - inbound : I'm allowed in One Direction, the response to the same traffic will come and get into the sender and it's security group without any problem .
     - 比如说 下面 这个 app security group 发出 一个 outbound request ,  对于 data security group 是 inbound request . 当这个 reponse 返回到 app security group 的时候. , app security group 的 inbound rules 是自动允许这个 request 返回来的. 
     - 对于 data security group 是 inbound request . 当这个 reponse 跑出 data security group 的时候. , data security group 的 outbound rules 是允许这个 reponse 跑出去的. 
     - ![](image/Pasted%20image%2020231002140637.png)
     - http 的 request 可以进来, 出去. 但是 当 内部发出一个 向外部的https 的 reques, 是不允许出去的, 因为 没有一个 https 的 rules先被定义好 
         - ![](image/Pasted%20image%2020231002141047.png)
 - outbound direction :  I'm allowed in One Direction (从 instance 发射出去 ), the response to the same traffic will come with   problem probably 
 - ![](image/Pasted%20image%2020231002135502.png)





中间 那个

----



![](image/Pasted%20image%2020231002135409.png)

anything inbound to the instance by default is definied, unless anything inbound to the instance by default will only be allowed if it is coming from another instance in the  same security group .

But  security group allow all outbound traffic by default 


![](image/Pasted%20image%2020231002135733.png)

![](image/Pasted%20image%2020231002140128.png)

Security group blue  and Security group  red 

outbound 被允许了, 还要看 destination instance 他的 securtiy group 的 inbound policy 


![](image/Pasted%20image%2020231002140236.png)

allow alle httos request firn siyrce "web secturiy group "


![](image/Pasted%20image%2020231002140516.png)


### 2.3.3 

![](image/Pasted%20image%2020231002140658.png)


### 2.3.4 com


![](image/Pasted%20image%2020231002140710.png)

-----






某个 inbound request 被 他的 securty


# 3 Review 

![](image/Pasted%20image%2020231002141304.png)


you can only have permit rules in the security groups
ACLs ist stateless rule, can man have to give inbound rules ad outbounds explicityly 



![](image/Pasted%20image%2020231002141358.png)


![](image/Pasted%20image%2020231002141418.png)


# 4 #

b
![](image/Pasted%20image%2020231002141453.png)



----

a ist worung 
c ist right 

![](image/Pasted%20image%2020231002141506.png)



--- 

c

![](image/Pasted%20image%2020231002141612.png)

在一个 subnet 中 instances 项目相互之间交流,  默认都行, 不需要任何 nat gateway , 不要任何 gateway 


![](image/Pasted%20image%2020231002141854.png)

-----

d 
d ist based on subnet level 
![](image/Pasted%20image%2020231002141904.png)



---------

ad

![](image/Pasted%20image%2020231002141935.png)




-----





