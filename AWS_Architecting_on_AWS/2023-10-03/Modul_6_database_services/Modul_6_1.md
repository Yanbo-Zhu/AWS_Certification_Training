

![](image/Pasted%20image%2020231003100158.png)


![](image/Pasted%20image%2020231003100244.png)


![](image/Pasted%20image%2020231003100324.png)

Imagine that your database services manager meets with you to discuss how to manage databases in the cloud. Here are some questions that they are asking.
At the end of this module, you meet with the database services manager and present some solutions


# 1 AWS Database services 
The database services manager asks, “What are the AWS database solutions?”
The database team is beginning to investigate opportunities for running databases in the cloud. The company wants you to identify which AWS database solutions they should consider.



![](image/Pasted%20image%2020231003100358.png)

AWS database engines are purpose-built and include relational, key-value, document, in-memory, graph, time series, wide-column, and ledger databases. You’ll learn how to pick the right database for your needs.
For more information, see “AWS Cloud Databases” at https://aws.amazon.com/products/databases/.


![](image/Pasted%20image%2020231003100421.png)


Relational sql databases 
- schema ist fixed. neede column and rows 

Unrelational database 
- document: use json 

transactional database

analytics processing 


For decades, the predominant data model that was used for application development was the relational data model. Relational databases such as Oracle, IBM DB2, SQL Server, MySQL, and PostgreSQL used this model. It wasn’t until the mid-to-late 2000s that other data models began to gain significant adoption and usage. To differentiate and categorize these new classes of databases and data models, the term NoSQL was coined. Often the term NoSQL is used interchangeably with nonrelational.
A relational database is a collection of data items with predefined relationships between them. These items are organized as a set of tables with columns and rows. Each column in a table holds a certain kind of data, and a field stores the actual value of an attribute. The rows in the table represent a collection of related values of one object or entity. This data can be accessed in many different ways without reorganizing the database tables themselves.
This module focuses on two structured query language (SQL) databases services, Amazon RDS and Amazon Aurora.
NoSQL is a term that is used to describe nonrelational database systems that are highly available, scalable, and optimized for high performance. Instead of the relational model, NoSQL databases use alternative models for data management, such as key-value pairs or document storage.
This module focuses on two NoSQL databases services, Amazon DynamoDB and Amazon ElastiCache.
For more information about relational databases, see “What is a Relational Database?” at https://aws.amazon.com/relational-database/. For more information about nonrelational databases, see “What is NoSQL?” at https://aws.amazon.com/nosql/.


----



![](image/Pasted%20image%2020231003100836.png)

Though many types of databases exist with varying features, this table shows some of the differences between SQL (relational) and NoSQL (nonrelational) databases.


--- 

![](image/Pasted%20image%2020231003100916.png)

When building resources in the cloud, consider the level of control that you need and the resources that you have for managing that resource.
For example, when running a database in the cloud, you can install a database on an Amazon Elastic Compute Cloud (Amazon EC2) instance. Or you can choose a managed database option such as Amazon RDS.
• Installing a database on an EC2 instance gives you complete control over all aspects of the database except the hardware. The trade-off is that this increased amount of control requires more resources and expertise to manage.
• Using a managed database service removes the undifferentiated work of managing your databases.
Databases that AWS manages provide systems for high availability, scalability, and backups. You can choose to use scaling, high availability, database backups, database software patches, database software installs, and operating system (OS) patches. In general, you are responsible only for optimizing your applications to make sure that the database layer works as well as possible with your application

# 2 Aamazon RDS

The database services manager asks, “How can we more efficiently manage our relational databases in the cloud?”
The database team has relational databases and are considering Amazon RDS. The company wants you to explain the benefits of running a database in a managed service and examine the features of Amazon RDS.


![](image/Pasted%20image%2020231003101050.png)

Amazon RDS is a web service that helps you to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity, while managing time-consuming database administration tasks. By using Amazon RDS, you can focus on your applications and business. Amazon RDS provides you with six familiar database engines to choose from, including Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and Microsoft SQL Server. Therefore, most of the code, applications, and tools that you already use with your existing databases can be used with Amazon RDS.
Amazon RDS automatically patches the database software and backs up your database. It stores the backups for a user-defined retention period and provides point-in-time recovery. You benefit from the flexibility of scaling the compute resources or storage capacity associated with your relational DB instance with a single API call.


---
![](image/Pasted%20image%2020231020114901.png)


Amazon RDS is available on six database engines, which optimize for memory, performance, or I/O. 
The database engines include the following: • Amazon Aurora • PostgreSQL • MySQL • MariaDB • Oracle Database • SQL Server


