

# 1 EC2 Overview (Elastic Compute Cloud )

- Elastic Compute Cloud (Ec2) allows you to launch Virtual Machines (VM)
    - EC2 is highly configuration server where you can choose AMI that affects options such as 
    - EC2 is considered the backbone of aws 
- AMI : Amazon machine Image: predefined configuration for a Virtual Machine
    - https://aws.amazon.com/ec2/instance-types/
- VM: 
    - an Emulation of a physical computer using software. 
    - Multiple VMs can run on the same physical serve 

![](image/Pasted%20image%2020230402090629.png)

# 2 VMs, Containers and Serverless

- VMs
    - Amazon Lightail: the managed virtual server service
- Container: virtualizing an Operation System (OS) to run multiple workloads on a single OS instance
    - Elastic Container Service (ECS)
    - Elastic Container Registry (ECR)
    - ECS Fargate 
    - Elastic Kubernetes Service (EKS) 
- Serverless : the underlying servers are managed by AWS. Don't worry or configure servers
    - AWS lambda

![](image/Pasted%20image%2020230402091011.png)

# 3 AWS Compute Service 例子

## 3.1 Elastic Container Service (ECS)


1  ECS Cluster 
使用 ECS . 就要创造一个新的 ECS cluster. 这中间连带着包含了创造 一个 新的 ECS instance , 一个新的 Cloudformation stack

![](image/Pasted%20image%2020230402093213.png)

![](image/Pasted%20image%2020230402093305.png)

2 EC2 Task 
![](image/Pasted%20image%2020230402093611.png)

![](image/Pasted%20image%2020230402093629.png)

2.1 add container

![](image/Pasted%20image%2020230402094346.png)

![](image/Pasted%20image%2020230402094704.png)

3 run the task 

![](image/Pasted%20image%2020230402095721.png)

![](image/Pasted%20image%2020230402095736.png)

![](image/Pasted%20image%2020230402095824.png)

4  deploy  一个之前已经建好的 ECS Cluster

![](image/Pasted%20image%2020230402094830.png)


6 删除一个 ecs cluster 

![](image/Pasted%20image%2020230402111751.png)

切换到 旧的 ecs version, 然后删除 cluster 
![](image/Pasted%20image%2020230402112017.png)

## 3.2 lambda
![](image/Pasted%20image%2020230402100031.png)

![](image/Pasted%20image%2020230402100100.png)

![](image/Pasted%20image%2020230402100113.png)

create a new test event
![](image/Pasted%20image%2020230402100221.png)

点击 test
![](image/Pasted%20image%2020230402100311.png)

![](image/Pasted%20image%2020230402100341.png)

 

# 4 High Performance Computing (HPC)


- The Nitro System
- Bar Metal Instance
    - Bottlerrocket
- HPC: A cluster of hundereds of thousands of servers with fast connections between each of then with the puperse of boosting computing capacity 
    - AWS ParallelCluster: An AWS-supported open source cluster management tool 

![](image/Pasted%20image%2020230402113142.png)

## 4.1 HPC 实际操作

https://docs.aws.amazon.com/parallelcluster/latest/ug/install.html
https://docs.aws.amazon.com/parallelcluster/latest/ug/what-is-aws-parallelcluster.html
https://docs.aws.amazon.com/parallelcluster/latest/ug/commands.html


1 install AWSParallelCluster 
https://docs.aws.amazon.com/parallelcluster/latest/ug/install.html

```
$ pip3 install "aws-parallelcluster<3.0" --upgrade --user
```

2 configure AWSParallelCluster
输入命令 pcluster configure 
![](image/Pasted%20image%2020230402123212.png)

有许多项需要你手动给入值
![](image/Pasted%20image%2020230402123703.png)


2.1 如何在ec2 中创建 key pair 

Ec2 中
![](image/Pasted%20image%2020230402123324.png)

![](image/Pasted%20image%2020230402123514.png)

3 然后在 cloudFormation 中能看到 产生的 stack (for parallelcluster)
![](image/Pasted%20image%2020230402123842.png)

这个stack 中创造了 三个 ressource 

![](image/Pasted%20image%2020230402124233.png)

4 pcluster create hello-world  

 ![](image/Pasted%20image%2020230402144336.png)


进入到 Cloudformation 中 查看新的 stack (for parallelcluster-hello-world)
![](image/Pasted%20image%2020230402144847.png)

Ec2 中也因此产生新的 instance for parallelcluster-hello-world

![](image/Pasted%20image%2020230402145002.png)


5 执行完pcluster create hello-world  , 会自动下载一个 pem key 在console 中 

![](image/Pasted%20image%2020230402145218.png)

upload 这个 .pem file 
![](image/Pasted%20image%2020230402145327.png)

这个file 在当前目录中 能显示出来了
![](image/Pasted%20image%2020230402145452.png)

6 chmod 400 myHPC.pem

![](image/Pasted%20image%2020230402145850.png)
![](image/Pasted%20image%2020230402145809.png)



7 plcuster ssh hello-world -i myHPC.pem
以此来进入 这个 instance 
![](image/Pasted%20image%2020230402145716.png)

![](image/Pasted%20image%2020230402145925.png)

8 Running your first job using SGE
![](image/Pasted%20image%2020230402150115.png)

8.1
vim hellhob.sh
![](image/Pasted%20image%2020230402150212.png)

8,2  sge install linux 
安装 sge 在 console, 这样就能使用 qsub 和  qstat 命令了 
需要自己查一下 怎么安装 这些东西 


9 pcluster delete hello-world

![](image/Pasted%20image%2020230402150756.png)

![](image/Pasted%20image%2020230402150815.png)



# 5 Edge computing and Hybrid computing

- Edge computing
    - when you push your computing workloads outside of your network to run close to the destination location
    - example: pushing computing to run on phones, lot devices, external servers not within your cloud network
- Hybrid Computing
    - your are able to run workloads on both your on-premise datacenter and aws virtual private Cloud (VPC)

- AWS Outputs
    - Physical rack of servers
- AWS Wavelength 
    - build and lauch you app in a telecom datacenter
    - your app have low latency by using 5G 
- VMWare Cloud on AWS 
    - manage on-premise virtual machines using VMWare as EC2 Instances 
- AWS Local Zones
    - edge datacenters located outside of an aws reguon
    - 就是说 edge datacenters 距离你的地方更近, 你的 app 想连接到 edge datacenters. edge datacenters 提供 aws 服务

![](image/Pasted%20image%2020230402202700.png)

## 5.1 Edge computing 实例1 : 对某个 local zones 开放 AWS Wavelength 功能

![](image/Pasted%20image%2020230402204306.png)


![](image/Pasted%20image%2020230402204330.png)

可以激活 local zones 

![](image/Pasted%20image%2020230402204515.png)

![](image/Pasted%20image%2020230402204712.png)


还要设置很多东西
![](image/Pasted%20image%2020230402204949.png) 

## 5.2 Edge computing 实例2 : CloudFormation 的 Function to deploy a edge function 

![](image/Pasted%20image%2020230402205438.png)

![](image/Pasted%20image%2020230402205515.png)

# 6 Cost & Capacity Management Computing Services 

可以用到的 aws service 去帮你实现 cost management 和 cpacity Management 

- EC2 Spot Instances, Reserved Instanced and Savings Plan
- AWS Batch
    - batch computing workloads
- AWS Compute Optimizer
    - reduce costs and improve performance 
- EC2 Autoscaling Groups (ASGs)
- Elastic load balancer (ELB)
- AWS Elastic beanstalk 




![](image/Pasted%20image%2020230402205858.png)







