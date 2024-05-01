
![](image/Pasted%20image%2020231002143219.png)

![](image/Pasted%20image%2020231002143318.png)


# 1 Business requests 

![](image/Pasted%20image%2020231002143328.png)

Imagine that your compute operations manager contacted you with questions about moving and building their workloads on Amazon Web Services (AWS). Here are some questions that they are asking.
At the end of this module, you meet with the compute operations manager and present some solutions.


# 2 Compute service 

The compute operations manager asks, “What AWS compute services are available?”

![](image/Pasted%20image%2020231002143804.png)

Virtual machines (VMs) provide the following benefits: 
• Hardware independence
• Faster provisioning speed, in minutes or hours 
• Pay-as-you-go pricing models instead of hardware purchases 
• More scale 
• Elastic resources 
• Greater agility 
• Reduced maintenance 

Amazon EC2 was one of the first AWS services released in 2006, and it continues to be a central component of cloud computing. New generations of EC2 instance types introduce greater compute efficiency that can help reduce compute costs.

Containerization provides the following benefits: 
• Platform independence
• A consistent runtime environment 
• Higher resource use 
• Easier and faster deployments 
• Isolation and sandboxing 
• Quicker start speed, so you can deploy in seconds

In 2014, Amazon Elastic Container Service (Amazon ECS) introduced the ability to run distributed applications on a managed cluster EC2 instances with Docker containers. Support for Kubernetes was released in 2017 with Amazon Elastic Kubernetes Service (Amazon EKS).

Serverless computing provides the following: 
• Continuous scaling 
• Built-in fault tolerance 
• Pay for value
• Zero maintenance


AWS Lambda also appeared in 2014, introducing serverless computing. With Lambda, you can run code without provisioning or managing EC2 instances. Serverless computing and containerization were combined in 2017 with the release of AWS Fargate. AWS Fargate is a serverless compute engine for containers that works with Amazon ECS and Amazon EKS.
AWS introduced specialized processors to support the implementation of artificial intelligence (AI) and machine learning (ML). AWS Inferentia chips were introduced in 2019 to provide high-performance machine learning inference chips, which AWS designed and built. These chips were created to support machine learning inference applications. AWS Trainiumwas introduced in 2021 as the second machine learning chip that AWS built. Trainium is optimized for high-performance deep learning training.
AWS has also custom-built processors and introduced a variety of AWS Graviton processors. Graviton processors are built around Arm cores and make extensive use of silicon. In 2018, AWS Graviton was released and built for scale-out workloads where you can share the load across a group of smaller instances. In 2020, AWS Graviton2 was released. It uses 64-bit Arm Neoverse cores to provide the best price performance for cloud workloads that run in Amazon EC2. In 2022, AWS Graviton3 was released to provide the best price performance for workloads in Amazon EC2.


![](image/Pasted%20image%2020231002143439.png)

# 3 EC2 instance 

The compute operations manager asks, “What should the team consider when deploying new and existing servers to Amazon EC2?”
The team needs information about EC2 instances. They need you to tell them what is required at launch and which advanced settings they should explore.

![](image/Pasted%20image%2020231002143501.png)

Amazon EC2 is the service that you use to create and run virtual machines. Your virtual machines in the AWS Cloud are called EC2 instances. Amazon EC2 is just like your traditional on-premises server, but it is available in the cloud. It can support workloads such as web hosting, applications, databases, authentication services, and anything else that a server can support.
On AWS, servers, databases, storage, and higher-level application components can be instantiated within seconds. You can treat these resources as temporary and disposable, free from the constraints of a fixed IT infrastructure. Elastic cloud computing redefines the way that you approach change management, testing, reliability, and capacity planning.


Virtualization: 
EC2 instance is a virtual machine on a physical host in AWS


![](image/Pasted%20image%2020231002143822.png)

You must consider many options before you start working with EC2 instances
Consider the following options: 
• Name and tags – How should your instance be identified? 
• Application and operating system (OS) image – What will you start running? 
• Instance type and size – What technical requirements do you have? 
• Authentication and key pair – How do you plan to connect to the instance? 
• Network settings and security – What virtual private cloud (VPC), subnet, and security groups will you use? 
• Configure storage – What type of block storage is best for your use case? 
• Placement and tenancy – Where should you run your EC2 instances? 
• Scripts and metadata – What can you do to automate your launch

---

![](image/Pasted%20image%2020231002143923.png)

On AWS, you can assign metadata to your resources in the form of tags. Each tag is a simple label that consists of a customer-defined key and an optional value. Use tags to filter resources. Tags can manage resource access control, track costs, help automate tasks, and keep you organized.

Although no tag types are required, you can create tags to categorize resources by purpose, owner, environment, or other criteria.

