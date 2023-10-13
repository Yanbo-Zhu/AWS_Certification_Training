
![](image/Pasted%20image%2020231013110311.png)

In this module, you will explore:
• Benefits of databases on AWS 
• Database types 
• Amazon Relational Database Service (Amazon RDS) 
• Amazon DynamoDB

In this module, you explored:
• Benefits of databases on AWS 
• Database types 
• Amazon RDS
• Amazon DynamoDB


# 1 Benefits of databases on AWS 


![](image/Pasted%20image%2020231013110413.png)

The benefits of databases in the AWS Cloud include:
• Purpose-built: AWS supports more than 15 purpose-built database engines, including relational, key-value, document, and more. With a variety of database options, you can build customer-focused, highly scalable, and distributed applications.
- Purpose built: rds and dymanodb
• Performance at scale: AWS offers databases that are three to five times faster than popular alternatives, or non-relational databases that give you microsecond to sub-millisecond latency. For example, with Amazon Aurora, you get five times the throughput of standard MySQL and three times the throughput of standard PostgreSQL.
• Fully managed: AWS manages database tasks such as server provisioning, patching, configuration, and backups.
• Secure and highly available: AWS databases are built for business-critical, enterprise workloads. They offer high availability, reliability, and security with multi-Region and end-to-end encryption support.

Resource To learn more about databases, visit the AWS documentation: https://aws.amazon.com/products/databases/

# 2 Database types 

![](image/Pasted%20image%2020231013110438.png)

Here’s a quick look at eight types of databases supported by AWS.
Relational databases store data with predefined table structures and relationships between them. They are used for traditional applications, such as enterprise resource planning (ERP), customer relationship management (CRM), and ecommerce.

Key-value databases are optimized for common access patterns, typically to store and retrieve large volumes of data. They are used for high-traffic website applications, ecommerce systems, and gaming applications.

In-memory databases are used for applications that require real-time access to data. They are used for caching, session management, gaming leaderboards, and geospatial applications.

Document databases are designed to store semi-structured data as JSON-like documents. They are used for content management, catalogs, and user profiles.

Wide column databases are types of NoSQL databases. They are used for high-scale industrial applications for equipment maintenance, fleet management, and route optimization.

Graph databases are for applications that must navigate and query millions of relationships between highly connected graph datasets with millisecond latency at large scale. They are used for fraud detection, social networking, and recommendation engines.

Time series databases efficiently collect, synthesize, and derive insights from data that changes over time and with queries spanning time intervals. They are used for IoT applications, DevOps, and industrial telemetry.

Ledger databases provide a centralized and trusted authority to maintain a scalable, immutable, and cryptographically verifiable record of transactions for every application. They are used for systems of record, supply chain, registrations, and banking transactions.
In this course, you will learn about relational and key-value databases.

Resource For more information about the various types of databases, visit the AWS products website: https://aws.amazon.com/products/databases/

![](image/Pasted%20image%2020231013110541.png)

AWS has services for each database type.
The AWS services offered for relational databases are Amazon Aurora, Amazon RDS, and Amazon Redshift. The AWS service offered for key-value databases is Amazon DynamoDB.
The AWS services offered for in-memory databases are Amazon ElastiCache for Memcached and Amazon ElastiCache for Redis. The AWS service offered for document databases is Amazon DocumentDB. The AWS service offered for wide column databases is Amazon Keyspaces. The AWS service offered for graph databases is Amazon Neptune. The AWS service offered for time series databases is Amazon Timestream.
The AWS service offered for ledger databases is Amazon Quantum Ledger Database (Amazon QLDB)


# 3 Relational databases 


![](image/Pasted%20image%2020231013110857.png)

A relational database is a collection of data records organized as a set of tables with rows and columns. Each row holds information about a record, and the columns contain attributes of the data. For example, a record row for a person might include attribute columns for name, age, height, weight, gender, and so on. The values for the person’s attributes would be shown in the record’s row.
 
Each row has an identifier column to uniquely distinguish the record from other records. The value in the identifier column is called a primary key. Other tables can reference a primary key. A record in another table that references a primary key is called a foreign key. For example, when a students registers for a course, the information about the course can be stored and retrieved from a relational database table. For this example, assume that the school has three tables:
• The first table contains the course listings. 
• The second table contains the list of course books. 
• The third table contains the list of course instructors.

When a student requests information, they get the course title (in this example, Cloud Computing) from the Course table, the course book name (Introduction to Cloud Computing) from the Books table, and the instructor name (Martha Rivera) from the Instructors table. These three tables are related by the Course_ID value found in all three tables.

Realational databse ist not not effeiidiecal because  it conatins the relation of database


![](image/Pasted%20image%2020231013110911.png)

Some benefits of relational databases are complex SQL, reduced redundancy, familiarity, and ACID principle.
The language used to query a dataset in a relational database is known as Structured Query Language (SQL). You can join multiple tables to query a dataset with SQL statements.

