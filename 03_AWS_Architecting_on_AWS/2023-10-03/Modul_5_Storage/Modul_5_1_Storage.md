
![](image/Pasted%20image%2020231003081412.png)


![](image/Pasted%20image%2020231003081438.png)

Imagine that your storage team lead meets with you so that they can understand how storage concepts translate to Amazon Web Services (AWS). Here are some questions that they are asking you.
At the end of this module, you will meet with the storage team lead and present some solutions.
# 1 Storage service

The storage team lead asks, “What are some services to consider when looking at block, file, and object storage?”


![](image/Pasted%20image%2020231003081520.png)

Block Storage: 
used it for database 
we'll save them and index them 

File Storage:
they can collaborate or applications

Object storage: 
S3
each object will be saved individually 

There are three types of cloud storage: object, file, and block. Each storage option has a unique combination of performance, durability, cost, and interface.
Block storage – Enterprise applications like databases or enterprise resource planning (ERP) systems often require dedicated, low-latency storage for each host. This storage is similar to direct-attached storage (DAS) or a storage area network (SAN). Block-based cloud storage solutions like Amazon Elastic Block Store (Amazon EBS) are provisioned with each virtual server and offer the ultra-low latency required for high-performance workloads.
File storage – Many applications must access shared files and require a file system. This type of storage is often supported with a Network Attached Storage (NAS) server. File storage solutions like Amazon Elastic File System (Amazon EFS) are ideal for use cases such as large content repositories, development environments, media stores, or user home directories.
Object storage – Applications developed in the cloud need the vast scalability and metadata of object storage. Object storage solutions like Amazon Simple Storage Service (Amazon S3) are ideal for building modern applications. Amazon S3 provides scale and flexibility. You can use it to import existing data stores for analytics, backup, or archive.


---


![](image/Pasted%20image%2020231003081738.png)


S3: for hot data
S3 Glacier for achive data 

AWS has solutions for your block, file, and object storage needs. In this module, you will learn about the following services: 
• Amazon EBS for block storage 
• Amazon EFS and Amazon FSx for file storage
• Amazon S3 and Amazon S3 Glacier for object storage

## 1.1 S3

The storage team lead asks, “How do we choose the right object storage solution for my use case?”

![](image/Pasted%20image%2020231003081826.png)

