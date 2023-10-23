

![](image/Pasted%20image%2020231004135923.png)



![](image/Pasted%20image%2020231004140016.png)


![](image/Pasted%20image%2020231004140038.png)


Imagine you are meeting with the chief technology officer, who is creating a backup and disaster recovery plan. They are interested in learning more about the tools and strategies available in the cloud, which will protect data and minimize downtime. During this module, you learn about topics that answer these questions.
At the end of this module, you meet with the chief technology officer and present some solutions.


# 1 Disaster Planning



![](image/Pasted%20image%2020231004140120.png)

The chief technology officer asks, “What strategies can we use to protect ourselves in the event of a disaster?”
With many resources moving to the cloud, the company needs to better understand the disaster recovery features and strategies available for the AWS services they will be using. The company is asking you to summarize these features.




![](image/Pasted%20image%2020231004140135.png)

Not all disaster recovery (DR) plans are created equal, and many fail. Testing, resources, and planning are vital components of a successful DR plan.

Testing
Test your DR plan to validate the implementation. Regularly test failover to your workload’s DR Region to verify that you are meeting recovery objectives. Avoid developing recovery paths that you rarely run. For example, you might have a secondary data store that is used for read-only queries. Plan to fail over to your secondary data store when your primary fails.

Resources 
Regularly run your recovery path in production. This will validate the recovery path and help you verify that resources are sufficient for operation throughout the event. Changes in your configuration in production must be mirrored in your DR network.


Planning 
The only recovery that works is the path you test frequently. The capacity of the secondary resources, which might have been sufficient when you last tested, may no longer be able to tolerate your load. This is why it is best to have a small number of recovery paths. Establish recovery patterns and regularly test them.



--- 



![](image/Pasted%20image%2020231004140318.png)


Fault tolerance: even if a problem happens, you will still continue. Users are not going to.  因为 资源部署在了其他 azs 

Production systems typically come with defined or implicit objectives in terms of uptime. A system is highly available when downtime is minimized in the event of a failure. Downtime is not eliminated, but it should be reduced to seconds or minutes.
High availability minimizes downtime and cost. It protects against failure. It keeps your business running with very little downtime and fast recovery at low cost.
Fault tolerance is often confused with high availability, but fault tolerance refers to the built-in redundancy of an application's components to prevent service interruption. However, it is at a higher cost.
Backup is critical to protect data and to provide business continuity. At the same time, it can be a challenge to implement well. The pace at which data is generated is growing exponentially. The density and durability of local disks is not benefiting from the same growth rate. Enterprise backup has become its own industry.
Disaster recovery is often overlooked as a component of availability. If a natural disaster makes one or more of your components unavailable or destroys your primary data source, can you restore service quickly and without lost data?


--- 



![](image/Pasted%20image%2020231004140619.png)

AWS is available in multiple Regions around the globe. You can choose the most appropriate location for your DR site, in addition to the site where your system is fully deployed. It is highly unlikely for a Region to be unavailable. But it is possible if a very large-scale event impacts a Region—for instance, a natural disaster.
AWS maintains a page that inventories current products and services offered by Region. AWS maintains a strict Region isolation policy so that any large-scale event in one Region will not impact any other Region. We encourage our customers to take a similar multi-Region approach to their strategy. Each Region should be able to be taken offline with no impact to any other Region.
If you have an AWS Direct Connect circuit to any AWS Region in the United States (US), it will provide you with access to all Regions in the US, including AWS GovCloud (US), without that traffic going through the public internet. Also, consider how you deploy applications. If you deploy to each Region separately, you can isolate that Region in case of disaster, and transfer all of your traffic to another Region.
If you are deploying new applications and infrastructure rapidly, you may want to have an active-active Region. Imagine you deploy something that causes a Region's applications to misbehave or to be unavailable. You can remove the Region from the active record set in Amazon Route 53, identify the root cause, and roll back the change before reactivating the Region.




--- 


![](image/Pasted%20image%2020231004140732.png)


RTO: the time, from  disaster happens , to the timeout the application is available again 

RPO:  
So the the shorter the RPO is, the more frequent the backups must taken

