
![](image/Pasted%20image%2020231012161516.png)

In this module, you will explore:
• Storage types 
• Amazon Elastic Block Store (Amazon EBS) 
• Amazon Elastic File System (Amazon EFS) 
• Amazon Simple Storage Service (Amazon S3)

In this module, you explored:
• Storage types • Amazon EBS • Amazon EFS • Amazon S3


![](image/Pasted%20image%2020231012161608.png)


AWS offers three categories of storage service – block storage, file storage, and object storage. You will learn about the AWS services that support these storage types.


Object stroage : 这里 的 file 只能整体处理 , S3
Block storage: EBS
File storage: ebs linux


# 1 Block storage 

![](image/Pasted%20image%2020231012161658.png)

With block storage, data is stored on a device in fixed-sized blocks (for example, 512 bytes). Applications and file systems regulate how blocks are accessed, combined, and modified.

The two types of block storage in AWS are Amazon EC2 instance store and Amazon Elastic Block Store (Amazon EBS).

With Amazon EBS Multi-Attach, you can attach a single Provisioned IOPS Solid State Drive (SSD) - (io1 or io2) volume to multiple instances in the same Availability Zone. Multi-Attach makes it possible for you to achieve higher application availability in clustered Linux applications that manage concurrent write operations.


Amazon ex2 instace ist only 
Ebs volumen ist running different volumens , 两者之间的链接 是通过 connecting


Amaozn ec2 instance
Instace store is  deleted, the amaozn c2 instance will be dleted


![](image/Pasted%20image%2020231012161733.png)


The two main categories for Amazon EBS volume types are solid state drives (SSD) and hard disk drives (HDD). SSDs are used for transactional workloads with frequent read/write operations with small input/output (I/O) size for faster I/O operations per second (IOPS). HDDs are used for large streaming workloads that need high throughput performance.

The following are Amazon EBS volume types: 
• General Purpose SSD (gp3, gp2): Provides a balance of price and performance for a wide variety of transactional workloads
• Provisioned IOPS SSD (io2 Block Express, io2, io1): Provides high-performance SSD designed for latency-sensitive transactional workloads
• Throughput Optimized HDD (st1): A low-cost HDD designed for frequently accessed, throughput intensive workloads
• Cold HDD (sc1): The lowest cost HDD designed for less frequently accessed workloads


Resource To learn more about volume types, see the online documentation: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volume-types.html.


# 2 File storage 

## 2.1 Amazon EFS 

![](image/Pasted%20image%2020231012162010.png)

File storage helps users, applications, and services access data in a shared file system. This is similar to a centralized shared network drive in a company where employees store and access files.

Amazon Elastic File System (Amazon EFS) is a scalable file system used with AWS Cloud services and on-premises resources. Amazon EFS supports thousands of connections from Amazon EC2 instances across multiple Availability Zones. On-premises servers can access Amazon EFS through AWS Direct Connect. You can mount an Amazon EFS file system in your virtual private cloud (VPC), through the Network File System versions 4.0 and 4.1 (NFSv4) protocol. We recommend using a current generation Linux NFSv4.1 client, such as those found in the latest Amazon Linux, Amazon Linux 2, Red Hat, Ubuntu, and macOS Big Sur AMIs, in conjunction with the Amazon EFS mount helper.

AWS also offers Amazon FSx for Windows File Servers. This service provides fully managed, highly reliable, and scalable file storage that is accessible over the open standard Server Message Block (SMB) protocol, with the following options:
• Single-AZ and Multi-AZ deployment 
• Microsoft Active Directory integration 
• Fully managed backups 
• HDD and SDD storage

Resources 
• To learn more about AWS VPN and inter-Region VPC peering with Amazon EFS, visit: https://aws.amazon.com/about-aws/whats-new/2018/10/amazon-efs-now-supports-aws-vpn-and-inter-region-vpc-peering
• To learn more about Amazon EFS limits, see the online documentation: https://docs.aws.amazon.com/efs/latest/ug/limits.htm



## 2.2 Amzon FSx

Fsx: file server for windows
Configure Nfs: Specify the ip of your elastice file server for windows

![](image/Pasted%20image%2020231012162038.png)


With Amazon FSx, you can choose from two file systems: Amazon FSx for Windows File Server for Windows-based applications and Amazon FSx for Lustre for compute-intensive workloads.

Amazon FSx for Windows File Server is designed for enterprise applications. It is a managed service backed by a native Windows file system. FSx for Windows File Server is an efficient lift-and-shift enterprise application to AWS. Built on SSD storage, FSx for Windows File Server is ideal for supporting Windows workloads that require shared storage. Examples include Customer Relationship Management (CRM), Enterprise Resource Planning (ERP), Microsoft .NET applications, and user home directories.