Amazon S3 is object-level storage. An object includes file data, metadata, and a unique identifier. Object storage does not use a traditional file and folder structure.
Amazon S3 storage tiers are all designed to provide 99.999999999 percent (11 9's) of data durability of objects over a given year. By default, data in Amazon S3 is stored redundantly across multiple facilities and multiple devices in each facility. Amazon S3 can be accessed through the web-based AWS Management Console, programmatically through the API and SDKs, or with third-party solutions (which use the API and SDKs).

With Amazon S3, you can:
• Accelerate innovation – Integrate S3 buckets as storage solutions for static files and rely less on traditional file systems.
• Increase agility – With hosted object storage, you won’t need to expand your storage as the quantity and size of data grows. Individual objects cannot be larger than 5 TB; however, you can store as much total data as you need.
• Reduce cost – Use the variety of storage tiers in Amazon S3 to spend less on infrequently accessed data. Archive data in Amazon S3 for your long-term storage needs.
• Strengthen security – Store your data in Amazon S3 and secure it from unauthorized access with encryption features and access management tools. Amazon S3 maintains compliance programs, such as payment card industry data security standards (PCI-DSS), HIPAA/HITECH, FedRAMP, EU Data Protection Directive, and FISMA. These compliance programs help you to meet regulatory requirements.


![](image/Pasted%20image%2020231003081935.png)


static website :  no interaction with 
Dynamic  website:  with kommunication with back in 


Amazon S3 provides you with flexible, low-cost object storage solutions. Some use cases for Amazon S3 include:
• Backup and restore – You can use Amazon S3 to store and retrieve any amount of data, at any time. You can use Amazon S3 as the durable store for your application data and file-level backup and restore processes. Amazon S3 is designed for 99.999999999 percent durability, or 11 9’s of durability.
• Data lakes for analytics – Run big data analytics, artificial intelligence (AI), machine learning (ML), and high-performance computing (HPC) applications to unlock data insights.
• Media storage and streaming – You can use Amazon S3 with Amazon CloudFront’s edge locations to host videos for on-demand viewing in a secure and scalable way. Video on demand (VOD) streaming means that your video content is stored on a server, and viewers can watch it at any time. You’ll learn more about Amazon CloudFront later in this course.
• Static website – You can use Amazon S3 to host a static website. On a static website, individual webpages include static content. They might also contain client-side scripts. Amazon S3’s object storage makes it easier to manage data access, replications, and data protection for static files.
• Archiving and compliance – Replace your tape with low-cost cloud backup workflows, while maintaining corporate, contractual, and regulatory compliance requirements.

Consider other storage solutions when you:
• Are frequently changing the data • Have block storage requirements

Learn more about how businesses are solving their storage challenges. For more information, see “How AWS Partners Are Utilizing Amazon S3 to Help Customers Solve for Scale” in AWS Partner Network (APN) Blog at https://aws.amazon.com/blogs/apn/how-aws-partners-are-utilizing-amazon-s3-to-help-customers-solve-for-scal


![](image/Pasted%20image%2020231003082152.png)



no folder in S3 bucekt , but you can mimic folder using prefixes 
by default the bucekt ist private. no one can access the bucket but the owner 

Amazon S3 stores data as objects within buckets. An object is composed of a file and any metadata that describes that file. To store an object in Amazon S3, upload the file into a bucket.
When you upload a file, you can set permissions on the object and add metadata. You can have one or more buckets in your account. For each bucket, you control who can create, delete, and list objects in the bucket. Choose the geographical AWS Region where Amazon S3 will store the bucket and its contents. You can access logs for the bucket and its objects. With Amazon S3, you can have up to 100 buckets in each account.
The diagram contains a virtual-hosted–style access URL made from a bucket and an object key. An object key is the unique identifier for an object in a bucket. The combination of a bucket, key, and version ID uniquely identifies each object. Every object can be uniquely addressed through the combination of the web service endpoint, bucket name, key, and optionally, a version.
For example, in the URL https://my-bucket.s3.amazonaws.com/2006-03-01/pup.jpg, my-bucket is the name of the bucket and "2006-03-01/pup.jpg" is the key. The “2006-03-01/” portion of the object key is called the prefix. For more information about creating object key names, see “Creating object key names” in the Amazon Simple Storage Service User Guide at https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-keys.ht


# 2 Securing objects

Think about how physical objects in an office building or home are protected. You have more than one option for how to secure your items:
• Security guards 
• A safe or a locker 
• A key or key card system
• Rules for entry 
• Employees only area
You use some or all of these options depending on the type of objects you are caring for


---


![](image/Pasted%20image%2020231003082422.png)

By default, all Amazon S3 resources — buckets, objects, and related resources (for example, lifecycle configuration and website configuration) — are private. Only the resource owner, an AWS account that created it, can access the resource. The resource owner can grant access permissions to others by writing access policies.
You can make a resource in Amazon S3 public, which allows anyone access. However, most Amazon S3 use cases do not require public access. Amazon S3 usually stores data from other applications. Public access is not recommended for these types of buckets. Amazon S3 includes a block public access feature. This feature acts as an additional layer of protection to prevent accidental exposure of customer data.

The resource owner can provide controlled access to a resource. You can grant access permissions to others by writing access policies.
For more information about Amazon S3 access control, see “Blocking public access to your Amazon S3 storage” in Amazon Simple Storage Service User Guide at https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html.


---



Resource-based policy hast prinpcle attirbue . 
princple 中不能有 regex, 但可以用 ${variable}
![](image/Pasted%20image%2020231003082522.png)

You can create and configure bucket policies to grant permission to your Amazon S3 buckets and objects.
Bucket policies are resource-based policies for your S3 buckets. Access control for your data is based on policies, such as IAM policies, S3 bucket policies, and AWS Organizations service control policies (SCPs).
Use JSON-based access policy language to write your bucket policy. You can use it to add or deny permissions for the objects in your bucket.
In the example, the bucket policy allows any principal to list the bucket and get any object from the bucket. You should consider limiting public access to buckets and objects in this way. Amazon S3 has tools that help you to prevent overly-permissive public buckets.


![](image/Pasted%20image%2020231003082828.png)

resource 的路径
arn
aws: aws, or aws-ch or aws-us
s3: Region: aws aoccunt:filename 

![](image/Pasted%20image%2020231003082934.png)
listBucekt 对应 Resource 中的第一项
GetObject 对应 resource 中 第二项为作用项


![](image/Pasted%20image%2020231003083051.png)

Sometimes you want to make sure that no matter what, a bucket will never see public access. Newly created Amazon S3 buckets and objects are private and protected by default. With Amazon S3 access control, you can stop all access to the bucket from ACLs, bucket polices, and cross-origin resource sharing (CORS) settings.
Public access is granted to buckets and objects through ACLs, bucket policies, or both. To avoid public access to all of your S3 buckets and objects, turn on block all public access at the account level. These settings apply account-wide for all current and future buckets.
You can protect yourself and your organization from information leaks by using S3 Block Public Access settings. Turn it on to prevent your operators from accidentally opening your buckets to the pub


---

![](image/Pasted%20image%2020231003083214.png)


![](image/Pasted%20image%2020231003083513.png)


1 Bucket policy kann not more 20kb 
2 each access point has own acces Point policy  
3 使用 access point 去分割 那些人 可以接触到那些资源

Amazon S3 Access Points simplify managing data access at scale for shared datasets in Amazon S3. S3 Access Points are named network endpoints that you can use to perform S3 object operations, such as GetObject and PutObject. Access points are attached to buckets. Each access point has distinct permissions and network controls that Amazon S3 applies for any request that is made through that access point.
In the example, a finance employee assumes the finance team IAM role and sends a GetObject request to your finance access point. With the access point policy, the finance role can get objects in doc-example-bucket with the prefixes /finance and /tax. The finance role does not have access to your sales and marketing prefixed objects or any other objects in your S3 bucket. The S3 bucket policy allows the finance access point to have access to your bucket.
Each access point enforces a customized access point policy that works in conjunction with the bucket policy attached to the underlying bucket. To restrict Amazon S3 data access to a private network, you can configure an access point to accept requests only from a virtual private cloud (VPC). You can also configure custom block public access settings for each access point.
You can only use access points to perform operations on objects. You can't use access points to perform other Amazon S3 operations, such as modifying or deleting buckets. S3 Access Points work with some, but not all, AWS services and features. For example, you can't configure S3 Cross-Region Replication to operate through an access poin


--- 


![](image/Pasted%20image%2020231003083725.png)


Cryptographic keys are used to encrypt your data at rest. Amazon S3 offers three options for encrypting your objects:
• Server-side encryption (SSE) with Amazon S3-managed keys (SSE-S3) – When you use SSE-S3, each object is encrypted with a unique key. As an additional safeguard, it encrypts the key itself with a primary key that it regularly rotates. Amazon S3 server-side encryption uses 256-bit Advanced Encryption Standard (AES-256) to encrypt your data.
• Server-side encryption with AWS KMS keys stored in AWS Key Management Service (AWS KMS) (SSE-KMS) – KMS keys stored in SSE-KMS are similar to SSE-S3, but with some additional benefits and charges. There are
separate permissions for the use of a KMS key that provides added protection against unauthorized access of your objects in Amazon S3. SSE-KMS also provides you an audit trail that shows when your KMS key was used, and by whom.
• Server-side Encryption with Customer-Provided Keys (SSE-C) – With SSE-C, you manage the encryption keys and Amazon S3 manages the encryption as it writes to disks. Also, Amazon S3 manages decryption when you access your objects.
For more information about server-side encryption, see “Protecting data using server-side encryption” in the Amazon Simple Storage Service User Guide at https://docs.aws.amazon.com/AmazonS3/latest/userguide/serv-side-encryption.html.


EBS 中
encryted value will be 解密 在 physicale host 然后 被给 instance 
![](image/Pasted%20image%2020231003084021.png)



S3
Server side encryption 
s3 中 encryption 发生在 server side 
![](image/Pasted%20image%2020231003084205.png)

sse: server-side encryption

sse-s3: 
s3 will So S3 will generate a data key for each object that needs to be encrypt


sse-kms

sse-c
client side encryption means the data is going to be encrypted before it is uploaded into s3 
s3 提供key, 但是加密要你自己来 


# 3 Storing objects  S3

Think about where you keep important objects in your office or home. There is more than one place to keep each thing.
• At your workplace 
• Another room on the same floor 
• The basement of the same building 
• A different building near yours • A storage unit in another location

You make decisions based on how often you use that object, and that decision can change over time. You choose Amazon S3 storage classes with similar considerations

---

![](image/Pasted%20image%2020231003084622.png)

一般是 
主要的bucket 用 s3 bucket 
第一个backup of  用 s3 standard-IA , 
第二个backup of  用 s3 one zone-IA

Each object in Amazon S3 has a storage class associated with it. All storage classes offer high durability (99.999999999 percent durability).

Choose a class depending on your use case scenario and performance access requirements:
• S3 Standard for general-purpose storage of frequently accessed data. • S3 Standard-Infrequent Access (S3 Standard-IA) for long-lived, but less frequently accessed data.
• S3 One Zone-Infrequent Access (S3 One Zone-IA) for long-lived, less frequently accessed data that can be stored in a single Availability Zone.
• S3 Glacier Instant Retrieval for archive data that is rarely accessed but requires a restore in milliseconds. 
• S3 Glacier Flexible Retrieval for the most flexible retrieval options that balance cost with access times ranging from minutes to hours. Your retrieval options permit you to access all the archives you need, when you need them, for one low storage price. This storage class comes with multiple retrieval options: 
    • Expedited retrievals (restore in 1–5 minutes). 
    • Standard retrievals (restore in 3–5 hours).
    • Bulk retrievals (restore in 5–12 hours). Bulk retrievals are available at no additional charge.
• S3 Glacier Deep Archive for long-term cold storage archive and digital preservation. Your objects can be restored in 12 hours or less.

S3 Intelligent-Tiering is an additional storage class that provides flexibility for data with unknown or changing access patterns. It automates the movement of your objects between storage classes to optimize cost.

S3 on Outposts (not pictured) delivers object storage to your on-premises AWS Outposts environment. Outposts will be discussed later in this course.

For more information about choosing the right storage class based on your use and cost requirements, see “Amazon S3 pricing” at https://aws.amazon.com/s3/pricing/.



---


自动帮你变更 access pattern 
一旦 你开始访问了, 又会便回到 Frequent access tier 
![](image/Pasted%20image%2020231003085200.png)

![](image/Pasted%20image%2020231003085343.png)

Amazon S3 Intelligent-Tiering is the only storage class that delivers automatic storage cost savings when data access patterns change, without performance impact or operational overhead. Your data moves between access tiers as usage patterns change.
When you assign an object to S3 Intelligent-Tiering, it is placed in the Frequent Access tier which has the same storage cost as S3 Standard. Objects not accessed for 30 days are then moved to the Infrequent Access tier where the storage cost is the same as S3 Standard-IA. After 90 days of no access, an object is moved to the Archive Instant Access tier, which has the same cost as S3 Glacier Instant Retrieval.
S3 Intelligent-Tiering is the ideal storage class for data with unknown, changing, or unpredictable access patterns, independent of object size or retention period. You can use S3 Intelligent-Tiering as the default storage class for virtually any workload, especially data lakes, data analytics, new applications, and user-generated content.

---

![](image/Pasted%20image%2020231003085425.png)

Amazon S3 Glacier is a service that gives you extremely-low cost, powerful, and flexible data storage solutions. The storage is purpose-built for your archived data.
Three storage class options help optimize your cost for what you need to retrieve and how fast.
Your data in Amazon S3 Glacier can be encrypted at rest. In addition, Amazon S3 Glacier products offer you a suite of features including compliance, audit logging, and cost management. Those features might not be available to you with a traditional archiving solution.
Like other Amazon S3 storage classes, Amazon S3 Glacier products can scale from gigabytes to exabytes of your data. Amazon S3 Glacier storage classes have 99.999999999 percent durability.
In mathematical terms, 11 nines of durability means that out of 10,000 objects, you might expect to lose one every 10 million years. We asked a large Hollywood studio to run the same Markov model to determine the number of nines for two copies of data on tape. They came back with 5–6 nines. Having six more nines means that the durability of Amazon S3 Glacier is six orders of magnitude more durable than two copies of your data on tape.
For more information, see “Amazon S3 Glacier storage classes” at https://aws.amazon.com/glacier/. 


---

![](image/Pasted%20image%2020231003085557.png)

upload the same file again, help your visioning this file 

hacker of version and multiple copy: more cost if version by used  
versioning feature ist by default 

Object lock: WORM, no one can delete it and 

object key is the the only sole factor that s3 will consider whether the same file ist uploaded . 
如果 versioning freature 没有被开启,  文件会被覆盖, 只剩下新的文件 
如果 versioning freature 被开启.  新的 version 会被 产生, 只要 object key (文件名 文件 extension 加 路径 一样 ) 一样 


Amazon S3 uses object storage. Thus, if you want to change a part of a file, you must make the change and then re-upload the entire modified file.
Buckets that use versioning can help you recover objects from accidental deletion or overwrite: 
• If you delete an object, instead of removing it permanently, Amazon S3 inserts a delete marker, which becomes the current object version.
• If you overwrite an object, it results in a new object version in the bucket. When S3 Versioning is turned on, you can restore the previous version of the object to correct the mistake.

The diagram shows a bucket that uses versioning with an object that has three versions. The current version ID is 131313. You can restore to the previous version ID of 121212. To delete versioned objects permanently, you must use DELETE Object versionId. This example deletes version ID 131313.
You can use S3 Object Lock for data retention or protection. By using the write once, read many (WORM) model, you can prevent accidental overwrites or deletions within Amazon S3 storage. Use retention periods for locking an object for a fixed period of time, or a legal hold for a lock until explicitly removed.

For more information about versioning, see “Using versioning in S3 buckets” at https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html.
For more information about S3 Object Lock, see “Using S3 Object Lock” at https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html.


---
expiration action 

![](image/Pasted%20image%2020231003090444.png)

lifecycle polices : user define  多少天后 变
intelligent tier : s3 决定多少天后 变. 

can hat mulitple lifecycle polices in the same bucket 
lifecycle polices can befinded on the bucket level, 也可定义 subnet of prefix 有这个 policy

同样的 bucket 不同的object 可以拥有不同 的 storage class  

With S3 Lifecycle policies, you can delete or move objects based on age. You should automate the lifecycle of your data that is stored in Amazon S3. Using S3 Lifecycle policies, you can have data cycled at regular intervals between different Amazon S3 storage types.
In this way, you reduce your overall cost because you are paying less for data as it becomes less important with time. In addition to being able to set lifecycle rules per object, you can also set lifecycle rules per bucket.
Amazon S3 supports a waterfall model for transitioning between storage classes. Lifecycle configuration automatically changes data storage tiers.

For more information about transitioning objects and managing your storage lifecycle by using S3 Lifecycle, see the following in the Amazon Simple Storage Service User Guide: 
• “Transitioning objects using Amazon S3 Lifecycle” at https://docs.aws.amazon.com/AmazonS3/latest/userguide/lifecycle-transition-general-considerations.html
• “Managing your storage lifecycle” at https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html


----

![](image/Pasted%20image%2020231003091251.png)

![](image/Pasted%20image%2020231003091533.png)

With Amazon S3, customers get a high level of availability and durability for their data in every AWS Region. Data that is stored in any Amazon S3 storage class is stored across a minimum of three Availability Zones. Each is separated by miles within a Region. For this reason, many AWS customers choose Amazon S3 to store their business-critical and application-critical data. The only exception is S3 One Zone-IA, which, as its name indicates, is a one-zone service.
Replication can help you do the following tasks:
• Replicate objects while retaining metadata – Ensure that your replica is identical to the source object if it is necessary.
• Replicate objects into different storage classes – Use replication to directly put objects into S3 Glacier Flexible Retrieval, S3 Glacier Deep Archive, or another storage class in the destination buckets.
• Maintain object copies under different ownership – Tell Amazon S3 to change replica ownership to the AWS account that owns the destination bucket.
• Keep objects stored over multiple AWS Regions – Meet compliance requirements by replicating data to another AWS Region.

First, identify the source bucket and data set. Then, select one or more destination buckets. You can use Same-Region Replication (SRR) for things like log aggregation or replicating between development and production accounts. If you must meet compliance or other requirements to have data in more than one geography, choose Cross-Region Replication.

Optionally, you can change the destination ownership of objects with an owner override. You might do this, for example, to restrict access to object replicas.
Learn how to meet business data resiliency. For more information, see “How to meet business data resiliency with Amazon S3 cross-Region replication” in the AWS Public Sector Blog at https://aws.amazon.com/blogs/publicsector/how-to-meet-business-data-resiliency-s3-cross-region-replication/.

To learn more about replication, see “Amazon S3 Replication” at https://aws.amazon.com/s3/features/replication/.


## 3.1 Addtional Amazon s3 features

Earlier you were provided some examples that related to securing and storing objects. Next, think about how you might place objects into your S3 buckets. You want to be efficient with how you upload the object and use features that help you manage what happens when the object is there.

Consider the following questions:
• What if you need to upload large objects? How do you upload them, and how does it work? 
• How can you increase the speed at which objects are uploaded to AWS Regions that are not close to you? • Can actions be automated based on events like when you upload an object?

---


if file ist more than more 5 gb 
the s3 will take the large file , then cut it off into segments and then upload it paraellel , using multiport , 不同的 request 
如果 其中一个失败了 -> 需要重听 

![](image/Pasted%20image%2020231003091545.png)


With a multipart upload, you can consistently upload large objects in manageable parts. This process involves three steps: • Initiating the upload • Uploading the object parts 
• Completing the multipart upload
When the multipart upload request is completed, Amazon S3 will recreate the full object from the individual pieces.

Improve the upload process of larger objects with the following features:
• Improved throughput – You can upload parts in parallel to improve throughput. • Quick recovery from any network issues – Smaller part sizes minimize the impact of restarting a failed upload due to a network error.
• Pausing and resuming object uploads – You can upload object parts over time. When you have initiated a multipart upload, there is no expiration. You must explicitly complete or cancel the multipart upload.
• Beginning an upload before you know the final object size – You can upload an object as you are creating it. 
• Uploading large objects – Using the multipart upload API, you can upload large objects, up to 5 TB.

Note: You cannot perform multipart uploads manually by using the console.

or more information about multipart uploads, see “Uploading and copying objects using multipart upload” in the Amazon Simple Storage Service User Guide at https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html.

----

使用 edge location , caching, 然后加速 

![](image/Pasted%20image%2020231003091814.png)

Amazon S3 Transfer Acceleration uses AWS globally distributed edge locations to facilitate fast data transfer into an S3 bucket. The data is routed to Amazon S3 over an optimized network path.

Use Transfer Acceleration when you: 
• Have customers all over the world who upload to a centralized bucket 
• Transfer gigabytes or terabytes of data across continents on a regular basis 
• Underutilize the available bandwidth when uploading to Amazon S3 over the internet

S3 Transfer Acceleration shortens the distance between client applications and AWS servers that acknowledge PUTS and GETS to Amazon S3. It uses a global network of hundreds of edge locations. AWS automatically routes your uploads and downloads through the closest edge locations to your application.

You can use the Amazon S3 Transfer Acceleration Speed Comparison tool to compare accelerated and non-accelerated upload speeds across Amazon S3 Regions.
For more information about Transfer Acceleration, see “S3 Transfer Acceleration” at https://aws.amazon.com/s3/transfer-acceleration/.

Learn more about the speed comparison tool. For more information, see “Using the Amazon S3 Transfer Acceleration Speed Comparison tool” in the Amazon Simple Storage Service User Guide at https://docs.aws.amazon.com/AmazonS3/latest/userguide/transfer-acceleration-speed-comparison.html.


![](image/Pasted%20image%2020231003092047.png)


![](image/Pasted%20image%2020231003092115.png)


---


![](image/Pasted%20image%2020231003092224.png)



![](image/Pasted%20image%2020231003092355.png)

With Amazon S3 Event Notifications, you can receive notifications when certain object events happen in your bucket. Event-driven models like this one mean that you no longer need to build or maintain server-based polling infrastructure to check for object changes. You also don’t pay for idle time of that infrastructure when there are no changes to process.
Amazon S3 can send event notification messages to the following destinations: 
• Amazon Simple Notification Service (Amazon SNS) topics 
• Amazon Simple Queue Service (Amazon SQS) queues 
• AWS Lambda functions


You specify the Amazon Resource Name (ARN) value of these destinations in the notification configuration.

In the example, you have a JPEG image uploaded to the images bucket that your website uses. Your website needs to be able to show smaller thumbnail preview images of each uploaded file. When the image object is added to the S3 bucket, an event notification is sent to invoke a series of AWS Lambda functions. The output of your Lambda functions is a smaller version of the original JPEG image and puts the object in your thumbnails bucket. S3 Event Notifications manage the activity in the bucket for you and automate the creation of your thumbnail.

For more information about Amazon S3 Event Notifications, see “Reliable event processing with Amazon S3 Event Notifications” on the AWS Storage Blog at https://aws.amazon.com/blogs/storage/reliable-event-processing-with-amazon-s3-event-notifications/.


---

![](image/Pasted%20image%2020231003092538.png)


Cost is an important part of choosing the right Amazon S3 storage solution.

Some of the Amazon S3 cost factors to consider include: 
• Storage – Per-gigabyte cost to hold your objects. You pay for storing objects in your S3 buckets. The rate that you’re charged depends on your objects' size, how long you stored the objects during the month, and the storage class. You incur per-request ingest charges when using PUT, COPY, or lifecycle rules to move data into any S3 storage class.
• Requests and retrievals – The number of API calls: PUT and GET requests. You pay for requests that are made against your S3 buckets and objects. S3 request costs are based on the request type, and are charged on the quantity of requests. When you use the Amazon S3 console to browse your storage, you incur charges for GET, LIST, and other requests that are made to facilitate browsing.
• Data transfer – Usually no transfer fee for data-in from the internet and, depending on the requester location and medium of data transfer, different charges for data-out.
• Management and analytics – You pay for the storage management features and analytics that are activated on your account’s buckets. These features are not discussed in detail in this course.

S3 Replication and S3 Versioning can have a big impact on your AWS bill. These services both create multiple copies of your objects, and you pay for each PUT request in addition to the storage tier charge. S3 Cross-Region Replication also requires data transfer between AWS Regions.

For more information about potential costs in Amazon S3, use the “AWS Pricing Calculator” at https://calculator.aws/#/.
For more information, see “Amazon S3 pricing” at https://aws.amazon.com/s3/pricing/. 


# 4 Shared file systems overview

The storage team lead asks, “What are some file-based options for building secure and scalable storage in the AWS Cloud?”


![](image/Pasted%20image%2020231003092644.png)


How do you handle an application that is running on multiple instances and must use the same file system?

Amazon EBS provides block storage, so it could be used as the underlying storage component of a self-managed file storage solution. Amazon EBS supports Multi-Attach for up to 16 Linux EC2 instance attachments, but it is a very specialized use case. In most cases, an EBS volume is attached to one Amazon Elastic Compute Cloud (Amazon EC2) instance. This limit makes it difficult to have the scalability, availability, and affordability of a fully managed file storage solution.

Amazon S3 is an option, but what if you need the performance and read/write capacity of a network file system? S3 is an object store system, not a block store, so changes overwrite entire files, not blocks of characters within files.

For high throughput changes to files of varying sizes, a file system will be superior to an object store system. Amazon Elastic File System (Amazon EFS) and Amazon FSx are ideal for this use case.
Using a fully managed cloud file storage solution removes complexities, reduces costs, and simplifies management. You will continue to learn about shared file systems in this section of the module.

Learn about the considerations and limitations of multi-attach. For more information, see “Attach a volume to multiple instances with Amazon EBS Multi-Attach” in the Amazon Elastic Compute Cloud User Guide for Linux Instances at https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes-multi.html

## 4.1 EFS (only for Linux)

security gourp should alow the mount target via  protocal 2049  nfsv4
![](image/Pasted%20image%2020231003092745.png)



Amazon EFS provides a scalable, elastic file system for Linux-based workloads for use with AWS Cloud services and on-premises resources.
You can create a file system, mount it on an Amazon EC2 instance, and then read and write data to and from your file system. You can mount an Amazon EFS file system in your VPC through the Network File System (NFS) versions 4.0 and 4.1 (NFSv4) protocol. You do not need to take action to expand the file system as your storage needs grow.
EC2 instances in your VPC can access Amazon EFS file systems concurrently, so applications that scale beyond a single connection can access a file system.

Availability and durability refer to the redundancy with which an Amazon EFS file system stores data within an AWS Region. You have the following choices for your file system's availability and durability: 
• Choosing a Standard storage class creates a file system that stores file system data and metadata redundantly across all Availability Zones within an AWS Region. You can also create mount targets in each Availability Zone in the AWS Region. Standard storage classes offer the highest levels of availability and durability.
• Choosing a One Zone storage class creates a file system that stores file system data and metadata redundantly within a single Availability Zone. File systems that use One Zone storage classes can have only a single mount target. This mount target is located in the Availability Zone in which the file system is created.

In this example, a VPC uses Amazon EFS standard storage class. The VPC has three private subnets, each in a different Availability Zone. With standard storage class, each subnet can have its own mount target. The EC2 instances in each subnet can access the file system through the mount target located in its Availability Zone.


---

File locking: 

![](image/Pasted%20image%2020231003093035.png)

efs can shrink or grow based on data 

Amazon EFS provides a shared, persistent layer that provides stateful applications the ability to elastically scale up and down. Examples include DevOps, web serving, web content systems, media processing, machine learning, analytics, search index, and stateful microservices applications. Amazon EFS can support a petabyte-scale file system, and the throughput of the file system also scales with the capacity of the file system.

Because Amazon EFS is serverless, you don’t need to provision or manage the infrastructure or capacity. Amazon EFS file systems can be shared with up to tens of thousands of concurrent clients, regardless of the type. These clients could be traditional EC2 instances or containers that run in one of your self-managed clusters. They might run in one of the AWS container services: Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS), and AWS Fargate. Or they might run in a serverless function that runs in Lambda.