上一次备份为 5 hours 前,  但是我们想把数据恢复成 30mins 前 的状态


Recovery Point Objective (RPO) is the acceptable amount of data loss measured in time. For example, if a disaster occurs at 1:00 p.m. (13:00) and the RPO is 12 hours, the system should recover all data that was in the system before 1:00 a.m. (01:00) that day. Data loss will, at most, span 12 hours—between 1:00 p.m. and 1:00 a.m.
Recovery Time Objective (RTO) is the time it takes after a disruption to restore a business process to its service level, as defined by the operational level agreement (OLA). For example, if a disaster occurs at 1:00 p.m. (13:00) and the RTO is 1 hour, the DR process should restore the business process to the acceptable service level by 2:00 p.m. (14:00).
A company typically decides on an acceptable RPO and RTO based on the financial impact to the business when systems are unavailable. The company determines financial impact by considering many factors, such as the loss of business and damage to its reputation because of downtime and the lack of systems availability. IT organizations plan solutions to provide cost-effective system recovery based on the RPO within the timeline and the service level established by the RTO.



---

![](image/Pasted%20image%2020231004141119.png)


Before discussing the various approaches to DR, it is important to review the AWS services and features that are the most relevant to it. This section provides a summary.
When planning for DR, consider the services and features that support data migration and durable storage. For some of the scenarios that involve either a scaled-down or a fully scaled deployment of your system in AWS, compute resources will be required as well.
During a disaster, you need to either provision new resources or fail over to existing preconfigured resources. These resources include code and content. But they can also include other pieces, such as Domain Name System (DNS) entries, network firewall rules, and virtual machines or instances.



---


![](image/Pasted%20image%2020231004141145.png)

When building your backup strategy, make a plan to duplicate your storage using a solution that meets your recovery needs.
AWS offers the following options for duplicating data in storage: • Amazon Simple Storage Service (Amazon S3) provides highly durable storage designed for mission-critical and
primary data storage. S3 Cross-Region Replication is a bucket-level configuration that permits copying objects across buckets in different AWS Regions.
• Amazon Simple Storage Service Glacier (Amazon S3 Glacier) provides low-cost storage for data archiving and backup. Archives are optimized for infrequent access when retrieval times of several hours are adequate.
• Amazon Elastic Block Store (Amazon EBS) gives you the ability to create point-in-time snapshots of data volumes. When the snapshot status is Completed, you can copy it from one AWS Region to another, or within the same Region.
• AWS Snow Family is a family of data transport solutions that move terabytes (TB) to petabytes of data into and out of AWS using storage devices. It is designed to be secure for physical transport. Snow Family devices help you retrieve a large quantity of data stored in Amazon S3 much quicker than using high-speed internet.
• Use AWS DataSync to sync files from on-premises or in-cloud file systems to Amazon Elastic File System (Amazon EFS). DataSync copies files over the internet or an AWS Direct Connect connection.


--- 



![](image/Pasted%20image%2020231004141327.png)



In the context of DR, it’s critical to be able to rapidly create virtual machines that you control. By launching instances in separate Availability Zones, you can protect your applications from the failure of a single location.
You can arrange for automatic recovery of an Amazon EC2 instance when a system status check of the underlying hardware fails. The instance will be rebooted (on new hardware if necessary). But it will retain its instance ID, IP address, Elastic IP addresses, Amazon EBS volume attachments, and other configuration details. For the recovery to be complete, you need to make sure that the instance automatically starts up any services or applications as part of its initialization process.
Amazon Machine Images (AMIs) are preconfigured with operating systems. Some preconfigured AMIs also include application stacks. You can also configure your own AMIs. In the context of DR, AWS strongly recommends that you configure and identify your own AMIs so that they can launch as part of your recovery procedure. Your AMIs should be preconfigured with your operating system of choice, plus the appropriate pieces of the application stack

---




![](image/Pasted%20image%2020231004141419.png)