Thousands of compute instances can access a single Amazon FSx file system at the same time, which provides the following: 
• On-premises access using AWS Direct Connect or AWS VPN. 
• Access from multiple virtual private clouds (VPCs), accounts, and AWS Regions using VPC peering or AWS Transit Gateway.

Amazon FSx for Windows File Server provides a shared file storage system for your Windows Amazon EC2 instances with high levels of throughput and submillisecond latency.

Amazon FSx for Windows File Server supports the following: 
• SMB protocol 
• Windows New Technology File System (NTFS) 
• Active Directory integration 
• Distributed File System (DFS)

You can mount Amazon FSx for Windows File Server on an Amazon EC2 Linux instance. For more information, see “Using Microsoft Windows file shares” in the Amazon FSx Windows User Guide at https://docs.aws.amazon.com/fsx/latest/WindowsGuide/using-file-shares.html



# 3 Object Storage (S3)

![](image/Pasted%20image%2020231013104334.png)

In object storage, files are stored as objects. Each object consists of data, metadata, and an object key. 
The metadata has information about the data (object size, object purpose, and more), and the object key is the unique identifier of the object. 
When you update files in object storage, the entire file object is updated, instead of a piece of a file, as in block storage.

![](image/Pasted%20image%2020231013104512.png)


Amazon Simple Storage Service (Amazon S3) is an object-level storage service. Instead of attaching the service to an instance, you retrieve data through the web. Amazon S3 is highly scalable, and you can store an unlimited amount of data.
The files, or objects, you upload to Amazon S3 consist of data and metadata. The metadata consists of information about the data, such as content type, last modified date, and more. The maximum file size for an object in Amazon S3 is 5 TB.
In addition to the data and metadata, an object’s key serves as a unique identifier.
Objects are stored in an S3 bucket, similar to a directory or folder on your computer. Buckets are created inside a Region. The name you assign to your bucket must be globally unique, even though the bucket is created inside a Region. When you store an object in a bucket, the combination of a bucket name, key, and version ID uniquely identifies the object. For example, if you store an object, called myphotos.zip in a bucket called doc, the URL would be as follows:
“https://doc.s3.amazonaws.com/2021-04-13/myphotos.zip” The key is 2021-04-13/myphotos.zip.
Bucket storage is private by default. You can apply access permission at the bucket level or at the object level, or both.


---

IAM policy is assigned to users
Bucket policay is assigned to bucket
Amazon s3 encrytion

![](image/Pasted%20image%2020231013104539.png)

Resource To learn more about Amazon S3, go to the online documentation: https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html



To grant users, groups, and roles access to Amazon S3, you use an AWS Identity and Access Management (IAM) policy. For example, you can attach an IAM role to an Amazon EC2 instance if an application running on the instance must retrieve a file from an S3 bucket.

Another way to grant access to an S3 bucket is to use a bucket policy. Bucket policies use JSON-based IAM policy language.
A bucket policy is restricted to 20 KB. Therefore, to configure highly granular access permissions to a large number of objects in a bucket, you can use an Amazon S3 access control list (ACL). ACLs define which accounts or groups are granted access to the bucket or object, and the type of access. When you create a bucket or an object, S3 Block Public Access is enabled by default and the ACL is disabled. Access can be further granulated when combined with bucket policies.

When you upload and download objects, you can protect your data by using secure Socket Layer/Transport Layer Security (SSL/TLS) or client-side encryption. You can also protect your Amazon S3 data at rest with server-side encryption and client-side encryption.

• Server-side encryption: Data is encrypted by Amazon S3 at the object level. When you download the object, Amazon S3 decrypts the data.
• Client-side encryption: Data is encrypted before you upload it to an S3 bucket.

An additional Amazon S3 security feature is S3 Block Public Access. It provides settings for access points, buckets, and accounts to help you manage public access to Amazon S3 resources. By default, new buckets, access points, and objects don’t permit public access

Resource To learn more about security, visit the online documentation: https://docs.aws.amazon.com/AmazonS3/latest/userguide/security.html

---


![](image/Pasted%20image%2020231013104807.png)


![](image/Pasted%20image%2020231013104901.png)

Factor: s and r
s: Storage space : big size
r: Request : when I downlaod and upload request , send request

S 向上: pay more in storage
R 向下, pay less in request

- amason s3 standrad and amaozn s3 standard inrquent access
    - Copy are assigend to 3 automacticallyy , usere can not congure it
- Amazzon s3 one zone infrequest  access :
    - the copy only exisited storage in 1 azs
- S3 Glacier
    - Storage  cost is quite lower, request is expensive (5 euro per request )

S3 intelligent-tiering
- Storaged class  will be adpoted ,
- Feature be enabled ,oder disabled by coustimner