Use Amazon EFS to lower your total cost of ownership for shared file storage. Choose Amazon EFS One Zone for data that does not require replication across multiple Availability Zones and save on storage costs. Amazon EFS Standard-Infrequent Access (EFS Standard-IA) and Amazon EFS One Zone-Infrequent Access (EFS One Zone-IA) are storage classes for files not accessed every day. They provide cost-optimized price and performance for these files.

Use Amazon EFS scaling and automation to save on management costs, and pay only for what you use.
For more information about Amazon EFS use cases, see “File Systems for Enterprise Applications” at https://aws.amazon.com/efs/enterprise-applications/

## 4.2 FSx (for Windows File Server)

![](image/Pasted%20image%2020231003093135.png)

can be mounted to server 
SMB: server managment block , mount the fsx with several instance 
nfs: use it in client comunicated client  

With Amazon FSx, you can quickly launch and run feature-rich and high-performing file systems. The service provides you with four file systems to choose from. This choice is based on your familiarity with a given file system or matching the feature sets, performance profiles, and data management capabilities to your needs.
FSx for Windows File Server provides fully managed Microsoft Windows file servers that are backed by a native Windows file system. Built on Windows Server, Amazon FSx delivers a wide range of administrative features such as data deduplication, end-user file restore, and Microsoft Active Directory.
FSx for Lustre is a fully managed service that provides high-performance, cost-effective storage. FSx for Lustre is compatible with the most popular Linux-based AMIs. They include Amazon Linux, Amazon Linux 2, Red Hat Enterprise Linux (RHEL), CentOS, SUSE Linux, and Ubuntu.
FSx for NetApp ONTAP provides fully managed shared storage in the AWS Cloud with the popular data access and management capabilities of ONTAP.
FSx for OpenZFS provides fully managed shared file storage built on the OpenZFS file system. It is powered by the AWS Graviton family of processors, and accessible through the NFS protocol (v3, v4, v4.1, v4.2).
For more information about Amazon FSx file system options, see “Choosing an Amazon FSx File System” at https://aws.amazon.com/fsx/when-to-choose-fsx/.



