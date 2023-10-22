

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

---

![](image/Pasted%20image%2020231022174350.png)

A global table is a collection of one or more DynamoDB tables, which are all owned by a single AWS account, identified as replica tables. A replica table (or replica, for short) is a single DynamoDB table that functions as part of a global table. Each replica stores the same set of data items. Any given global table can only have one replica table per Region, and every replica has the same table name and the same primary key schema.
DynamoDB global tables provide a fully managed solution for deploying a multi-Region, multi-active database, without having to build and maintain your own replication solution. When you create a global table, you specify the Regions where you want the table to be available. DynamoDB performs all the necessary tasks to create identical tables in these Regions and propagate ongoing data changes to all of them. DynamoDB communicates these changes over the AWS network backbone.
For more information about Amazon DynamoDB global tables, see “Amazon DynamoDB global tables” at https://aws.amazon.com/dynamodb/global-tables/.


# 4 Database Caching 

The database services manager asks, “How can we cache databases in the cloud to maximize performance?”
The database team has identified some common queries that are causing a lot of read traffic. The company is looking for your advice on how to cache this commonly accessed data to improve performance and decrease the load on the databases

---

![](image/Pasted%20image%2020231022174442.png)

To determine whether your application should use database caching, consider the following points:
• Speed and expense – Some database queries are inherently slower and more expensive than others. For example, queries that perform joins on multiple tables are significantly slower and more expensive than simple, single-table queries. If requesting data requires a slow and expensive query, it's a candidate for caching.
• Data and access pattern – Determining what to cache also involves understanding the data itself and its access patterns. For example, it doesn't make sense to cache data that is rapidly changing or is seldom accessed. For caching to provide meaningful benefit, the data should be relatively static and frequently accessed, such as a personal profile on a social media site.
• Cache validity – Data can become out-of-date while it is stored in cache. Writes that occur on that data in the database might not be reflected in that cached data. To determine whether your data is a candidate for caching, you must determine your application's tolerance for occasionally inaccurate cached data


![](image/Pasted%20image%2020231022174507.png)

Without caching, EC2 instances read and write directly to the database. With caching, an instance first attempts to read from a cache, which uses high performance memory. For example, database caches on AWS such as Amazon ElastiCache and Amazon DynamoDB Accelerator (DAX) are in-memory databases. They use a cache cluster that contains a set of cache nodes distributed between subnets. Resources within those subnets have high-speed access to those nodes.
In this example, a VPC has an app subnet and a data subnet in each of two Availability Zones. The application servers in both app subnets connect to a primary database in one data subnet. The other data subnet holds a replica database. A cache cluster spans both app subnets with cache nodes in each.
When you’re using a cache for a backend data store, a side-cache is a common approach. Canonical examples include both Redis and Memcached. These caches are general-purpose and are decoupled from the underlying data store. They can help with both read and write throughput, depending on the workload and durability requirements.



---

## 4.1 Common Caching Strategy 

![](image/Pasted%20image%2020231022174533.png)

Multiple strategies are available for keeping information in the cache in sync with the database. Two common caching strategies include lazy loading and write-through.
In lazy loading, updates are made to the database without updating the cache. In the case of a cache miss, the information that is retrieved from the database can be subsequently written to the cache. Lazy loading loads data that the application needs into the cache, but it can result in high cache-miss-to-cache-hit ratios in some use cases.

---


![](image/Pasted%20image%2020231022174614.png)

An alternative strategy is to write through to the cache every time the database is accessed. This approach results in fewer cache misses. The result is improved performance, but it requires additional storage for data that the applications might not need.
The best strategy depends on your use case. It is critical to understand the impact of stale data on your use case. If the impact is high, then consider maintaining freshness with write-throughs. If the impact is low, then lazy loading might be sufficient. It also helps to understand the frequency of change of the underlying data because it affects the performance and cost tradeoffs of the caching strategies.
After you decide on a strategy for maintaining your cache, you will want to implement this approach within your application.

For more information about ElastiCache, see “Caching strategies” in the following resources: 
• Amazon ElastiCache for Redis User Guide at https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/Strategies.html.
• Amazon ElastiCache for Memcached User Guide at https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/Strategies.html.


---


![](image/Pasted%20image%2020231022174645.png)

Lazy loading can have stale data, but doesn't fail with empty nodes. Write-through maintains fresh data, but can fail with empty nodes and can populate the cache with superfluous data. By adding a time to live (TTL) value to each write to the cache, you can maintain fresh data without cluttering the cache with extra data.
TTL is an integer value that specifies the number of seconds or milliseconds until the key expires. When an application attempts to read an expired key, it is treated as though the data is not found in cache. Thus, the database is queried and the cache is updated. As a result, it keeps data from getting too stale and requires that values in the cache are occasionally refreshed from the database.