In the example, each instance has a tag with key “Owner” and values of “Dev1,” “Dev2,” or “Dev3.” An AWS Command Line Interface (AWS CLI) command is sent from a terminal. This CLI command will stop all EC2 instances in a Region that have a key-value pair of Owner:Dev2. Remember that your tags are case-sensitive. Your workflows that involve tag key-value pairs need an exact string match to work properly.

For more information about AWS tagging strategies, see “Tagging AWS resources” in the AWS General Reference at https://docs.aws.amazon.com/general/latest/gr/aws_tagging.htm

## 3.1 AMI Amazon Machine Image

![](image/Pasted%20image%2020231002144004.png)

An AMI provides the information that is required to launch an instance, which is a virtual server in the cloud. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations. Specify a source AMI when you launch an instance.

An AMI includes the following attributes: 
• A template for the root volume for the instance (for example, an OS, an application server, and applications) 
• Launch permissions that control which AWS accounts can use the AMI to launch instances • Block device mapping that specifies the volumes to attach to the instance when it's launched


---

![](image/Pasted%20image%2020231002144219.png)

You can use AMIs that AWS provides, or create your own custom AMIs.
You can buy or sell AMIs through the following sources: 
• AWS user community
• AWS Marketplace

Alternatively, you can select one of your own custom AMIs and share with other AWS accounts. Some organizations create custom AMIs to speed up deployment based on internal requirements. Tools that are used in customization include Chef, Puppet, and cloud-init.

To create a custom AMI, launch an instance and customize it to meet your requirements. Then, save that configuration as a custom AMI. Instances that are launched from this custom AMI will use all of your customizations. These custom AMIs can also be published for internal, private, or external public use. As a publisher of an AMI, you are responsible for the initial security posture of the machine images that you use in production.

For more information about AMIs, see “Amazon Machine Images (AMI)” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html.



![](image/Pasted%20image%2020231002144319.png)

You can choose from more than 400 types of EC2 instances to run applications that you move to the cloud. Each instance type comes in different sizes, with different allotments of virtual CPUs (vCPUs), and memory. Choosing the right instance sizes is critical to using them efficiently. An instance's full type consists of its family name, followed by the generation number, any additional properties, and then the size.
In the example, explore the following pieces of the instance type name:
• c – The first letter is the instance family. For example, the c family is compute optimized. A few types of instances are general purpose EC2 instances, burstable instances, and compute-intensive and memory-intensive instances.
• 6 –The next number is the generation, which gradually increases as AWS upgrades hardware in its data centers.
• g – Sometimes one or more letters appear after the generation. The letters represent additional properties. In this example, the g stands for Graviton2, an ARM-based processor that AWS developed. Choose properties based on your needs, like optimized networking throughput or storage.
• xlarge – The last part represents the size of the instance, which includes the CPU, memory, storage, and network performance.
This instance type is read as a c-type instance from the sixth generation, with a Graviton2 processor and an extra-large size deployment.


g ist gravition.   That's a specific hardware or CPU that integrates is used



![](image/Pasted%20image%2020231002144433.png)

Pick the optimal instance family for the type of workload that you plan to deploy. This step saves time and cost, and reduces the need to resize later. Some instance types are only available in certain Regions.
General purpose 
• Balance of compute, memory, and networking 
• Diverse workloads 
• Web applications

Compute optimized 
• Compute-bound applications 
• High-performance processors 
• Media transcoding
• Scientific modeling 
• Machine learning

Memory optimized 
• Fast delivery of large data sets in memory 
• Database servers 
• Web caches
• Data analytics

Accelerated computing
• High-graphics processing 
• Graphics processing unit (GPU) bound 
• Machine learning 
• High performance computing (HPC)
• Autonomous vehicles

Storage optimized 
• High sequential read/write 
• Large data sets 
• NoSQL databases
• Amazon OpenSearch Service

The instance types that are listed here are only a subset of what you can choose from in Amazon EC2. For more information about instance types, see “Amazon EC2 Instance Types” at https://aws.amazon.com/ec2/instance-types/.

the new generation in the same family 价格越便宜 
Next-generation EC2 instances generally increase compute capabilities and reduce processing costs that are associated with running the instance. Use the latest generation of instances to get the best performance while saving on compute costs
![](image/Pasted%20image%2020231002144611.png)

## 3.2 AWS Compute Optimizer

![](image/Pasted%20image%2020231002144651.png)

Select optimal instances for Amazon EC2 and Amazon EC2 Auto Scaling groups from more than 140 instances from the M, C, R, T, and X families.
Get started – Opt in to AWS Compute Optimizer for your individual accounts, management accounts, or all member accounts in your organization. Compute Optimizer uses machine learning (ML) to analyze the current configuration of your resources and your usage data from Amazon CloudWatch. You receive compute recommendations based on your configuration and usage.