When you are dealing with a disaster, you might need to fail over to another site. This requires modifying network settings to initiate the failover. It might also require adjusting network settings within the failover site. AWS offers several services and features that you can use to manage and modify network settings: 
• Route 53 includes a number of global load balancing capabilities. This can be effective when you are dealing with DNS endpoint health checks, the ability to failover between multiple endpoints, and static websites hosted in Amazon S3.
• ELB automatically distributes incoming application traffic across multiple Amazon EC2 instances. You achieve greater fault tolerance in your applications by ELB providing the load-balancing capacity that is needed in response to incoming application traffic. You can pre-allocate your load balancer to identify its DNS name and simplify running your DR plan. Amazon Route 53 and ELB are highly available resources by default.
• In the context of DR, you can use Amazon VPC to extend your existing network topology to the cloud. This can be especially appropriate when recovering enterprise applications that are typically on the internal network.
• Set up a dedicated network connection from your premises to AWS with Direct Connect. This can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections.



---



![](image/Pasted%20image%2020231004141515.png)


With Amazon RDS, you can plan for high availability using the following methods: 
• Create a Multi-AZ DB instance deployment, which creates a primary instance and a standby instance to provide failover support. However, the standby instance does not serve traffic.
• Create a Multi-AZ DB cluster deployment, which creates two standby instances that can also serve read traffic.
• Use a snapshot to create a Read Replica in a different Region. This replica can be promoted to primary in the event of disaster.
    o Promoting a Read Replica requires a reboot and has a higher RTO than failing over to a standby instance.
• Save a manual database (DB) snapshot or a DB cluster snapshot in a separate Region. 
• Share a manual snapshot with up to 20 other AWS accounts.

Amazon RDS Read Replicas for MySQL and MariaDB now support Multi-AZ deployments. By running a secondary copy of a database, you can build a resilient DR strategy and simplify your database engine upgrade process.

Global tables build on the DynamoDB global footprint to provide you with the following: 
• A fully managed, multi-Region, and multi-active database that replicates your DynamoDB tables. 
• A replica of your DynamoDB tables across your choice of AWS Regions. Unlike read replicas and secondary instances, DynamoDB treats all replicas in a global table as a single unit, with every table having the same table name and primary key. If one replica fails, you can access data using replicas in other Regions.


----


![](image/Pasted%20image%2020231004141553.png)

Time is valuable in DR. Use AWS CloudFormation templates and scripting to deploy your resources efficiently. Use CloudFormation to define your infrastructure and deploy it consistently across AWS accounts and Regions. CloudFormation uses predefined pseudo-parameters to identify the AWS account and AWS Region in which it is deployed. You can implement condition logic in your CloudFormation templates to deploy the scaled-down version of your infrastructure in the DR Region.
For EC2 instance deployments, an AMI supplies information about hardware configuration and installed software. You can implement an EC2 Image Builder pipeline that creates the AMIs you need. Copy these to both your primary and backup Regions to provide everything you need to redeploy or scale-out your workload in a new Region.
To start EC2 instances or provision other AWS resources, you can create scripts using AWS Command Line Interface (AWS CLI) or AWS SDK


# 2 AWS Backup 



![](image/Pasted%20image%2020231004141634.png)

The chief technology officer asks, “How can we centralize and automate our backup strategy?”
To increase the efficiency and reliability of their backup strategy, the company would like to manage backups from a single location. The company is asking you to propose a solution that meets this requirement.


![](image/Pasted%20image%2020231004141645.png)