# 5 Dara migration tools 

![](image/Pasted%20image%2020231003093402.png)

The storage team lead asks, “How can we move lots of data to the cloud in a relatively short time period?”
The storage team must plan data migrations from on-premises data centers to the AWS Cloud. The company wants your advice to choose the right tools


---


![](image/Pasted%20image%2020231003093428.png)

Before selecting which tool to use, you should know the following information: 
• Where you are moving data 
• For what use cases 
• The types of data that you are moving 
• The network resources available

AWS offers a wide variety of services and AWS Partner tools to help you migrate your datasets (files, databases, machine images, block volumes, or tape backups). In this module, you will learn about the following tools:
• AWS Storage Gateway simplifies on-premises adoption of AWS storage. You can use Storage Gateway to seamlessly connect and extend your on-premises applications to AWS storage. It supports multiple file transfer protocols: Server Message Block (SMB), Network File System (NFS), and Internet Small Computer Systems Interface (iSCSI).
• AWS DataSync is a data transfer service that facilitates moving data between on-premises storage and Amazon EFS, Amazon FSx, and Amazon S3.
• AWS Transfer Family permits the transfer of files into and out of Amazon S3 or Amazon Elastic File System (EFS) over the following protocols. (The Transfer Family will not be covered in this course.)
    • Secure Shell File Transfer Protocol (SFTP)
    • File Transfer Protocol Secure (FTPS) 
    • File Transfer Protocol (FTP) 
    • Applicability Statement 2 (AS2)
    • AWS Snow Family is a group of edge computing, data migration, or edge storage devices that are designed for secure, physical transport.

