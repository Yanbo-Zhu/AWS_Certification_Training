![](image/Pasted%20image%2020230403171849.png)# 1 Types of Storage Services


- Elastic Block Store (EBS) - based on Block stroge
    - a mount drive  .It can be attatch to EC2 instance 
    - 同一个 Elastic Block Store (EBS) - Block  只能被贴到 一个 vm 中 
- AWS Elastic File Storage (EFS) - based on File systems 
    - 这个 file share ist accessable by multiple users oder VMs
- Amazon simple Storage Service (S3) - based on Object storage 
    - just upload files , not worry about underlying infrastructure
    - s3 中的object 可以通过 https 的方式 上传 或者 下载到 某处

![](image/Pasted%20image%2020230402211908.png)

# 1 Introduction to S3 

Simple Storage Service - based on Object-Storage

## 1.1 Object Storage 的介绍

![](image/Pasted%20image%2020230402214105.png)

## 1.2 S3 Object 和 S3 Bucket  

![](image/Pasted%20image%2020230402214303.png)c

# 2 S3 Storage Classes

根据 retrieval time, accessibility , Burability  划分出来的 不同的 s3 storage class
相应的价格也不一样

- S3 Standard
- S3 Intelligent Tierung
- S3 Standard-IA
- S3 One-Zone-IA
- S3 Glacier
- S3 Glacier Deep Archive
 ![](image/Pasted%20image%2020230402214747.png)

# 3 AWS Snow Family

AWS snow family 是 storage and compute devices which ist used to physically move data in or out the cloud in S3

三个不同的规格 有着 不同的 移动速度, 移动data size 和 花费

![](image/Pasted%20image%2020230402215225.png)

# 4 AWS 中的 Storage 相关的 aws  Services

- Simple Storage Service (S3)
- S3 Glacier 
- Elastic Block Store (EBS)
    - mounted drive to a ec2
    - 一次只能 mounte 到某一个 ec2 instance 
- Elastic File Storage (EFS)
    - NFS file system service can mout to multiple Ec2 instance at the same time 
    - EFS volumn is serverless 
- Storage Gateway
    - hybird cloud storage service that extends your on-premise storage to cloud . 就是你本地的文件 也可以挂载到 ec2 上面. 
    - File Gateway
    - Volume Gateway
    - Tape Gateway 
- AWS Snow Family: storage devices used to pyhsically migrate large amounts of data to the cloud
    - Snowcone
    - Snowball Edge
    - Snowmobile
- AWS Backup: managed backup service 
- CloudEndure Disaster Recovery : continuously replicated yor machines into a low-cost staging area . Enabiling fast and reliable recovery 
- Amzaon FSxL rich and highly-perfomact file system
    - Amazon FSx for windows File Server: mount FSx to windows Servers 
    - Amazon FSx for Lustre file system: mount FSX to Linux Server

![](image/Pasted%20image%2020230402220203.png)

 ![](image/Pasted%20image%2020230403143801.png)


# 5 实操

## 5.1 S3 例子
0 by default. , up to 100 bucket in a aws account
![](image/Pasted%20image%2020230403150146.png)


修改这个上限 
进入到 aws service Quotas 
![](image/Pasted%20image%2020230403150311.png)

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



## 5.2 Elastic Block Store EBS 例子

1 create value 
方法1 进入 ec2 ->  Elastic Block Store volumn
![](image/Pasted%20image%2020230403162957.png)

![](image/Pasted%20image%2020230403163255.png)


方法2 在 创建新的ec2 的时候 add a ebs volumn 

- Delete On Termination: 可以选择, 再删除 ec2 instance 的时候, 是保留这个 volumn, 还是 连带着 这个 volumn 一起删除了. 
![](image/Pasted%20image%2020230403163922.png)

## 5.3 Elastic File Storage  EFS Follow Along

Elastic File Storage   创建的 file system volumb can be attached with multiple Ec2 instance 

### 5.3.1 create a new file system 
![](image/Pasted%20image%2020230403164236.png)

![](image/Pasted%20image%2020230403164331.png)

![](image/Pasted%20image%2020230403164541.png)


1.1 create access point of this file system
这个 被用到 在 Mount on Ec2 Linux instances using EFS Mount helper 
![](image/Pasted%20image%2020230403164630.png)


### 5.3.2 Mount on Ec2 Linux instances using EFS Mount helper 
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

### 5.3.3 检查  efs volumn 是否成功 attach 到 ec2 instance 上面了 
3.1 通过 aws cloud shell  登录 到这个新创造的 ec2 
upload the pem 文件 contians the key pair 
![](image/Pasted%20image%2020230403165518.png)

必须修改一下权限 
![](image/Pasted%20image%2020230403165651.png)

3.2  通过 ssh  登录 到这个新创造的 ec2 通过 access key (in .pem  文件)
查看 /mbt/efs 中存在 这个 mounted efs volumn 

![](image/Pasted%20image%2020230403165947.png)


## 5.4 Snow Family 例子

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




