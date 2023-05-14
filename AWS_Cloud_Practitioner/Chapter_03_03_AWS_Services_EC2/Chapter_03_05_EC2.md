

# 1 Introduction to EC2
6:57:27 Introduction to EC2

Elastic Compute Cloud (EC2) is a highly configurable virtual server.
EC2 is a resizable compute capacity. It takes minutes to launch new instances.
Anything and everything on AWS uses EC2 Instance underneath.

![](image/Pasted%20image%2020230513205253.png)

Choose OS via Amazon Machine Image (AMI)
- Red Hat
- ubuntu
- Microsoft Windows
- Amazon Linux
- Suse

Choose Instance Type
- t2.nano
    - $0.0065/hour ($4.75/month)
    - 1 vCPU 
    - 0.5GB Mem
- C4.8xlarge
    - $1.591/hour ($1161.43/month)
    - 36 vCPU 60GB Mem 
    - 10 Gigabit performance

Add Storage (EBS, EFS)
- SSD, HDD, Virtual Magnetic Tape, Multiple Volumes

Configure Instance
- Security Groups, Key Pairs, UserData, IAM Roles, Placement Groups

# 2 EC2 Instance Families

6:59:00 EC2 Instance Families


[Amazon EC2 Instance Types](https://aws.amazon.com/ec2/instance-types/#:%7E:text=Instance%20types%20comprise%20varying%20combinations,of%20resources%20for%20your%20applications.)

**What are Instance Families?**

Instance families are different combinations of CPU, Memory, Storage and Networking capacity.
Instance families allow you to choose the appropriate combination of capacity to meet your application’s unique requirements.
Different instance families are different because of the varying hardware used to give them their unique properties.
Commonly instance families are called “Instance Types” but an instance type is a combination of size and family.


**General Purpose**
A1 T2 T3 T3a T4g M4 M5 M5a M5n M6zn M6g M6i Mac  
balance of compute, memory and networking resources  
**Use-cases** web servers and code repositories

**Compute Optimized**
C5 C4 Cba C5n C6g C6gn
Ideal for compute-bound applications that benefit from high-performance processor  
**Use-cases** scientific modeling, dedicated gaming servers, and ad server engines

**Memory Optimized**
R4 R5 R5a R5b R5n X1 X1e High Memory z1d
fast performance for workloads that process large data sets in memory.  
**Use-cases** in-memory caches, in-memory databases, real time big data analytics

**Accelerated Optimized**
P2 P3 P4 G3 G4ad G4dn F1 Inf1 VT1  
hardware accelerators, or co-processors
**Use-cases** Machine learning, computational finance, seismic analysis, speech recognition

**Storage Optimized**
I3 I3en D2 D3 D3en H1
high, sequential read and write access to very large data sets on local storage
**Use-cases** NoSQL, in-memory or transactional databases, data warehousing


# 3 EC2 Instance Types
7:01:43 EC2 Instance Types
Commonly instance families are called “Instance Types” but an instance type is a combination of size and family.
Instance types 指的是 instance size 和 instance family 的结合 
An instance type is a particular instance size and instance family:

## 3.1 EC2 Instance sizes
A common pattern for instance sizes:

    nano
    micro
    small
    medium
    large
    xlarge
    2xlarge
    4xlarge
    8xlarge
    ….

There are many exceptions to this pattern for sizes e.g.
    c6g.metal – is a bare metal machine.
    C5.9xlarge – Is not a power of 2 or even number size

## 3.2 EC2 Instance Type 

EC2 Instance Sizes generally double in price and key attributes
Name 	vCPU 	RAM (GIB) 	On-Demand per hour 	On-Demand per month
t2.small 	1 	12 	$0.023 	$16.79
t2.medium 	2 	24 	$0.0464 	$33.87
t2.large 	2 	36 	$0.0928 	$67.74
t2.xlarge 	4 	54 	$0.1856 	$135.48

# 4 Dedicated Host vs Dedicated Instances

7:03:29 Dedicated Host vs Dedicated Instances

这两个 都存在 在 aws 服务中
Dedicated Host 这什么时候 使用: let you bring-your-own-license based on the machine characteristics 

![](image/Pasted%20image%2020230513210345.png)

# 5 EC2 Tenancy

EC2 has three levels of tenancy:
- Dedicated host: Your server lives here and you have control of the physical attributes
- Dedicated Instance: Your server always lives here
- Default: Your instance lives here until reboot

![](image/Pasted%20image%2020230513210842.png)

![](image/Pasted%20image%2020230513211705.png)

# 6 实际操作 Launch an EC2, SSH and Sessions Manager  
7:06:17 Launch an EC2, SSH and Sessions Manager

## 6.1 生成一个新的 EC2

![](image/Pasted%20image%2020230513211421.png)

![](image/Pasted%20image%2020230513211839.png)

![](image/Pasted%20image%2020230513212001.png)

keypair
![](image/Pasted%20image%2020230513212044.png)

## 6.2 在 cloudshell 中 用ssh 连上这个新的 ec instance 

先要upload 之前生成的 key pair  (.pem)

![](image/Pasted%20image%2020230513212927.png)

![](image/Pasted%20image%2020230513212941.png)

![](image/Pasted%20image%2020230513213113.png)

![](image/Pasted%20image%2020230513213653.png)

## 6.3 使用 session manager

![](image/Pasted%20image%2020230513214250.png)
 
# 7 实际操作: 设置 Elastic IP
7:26:33 Elastic IP

ec2 instance 每次 reboot 后, public ipv4 addresse 地址都会改变 . 
但是我们想要 ip addresse 是固定的

![](image/Pasted%20image%2020230513214545.png)

![](image/Pasted%20image%2020230513214905.png)


# 8 实际操作:  AMI and Launch Template

7:29:30 AMI and Launch Template

用一个存在的 instance 生成 AMI 
用 生成好的 AMI  去 创造一个 Launch Template
![](image/Pasted%20image%2020230513220305.png)


再用 这个  Launch Template 去 创造一个新的 ec2 instance 
![](image/Pasted%20image%2020230513220345.png)

7:35:45 Launch an ASG
7:40:08 Launch an ALB
7:46:41 Cleanup