Learn more about on-premises AWS storage services. For more information, see “Comparing your on-premises storage patterns with AWS Storage services” in the AWS Storage Blog at https://aws.amazon.com/blogs/storage/comparing-your-on-premises-storage-patterns-with-aws-storage-services/.



---



![](image/Pasted%20image%2020231003093641.png)

AWS Storage Gateway connects an on-premises software appliance with cloud-based storage. It provides seamless integration with data security features between your on-premises IT environment and the AWS storage infrastructure.
You can use the service to store data in the AWS Cloud for scalable and cost-effective storage that helps maintain data security. Storage Gateway offers file-based, volume-based, and tape-based storage solutions, which are integrated with IAM, AWS KMS, AWS CloudTrail, and Amazon CloudWatch.


---

![](image/Pasted%20image%2020231003093926.png)

![](image/Pasted%20image%2020231003094021.png)

smb 
fns 
每一个需要配一个独立的  file gateway 
后两个用 isito 


Choose a Storage Gateway type that is the best fit for your workload.
Amazon S3 File Gateway presents a file interface that you can use to store files as objects in Amazon S3. You use the industry-standard NFS and SMB file protocols. Access your files through NFS and SMB from your data center or Amazon EC2, or access those files as objects directly in Amazon S3.

Amazon FSx File Gateway provides fast, low-latency, on-premises access to fully managed, highly reliable, and scalable file shares in Amazon FSx for Windows File Server. It uses the industry-standard SMB protocol. You can store and access file data in Amazon FSx with Microsoft Windows features, including full New Technology File System (NTFS) support, shadow copies, and ACLs.