---


![](image/Pasted%20image%2020231003101238.png)


使用 url  比起使用 ip addresse 有好处 
当 一个 database 的链接失效的时候, aws 会变化 url , 转到 另一个 db, 把信息传到那边去 
cname : url of databse 


Amazon RDS Multi-AZ deployments provide enhanced availability and durability for database (DB) instances, which makes them a natural fit for production database workloads. When you provision a Multi-AZ DB instance, Amazon RDS synchronously replicates the data to a standby instance in a different Availability Zone.
You can modify your environment from Single-AZ to Multi-AZ at any time. Each Availability Zone runs on its own physically distinct, independent infrastructure and is engineered to be highly reliable.


--- 


![](image/Pasted%20image%2020231003101430.png)

In case of the primary instance failure, Amazon RDS performs an automatic failover to the standby instance.
In this example, two EC2 instances in separate Availability Zones are connected to the primary database in one Availability Zone. A standby database is hosted in the other Availability Zone. When the primary database fails, Amazon RDS promotes the secondary database to primary. Because it assumes the primary databases endpoint, the EC2 instances can resume traffic with the new primary database. Meanwhile, a new standby database is created in the other Availability Zone.


---



![](image/Pasted%20image%2020231003101704.png)


With Amazon RDS, you can create read replicas of your database. Amazon automatically keeps them in sync with the primary DB instance. Read replicas are available in Amazon RDS for Aurora, MySQL, MariaDB, PostgreSQL, Oracle, and Microsoft SQL Server.

Read replicas can help you do the following tasks: 
• Relieve pressure on your primary node with additional read capacity. 
• Bring data close to your applications in different AWS Regions. 
• Promote a read replica to a standalone instance as a disaster recovery (DR) solution if the primary DB instance fails.

You can add read replicas to handle read workloads so that your primary database doesn’t become overloaded with read requests. Depending on the database engine, you can also place your read replica in a different Region from your primary database. This placement gives you the ability to have a read replica closer to a particular location.

You can configure a source database as Multi-AZ for high availability and create a read replica in Single-AZ for read scalability. With Amazon RDS for MySQL and MariaDB, you can also set the read replica as Multi-AZ, and as a DR target. When you promote the read replica to be a standalone database, it will be replicated to multiple Availability Zones.

For more information about read replicas, see “Working with DB instance read replicas” in the Amazon Relational Database Service (RDS) User Guide at https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html#USER_ReadRepl.PostgreSQ L.

**For Accessibility: Two instances in the application tier connect to a primary database instance in the database tier. This database can perform read/write operations. Amazon RDS uses asynchronous replication to create a read replica of this database. A third instance in the application tier connects to the read replica, which can only perform read operations. End Description

---

kms: key manage service 
![](image/Pasted%20image%2020231020115139.png)

Amazon RDS provides encryption of data at rest by using the AWS Key Management Service (AWS KMS). AWS KMS is a managed service that provides the ability to create and manage encryption keys and then encrypt and decrypt your data with those keys. All of these keys are tied to your AWS account, and you fully managed them. AWS KMS provides an additional layer of protection against unauthorized access to the underlying storage of your Amazon RDS instance. AWS KMS uses industry-standard AES-256 encryption to protect data that is stored on the underlying host that your Amazon RDS instance is running on


---

you're stealing horizontally

![](image/Pasted%20image%2020231003101832.png)




## 2.1 Amazon Aurora 


![](image/Pasted%20image%2020231020115200.png)

Amazon Aurora is an enterprise-class relational database. It is compatible with MySQL and PostgreSQL relational databases. It is up to five times faster than standard MySQL databases and up to three times faster than standard PostgreSQL databases. Aurora helps to reduce your database costs by reducing unnecessary I/O operations, while ensuring that your database resources remain reliable and available. Consider Aurora if your workloads require high availability. It replicates six copies of your data across three Availability Zones and continuously backs up your data to Amazon Simple Storage Service (Amazon S3).
Aurora supports network isolation, encryption at rest and in transit, and compliance and assurance programs. Aurora is managed by Amazon RDS, so it requires no server provisioning, software patching, setup, configuration, or backups.


---


![](image/Pasted%20image%2020231003102218.png)