Cross-service integration – Recommendations can be exported to Amazon Simple Storage Service (Amazon S3), where they are integrated with AWS Cost Explorer and AWS Systems Manager.

Reconfigure resources – Use the recommendations to reconfigure your resources for cost reduction and improved performance.

## 3.3 Amazon EC2 key pairs 

![](image/Pasted%20image%2020231002144745.png)

A key pair, which consists of a private key and a public key, is a set of security credentials. You use a key pair to prove your identity when connecting to an instance. Amazon EC2 stores the public key and you store the private key. You use the private key instead of a password to securely access your instances. Anyone who possesses your private keys can connect to your instances, so it's important that you store your private keys in a secure place.


## 3.4 Tenancy 
https://stackoverflow.com/questions/64309679/aws-dedicated-host-vs-dedicated-instance-why-the-first-is-more-expensive-than

租期；租用

![](image/Pasted%20image%2020231002144917.png)


Shared tenancy (by default ): 
By default, EC2 instances have shared tenancy, which means that multiple AWS accounts might share the same physical hardware.
- 只占用  physical host 某个instance.  你在用的时候，  别人可以使用同个 host 的其他的 instance 

---

dedicated instance:  
Dedicated Instances are EC2 instances that are physically isolated at the host hardware level. They are isolated from instances that aren't dedicated and from instances that belong to other AWS accounts.
- 当你 使用的时候 physical host 全部占用 . **Its not lockdown to you**, when you use it.  the hardware is "yours" (you are not sharing it with others) for the time your instance is running.
- 空出来的时候, 别人也是用得了.
- 当你下次再运行 会在不同的个 physical hardware 上面运行 。 you can get some other hardware somewhere else.  You stop/start it, you may get different physical machine later on (maybe older, maybe newer, maybe its specs will be a bit different)， whichever is not occupied by others at the time.**

"Dedicated Instances are Amazon EC2 instances that run in a virtual private cloud (VPC) on hardware that's dedicated to a single customer... Dedicated Instances may share hardware with other instances from the same AWS account that are not Dedicated Instances."

This means that **no other AWS Account will run an instance on the same Host**, but other instances (both dedicated and non-dedicated) from the same AWS Account might run on the same Host.

**Billing is per-instance**, with a cost approximately 10% more than the normal instance charge (but no extra charge if it is the largest instance in the family, since it requires the whole host anyway).

--- 

Dedicated host :  
When you launch instances on a Dedicated Host, the instances run on a physical server with EC2 instance capacity fully dedicated to your use. You are provided an isolated server with configurations that you can control. With Dedicated Hosts, you have the option to have AWS automatically select a server to place your instance. Or you can manually select a dedicated server to place your instance.
- 当你 使用的时候 ， physical host 全部占用 
- 空出来 别人也是用不了。 Will not share the physical hosts, when the hosts are not used
- 一直会在同一个 physical hardware 上运行。With Dedicated Host the physical server is basically yours. It does not change, **it's always the same physical machine for as long as you are paying**

As soon as you 'allocate' a Dedicated Host, **you start paying for that whole host**.

A host computer is very big. In fact, it is the size of the largest instance of the selected family, but can be divided-up into smaller instances of the same family. ("You can run any number of instances up to the core capacity associated with the host.")

Any instances that run on that Host are not charged, since you are already being billed for the Host.

That is why a Dedicated Host is more expensive than a Dedicated Instance -- the charge is for the _whole host_.


Thus, you can deploy instances by using configurations to address corporate compliance and regulatory requirements. With Dedicated Hosts, you can use your existing per-socket, per-core, or per-VM software licenses. These software licenses are bound to VMs, sockets, or physical cores, subject to your license terms, and include, among others:
• Microsoft Windows Server 
• Microsoft SQL Server 
• SUSE Linux Enterprise Server 
• Red Hat Enterprise Linux

For more information about Dedicated Hosts, see “Amazon EC2 Dedicated Hosts” at https://aws.amazon.com/ec2/dedicated-hosts/.


## 3.5 # Instance Purchasing Options： On-Demand， Reserved， Spot


On-demand instances: 完全属于你， 用的时候不会丢失 ， 不用提前预定 
A Reserved Instance： 要提前签合同预定， long-term use 1-3 年的合同 
A spot instance： 别人不用的机器 你才会用， 并且可能 随时被掠夺走。

On-Demand Instances and Reserved Instances offer different pricing models so that organizations can choose the most appropriate configuration based on their organizational consumption and needs. Configurations of EC2 instances are available with both Reserved and On-Demand pricing.
On-demand computing instances are computing instances that are available when needed. On-demand instances are charged by either the second or hour of use, and facilitate autoscaling.

