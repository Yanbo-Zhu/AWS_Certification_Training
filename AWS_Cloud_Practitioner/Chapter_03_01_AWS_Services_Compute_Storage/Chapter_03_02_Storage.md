![](image/Pasted%20image%2020230403171849.png)

# 1 Types of Storage Services


- Elastic Block Store (EBS) - based on Block stroge. 
    - 使用情景: When you need a virtual hard drive attached to a VM
    - a mount drive  .It can be attatch to EC2 instance . 
    - 同一个 Elastic Block Store (EBS) - Block  只能被贴到 一个 vm 中 
    -  Data is split into evenly split blocks
    - Directly accessed by the Operation System
    -   Supports only a single write volume
- AWS Elastic File Storage (EFS) - based on File systems. 
    - 使用情景: When you need a file-share where multiple users or VMs need to access the same drive
    - 这个 file share ist accessable by multiple users oder VMs
    - File is stored with data and metadata
    -  Multiple connections via a network share
    -  Supports multiple reads. Writing locks the file.
- Amazon simple Storage Service (S3) - based on Object storage . 
    - 使用情景: When you just want to upload files, and not have to worry about the underlying infrastructure. Not intended for high IOPs
    - just upload files , not worry about underlying infrastructure
    - s3 中的object 可以通过 https 的方式 上传 或者 下载到 某处
    -   Object is stored with data, metadata, and a Unique ID
    -   ~~Scales with limited no file limit or storage limit~~
    -   Scales with an unlimited number of objects in a bucket
    -   Supports multiple reads and writes (no locks)


![](image/Pasted%20image%2020230402211908.png)

# 2 Introduction to S3 

Simple Storage Service - based on Object-Storage


## 2.1 Object Storage 的介绍