For example, suppose you submit a query for a person’s home address from a city database. The data from the Person table and Address table is joined to supply a full mailing address. The Person table returns the person’s first and last names, and the Address table returns the street address, city, state, and postal code.

To reduce redundancy, instead of storing the same data across multiple tables in a database, relational databases store the data in one table and reference it from other tables. For example, if three people live in the same home, instead of saving the physical address three times in the same table as the residents’ names, an Address table can have one item for the physical address and reference that data every time a location query is made for the residents.

Since relational databases have been popular since the 1970s, many technical professionals are familiar with relational databases.
Relational databases are accurate by adhering to the atomicity, consistency, isolation, and durability (ACID) principle.


---


![](image/Pasted%20image%2020231013111013.png)



For on-premises databases, the customer is responsible for managing all database aspects, including:
• Application optimization • Scaling • High availability • Database backups • Database software patches and installations • Operating system (OS) patches and installations • Server maintenance • Rack and stack (the assembly of computer hardware in a system, computer cabinet, or rack) • Server room power, HVAC, and network

For databases deployed and hosted in an Amazon Elastic Compute Cloud (Amazon EC2) instance, the customer and AWS share responsibility. The customer is responsible for:
• Application optimization • Scaling • High availability • Database backups • Database software patches and installations • OS patches


AWS is responsible for:
• OS installation • Server maintenance • Rack and stack • Server room power, HVAC, and network


![](image/Pasted%20image%2020231013111042.png)

For database hosted in a managed AWS database service, the customer is responsible for application optimization and AWS is responsible for everything else, including:
• Scaling • High availability • Database backups • Database software patches and installations • OS patches and installations • Server maintenance • Rack and stack • Server room power, HVAC, and network


# 4 Amazon Relational Database Service (Amazon RDS)

![](image/Pasted%20image%2020231013111329.png)

Amazon RDS is a managed web service that helps customers create and manage highly scalable and secure relational databases in the AWS Cloud. Customers are not responsible for hardware provisioning, database setup, software patching, and backups. AWS manages the common database administration tasks.
Amazon RDS supports most relational database engines, including commercial (such as Oracle and Microsoft SQL Server [MSSQL]), open source (MySQL, PostgreSQL, and MariaDB), and Amazon Aurora. With Amazon RDS, you store and transmit data securely.
Resource To learn more, review the Amazon RDS documentation: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html




![](image/Pasted%20image%2020231013111334.png)


A database (DB) instance is a building block of Amazon RDS. A DB instance is an isolated database environment running in the cloud. You can have multiple databases with a single DB instance and access them using AWS Command Line Interface (AWS CLI), Amazon RDS API operations, or the AWS Management Console. Amazon RDS supports access to DBs using any standard SQL client application. It does not allow direct host access.
Each DB instance supports a DB engine (such as Oracle, MSSQL, PostgreSQL, and others). Features and configuration differ depending on the database engine. For example, if you run an Oracle database engine, the database name is used to set the value of ORACLE_SID (Oracle System ID), which is required to establish a connection to the Oracle RDS instance.
Resource To learn more about DB instances, visit the online documentation: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.html



![](image/Pasted%20image%2020231013111341.png)

![](image/Pasted%20image%2020231013111350.png)


Burstable : 可突发的，可爆发的：指某种资源或系统在短时间内能够承受突然增加的需求或负载。
database performance will increase according to the demand on your database until it reaches the perfromance
The amoount of monmey  which you have
平常增加 Credit , performance brust 就会花费平常攒的 credits

Amazon RDS DB instances run on Amazon EC2 instances managed by AWS. When you create a DB instance, the DB instance class you select determines the computation and memory capacity of the Amazon RDS DB instance.
The three DB instance class types that are supported by Amazon RDS are standard, memory optimized, and burstable performance.
• Standard is used for general purpose instances. The available DB instance classes are db.m6g, db.m6gd, db.m6i, db.m5d, db.m5, db.m4, and db.m3.
• Memory optimized is used for memory-intensive applications. The available DB instance classes are db.x2g, db.z1d, db.x1e, db.x1, db.r6g, db.r6gd, db.r6i, db.r5b, db.r5d, db.r5, and db.r3.
• Burstable performance is used for baseline performance level, with the ability to burst to full CPU usage. The available DB instance classes are db.t4g, db.t3, and db.t2.

Resource 
To learn about DB instance classes and more, visit: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.DBInstanceClass.html


---


![](image/Pasted%20image%2020231013111717.png)

For database and log storage, Amazon RDS DB instances use Amazon Elastic Block Store (Amazon EBS) volumes for MySQL, MariaDB, PostgreSQL, Oracle, and MSSQL engines. Amazon RDS automatically stripes across multiple Amazon EBS volumes to enhance performance depending the amount of storage requested.
The three storage types that are provided by Amazon RDS are general purpose SSD, provisioned IOPS, and magnetic.
• General purpose SSD volumes are a cost-effective storage used for a broad range of workloads.
• Provisioned IOPS storage is used for I/O-intensive database workloads that require low I/O latency and throughput.
• Magnetic storage is used for backward compatibility. This storage is not recommended for new storage needs.