---

A Reserved Instance requires a lock-in contract to reserve a full instance for a given time period of either one or three years. On-Demand Instances are billed in hours and seconds and require no lock-in period—they can be turned on or off at will. Compare this This is to renting a car park in the city for a year or on a daily rate. If you work full-time in the city, the yearly rate would be more cost-effective. If you work partly remote, the daily rate may make more sense.
A reserved instance is an instance where an organization commits to purchase a specified compute capacity for a specified period of time. It is essentially a contract to purchase a computing instance and can be for one to three years. By purchasing instances based upon long-term use, the organization can receive substantial savings over on-demand pricing. 

---

A spot instance is an instance that is pulled from unused AWS capacity. Spot instances are sold in an auction-like manner in which an organization places a bid.

---


可以和 组合为 

Dedicated Reserved Hosts
Dedicated On-Demand Hosts
Dedicated Reserved Instances
Dedicated On-Demand Host

## 3.6 Reserved or dedicated capacity

1 On-Demand Capacity Reservations 
On-Demand Capacity Reservations enable you to reserve compute capacity for your EC2 instances in a specific Availability Zone for any duration. Capacity reservations mitigate against the risk of being unable to get On-Demand capacity in case of capacity constraints and ensure that you always have access to EC2 capacity when you need it, for as long as you need it.

On-Demand Capacity Reservations are recommended for:
- Business-critical events or workloads that require capacity assurance
- Workloads that need to meet regulatory requirements for high availability
- Disaster recovery


2 Amazon EC2 Capacity Blocks for ML
With Amazon EC2 Capacity Blocks for ML, you can easily reserve GPU instances for a future date to run your machine learning (ML) workloads. You pay only for the amount of compute time that you need, with no long-term commitment. EC2 Capacity Blocks can be used to reserve Amazon EC2 P5 instances.

EC2 Capacity Blocks are recommended for:  
- Training and fine-tuning ML models
- Running experiments and building prototypes
- Planning for future surges in demand for ML applications


3 Dedicated Host
A Dedicated Host is a physical EC2 server fully dedicated for your use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses, including Windows Server, SQL Server, and SUSE Linux Enterprise Server (subject to your license terms). Dedicated Hosts can be purchased On-Demand (hourly) or can be purchased as part of Savings Plans.  

Dedicated Hosts are recommended for:
- Users looking to save money on licensing costs
- Workloads that need to run on dedicated physical servers
- Users looking to offload host maintenance onto AWS, while controlling their maintenance event schedules to suit their business’s operational needs

## 3.7 Placement groups and use cases 

![](image/Pasted%20image%2020231002145208.png)

The Amazon EC2 service attempts to spread out all of your instances across underlying hardware to minimize correlated failures. You can use placement groups to influence the placement of a set of interdependent instances to meet the needs of your workload.
Cluster placement groups are recommended for your applications that benefit from low network latency, high network throughput, or both. They are also recommended when the majority of the network traffic is between the instances in your group. HPC workloads can require this level of connectivity in your VPC.
Spread placement groups are recommended for applications that have a small number of critical instances that should be kept separate from each other. Services that require maximum uptime, such as a medical health record system, are more fault-tolerant in a spread.
Partition placement groups can be used to deploy your large distributed and replicated workloads. You can use partitions to avoid same-time hardware failures for multiple components.
You can find examples of different types of placement groups in the documentation. For more information, see “Placement groups” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.htm


![](image/Pasted%20image%2020231002145743.png)

When creating your EC2 instances, you have the option of passing user data to the instance. User data can automate the completion of the instance launch. For example, it might patch and update the instance AMI, fetch and install software license keys, or install additional software. User data is implemented as a shell script or cloud-init directive that runs with root or administrator privilege. It runs after the instance launches but before it becomes accessible on the network.
• Run by cloud-init on Linux. • Run by EC2Launch service on Windows.
You can specify both a batch script and a Windows PowerShell script. Then, the batch script runs first and the Windows PowerShell script runs next, regardless of the order that they appear in the instance user data


![](image/Pasted%20image%2020231002145923.png)

Instance metadata is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into categories, for example, host name, events, and security groups.
The diagram contains a user data script on an Amazon Linux 2 instance that runs at first launch. During instance launch, the EC2 instance requests a session token. It uses that token to request the public hostname of the EC2 instance at the following endpoint: http://169.254.169.254/latest/meta-data/public-hostname.
The instance metadata is then passed as the hostname in the operating system.


# 4 Storage for EC2 instances 

![](image/Pasted%20image%2020231002150106.png)

The compute operations manager asks, “How do we know which volume type to attach to our EC2 instances?”

### 4.1.1 Amazon Elastic Block Store (Amazon EBS) 