[Object storage](https://en.wikipedia.org/wiki/Object_storage)

![](image/Pasted%20image%2020230402214105.png)

data storage architecture that manages data as objects, **as opposed** to other storage architectures such as:
-   file systems that manage data as files and fire file hierarchy, and
-   block storage which manages data as blocks within sectors and tracks.

S3 provides you with **unlimited storage**.
You don’t need to think about the underlying infrastructure
The S3 Console provides an interface for you to upload and access your data

## 2.2 S3 Object 和 S3 Bucket  

![](image/Pasted%20image%2020230402214303.png)

### 2.2.1 S3 Object

Objects contain your data. They are like files.
An object may consist of:
-   **Key** this is the name of the object
-   **Value** the data itself is made up of a sequence of bytes
-   **Version ID** the version of the object (when versioning is enabled)
-   **Metadata** additional information attached to the object

### 2.2.2 S3 Bucket

Buckets hold objects. Buckets can also have folders which in turn hold objects
S3 is a universal namespace so bucket names must be unique (think like having a domain name)
You can store an individual object from **0 Bytes to 5 Terabytes** in size

# 3 S3 Storage Classes

[Storage classes](https://activate-next.workshop.aws/002_services/002_storage/003_s3.html)
    - AWS offers a range of S3 storage classes that trade **Retrieval Time, Accessibility and Durability** for **Cheaper Storage**
根据 retrieval time, accessibility , Burability  划分出来的 不同的 s3 storage class
相应的价格也不一样

贵
- S3 Standard
    - Fast! 99.99% Availability, 11 9’s Durability. Replicated across at least three AZs
- S3 Intelligent Tierung
    - Uses ML to analyze object usage and determine the appropriate storage class. Data is moved to the most cost-effective access tier, without any performance impact or added overhead.
- S3 Standard-IA
    - Still Fast! Cheaper if you access files less than once a month. Additional retrieval fee is applied. 50% less than Standard (reduced availability)
- S3 One-Zone-IA
    - Still Fast! Objects only exist in one AZ. Availability (is 99.5%). but cheaper than Standard IA by 20% less  (Reduce durability) Data could get destroyed. A retrieval fee is applied.
- S3 Glacier
    - For long-term cold storage. Retrieval of data can take minutes to hours but the off is very cheap storage
- S3 Glacier Deep Archive
    - The lowest cost storage class. Data retrieval time is 12 hours.
便宜

S3 Outposts has its own storage class.
 ![](image/Pasted%20image%2020230402214747.png)

# 4 AWS Snow Family

[AWS re:Invent recap: Optimize your data migration with AWS Snow Family](https://aws.amazon.com/blogs/storage/aws-reinvent-recap-optimize-your-data-migration-with-aws-snow-family/)
[AWS Snowball Edge Device Differences](https://docs.aws.amazon.com/snowball/latest/developer-guide/device-differences.html)

AWS Snow Family are **storage and compute devices used to physically move data in or out the cloud** when moving data over the internet or private connection it to slow, difficult or costly.

**Snowcone**
Comes in two sizes:
-   8 TB of Storage (HHD)
-   14 TB of Storage (SSD)

**Snowball Edge**
Comes generally in two type:
-   Storage Optimized
    -   80 TB
-   Compute Optimized
    -   39.5 TB

**Snowmobile**
100 PB of storage
Data is delivered to Amazon S3

三个不同的规格 有着 不同的 移动速度, 移动data size 和 花费

![](image/Pasted%20image%2020230402215225.png)

# 5 AWS 中的 Storage 相关的 aws  Services

- Simple Storage Service (S3)
    - is an `object storage` service that offers industry-leading scalability, data availability, security, and performance. Think of it as a `"hard drive in the cloud"` with a lot of available space.
- S3 Glacier 
    - low cost storage for `archiving and long-term backup` Trade-off: You may have to wait several hours to access data stored here. Use case: for data that you must hold on to but are unlikely to look at often. Example: an enterprise company that must store records for many years under a litigation hold.
- Elastic Block Store (EBS)
    - mounted drive to a ec2
    - 一次只能 mounte 到某一个 ec2 instance 
    - Elastic Block Store`- is a persistent block storage service. It is a virtual hard drive in the cloud you attach to EC2 instances. You can choose different kinds of hard drives: **SSD, IOPS SSD, Throughput HHD, Cold HHD​**
- Elastic File Storage (EFS)
    - NFS file system service can mout to multiple Ec2 instance at the same time 
    - EFS volumn is serverless 
- Storage Gateway
    - hybird cloud storage service that extends your on-premise storage to cloud . 就是你本地的文件 也可以挂载到 ec2 上面. 
    -   **File Gateway** extends your local storage to AWS S3
    -   **Volume Gateway** caches your local drives to S3 so you have a continuous backup of local files in the cloud
    -   **Tape Gateway** stores files onto virtual tapes for backing up your files on very cost-effective long-term storage.
- AWS Snow Family: storage devices used to pyhsically migrate large amounts of data to the cloud
    - Snowball and Snowball Edge are briefcase-size data storage devices. 50-80 Terabytes
    -   [**Snowball edge**](https://aws.amazon.com/snow/) - A version of Snowball for even larger sets of data - `100 TB`
    -   [**Snowmobile**](https://aws.amazon.com/snowmobile/) is a cargo container filled with racks of storage and compute that is transported via semi-trailer tractor truck to transfer up to 100PB of data per trailer
    -   **Snowcone** is a very small version of Snowball that can transfer 8TB of data.
- AWS Backup: managed backup service 
- CloudEndure Disaster Recovery : continuously replicated yor machines into a low-cost staging area . Enabiling fast and reliable recovery 
- Amzaon FSxL rich and highly-perfomact file system
    - Amazon FSx for windows File Server: mount FSx to windows Servers 
    - Amazon FSx for Lustre file system: mount FSX to Linux Server

![](image/Pasted%20image%2020230402220203.png)

 ![](image/Pasted%20image%2020230403143801.png)


# 6 实操

## 6.1 S3 例子
0 by default. , up to 100 bucket in a aws account
![](image/Pasted%20image%2020230403150146.png)


修改这个上限 
进入到 aws service Quotas 
![](image/Pasted%20image%2020230403150311.png)

https://aws.amazon.com/about-aws/whats-new/2021/04/service-quotas-available-aws-govcloud-us-regions/
You can now use Service Quotas in AWS GovCloud (US) Regions to view and manage your service quotas at scale as your AWS workloads grow.
The AWS Service Quotas service can be used by companies to centrally request and track service limit increases for their AWS accounts. AWS Service Quotas enables you to view and manage your AWS service quotas in a single location, monitor usage, and request increases for those quotas.

![](image/Pasted%20image%2020230403150320.png)



1 upload 某些东西 到 s3
storage class 中 不同的 Tier, 价格不一样 

![](image/Pasted%20image%2020230403144755.png)

Encryption  of files
![](image/Pasted%20image%2020230403145023.png)

2 Life cycle of s3 bucket 
![](image/Pasted%20image%2020230403145942.png)

move things to galcier after 30 days
![](image/Pasted%20image%2020230403145905.png)

3 empty a s3 bucket and then delete
delete 之前 一定要先 empty 这个 bucket
![](image/Pasted%20image%2020230403150100.png)



## 6.2 Elastic Block Store EBS 例子

1 create value 
方法1 进入 ec2 ->  Elastic Block Store volumn
![](image/Pasted%20image%2020230403162957.png)

![](image/Pasted%20image%2020230403163255.png)


方法2 在 创建新的ec2 的时候 add a ebs volumn 

- Delete On Termination: 可以选择, 再删除 ec2 instance 的时候, 是保留这个 volumn, 还是 连带着 这个 volumn 一起删除了. 
![](image/Pasted%20image%2020230403163922.png)

## 6.3 Elastic File Storage  EFS Follow Along

Elastic File Storage   创建的 file system volumb can be attached with multiple Ec2 instance 

### 6.3.1 create a new file system 
![](image/Pasted%20image%2020230403164236.png)

![](image/Pasted%20image%2020230403164331.png)

![](image/Pasted%20image%2020230403164541.png)


1.1 create access point of this file system
这个 被用到 在 Mount on Ec2 Linux instances using EFS Mount helper 
![](image/Pasted%20image%2020230403164630.png)


### 6.3.2 Mount on Ec2 Linux instances using EFS Mount helper 
https://docs.aws.amazon.com/efs/latest/ug/mounting-fs-mount-helper-ec2-linux.html

2.1 当 ec2 instance 已经存在, 然后 后来才 attach a efs 到这个 instance 上  
点击 attach
![](image/Pasted%20image%2020230403164721.png)****

或者相关的命令行 
![](image/Pasted%20image%2020230403164810.png)

2.2   在新建一个 ec2 instance 的时候 , 选择附上 一个 file system 
![](image/Pasted%20image%2020230403164959.png)

在创造这个 ec2 instance 的时候 创新 一个 key pair, 并且下载 这 key pair 
在下载的时候 会自动下载一个 pem 文件 

![](image/Pasted%20image%2020230403165156.png)

### 6.3.3 检查  efs volumn 是否成功 attach 到 ec2 instance 上面了 
3.1 通过 aws cloud shell  登录 到这个新创造的 ec2 
upload the pem 文件 contians the key pair 
![](image/Pasted%20image%2020230403165518.png)

必须修改一下权限 
![](image/Pasted%20image%2020230403165651.png)

3.2  通过 ssh  登录 到这个新创造的 ec2 通过 access key (in .pem  文件)
查看 /mbt/efs 中存在 这个 mounted efs volumn 

![](image/Pasted%20image%2020230403165947.png)


## 6.4 Snow Family 例子

import or export data from S3

![](image/Pasted%20image%2020230403171346.png)
1 create new job 
![](image/Pasted%20image%2020230403171410.png)

![](image/Pasted%20image%2020230403171835.png)

Choose you snow device
不同地区 能够提供的 选项 是不同的 , 是有限的
![](image/Pasted%20image%2020230403171856.png)

同样在 Choose you snow device  这页
![](image/Pasted%20image%2020230403171931.png)