Tape Gateway presents an iSCSI-based virtual tape library (VTL) of virtual tape drives and a virtual media changer to your on-premises backup application. Tape Gateway stores your virtual tapes in Amazon S3 and creates new ones automatically, which simplifies management and your transition to AWS.

Volume Gateway presents block storage volumes of your applications by using the iSCSI protocol. You can asynchronously back up data that is written to these volumes as point-in-time snapshots of your volumes. Then, you can store it in the cloud as Amazon EBS snapshots. You can back up your on-premises Volume Gateway volumes by using the service’s snapshot scheduler or by using the AWS Backup service.



## 5.1 两种 传输形式的区别 Storage Gateway and DataSync

![](image/Pasted%20image%2020231003094052.png)

The Storage Gateway Appliance supports the following protocols to connect to your local data: • NFS or SMB for files 
• iSCSI for volumes 
• iSCSI VTL for tapes

Your storage gateway appliance runs in one of four modes: Amazon S3 File Gateway, Amazon FSx File Gateway, Tape Gateway, or Volume Gateway.
Data that is moved to AWS by using Storage Gateway can be sent to the following destinations through the Storage Gateway managed service: 
• Amazon S3 (Amazon S3 File Gateway, Tape Gateway)
• Amazon S3 Glacier (Amazon S3 File Gateway, Tape Gateway) 
• Amazon FSx for Windows File Server (Amazon FSx File Gateway)
• Amazon EBS (Volume Gateway)