![](image/Pasted%20image%2020231002150116.png)

![](image/Pasted%20image%2020231002150407.png)

block based storage : Storing the files and something like that in in blocks instead of making changes and so on is suitable for this kind of storage
Block storage is technology that controls data storage and storage devices. It takes any data, like a file or database entry, and divides it into blocks of equal sizes. The block storage system then stores the data block on underlying physical storage in a manner that is optimized for fast access and retrieval


primary : root volumes. ebs backed 

ebs voLumes and instance have to be in the same the AZ 

connection and kommunication between instanc and ebs volumens : via iops 
I can detach a ebs olumen and re tach it to another instance

Amazon EBS volumes provide durable, detachable, block-level storage for your Amazon EC2 instances. EBS volumes are mounted to the instances. Therefore, they can provide extremely low latency between where the data is stored and where it might be used on the instance. For this reason, they can be used to run a database with an Amazon EC2 instance.
You can create Amazon EBS snapshots as a point-in-time copy of your data. They are also used to store data for your AMIs. Snapshots are kept in Amazon S3, and they can be reused to create new EC2 instances later.
For more information about Amazon EBS, see “Amazon Elastic Block Store (Amazon EBS)” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html

---



![](image/Pasted%20image%2020231002150749.png)

General purpose solid state drive (SSD) volumes (gp2 and gp3) offer cost-effective storage that is ideal for a broad range of use cases. These volume types are ideal for boot volumes, small and medium-sized databases, and development and test environments.
Provisioned IOPS SSD volumes (io1 and io2) are designed to meet the needs of I/O intensive workloads. For example, database workloads might be sensitive to storage performance and consistency. Provisioned IOPS SSD volumes use a consistent IOPS rate. You specify the rate when you create the volume. Amazon EBS delivers the provisioned performance 99.9 percent of the time.
Throughput-optimized hard disk drive (HDD) volumes (st1) provide low-cost magnetic storage that defines performance in terms of throughput rather than IOPS. This volume type is a good fit for large, sequential workloads such as Amazon EMR; extract, transform, and load (ETL); data warehouses; and log processing.
Cold HDD (sc1) volumes provide low-cost magnetic storage that defines performance in terms of throughput rather than IOPS. sc1 is a good fit for large, sequential cold-data workloads. sc1 provides inexpensive block storage if you require infrequent access to your data.
For more information about Amazon EBS volume types, see “Amazon EBS volume types” at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html

burstable 是个重要的特性 


---

![](image/Pasted%20image%2020231002150910.png)

SSD-backed volumes are optimized for transactional workloads that involve frequent read/write operations with small I/O size, where the dominant performance attribute is IOPS.

Use cases for General Purpose SSD volumes include: 
• Transactional workloads 
• Virtual desktops
• Medium-sized, single-instance databases
• Low-latency interactive applications
• Boot volumes 
• Development and test environments

Use cases for Provisioned IOPS SSD volumes include: 
• Workloads that require sustained IOPS performance or more than 16,000 IOPS 
• I/O intensive database workloads

Specific use cases for io2 Block Express include: 
• Sub-millisecond latency 
• Sustained IOPS performance
• More than 64,000 IOPS or 1,000 MiB/s of throughput

For more information about Amazon EBS SSD, see “Solid state drives (SSD)” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#solid-state-drives


![](image/Pasted%20image%2020231002150923.png)

HDD-backed volumes are optimized for large streaming workloads where throughput, measured in MiB/s, is a better performance measure than IOPS.
Use cases for Throughput Optimized HDD volumes include: 
• Big data
• Data warehouses 
• Log processing

Use cases for Cold HDD volumes include:
• Throughput-oriented storage for data that is infrequently accessed 
• Scenarios where the lowest storage cost is important

For more information about Amazon EBS HDD, see “Hard disk drives (HDD)” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html#hard-disk-drives.


### 4.1.2 Instance store volumes

![](image/Pasted%20image%2020231002151005.png)

IOPS是一个用于电脑存储设备性能测试的量测方式，可以视为是每秒的读写次数。和其他性能测试一様，存储设备制造商提出的IOPS不保证就是实际应用下的性能。  

instance stops, store volumne 会被 会被自动删除
但是 Instance store volumes 的 iops 比 ebs  高

又想 保持 告诉访问, 又想数据不损失 怎么办: 
使用  distributed architecture. replicate my data across multiple instances  . aws replicate the data across AZs 
aws  使用 NoSQL. Dynamo DB. because it is unlimited scaling

An instance store provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer.
An instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content. It is also good for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.

An instance store is: 
• Directly attached block-level storage
• Low-latency
• High IOPS and throughput 
• Reclaimed when the instance is stopped or terminated