When cache memory is full, the cache engine removes data from memory to make space for new data. It chooses this data based on the eviction policy that you set. An eviction policy evaluates the following characteristics of your data: 
• Which were accessed least recently? 
• Which have been accessed least frequently? 
• Which have a TTL set and the TTL value?


# 5 Amazon ElastiCahce

![](image/Pasted%20image%2020231003110024.png)

Amazon ElastiCache is a web service that facilitates setting up, managing, and scaling a distributed in-memory data store or cache environment in the cloud. It provides a high-performance, scalable, and cost-effective caching solution. At the same time, it helps remove the complexity that is associated with deploying and managing a distributed cache environment.
ElastiCache supports two open-source in-memory engines (in-memory as compared to disk): • Redis • Memcached
For more information about ElastiCache, see “Amazon ElastiCache” at https://aws.amazon.com/elasticache/. 



---

![](image/Pasted%20image%2020231022174804.png)

ElastiCache offers fully managed capabilities for two popular, open-source compatible in-memory data stores: Memcached and Redis.
With ElastiCache for Memcached, you can build a scalable caching tier for data-intensive apps. The service works as an in-memory data store and cache to support the most demanding applications requiring sub-millisecond response times. ElastiCache for Memcached is fully managed, scalable, and secure, which makes it an ideal candidate for use cases where frequently accessed data must be in memory. This engine offers a simple caching model with multi-threading. The service is a popular choice for use cases such as web, mobile apps, gaming, ad tech, and ecommerce. The Memcached-compatible service also supports Auto Discovery.

ElastiCache for Redis is an in-memory data store that provides sub-millisecond latency at internet scale. ElastiCache for Redis combines the speed, simplicity, and versatility of open-source Redis with manageability, security, and scalability from Amazon. It can power the most demanding real-time applications in gaming, ad tech, ecommerce, healthcare, financial services, and Internet of Things (IoT).
For more information, see “Comparing Redis and Memcached” at https://aws.amazon.com/elasticache/redis-vs-memcached/.


---

# 6 Amazon DynamoDB Accelerator 

![](image/Pasted%20image%2020231003110201.png)

DynamoDB is designed for scale and performance. In most cases, the DynamoDB response times can be measured in single-digit milliseconds. However, certain use cases require response times in microseconds. For those use cases, DynamoDB Accelerator (DAX) delivers fast response times for accessing eventually consistent data.
DAX is a caching service compatible with DynamoDB that provides fast in-memory performance for demanding applications.
You create a DAX cluster in your Amazon VPC to store cached data closer to your application. You install a DAX client on the EC2 instance that is running your application in that VPC. At runtime, the DAX client directs all of your application's DynamoDB requests to the DAX cluster. If DAX can process a request directly, it does so. Otherwise, it passes the request through to DynamoDB.
For more information about memory acceleration, see “In-Memory Acceleration with DynamoDB Accelerator (DAX)” in the Amazon DynamoDB Developer Guide at https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html.

# 7 Database migration tools 

![](image/Pasted%20image%2020231003110359.png)

The database services manager asks, “What tools are available for migrating an existing database to the AWS Cloud?”
The database team is planning to move some of their on-premises databases to the cloud. The company wants you to identify tools that can help them with this process and minimize downtime.



![](image/Pasted%20image%2020231003110412.png)

heterroegense database migration: no sql db to sql db  也是可以的 , 
source can aws or on-premises .    或者 aws to aws 

AWS Database Migration Service (AWS DMS) replicates data from a source to a target database in the AWS Cloud. You create a source and a target connection to tell AWS DMS where to extract from and load to. Then you schedule a task that runs on this server to move your data. AWS DMS creates the tables and associated primary keys if they don't exist on the target.
AWS DMS supports migration between the most widely used databases, which include Oracle, PostgreSQL, SQL Server, Amazon Redshift, Aurora, MariaDB, and MySQL. It also supports homogenous (same engine) and heterogeneous (different engines) migrations. You can use the service to migrate between on-premises databases, Amazon EC2 databases, and Amazon RDS databases. However, you cannot migrate between two on-premises databases. Either the source or the target database (or both) must reside in Amazon RDS or on Amazon EC2.
With AWS DMS, you can also use a Snowball Edge device as a migration target. You would use this method if your environment has poor internet connectivity or if the source database is too large to move over the internet. You would also use it if your organization has privacy or security requirements.
AWS DMS automatically handles formatting of the source data for consumption by the target database. It does not perform schema or code conversion.
For homogenous migrations, you can use native tools to perform these conversions. For heterogeneous migrations, you can use the AWS Schema Conversion Tool (AWS SCT).
For more information about AWS DMS, see “What is AWS Database Migration Service?” in the AWS Database Migration Service User Guide at https://docs.aws.amazon.com/dms/latest/userguide/Welcome.html.