AWS Backup is a fully managed backup service that helps you centralize and automate the backup of data across AWS services. AWS Backup also helps customers support their regulatory compliance obligations and meet business continuity goals.
AWS Backup works with AWS Organizations. It centrally deploys data protection policies to configure, manage, and govern your backup activity. It works across your AWS accounts and resources, including Amazon EC2 instances and Amazon EBS volumes. You can back up databases such as DynamoDB tables, Amazon DocumentDB and Amazon Neptune graph databases, and Amazon RDS databases, including Amazon Aurora database clusters. You can also back up Amazon EFS, Amazon S3, AWS Storage Gateway volumes, and all versions of Amazon FSx, including FSx for Lustre and FSx for Windows File Server.
For a full list of AWS services supported by AWS Backup, see “AWS Backup” (https://aws.amazon.com/backup/).
For more information about managing backups, see “AWS Backup – Automate and Centrally Manage Your Backups” in the AWS News Blog (https://aws.amazon.com/blogs/aws/aws-backup-automate-and-centrally-manage-your-backups/).



![](image/Pasted%20image%2020231004141719.png)

Simplicity – AWS simplifies your backup plan. Unlike other tools, AWS Backup does not need custom backup scripts. It provides a central place to manage and monitor your backups. The AWS Backup plan is a set of rules that define your backup. The rules include when to start the backups, the duration of the backup window, and the retention period. One of the core capabilities of AWS Backup is the ability to use tags to affect the backup of resources you’d like to protect.
Compliance – You can enforce backup policies, encrypt your backups, protect your backups from manual deletion, and prevent changes to your backup lifecycle settings. You can use the consolidated logs of backup activity across AWS services to perform compliance audits. AWS Backup complies with Payment Card Industry (PCI) and International Organization for Standardization (ISO) standards, and is eligible under Health Insurance Portability and Accountability Act (HIPAA).
Control costs – AWS Backup reduces the risk of downtime, which can negatively impact your business. You can also reduce operating costs by reducing time spent on manual configuration and by automating backups.



--- 



![](image/Pasted%20image%2020231004141810.png)


aws backup ist integrated with aws organization 


When you create a backup plan, you specify the following: • Schedule – Set the frequency of the backups and the window of time during which to conduct backups. 
• Lifecycle – Determine when a backup is moved to cold storage, and when a backup expires. 
• Vault – AWS Backup keeps backups in an AWS Backup vault. You specify which backup vault your backup plan uses.
    o When you create a backup vault, you assign an AWS Key Management Service (AWS KMS) encryption key to encrypt backups that do not have their own encryption methods.
• Tags for backup – You specify tags that will be assigned to backups created by this plan.

You assign the resources to back up with your backup plan. You also define which AWS Identity and Access Management (IAM) role that AWS Backup will use to gain the needed access to these resources. You can assign resources using the following methods: • Tags – You can provide a tag value; all AWS resources with that tag will be backed up using this plan. • Resource IDs – You can use Resource IDs for specific resources, such as a specific DynamoDB table or Amazon EBS volume.
AWS Backup works with other AWS services to monitor its workloads, such as Amazon CloudWatch, Amazon EventBridge, AWS CloudTrail, and Amazon Simple Notification Service (Amazon SNS).
For more information about using these services to monitor activity in AWS Backups, see “Monitoring” in the AWS Backup Developer Guide (https://docs.aws.amazon.com/aws-backup/latest/devguide/monitoring.html).
For more information about managing backup policies across accounts with AWS Organizations, see “Managing AWS Backup resources across multiple AWS accounts” in the AWS Backup Developer Guide (https://docs.aws.amazon.com/aws-backup/latest/devguide/manage-cross-account.html).



# 3 Recovery strategies 

![](image/Pasted%20image%2020231004141911.png)
The chief technology officer asks, “Which disaster recovery strategy minimizes downtime but is also cost effective?”
The company is exploring configurations that will deliver business continuity and minimize downtime in the event of an error. Some of these solutions are more expensive than others. The company is asking you to summarize these strategies and their relative cost



![](image/Pasted%20image%2020231004141948.png)

This section outlines four DR scenarios that highlight the use of AWS and then compares AWS with traditional DR methods (sorted from highest to lowest RTO and RPO), as follows: 
1. Backup and restore 2. Pilot light 3. Warm standby 4. Multi-site active/active


--- 



![](image/Pasted%20image%2020231004142019.png)

In most traditional environments, data is backed up to tape and sent offsite regularly. If you use this method, it can take a long time to restore your system in the event of a disruption.
Amazon S3 is an ideal destination for quick access to your backup. You typically transferring data to and from Amazon S3 through the network and it is therefore accessible from any location. You can also use a lifecycle policy to move older backups to progressively more cost-efficient storage classes over time.
In this example, data from a remote server is backed up to Amazon S3 into /mybucket. A lifecycle policy moves each backup to S3 Standard-Infrequent Access (S3 Standard-IA) once it has been in /mybucket for some time. Later, the backup is moved to Amazon S3 Glacier.
If the remote server fails, you can restore services by deploying a disaster recovery VPC. Use CloudFormation to automate deployment of core networking. Create an EC2 instance using an AMI that matches your remote server. Then restore your systems by retrieving your backups from Amazon S3. You then adjust DNS records to point to AWS


-----


![](image/Pasted%20image%2020231004142132.png)


With the pilot light approach, you replicate your data from one environment to another and provision a copy of your core workload infrastructure. In this example, you replicate the production web server, app server, and database in a recovery environment. Route 53 routes all traffic to the production environment.
Resources required to support data replication and backup, such as databases and object storage, are always on. Other elements, such as application servers, are loaded with application code and configurations, but are switched off. These elements are only used during testing or when disaster recovery failover is invoked. Unlike the backup and restore approach, your core infrastructure is always available. You always have the option to quickly provision a full-scale production environment by switching on and scaling out your application servers.
The pilot light architecture is relatively inexpensive to implement. In the preparation phase of DR, it is important to consider the use of services and features that support data migration and durable storage


![](image/Pasted%20image%2020231004142319.png)

When disaster strikes, the servers in the recovery environment start up. Route 53 then begins sending production traffic to the recovery environment. The essential infrastructure pieces include DNS, networking features, and various Amazon EC2 features.
For more information about pilot light solutions, see “Disaster Recovery (DR) Architecture on AWS, Part III: Pilot Light and Warm Standby” in the AWS Architecture Blog (https://aws.amazon.com/blogs/architecture/disaster-recovery-dr-architecture-on-aws-part-iii-pilot-light-and-warm-standby/).


----

![](image/Pasted%20image%2020231004142402.png)


build a complete copy with in at low capacity 

The warm standby approach involves creating a scaled down, but fully functional copy of your production environment in a recovery environment. By identifying your business-critical systems, you can fully duplicate these systems on AWS and have them always on. This decreases the time to recovery because you do not have to wait for resources in the recovery environment to start up.
In this example, you replicate the web servers and app servers in the recovery environment as Auto Scaling groups. The Auto Scaling groups can run the minimum number of instances and smallest EC2 instance sizes possible. This solution is not scaled to take a full production load, but it is fully functional. You can use it for nonproduction work, such as testing, quality assurance, and internal use. Use Route 53 to distribute requests between the production and recovery environments. You copy the database into the recovery environment and use data replication to keep it current.
In the diagram, there are two systems running: the production environment and a low-capacity system running in the recovery environment. Warm standby in the recovery environment requires that all necessary components run continuously, but not scaled for production traffic. It is best practice to do continuous testing using a subset of production traffic to the DR site.


![](image/Pasted%20image%2020231023154223.png)


If the production environment is unavailable, Route 53 switches over to the recovery environment. The recovery environment automatically scales its capacity out in the event of a failover from the primary system. For your critical loads, warm standby RTO is as long as it takes to fail over. For all other loads, it takes as long as it takes you to scale up. The RPO depends on the replication type.

---


![](image/Pasted%20image%2020231004142516.png)


In an active/active configuration, a multi-site solution runs in two environments. In this example, both Production A and Production B environments run web servers, app servers, and databases to handle production traffic. Route 53 routes traffic between the two environments.
This architecture potentially has the least amount of downtime. It has more costs associated with it, because more environments are running. You can use a DNS service that supports weighted routing, such as Route 53, to route production traffic to different sites that deliver the same application or service.

![](image/Pasted%20image%2020231023154310.png)

In a disaster situation in the Production A environment, you can adjust the DNS weighting and send all traffic to the Production B environment. The capacity of the AWS service can be rapidly increased to handle the full production load. You can use Amazon EC2 Auto Scaling to automate this process. You might need some application logic to detect the failure of the primary database services and cut over to the parallel database services running in AWS.
This pattern potentially has the least amount of downtime. It has more costs associated with it, because more systems are running. The cost of this scenario is determined by how much production traffic is handled by AWS during normal operation. In the recovery phase, you pay for only what you use for the duration that the DR environment is required at full scale. To further reduce cost, purchase Amazon EC2 Reserved Instances for AWS servers that must be always on.
For more information about multi-site active/active solutions, see “Disaster Recovery (DR) Architecture on AWS, Part IV: Multi-site Active/Active” in the AWS Architecture Blog (https://aws.amazon.com/blogs/architecture/disaster-recovery-dr-architecture-on-aws-part-iv-multi-site-active-active/).

--- 


DR: DIaster recovery 

![](image/Pasted%20image%2020231004142725.png)


You deliver business continuity by making sure that critical business functions continue to operate or recover quickly despite serious disasters. Applications can be placed on a spectrum of complexity.
The figure shows a spectrum for the four scenarios, arranged by how quickly a system can be available to users after a DR event. With AWS, you can operate each of these DR strategies in a cost-effective way. These are just examples of possible approaches. Other variations and combinations of these are also possible.
In case of disaster, both pilot light and warm standby offer the capability to limit data loss (RPO). Both offer sufficient RTO performance that limits downtime. Between these two strategies, you have a choice of optimizing for RTO or for cost.


# 4 Review 

![](image/Pasted%20image%2020231004142814.png)

Imagine you are now ready to talk to the chief technology officer and present solutions that meet their architectural needs. Think about how you would answer the questions from the beginning of the lesson.
Your answers should include the following solutions: 
• Some of the ways the company can protect itself in the event of a disaster are the following: 
    • Duplicate data using different AWS storage services. 
    • Create quickly deployable AMIs to launch compute resources. 
    • Design the network with multiple failover mechanisms that will route traffic away from failed components.
    • Use database snapshots and backups.
• AWS Backup is a fully managed backup service that you can use to centralize and automate the backup of data across AWS services.
• The company should choose between backup and restore, pilot light, low-capacity standby on AWS, and multi-site active/active DR solutions.


# 5 Knowledge Check 

b

![](image/Pasted%20image%2020231004142824.png)

The correct answer is B, Pilot light.
The pilot light architecture is relatively inexpensive to implement. Other elements, such as application servers, are loaded with application code and configurations, but are switched off. These elements are only used during testing or when disaster recovery failover is invoked. Unlike the backup and restore approach, your core infrastructure is always available. You always have the option to quickly provision a full-scale production environment by switching on and scaling out your application servers.


---

b


![](image/Pasted%20image%2020231004142911.png)


The correct answer is B, Pilot light.
The pilot light architecture is relatively inexpensive to implement. Other elements, such as application servers, are loaded with application code and configurations, but are switched off. These elements are only used during testing or when disaster recovery failover is invoked. Unlike the backup and restore approach, your core infrastructure is always available. You always have the option to quickly provision a full-scale production environment by switching on and scaling out your application servers.



-----


a c e 

worng d: no read replicas 



![](image/Pasted%20image%2020231004142924.png)


The correct answers are A, C, and E, encrypted backups, works across multiple services, and incremental backups.
Encrypted backups – Set the AWS KMS encryption key used to encrypt backups in the vault.
Works across multiple services – AWS Backup works across your AWS accounts. It includes Amazon EC2 instances, Amazon EBS volumes, Amazon RDS databases, DynamoDB tables, Amazon EFS, FSx for Lustre, FSx for Windows File Server, and Storage Gateway volumes. The protection for Amazon RDS databases includes Aurora clusters.
Incremental backups – AWS Backup stores your periodic backups incrementally. The first backup of an AWS resource backs up a full copy of your data. For each successive incremental backup, only the changes to your AWS resources are backed up.
For more information about AWS Backup features, see “AWS Backup features” (https://aws.amazon.com/backup/features/).



-------

b

![](image/Pasted%20image%2020231004143053.png)

1 highly available
2 minimalize  TRO  


The correct answer is B, Run a Multi-AZ DB instance in the same Region.
Multi-AZ is a feature of Amazon RDS that provisions a standby replica in another Availability Zone. The replica is kept in sync with your primary RDS instance.
In case of an infrastructure failure, Amazon RDS performs an automatic failover to the standby. In this way, you can resume database operations as soon as the failover is complete. The DB instance that failed is replaced with a new standby replica. Failover to a standby instance is faster than promoting a read replica because a read replica has to reboot.