Instance stores are available in HDD, SSD, and non-volatile memory express SSD (NVMe SSD) varieties. Use cases for an instance store include: 
• Buffers
• Cache 
• Temporary data



### 4.1.3 Amazon EC2 pricing options 

The compute operations manager asks, “How can we optimize cost for compute resources?”


![](image/Pasted%20image%2020231002151810.png)

With On-Demand Instances, you can pay for compute capacity by the second or hour, with no long-term commitments. On-Demand Instances are ideal for short-term, irregular workloads that cannot be interrupted. 

You can also choose On-Demand initially to determine your needs based on usage.

• Pay for compute capacity per second (for Linux, Windows, Windows with SQL Enterprise, Windows with SQL Standard, and Windows with SQL Web) or per hour (for all other OSs).
• There are no long-term commitments. 
• There are no upfront payments. 
• Increase or decrease your compute capacity depending on the demands of your application.

Savings Plans and Spot Instances give you cost savings with a different type of commitment. The next few slides describe when it is best to use which plans, based on your need.


---
https://aws.amazon.com/ec2/pricing/

1  On-Demand Instances 
On-Demand Instances let you pay for compute capacity by the hour or second with no long-term commitments. This frees you from the costs and complexities of planning, purchasing, and maintaining hardware and transforms what are commonly large fixed costs into much smaller variable costs.

On-Demand Instances are recommended for:  
- Users that prefer the low cost and flexibility of EC2 without any upfront payment or long-term commitment
- Applications with short-term, spiky, or unpredictable workloads that cannot be interrupted
- Applications being developed or tested on EC2 for the first time


2  Saving Plans
Savings Plans is a flexible pricing model that can help you reduce your bill by up to 72% compared to On-Demand prices, in exchange for a commitment to a consistent amount of usage (measured in $/hour) for a 1- or 3-year term.

AWS offers three types of Savings Plans: 
- Compute Savings Plans, 
- EC2 Instance Savings Plans:   
- Amazon SageMaker Savings Plans.

Compute Savings Plans apply to usage across Amazon EC2, AWS Lambda, and AWS Fargate.

Savings Plans are recommended for:  
- Committed and steady-state usage
- Users looking to take advantage of the latest compute offerings while continuing to save money

EC2 svaing plans:  only ec2 instance
Compute saving plans : fargat , ec2 instance, lambda, container


3 Spot Instances
谁出的钱多, 谁就能终结其他出钱少的人,  马上给你用 这个 instances
Amazon EC2 Spot Instances let you take advantage of unused EC2 capacity in the AWS cloud and are available at a discount of up to 90% compared to On-Demand prices.

Spot Instances are recommended for:
- Fault tolerant or stateless workloads  
- Applications that can run on heterogeneous hardware  
- Applications that have flexible start and end times

---



![](image/Pasted%20image%2020231002152041.png)

ec2 instance saving plans
- only use ec2instance
- only on a fix region 

compute saving plans
- any region 
- lambda , storage 都可用

Compute Savings Plans provide the most flexibility. The price can be up to 66 percent off On-Demand rates. These plans automatically apply to your EC2 instance usage, regardless of instance family, size, Region, Availability Zone, OS, or tenancy. They also apply to your Fargate and Lambda usage.
With a Compute Savings Plan, you can move a workload from C5 to M5, shift your usage from Ireland to London, or migrate your application from Amazon EC2 to Amazon ECS using Fargate at any time.
EC2 Instance Savings Plans provide savings up to 72 percent off On-Demand, with a commitment to a specific instance family in a chosen AWS Region. These plans automatically apply to usage within the specified family in a Region. They apply regardless of Availability Zone, size (for example, m5.xlarge or m5.2xlarge), OS (for example, Windows or Linux), or tenancy (Host, Dedicated, or Default).
With an EC2 Instance Savings Plan, you can change your instance size within the instance family or the OS. You can also move from Dedicated tenancy to Default and continue to receive the discounted rate that your EC2 Instance Savings Plan provides.
We recommend Savings Plans over Reserved Instances. Like Reserved Instances, Savings Plans offer lower prices (up to 72 percent savings compared to On-Demand Instance pricing). In addition, Savings Plans offer you the flexibility to change your usage as your needs evolve.

---


![](image/Pasted%20image%2020231002152158.png)