---


![](image/Pasted%20image%2020231003110457.png)

The AWS Schema Conversion Tool (AWS SCT) makes heterogeneous database migrations predictable. It automatically converts the source database schema and a majority of the database code objects. The conversion includes views, stored procedures, and functions. They are converted to a format that is compatible with the target database. Any objects that cannot be automatically converted are marked so that they can be manually converted to complete the migration.
The AWS SCT can also scan your application source code for embedded SQL statements and convert them as part of a database schema conversion project. During this process, the AWS SCT optimizes code that is built for the cloud. It converts legacy Oracle and SQL Server functions to their equivalent AWS service, thus modernizing the applications at the same time of database migration.
After the schema conversion is complete, AWS SCT can help migrate data from various data warehouses to Amazon Redshift by using built-in data migration agents.
For more information about the AWS SCT, see “AWS Schema Conversion Tool” at https://aws.amazon.com/dms/schema-conversion-tool/

# 8 Review 

![](image/Pasted%20image%2020231022175044.png)



Imagine that you are now ready to talk to the database services manager and present solutions that meet their architectural needs.
Think about how you would answer the questions from the beginning of the lesson.
Your answers should include the following solutions: • AWS offers services that support relational and nonrelational databases. • You can manage your relational databases efficiently with Amazon RDS and Amazon Aurora. • You can manage your nonrelational key-value databases with Amazon DynamoDB. • You can use Amazon ElastiCache and Amazon DynamoDB Accelerator for database caching. • You can use AWS Database Migration Service to migrate your databases to the cloud.

## 8.1 Capstone 

![](image/Pasted%20image%2020231003110749.png)


At the end of this course is a Capstone Lab project. You will be provided a scenario and asked to build an architecture based on project data, best practices, and the Well-Architected Framework.
Note: The diagram on this slide contains several abbreviations. The following list includes some services that are not covered in this module, but are included for completeness: 
• EFS
• Aurora 
• NAT 
• VPC

Amazon Elastic File Service
Amazon Aurora
network address translation 
virtual private gateway



In this module, you explored AWS database services and resources.
Review the capstone architecture to explore some of the design decisions. This architecture helps you provide the following benefits: 
• In the capstone, you set up an application that requires a MySQL database. Amazon Aurora supports this engine. Using a managed service for hosting the database also provides the following benefits:
    • You do not have to manage server OS patches or database software updates. 
    • Amazon Aurora helps you configure scaling, backups, and high availability.
• The capstone architecture achieves resiliency by using an Aurora replica. If the primary instance fails, the replica can be promoted to primary

# 9 Knowledge check 

b

![](image/Pasted%20image%2020231003110805.png)

![](image/Pasted%20image%2020231003110906.png)

The correct answer is B: It provides automatic failover across Availability Zones.
When you provision a Multi-AZ DB instance, Amazon RDS synchronously replicates the data to a standby instance in a different Availability Zone. In case of the primary instance failure, Amazon RDS performs an automatic failover to the standby instance. Database operations can be resumed as soon as the failover is complete. Because the endpoint for your DB instance remains the same after a failover, your application can resume database operation. You don’t need to manually intervene in the administration.

----

a

![](image/Pasted%20image%2020231003110914.png)

The correct answer is A: Amazon ElastiCache for Redis. ElastiCache for Redis sorts and ranks datasets.
For more information about Redis and Memcached, see the following resources:
• “Comparing Redis and Memcached” at https://aws.amazon.com/elasticache/redis-vs-memcached/ 
• The “Performance at Scale with Amazon ElastiCache” whitepaper at https://d0.awsstatic.com/whitepapers/performance-at-scale-with-amazon-elasticache.pdf


------------

d


![](image/Pasted%20image%2020231003111004.png)


The correct answer is D: tables can be in different AWS Regions.
When you create a global table, you specify the Regions where you want the table to be available. DynamoDB performs all the necessary tasks to create identical tables in these Regions and to propagate ongoing data changes to all of them.
For more information about Amazon DynamoDB global tables, see “Amazon DynamoDB global tables” at https://aws.amazon.com/dynamodb/global-tables/.

--------
c
b: aurora database have 15 replicas maxiaml 

![](image/Pasted%20image%2020231003111044.png)



![](image/Pasted%20image%2020231003111141.png)


The correct answer is C: Aurora is compatible with MySQL or PostgreSQL.
Aurora is an enterprise-class relational database. It is compatible with MySQL or PostgreSQL relational databases. It is up to five times faster than standard MySQL databases and up to three times faster than standard PostgreSQL databases.
For more information about Amazon Aurora storage, see “Amazon Aurora storage and reliability” at https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.StorageReliability.htm