AWS Backup can be used to schedule volume snapshots with Volume Gateway.

---


![](image/Pasted%20image%2020231003094122.png)


Manual tasks that are related to data transfers can slow down migrations and burden IT operations. DataSync facilitates moving large amounts of data between on-premises storage and Amazon EFS, Amazon FSx, and Amazon S3. By default, data is encrypted in transit by using TLS 1.2. DataSync automatically handles scripting copy jobs, scheduling and monitoring transfers, validating data, and optimizing network usage.
Reduce on-premises storage infrastructure by shifting SMB-based data stores and content repositories from file servers and NAS arrays to Amazon S3 and Amazon EFS for analytics.
DataSync deploys as a single software agent that can connect to multiple shared file systems and run multiple tasks. The software agent is typically deployed on premises through a virtual machine to handle the transfer of data over the wide area network (WAN) to AWS. On the AWS side, the agent connects to the DataSync service infrastructure. Because DataSync is a service, there is no infrastructure for customers to set up or maintain in the cloud. DataSync configuration is managed directly from the console.

## 5.2 Offline data migration 



![](image/Pasted%20image%2020231003094431.png)

![](image/Pasted%20image%2020231003094638.png)

snowball  上传速率更大 

AWS Snowcone is ruggedized, secure, and purpose-built for use outside of a traditional data center. Its small size makes it a perfect fit for tight spaces or where portability is a necessity and network connectivity is unreliable. For more information, see “AWS Snowcone” at https://aws.amazon.com/snowcone/.
Snowball Edge is a petabyte-scale data transport option that doesn’t require you to write code or purchase hardware to transfer data. All that you need to do is create a job in the console, and a Snowball appliance will be shipped to you. Attach the appliance into your local network and transfer the files directly onto it. When the device is ready to be returned, the E Ink shipping label will automatically update the return address. Thus, it ensures that the device is delivered to the correct AWS facility. For more information, see “AWS Snowball FAQs” at https://aws.amazon.com/snowball/faqs/.
Snowball Edge Optimized is ideal for edge processing use cases that require additional computing, memory, and storage power in remote, disconnected, or harsh environments. For more information, see “AWS Snowball Edge Specifications” at https://docs.aws.amazon.com/snowball/latest/developer-guide/specifications.htm