A Spot Instance is an instance that uses spare EC2 host capacity. Spot Instances give you up to 90 percent savings compared to On-Demand Instances. Because Spot Instances permit you to request unused EC2 instances at steep discounts, you can lower your Amazon EC2 costs for flexible workloads.
The hourly price for a Spot Instance is called a Spot price. The Spot price of each instance type in each Availability Zone is set by Amazon EC2. The price is adjusted gradually, based on the long-term supply and demand for Spot Instances. Your Spot Instance runs whenever capacity is available, and if your requested maximum price is higher than the Spot price. If your Spot request cannot be fulfilled, it fails.
An interruption occurs when there is currently no capacity for your request at your maximum price. You receive a notification two minutes before the event.
You can get faster results by increasing throughput up to 10 times, while still staying under budget. You can still diversify instances by choosing different types, sizes, and Availability Zones.
Launch your Spot Instances through AWS services, such as Amazon Elastic Container Service (Amazon ECS), AWS Batch, Amazon EMR, or by using integrated third parties.
For more information, see “Spot Instances” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html.


![](image/Pasted%20image%2020231002152657.png)

instantaneous 
stingy  吝啬 

ec2 spot instance: 
- 谁出钱多, 就马上把你的instance 给抢了. 
用 Spot fleet 出价 : 
- m5 c3 i2 这几个 instance type  我的最高价是 xx. 

Spot Instances are ideal for your fault-tolerant, flexible, loosely coupled, or stateless workloads.
Some common use cases for Spot Instances include: 
• Image and media rendering – You can manage and scale your on-premises or cloud rendering workloads cost effectively with near limitless capacity.
• Web services – Deploy an EC2 Spot Fleet behind your load balancer to scale to tens of thousands of instances, serving billions of service requests.
• Big data and analytics – Fast-track big data, machine learning, and natural language processing (NLP) workloads with Spot Instances. Spot Instances provide acceleration, scale, and deep cost savings to run time-critical, hyper-scale workloads for rapid data analysis.

Other use cases include: 
• Containerized workloads 
• Continuous integration/continuous delivery (CI/CD) and testing 
• HPC

EC2 Spot Instances are also integrated into multiple AWS services, such as Amazon EC2 Auto Scaling groups, Amazon EMR, Amazon ECS, and AWS Batch.

Learn about how companies like Western Digital use Spot Instances. For more information, see “Western Digital HDD Simulation at Cloud Scale – 2.5 Million HPC Tasks, 40K EC2 Spot Instances” in AWS News Blog at https://aws.amazon.com/blogs/aws/western-digital-hdd-simulation-at-cloud-scale-2-5-million-hpc-tasks-40k-ec2-spot-instances/.


---


![](image/Pasted%20image%2020231002152733.png)

Create your strategy for purchasing EC2 instances to get the most for your budget. 
• Use Savings Plans to budget for your defined compute needs. This part is more of a fixed cost, which will not change for you from month to month.
• Launch Spot Instances for your more flexible workloads that take into account failure or missing capacity short-term.
• For the rest, use On-Demand EC2 instances and pay the list price for your compute.

# 5 AWS Lambda

serverless computing 
The compute operations manager asks, “Where can we start with serverless compute options?”


![](image/Pasted%20image%2020231002152912.png)

What is serverless computing? W
ith serverless computing, you can build and run applications and services without thinking about servers. Serverless applications don't require you to provision, scale, and manage any servers. You can build them for nearly any type of application or backend service. Everything that is required to run and scale your application with high availability is handled for you.

Why use serverless computing? 
With serverless applications, your developers can focus on their core product instead of worrying about managing and operating servers or runtimes. Because of this reduced overhead, developers can reclaim time and energy that can be spent on developing great products that scale and are reliable.
For more information, see “Serverless on AWS” at https://aws.amazon.com/serverless/. 



![](image/Pasted%20image%2020231002153303.png)

lambda, take a image, create a small instance, then run function code. and then upload the result  to bucket 
怎么付钱 user change time cosuming and the momory that is has utizied. don charge the instance  

14.5s x 10G 就要付30欧元 

![](image/Pasted%20image%2020231002153631.png)

==if the cod eurns for up to 15 minutes. do not use the lambda . This case use ecs contains oder eks ==


With Lambda, you can run code without provisioning or managing servers. The service runs your code on a high-availability compute infrastructure and performs all administration of the compute resources. 
These resources include: 
• Server and OS maintenance 
• Capacity provisioning and automatic scaling 
• Code monitoring and logging

All that you must do is supply your code in one of the languages that Lambda supports: Node.js, Java, C#, Python, Go, Ruby, and PowerShell.
The core components of Lambda are the event source and the Lambda function. Event sources publish events. A Lambda function is the custom code that you write to process the events. Lambda runs your function.
A Lambda function consists of your code, associated dependencies, and configuration. 
Configuration includes information such as: 
• The handler that will receive the event 
• The AWS Identity and Access Management (IAM) role that Lambda can assume to run the Lambda function on your behalf
• The compute resource that you want allocated 
• The delivery timeout

