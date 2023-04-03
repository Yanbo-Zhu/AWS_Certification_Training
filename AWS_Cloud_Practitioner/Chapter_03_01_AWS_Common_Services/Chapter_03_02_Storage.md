# 1 Types of Storage Services


- Elastic Block Store (EBS) - based on Block stroge
    - a mount drive  .It can be attatch to EC2 instance 
    - 同一个 Elastic Block Store (EBS) - Block  只能被贴到 一个 vm 中 
- AWS Elastic File Storage (EFS) - based on File systems 
    - 这个 file share ist accessable by multiple users oder VMs
- Amazon simple Storage Service (S3) - based on Object storage 
    - just upload files , not worry about underlying infrastructure
    - s3 中的object 可以通过 https 的方式 上传 或者 下载到 某处

![](image/Pasted%20image%2020230402211908.png)

# 2 Introduction to S3 

Simple Storage Service - based on Object-Storage

## 2.1 Object Storage 的介绍

![](image/Pasted%20image%2020230402214105.png)

## 2.2 S3 Object 和 S3 Bucket  

![](image/Pasted%20image%2020230402214303.png)c

# 3 S3 Storage Classes

根据 retrieval time, accessibility , Burability  划分出来的 不同的 s3 storage class
相应的价格也不一样

- S3 Standard
- S3 Intelligent Tierung
- S3 Standard-IA
- S3 One-Zone-IA
- S3 Glacier
- S3 Glacier Deep Archive
 ![](image/Pasted%20image%2020230402214747.png)

# 4 AWS Snow Family

AWS snow family 是 storage and compute devices which ist used to physically move data in or out the cloud in S3

三个不同的规格 有着 不同的 移动速度, 移动data size 和 花费

![](image/Pasted%20image%2020230402215225.png)

# 5 AWS 中的 Storage 相关的 aws  Services

- Simple Storage Service (S3)
- S3 Glacier 
- Elastic Block Store (EBS)
    - mounted drive to a ec2
    - 一次只能 mounte 到某一个 ec2 instance 
- Elastic File Storage (EFS)
    - NFS file system service can mout to multiple Ec2 instance at the same time 
- Storage Gateway
    - hybird cloud storage service that extends your on-premise storage to cloud . 就是你本地的文件 也可以挂载到 ec2 上面. 
    - File Gateway
    - Volume Gateway
    - Tape Gateway 


![](image/Pasted%20image%2020230402220203.png)


5:40:10 S3 Follow Along
5:47:34 EBS Follow Along
5:50:24 EFS Follow Along
5:59:58 Snow Family Follow Along