Amazon S3 has six primary storage classes.
• Amazon S3 Standard is the default storage class. It is used for general-purpose storage, such as websites and content distribution. S3 Standard is cost effective for frequently accessed data. Data is stored across a minimum of three Availability Zones.

• Amazon S3 Standard-Infrequent Access (S3 Standard-IA) is for data that is accessed less frequently, but the data must be highly available upon request. Data is stored across a minimum of three Availability Zones. S3 Standard-IA has a low per-GB storage price with a data retrieval fee.

• Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA) is for data that is accessed less frequently and can be easily re-created if lost. In S3 One Zone-IA, data is stored in a single Availability Zone. This is ideal for a low-cost option for infrequently access data storage.

• S3 Intelligent-Tiering is used for data with changing or unknown access patterns. S3 Intelligent-Tiering optimizes storage costs by automatically moving data to the most cost-effective access layer depending on access patterns.

• Amazon S3 Instant Retrieval is an archive storage class that delivers the lowest-cost storage for long-lived data that is rarely accessed and requires retrieval in milliseconds.

• Amazon S3 Glacier Flexible Retrieval (formerly S3 Glacier) - delivers the most flexible retrieval options that balance cost with access times ranging from minutes to hours and with free bulk retrievals.

• S3 Glacier Deep Archive is for archiving data that is not accessed often. If you must retrieve the data, the default retrieval time is 12 hours. To reduce costs, you can retrieve data in bulk with a retrieval time of 48 hours.

To learn more about additional S3 options, such as S3 on Outpost, visit https://aws.amazon.com/outposts/

![](image/Pasted%20image%2020231013105301.png)

When you update an object in an S3 bucket, the new object replaces the previous object. For example, when you update an image file in your bucket with the same object name, the previous image is deleted. You can use Amazon S3 versioning to keep both objects.

Amazon S3 versioning keeps multiple versions of an object in the same bucket. This feature protects you from accidentally deleting objects. When you enable versioning, all objects that you upload will be versioned and have a version ID. Objects created prior to enabling versioning might inherit a version ID of null.

If you delete an object after enabling versioning, the object will have a delete marker. You can remove the marker at a later time. Buckets can be in three types of versioning states:
• Unversioned (default): Versioning is not applied for any objects. 
• Versioning-enabled: All objects are versioned. 
• Versioning-suspended: New objects will receive a version ID of null, and if an object with the same key and a version ID of null already exists, it will be overwritten. However, existing objects that do not carry the null ID will be preserved.

Resource To learn more about versioning, see the online documentation: https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html



# 4 Knowledge 


![](image/Pasted%20image%2020231013105353.png)

Which of the following is a typical use case for Amazon Simple Storage Service (Amazon S3)?
A. Object storage for media hosting 
B. Object storage for a boot drive 
C. Block storage for an EC2 instance 
D. File storage for multiple EC2 instances

The correct response option is A. Object storage for media hosting.
Explanation: Amazon S3 is an object storage service designed for large objects like media files. Because you can store unlimited objects, and each individual object can be up to 5 TBs, Amazon S3 is an ideal location to host video, photo, and music files.


---

![](image/Pasted%20image%2020231013105454.png)

Which of the following storage services is recommended if a customer needs a storage layer for a high-transaction relational database on an EC2 instance?
A. Amazon Simple Storage Service (Amazon S3) 
B. Amazon Elastic File System (Amazon EFS) 
C. Amazon Elastic Block Store (Amazon EBS) 
D. Amazon S3 Glacier

The correct response option is C. Amazon Elastic Block Store (Amazon EBS).
Explanation: Amazon EBS is ideal for a high-transaction database storage layer. Amazon S3 is ideal for write once read many (WORM) storage. Amazon EFS is for ideal for when you have multiple servers that need access to the same set of files.


---

![](image/Pasted%20image%2020231013110022.png)


An employee at a healthcare facility must store 7 years of patient information that is rarely accessed. Which Amazon S3 storage tier should they use?
A. Amazon S3 Standard 
B. Amazon S3 Glacier Deep Archive 
C. Amazon S3 Standard-Infrequent Access 
D. Amazon S3 Intelligent-Tiering

上
Vault lock featur in s3 clacier deep archive :  no one can delete the file be in before the seven years ends, even the root user can not deleted files


The correct response option is B. Amazon S3 Glacier Deep Archive.
Explanation: Amazon S3 Glacier Deep Archive is the lowest-cost storage class. 
It supports long-term retention and digital preservation for data that might be accessed once or twice in a year. It is designed for customers – particularly in highly regulated industries, such as Financial Services, Healthcare, and Public Sectors – that retain datasets for 7–10 years or longer to meet regulatory compliance requirements.

---

