There is no additional charge for creating Lambda functions. You do incur charges for running a function and for data transfer between Lambda and other AWS services. Some optional Lambda features, for example provisioned concurrency, also incur charges.
For more information about provisioned concurrency, see “Managing Lambda reserved concurrency” in the AWS Lambda Developer Guide at https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html.

For more information about Lambda pricing, see “AWS Lambda Pricing” at https://aws.amazon.com/lambda/pricing

---


![](image/Pasted%20image%2020231002153514.png)

A Lambda function can be invoked manually or by an AWS service. Some of these services are covered in more detail later in this course.
If you want a way to configure an HTTPS endpoint in front of your function, consider using AWS Lambda Function URLs.
For more information about Lambda Function URLs, see “Announcing AWS Lambda Function URLs: Built-in HTTPS Endpoints for Single-Function Microservices” in the AWS News Blog at https://aws.amazon.com/blogs/aws/announcing-aws-lambda-function-urls-built-in-https-endpoints-for-single-function-microservices/.


---



![](image/Pasted%20image%2020231002153528.png)

AWS Lambda is a cost-effective solution for a number of tasks. 
Consider the following use cases: 
• Web applications 
    • Static websites
    • Complex web applications
    • Packages for Flask and Express

• Backends
    • Applications and services
     • Mobile
    • Internet of things (IoT)
• Data processing
    • Real-time processing
     • Amazon EMR 
     • AWS Batch
• Chatbots
    • Powering chatbot logic
• Amazon Alexa 
    • Powering voice-activated applications 
    • Alexa Skills Kit
• IT automation: 
    • Policy engines
    • Extending AWS services
    • Infrastructure management

For more information about Lambda use cases, see “Common Lambda application types and use cases” in the AWS Lambda Developer Guide at https://docs.aws.amazon.com/lambda/latest/dg/applications-usecases.html

# 6 Review 

![](image/Pasted%20image%2020231017175327.png)

Imagine that you are now ready to talk to the compute operations manager and present solutions that meet their architectural needs.
Think about how you would answer the questions from the beginning of the lesson about compute.

Your answers should include the following solutions: 
• Identify AWS services that are used to create compute capacity in your accounts.
• Consider things like AMIs, instance types and sizes, authentication, placement, tenancy, scripting, and metadata in Amazon EC2.
• Build and attach Amazon EBS and instance store volumes based on your needs. 
• Plan for the future cost of compute by using a combination of Savings Plans, Spot Instances, and On-Demand Instances.
• Use AWS Lambda to reduce manual work and manage cost for developers. 

![](image/Pasted%20image%2020231017175415.png)

# 7 Capstone check-in

![](image/Pasted%20image%2020231017175546.png)
At the end of this course is a Capstone Lab project. You will be provided a scenario and asked to build an architecture based on project data, best practices, and the Well-Architected Framework

![](image/Pasted%20image%2020231017175558.png)

In this module, you explored AWS compute services like Amazon EC2 and AWS Lambda.
Review the capstone architecture to explore some of the design decisions. This architecture helps you provide the following benefits: 
• EC2 instances can quickly create your WordPress website. You can use an AWS Marketplace AMI for WordPress, or you can use a script to install WordPress with user data at EC2 launch time.
• NAT gateways allow outbound traffic from your EC2 instances in private subnets. In this way, your private EC2 instances can connect to the internet through the internet gateway. It stops external sources from initiating connections to your private EC2 instances.

You place the EC2 instances into your application subnet for the three-tier architecture. Think about the kind of manual effort that will be required if your team is managing up to four EC2 instances at once.
What if you want to scale your application in or out to save on cost without sacrificing performance? What can you do to automate the creation of new EC2 instances? You’ll explore scaling and monitoring tools, load balancers, and EC2 launch templates later in this course


# 8 Knowledge Check 

a 不对 , vpc 可以选择 
b d

![](image/Pasted%20image%2020231003080749.png)

The correct answer is B and D.
AMIs include block device mapping that specifies the volumes to attach to the Amazon EC2 instance when it is launched. You can launch multiple instances from a single AMI.
An Amazon Machine Image (AMI) provides the information that is required to launch an instance. You must specify an AMI when you launch an instance.
You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.
For more information about AMIs, see “Amazon Machine Images (AMI)” in the Amazon EC2 User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html.


---

a

![](image/Pasted%20image%2020231003081102.png)

The correct answer is A, the letter m.
The first letter (or letters) in the instance type name before the first number tells you what instance family the EC2 instance is from.
For more information about EC2 instance types, see “Amazon EC2 Instance Types” at https://aws.amazon.com/ec2/instance-types/

---

![](image/Pasted%20image%2020231003081130.png)

cd

The correct answer is C and D. Lambda functions can be allocated up to 10 GB of memory. Lambda functions run for up to 15 minutes.