Resource 
To learn more about DB instance classes, visit the online documentation: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.htm




![](image/Pasted%20image%2020231013111729.png)


When you create an Amazon RDS DB instance, you create it in a private subnet inside your Amazon Virtual Private Cloud (Amazon VPC). When database queries are performed by web applications, content management systems, microservices, and so on, they do so within the isolated boundary of the VPC, which avoids exposing the DB instance to the internet from a public subnet.

Network security best practices include the following recommendations:
• Create an individual AWS Identity and Access Management (IAM) user for each person who manages Amazon RDS resources
• Do not use the AWS root account to manage Amazon RDS resources 
• Grant each user the minimum set of permissions required to perform their duties 
• Enable Amazon RDS encryption to secure instances and snapshots at rest 
• Rotate IAM credentials regularly • Create Amazon RDS DB instances inside private subnets


![](image/Pasted%20image%2020231013111821.png)


You can back up your databases in multiple ways, including using automatic backups and database snapshots.

Automatic backups: When you create an Amazon RDS database, automatic backups are enabled by default. Amazon RDS will back up the entire database and transaction logs by creating a storage volume snapshot of your DB instance. We recommend that you set the 30-minute backup time when the database has minimum activity to avoid latency issues. You can also configure the backup retention period, which is the number of days that backups are kept, up to 35 days. You can restore your DB instance to any specific time during the backup retention period, which creates a new DB instance.

Database snapshots: You can take manual database snapshots of your DB instance if you want to keep your automated backups for longer than 35 days. Snapshots are saved in Amazon Simple Storage Service (Amazon S3), and are available until you delete them.

Resource To learn more about backing up databases, visit the AWS website: https://aws.amazon.com/rds/features/backup





![](image/Pasted%20image%2020231013111856.png)
![](image/Pasted%20image%2020231013111950.png)

For redundancy, Amazon RDS creates a secondary copy of your database in another Availability Zone (AZ) when you enable Amazon RDS Multi-AZ. Amazon RDS uses the secondary copy of a database as a standby database in case the primary database stops responding to requests. If that occurs, Amazon RDS sets the standby database to be the primary database, and then either creates another standby DB instance or demotes the previous primary to standby to keep the Multi-AZ configuration active.

Achicve high avaialabilty: sync and recove r
Recover: Use tge standby database to recover primary database

# 5 Amazon DynamoDB

![](image/Pasted%20image%2020231013112030.png)

Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. DynamoDB is a key-value database service.
Since DynamoDB is serverless, you do not have to provision, patch, install, or manage software applications and servers. DynamoDB offers encryption at rest for protecting sensitive data.
DynamoDB automatically spreads the data and traffic for your tables over a sufficient number of servers to handle your throughput and storage requirements, while maintaining consistent and fast performance. All of your data is stored on solid state disks (SSDs) and is automatically replicated across multiple Availability Zones in an AWS Region. This provides built-in high availability and data durability. You can use global tables to keep DynamoDB tables in sync across AWS Regions.

![](image/Pasted%20image%2020231013112051.png)


The core components of DynamoDB are tables, items, and attributes: 
• Tables: DynamoDB stores data in tables. A table is a collection of data.
• Items: Each table contains zero or more items. An item is a group of attributes that is uniquely identifiable among all of the other items. You can store an unlimited number of items in a table.
• Attributes: Each item is composed of one or more attributes. An attribute is a fundamental data element that does not need to be broken down any further.

You must define a partition key for each DynamoDB table. This determines the bounding of items for automatic relocation across multiple partitions (underlying AWS resources) for performance reasons. You must also define a primary key for each table. If the partition key is unique, it can also be used as the primary key. If not, then a sort key must also be chosen, and you have a composite primary key (consisting of the partition key and the sort key together).

Resource 
To learn more, visit the DynamoDB developer guide:
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreCom ponents.html


# 6 Knowledge Check


![](image/Pasted%20image%2020231013112156.png)

An AWS solutions architect needs a database for a dataset that has variations in the data. Not every piece of data shares the same attributes. Which database should the solutions architect choose?
A. Amazon Relational Database Service (Amazon RDS) 
B. Amazon Neptune 
C. Amazon DynamoDB 
D. Amazon Quantum Ledger Database (Amazon QLDB)

The correct response option is C. Amazon DynamoDB.
Explanation: Amazon DynamoDB allows for a flexible schema, so each item can have variations in the attributes outside of the primary and secondary key.


---
![](image/Pasted%20image%2020231013112255.png)


When using Amazon Relational Database Service (Amazon RDS), which database task is the customer’s responsibility?
1. Optimize the database 
2. Provision and manage the underlying infrastructure 
3. Install the RDBMS onto the DB instance 
4. Install patches to the OS for the DB instance

The correct response option is A. Optimize the database.
Explanation: When using Amazon RDS, customers are not responsible for the underlying environment the database runs on. Instead, they can focus on optimizing their database. AWS manages the underlying components of Amazon RDS.

















