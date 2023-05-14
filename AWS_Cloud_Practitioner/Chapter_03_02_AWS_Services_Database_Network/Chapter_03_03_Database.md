
# 1 基本概念解释

## 1.1 Database

6:05:26 What is a Database

[Database](https://en.wikipedia.org/wiki/Database)

A database is a data store that stores semi-structured and structured data.

A database is a more complex data stores because it requires using formal design and modeling techniques

Databases can be generally categorized as either:
- **Relational databases**
    - Structured data that strongly represents tabular data (tables, rows, and columns)
        - Row-oriented or Columnar-oriented
- **Non-relational databases**
    - Semi-structured that may or may not distantly resemble tabular data.

Databases have a rich set of functionality:
-   specialized language to query (retrieve data)
-   specialized modeling strategies to optimize retrieval for different use cases
-   more fine-tune control over the transformation of the data into useful data structures or reports

Normally, a database infers someone is using a **relational row-oriented datastore**

## 1.2 data warehouse
6:06:56 What is a data warehouse?
[What is Data Warehouse? Types, Definition & Example](https://www.guru99.com/data-warehousing.html)
数据仓库是用于报告和数据分析的系统，被认为是商业智能的核心组件。

data warehouse: A relational data store designed for analytic workloads, which is generally column-oriented data-store
Companies will have terabytes and millions of rows of data, and they need a fast way to be able to produce analytics reports

Data warehouses generally perform **aggregation**
-   aggregation is grouping data eg. find a total or average
-   Data warehouses are optimized around columns since they need to quickly aggerate column data

Data warehouses are generally designed to be HOT
-   Hot means they can return queries very very fast even though they have vast amounts of data

Data warehouses are infrequently accessed meaning they aren’t intended for real-time reporting, but maybe once or twice a day or once a week to generate business and user reports.
A data warehouse needs to consume data from a relational database on a regular basis.


![](image/Pasted%20image%2020230513114838.png)

## 1.3 key value store##

6:08:25 What is a key value store?

A key/value stores a unique key alongside a value
Key values stores are dumb and fast.

They generally lack features like:
    Relationships
    Indexes
    Aggregation 

![](image/Pasted%20image%2020230513115125.png)

A simple key/value store will interpret this data resembling a dictionary (aka Associative arrays or hash)
A key/value store can resemble tabular data, it does not have to have consistent columns per row (hence its schemaless). 看起来像表格, 但是他不是table 构造的, 因为有的coloumns 中根本那就没有值 
Due to their simple design, they can scale well beyond a relational database

## 1.4 document database
6:10:11 What is a document database?
[Document-oriented database](https://en.wikipedia.org/wiki/Document-oriented_database)

A document store is a NoSQL database that stores documents as its primary data structure.
A document could be an XML but more commonly is JSON or JSON-Like
Document stores are a sub-class of Key/Value stores
The components of a document store compared to a Relational database

![](image/Pasted%20image%2020230513115400.png)

# 2 NoSQL Database Services
6:11:08 NoSQL Database Services

1. DynamoDB 
    1. is a serverless NoSQL key/value and document database. It is designed to scale to billions of records with guaranteed consistent data return in at least a second. You don’t have to worry about managing shards!​
    3. DynamoDB is AWS’s flagship database service meaning whenever we think of a database service that just scales, is cost effective and very fast we should think DynamoDB (aws 默认使用这种类型的 db)
    4. when you want a massively saclable database 就是使用它
    5. ![](image/Pasted%20image%2020230513115722.png)
3. DocumentDB 
    1. is a NoSQL document database that is “MongoDB compatible”​
    2. MongoDB is very popular NoSQL among developers. There were open-source licensing issues around using open-source MongoDB, so AWS got around it by just building their own MongoDB database.​
    3. when you wann use MongoDB , 使用它
4. Amazon Keyspaces
    1. is a fully managed Apache Cassandra database. 
    2. Cassandra is an open-source NoSQL key/value database similar to DynamoDB in that is columnar store database but has some additional functionality.
    3. When you want to use Apache Casandra.
    4. when you wann use  Apache Casandra , 使用它

# 3 Relational Database Services
6:12:59 Relational Database Services


Relational Database Service (RDS) - is a relational database service that supports multiple SQL engines. Relational is synonymous with SQL and Online Transactional Processing (OLTP). Relational database are the most commonly used type of database among tech companies and start-ups. ​

RDS Supports the following SQL Engines: ​
- MySQL – The most popular open-source SQL database that was purchased and now owned by Oracle.​
- MariaDB – When Oracle bought MySQL a fork (copy) of MySQL was made under a different open-source license.​
- Postgres (PSQL) – Most popular open-source SQL database among developers. Has rich-features over MySQL but at added complexity​
- Oracle – Oracle’s proprietary SQL database. Well used by Enterprise companies. You have to buy a license to use it.​
- Microsoft SQL Server – Microsoft’s proprietary SQL database. You have to buy a license to use it.​
- Aurora – Fully managed database.

Aurora 
- is a fully managed database of either MySQL (5x faster) and PSQL (3x faster) database.​ 
- 使用它, When you want a highly available, durable, scalable and secure relational database for Postgres or MySQL​

Aurora Serverless
- is the serverless on-demand version of Aurora. 
- 使用它,  When you want “most” of the benefits of Aurora but can trade to have cold-starts or you don’t have lots of traffic demand​

RDS on VMware 
- allows you to deploy RDS supported engines to on an-premise data-center. The datacenter must be using VMware for server virtualization. 
- 使用它, When you want databases managed by RDS on your own datacenter​


# 4 Other Database Services
6:15:48 Other Database Services

- Redshift 
    - is a petabyte-size data-warehouse. Data-warehouses are for Online Analytical Processing (OLAP)​ Data-warehouses can be expensive because they are keeping data “hot”. Meaning that we can run a very complex query and a large amount of data and get that data back very fast.​ 
    - 使用它, When you want to quickly generate analytics or reports from a large amount of data.​
- ElastiCache 
    - is a managed database of the in-memory and caching open-source databases Redis or Memcached. 
    - 使用它, When you need to improve the performance of application by adding a caching layer in-front of web-server or database.​
- Neptune 
    - is a managed graph database. Data is represented as interconnected nodes.​ 
    - 使用它, When you need to understand the connections between data eg. Mapping Fraud Rings or Social Media relationships​.
- Amazon Timestreams 
    - is a fully managed time series database. Think of devices that send lots of data that are time-sensitive such as IoT devices. 
    - 使用它, When you need to measure how things change over time.​
- Amazon Quantum Ledger Database 
    - is a fully managed ledger database that provides transparent, immutable and cryptographically variable transaction logs. ​
    - 使用它, When you need to record history financial activities that can be trusted
- Database Migration Service (DMS ) 用于数据迁移
    - is database migration service.  用于数据迁移 You can us it to migrate from:​
        - on-premise database to AWS​
        - from two database in different or the same AWS accounts using different SQL engines​
        - from an SQL to NoSQL database​

# 5 实际操作

## 5.1 DynamoDB Follow Along

![](image/Pasted%20image%2020230513145741.png)

用 PartiQL Query language 查询 DynamoDB
![](image/Pasted%20image%2020230513150315.png)

## 5.2 RDS Relation Dabase Service Follow Along
6:22:34 RDS Relation Database Service Follow Along



## 5.3 Redshift (Data warehouse)
6:28:51 Redshift Follow Along

![](image/Pasted%20image%2020230513151403.png)

Query data
![](image/Pasted%20image%2020230513151847.png)

![](image/Pasted%20image%2020230513151914.png)

![](image/Pasted%20image%2020230513152124.png)