# 6 Review


![](image/Pasted%20image%2020231003094714.png)

Imagine that you are now ready to talk to the storage team lead and present solutions that meet their architectural needs.
Your answers should include the following solutions: 
• Use Amazon EBS for block-level storage. Amazon S3 and Amazon S3 Glacier have object-level storage options to review. For file-level storage, choose Amazon EFS or Amazon FSx.
• Review the Amazon S3 storage classes. Think about the objects that you are storing and how often they will be accessed. Use that information to choose a cost-effective solution. Consider using Amazon S3 Glacier for long-term archive data.
• Amazon EFS is a quick, straightforward, and scalable file storage solution that supports the NFS protocol. For more specialized solutions, learn more about the Amazon FSx family of services.
• To move data from one source to another destination, use AWS DataSync. For hybrid storage solutions, use AWS Storage Gateway. For an offline way to move data from on-premises to AWS Cloud destinations, use the AWS Snow Family


![](image/Pasted%20image%2020231020114020.png)


# 7 Capstone Architecture

![](image/Pasted%20image%2020231003094749.png)

At the end of this course is a Capstone Lab project. You will be provided a scenario and asked to build an architecture based on project data, best practices, and the Well-Architected Framework


![](image/Pasted%20image%2020231020114111.png)

In this module, you explored multiple storage solutions. You are now able to build the following for the capstone project: 
• A shared file storage system for your WordPress application that uses Amazon EFS Standard
This solution automatically creates one EFS mount target for you in each Availability Zone. The WordPress installation directory is placed on the EFS mount so that multiple EC2 instances can read it. If one instance fails and is replaced, the files already exist in an accessible and redundant file share.

The WordPress website also requires you to build a database to use for the three-tier architecture. You should think about what options there are in AWS for database services. You will explore this topic in the next module.

For accessibility: Partial selection of capstone architecture with one VPC in one Region. Two Availability Zones are shown. Each has a public subnet, app subnet, and database subnet. An internet gateway is placed at the edge of the VPC. Each Availability Zone has a NAT gateway in a public subnet. App servers and an EFS mount target are placed in each app subnet. An Amazon EFS file system is placed in the VPC but is connected to EFS mount targets in each app subnet. App servers communicate with the EFS mount targets in their own subnets to reach the EFS file system. App servers send requests to the public internet through a NAT gateway in their Availability Zone. End description.


# 8 Know Ledge


d

![](image/Pasted%20image%2020231003094804.png)

The answer is D, Cross-Region Replication.

S3 Cross-Region Replication (CRR) is used to copy objects across Amazon S3 buckets in different AWS Regions. CRR can help you do the following tasks: 
• Meet compliance requirements – Although Amazon S3 stores your data across multiple geographically distant Availability Zones by default, compliance requirements might dictate that you store data at greater distances. To satisfy these requirements, use Cross-Region Replication to replicate data between distant AWS Regions.
• Minimize latency – Imagine that your customers are in two geographic locations. You can minimize latency in accessing objects by maintaining object copies in AWS Regions that are geographically closer to your users.
• Increase operational efficiency – If you have compute clusters in two different AWS Regions that analyze the same set of objects, you might choose to maintain object copies in those Regions.


---

b

![](image/Pasted%20image%2020231003094822.png)

The answer is B, event notification.
With Amazon S3 Event Notifications, you can receive notifications when certain object events happen in your bucket. These notifications can invoke actions in other AWS services like AWS Lambda.
For more information about Amazon S3 Event Notifications, see “Reliable event processing with Amazon S3 Event Notifications” in the AWS Storage Blog at https://aws.amazon.com/blogs/storage/reliable-event-processing-with-amazon-s3-event-notifications/.



----
d

![](image/Pasted%20image%2020231003094849.png)


The answer is D, Amazon EFS.

Other file sharing systems are available to choose from like Amazon FSx for Lustre or Amazon FSx for OpenZFS. However, neither of these solutions is presented as a possible answer. Amazon EFS presents a scalable file system that can be mounted with the Network File System (NFS) protocol by multiple Linux EC2 instances.

AWS Storage Gateway supports hybrid environments, which is not mentioned here. FSx for Windows File Server would permit a Linux application to mount the file system through Server Message Block (SMB). However, it can be a complicated solution to implement. Amazon S3 is an object storage solution, and it does not natively present you with a mountable file system.



------

c: for server , when it 
b
e



![](image/Pasted%20image%2020231003094916.png)

The correct answer is B, C, and E: Tape Gateway, Volume Gateway, and File Gateway. A fourth mode is also available for Amazon FSx File Gateway