An Amazon Aurora DB cluster consists of one or more DB instances and a cluster volume that manages the data for those DB instances. The instances perform the compute functions of the database while the cluster volume stores the actual data.
Aurora offers two instance types: 
• Primary instance – Supports read and write operations and performs all the data modifications to the cluster volume. Each Aurora DB cluster has one primary instance.
• Aurora replica – Supports read operations only. Each Aurora DB cluster can have up to 15 Aurora replicas in addition to the primary instance. Multiple Aurora replicas distribute the read workload. You can increase availability by locating Aurora replicas in separate Availability Zones. You can have a read replica in the same Region as the primary instance.

An Aurora cluster volume is a virtual database storage volume that spans multiple Availability Zones. Each Availability Zone has a copy of the DB cluster data. Storage in the cluster volume is replicated across hundreds of storage nodes. Aurora presents the cluster volume as a single, logical volume to the primary instance and to Aurora replicas in the DB cluster. Write operations to the cluster volume are often available to Aurora replicas in less than 100 milliseconds.


---


![](image/Pasted%20image%2020231003103236.png)

Aurora Serverless v2 is an on-demand, auto scaling configuration for Amazon Aurora. Aurora Serverless v2 helps to automate the processes of monitoring the workload and adjusting the capacity for your databases. Capacity is adjusted automatically based on application demand. You're charged only for the resources that your DB clusters consume. Thus, Aurora Serverless v2 can help you to stay within budget and avoid paying for computer resources that you don't use.
With Aurora Serverless v2, your database automatically scales capacity to accommodate the application's peak load and scales back down when the surge of activity ceases. With Aurora Serverless v2, you no longer need to provision for peak or average capacity. You can specify an upper capacity limit to handle your most demanding workloads, and that capacity isn't used unless it's needed.
You also set your minimum capacity setting. The scaling rate for an Aurora Serverless v2 DB instance depends on its current capacity. The higher the current capacity, the faster it can scale up. You might need the DB instance to quickly scale up to a very high capacity. If so, consider setting the minimum capacity to a value where the scaling rate meets your requirement. This type of automation is especially valuable for multitenant databases, distributed databases, development and test systems, and other environments with highly variable and unpredictable workloads.




# 3 Amazon DynamoDB 

The database services manager asks, “How can we build a scalable key-value NoSQL database?”
The database team is considering using NoSQL databases in some of their workloads. The company wants you to identify a high-performance key-value database solution.

![](image/Pasted%20image%2020231020120001.png)

DynamoDB is a fully managed NoSQL database service. The service itself manages the complexity of running this massively scalable, distributed NoSQL database. The software developers can focus on building applications instead of managing infrastructure.
NoSQL databases are designed for scale, but their architectures are sophisticated and significant operational overhead can be a part of running a large NoSQL cluster. DynamoDB removes the need to become an expert in advanced distributed computing concepts. You only need to learn DynamoDB’s straightforward API by using the SDK for the programming language of choice.
DynamoDB is cost effective. You pay for the storage that you are consuming and the I/O throughput that you have provisioned. It is designed to scale elastically while maintaining high performance. You can choose to provision a small amount of capacity when the storage and throughput requirements of an application are low. If you choose auto scaling, additional capacity is provisioned when the required I/O throughput increases, within limits that you set. The on-demand choice permits an application to seamlessly grow to support millions of users that make thousands of concurrent requests to the database every second.
DynamoDB supports end-to-end encryption and fine-grained access control

---
![](image/Pasted%20image%2020231020120041.png)

NoSQL databases use a variety of data models to access and manage data. These types of databases are optimized specifically for applications that require large data volume, low latency, and flexible data models. NoSQL databases are optimized by relaxing some of the data consistency restrictions of other databases. One common model is key-value data.
Key-value databases are good for use cases where the requested data can be associated with a single primary key. Consider this example of a video game’s user profile database. Each item has a collection of key-value pairs, including keys such as TopScore, UserID, and Level. All key-value pairs for an item are associated with the primary key, GamerTag. You can rapidly retrieve any of these key-value pairs by locating their GamerTag



---

use case 


![](image/Pasted%20image%2020231003103900.png)

Game makers can support simple player profile pages by using DynamoDB. You can store user profile data in DynamoDB using GamerTag as the key. When a profile page loads, the application only needs to make a single read request to DynamoDB by using the GamerTag value. In addition, when a new game launches, DynamoDB can scale rapidly to provide enough storage and throughput to support spikes in traffic.
For more information about gaming use cases, see “Amazon DynamoDB: Gaming use cases and design patterns” in the AWS Database Blog at https://aws.amazon.com/blogs/database/amazon-dynamodb-gaming-use-cases-and-design-patterns/.



![](image/Pasted%20image%2020231003103907.png)


