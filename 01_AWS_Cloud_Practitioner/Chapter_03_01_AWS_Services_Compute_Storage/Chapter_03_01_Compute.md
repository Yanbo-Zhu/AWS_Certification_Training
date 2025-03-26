

# 1 EC2 Overview (Elastic Compute Cloud )

- Elastic Compute Cloud (Ec2) allows you to launch Virtual Machines (VM)
    - EC2 is highly configuration server where you can choose AMI that affects options such as 
    - EC2 is considered the backbone of aws 
- AMI : Amazon machine Image: predefined configuration for a Virtual Machine
    - https://aws.amazon.com/ec2/instance-types/
- VM: 
- A `Virtual Machine` (VM) is an emulation of a physical computer using software. ​
- Server Virtualization allows you to easily **create**, **copy**, **resize** or **migrate** your server.​
- Multiple `VMs` can run on the same physical server so you can share the cost with other customers.​
- Imagine if your server or computer was an executable file on your computer

`EC2` is considered the backbone of AWS because the majority of AWS services are using `EC2` as their underlying servers. eg. S3, RDS, DynamoDB, Lambdas
`EC2` is a highly configurable server where you can choose `AMI` that affects options such as:​
-   The amount of CPUs​
-   The amount of Memory (RAM)​
-   The amount of Network Bandwidth​
-   The Operation System (OS) eg. Windows 10, Ubuntu, Amazon Linux 2​
-   Attach multiple virtual hard-drives for storage eg. Elastic Block Store (EBS)​

![](image/Pasted%20image%2020230402090629.png)

# 2 VMs, Containers and Serverless

- VMs
    - Amazon LightSail - is the managed virtual server service. It is the “friendly” version of EC2 Virtual Machines
- Container: 
    - virtualizing an Operation System (OS) to run multiple workloads on a single OS instance. Containers are generally used in micro-service architecture (when you divide your application into smaller applications that talk to each other)
- Container 相关的AWS Services 
    - Elastic Container Service (ECS) - is a container orchestration service that support Docker containers. Launches a cluster of server(s) on EC2 instances with Docker installed. When you need Docker as a Service, or you need to run containers.​
    - Elastic Container Registry (ECR) - is repository for container images. In order to launch a containers you need an image.​ An image just means a saved copy. A repository just means a storage that has version control.​
    - ECS Fargate - is a serverless orchestration container service. It is the same as ECS expect you pay-on-demand per running container (With ECS you have to keep a EC2 server running even if you have no containers running) AWS manages the underlying server, so you don’t have to scale or upgrade the EC2 server.
    - Elastic Kubernetes Service (EKS) - is a fully managed Kubernetes service. Kubernetes (K8) is an open-source orchestration software that was created by Google and is generally the standard for managing microservices. When you need to run Kubernetes as a Service.​
- Serverless : 
    - the underlying servers are managed by AWS. Don't worry or configure servers
    - AWS Lambda is a serverless functions service. You can run code without provisioning or managing servers. You upload small pieces of code, choose much memory and how long function is allowed to run before timing out. You a charged based on the runtime of the serverless function rounded to the nearest 100ms.​

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
    - A combination of dedicated hardware and lightweight hypervisor enabling faster innovation and enhanced security. All new EC2 instance types use the Nitro System.​
    -   **Nitro Cards** — specialized cards for VPC, EBS and Instance Storage and controller card​
    -   **Nitro Security Chips** — Integrated into motherboard. Protects hardware resources.​
    -   **Nitro Hypervisor** — lightweight hypervisor Memory and CPU allocation Bare Metal-like performance​
- Bar Metal Instance
    - Bottlerrocket
    - You can launch EC2 instance that have no hypervisor so you can run workloads directly​
    - on the hardware for maximum performance and control. The M5 and R5 EC2 instances run are bare metal.​
        - **Bottlerocket** is a Linux-based open-source operation system that is purpose-built by AWS for running containers on Virtual Machines or bare metal hosts
- HPC: 
    - A cluster of hundreds of thousands of servers with fast connections between each of them with the purpose of boosting computing capacity. When you need a supercomputer to perform computational problems to large to fix on a standard computers or would take to long.
    - AWS ParallelCluster is an AWS-supported open source cluster management tool that makes it easy for you to deploy and manage High Performance Computing (HPC) clusters on AWS.


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
    -  is physical rack of servers that you can put in your data center. AWS Outposts allows you to use AWS API and Services such as EC2 right in your datacenter.
- AWS Wavelength 
    - build and lauch you app in a telecom datacenter
    - your app have low latency by using 5G 
    - AWS Wavelength allows you to build and launch your applications in a telecom datacenter. By doing this your applications with have ultra-low latency since they will be pushed over a the 5G network and be closest as possible to the end user.
- VMWare Cloud on AWS 
    - manage on-premise virtual machines using VMWare as EC2 Instances 
    - allows you to manage on-premise virtual machines using VMWare as EC2 instances.​ The data-center must being using VMWare for Virtualization.
- AWS Local Zones
    - edge datacenters located outside of an aws region
    - are edge datacenters located outside of an AWS region so you can use AWS closer to end destination.​ When you need faster computing, storage and databases in populated areas that are outside of an AWS Region​
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

# 6 Cost & Capacity Management  

可以用到的 aws service 去帮你实现 cost management 和 cpacity Management 

EC2 Spot Instances, Reserved Instanced and Savings Plan​ - Ways to save on computing, by paying up in full or partially, by committing to a yearly contracts or by being flexible about availability and interruption to computing service.

AWS Batch - plans, schedules, and executes your batch computing workloads across the full range of AWS compute services, can utilize Spot Instance to save money.​

AWS Compute Optimizer - Suggests how to reduce costs and improve performance by using machine learning to analyze you previous usage history

EC2 Autoscaling Groups (ASGs)​ - Automatically adds or remove EC2 servers to meet the current demand of traffic. Will save you money and meet capacity since you only run the amount of servers you need.​

Elastic Load Balancer (ELB)​ - Distributes traffic to multiple instance, can re-route traffic from unhealthy instance to healthy instances.​ Can route traffic to EC2 instances running in different Availability Zones ​

Elastic Beanstalk (EB) - is for easily deploying web-applications without developers having to worry about setting up and understanding the underlying AWS Services. Similar to Heroku. ​


![](image/Pasted%20image%2020230402205858.png)