Imagine that you have an ecommerce application to sell products to your customers. You need the web store to display an accurate inventory. This task becomes a significant challenge during peak traffic and holiday sales. DynamoDB supports a flexible schema to accommodate data for a variety of products. It can also manage many concurrent read and write operations while maintaining the accuracy of stored data.


---

![](image/Pasted%20image%2020231003103938.png)

DynamoDB stores data in tables. When creating a table, you must specify a table name and a partition key, which are the only two required entities.
DynamoDB uses primary keys to uniquely identify each item in a table and secondary indexes to provide more
query flexibility. Two types of primary keys are supported: 
• Simple primary key – A simple primary key is composed of just one attribute, which is designated as the partition key. If you use only the partition key, no two items can have the same value.
• Composite primary key – A composite primary key is composed of both a partition key and a sort key. In this case, the partition 
key value for multiple items can be the same, but their sort key values must be different.


You work with the core components: tables, items, and attributes. A table is a collection of items, and each item is a collection of attributes. In this example, the table includes two items, with simple primary keys Hammer57 and FluffyDuffy. The item with the primary key Hammer57 includes three attributes: GameID, TopScore, and Genre. The primary key for FluffyDuffy includes a Subscription attribute, and it does not include the Genre attribute.

For more information about the components of DynamoDB, see “Core Components of Amazon DynamoDB” in the Amazon DynamoDB Developer Guide at https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html.



---


![](image/Pasted%20image%2020231003104008.png)


When planning for capacity in DynamoDB, you must consider the expected number of read/write requests per second and the size of those requests. This information helps you choose the capacity mode for your table. It also helps you design your table to manage message size.

On-demand capacity mode is a pay-per-request model. On-demand capacity mode is best when you: 
• Have unknown workloads 
• Have unpredictable traffic 
• Prefer to pay for only what you use

With provisioned capacity mode, you set a maximum number of RCUs and WCUs. When traffic exceeds those limits, DynamoDB throttles those requests to control your costs. You can adjust your provisioned capacity by using auto scaling. Provisioned capacity mode is best when you: 
• Have predictable application traffic 
• Have traffic that is consistent or changes gradually 
• Can forecast capacity requirements to control costs


For more information about DynamoDB auto scaling, see “Amazon DynamoDB auto scaling: Performance and cost optimization at any scale” in the AWS Database Blog at https://aws.amazon.com/blogs/database/amazon-dynamodb-auto-scaling-performance-and-cost-optimization-at-any-scale/.


--- 


![](image/Pasted%20image%2020231003104519.png)

When your application writes data to a DynamoDB table and receives an HTTP 200 response (OK), the write has occurred and is durable. The data is eventually consistent across all storage locations, usually within one second or less. DynamoDB supports eventually consistent and strongly consistent reads.
Eventually consistent reads When you read data from a DynamoDB table, the response might not reflect the results of a recently completed write operation. The response might include some stale data. If you repeat your read request after a short time, the response should return the latest data.
Strongly consistent reads When you request a strongly consistent read, DynamoDB returns a response with the most up-to-date data, which reflects updates from all prior successful write operations. A strongly consistent read might not be available if a network delay or outage occurs.
DynamoDB uses eventually consistent reads, unless you specify otherwise. Read operations (such as GetItem, Query, and Scan) provide a ConsistentRead parameter. If you set this parameter to true, DynamoDB uses strongly consistent reads during the operation.



# 4 ElastiCache 


![](image/Pasted%20image%2020231003110024.png)





![](image/Pasted%20image%2020231003110201.png)



# 5 Database migration tools 

![](image/Pasted%20image%2020231003110359.png)


![](image/Pasted%20image%2020231003110412.png)

heterroegense database migration: no sql db to sql db  也是可以的 , 
source can aws or on-premises .    或者 aws to aws 




![](image/Pasted%20image%2020231003110457.png)



# 6 Review 

![](image/Pasted%20image%2020231003110749.png)




# 7 Knowledge check 

b

![](image/Pasted%20image%2020231003110805.png)


![](image/Pasted%20image%2020231003110906.png)



----

a

![](image/Pasted%20image%2020231003110914.png)



------------

d


![](image/Pasted%20image%2020231003111004.png)




--------
c
b: aurora database have 15 replicas maxiaml 

![](image/Pasted%20image%2020231003111044.png)



![](image/Pasted%20image%2020231003111141.png)


# 8 Lab 

![](image/Pasted%20image%2020231003111201.png)


![](image/Pasted%20image%2020231003111211.png)


![](image/Pasted%20image%2020231004132029.png)


















