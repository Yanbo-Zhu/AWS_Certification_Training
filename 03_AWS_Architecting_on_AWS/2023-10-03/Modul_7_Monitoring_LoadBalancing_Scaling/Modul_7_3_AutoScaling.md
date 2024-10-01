

The operations manager asks, “How can we dynamically increase and decrease capacity to meet changing demand?”
Your operations team needs to compare auto scaling features to determine best practices.


![](image/Pasted%20image%2020231003133603.png)

ssl offloading
ssl certizeiter are uploaded into alb . 所以 target 段 不在需要 ssl zertificate 
需要重听 


![](image/Pasted%20image%2020231003133500.png)


AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. Using AWS Auto Scaling, you can set up application scaling for multiple resources across multiple services in minutes.
The service provides a simple, powerful user interface that you can use to build scaling plans for resources. For example, these resources might include EC2 instances, Spot Fleets, and other compute and database services. AWS Auto Scaling makes scaling simple with recommendations for you to optimize performance and costs, or to balance between them.
AWS Auto Scaling provides application scaling for multiple resources such as Amazon EC2, Amazon DynamoDB, Amazon Aurora, and many more across multiple services  in short intervals



# 1 ec2 auto scaling 

![](image/Pasted%20image%2020231003133658.png)

With Amazon EC2 Auto Scaling, you can build scaling plans that automate how groups of different EC2 resources respond to changes in demand. You can optimize availability, costs, or a balance of both.
If you specify scaling policies, then Amazon EC2 Auto Scaling can launch or terminate instances as demand on your application increases or decreases. Amazon EC2 Auto Scaling integrates with ELB so that you can attach one or more load balancers to an existing Amazon EC2 Auto Scaling group. After you attach the load balancer, it automatically registers the instances in the group and distributes incoming traffic across the instances.
In the example, one VPC has two subnets in two separate Availability Zones. Two EC2 instances are launched in each subnet as part of one single auto scaling group. An existing load balancer is shown separately, but registering the auto scaling group is optional.


## 1.1 Elasticity: Scaling in and out


![](image/Pasted%20image%2020231023121337.png)

Cloud computing addresses the problem of overuse and underuse of resources through the concept of scaling. What does this concept mean? As your business grows and demand for your applications increases, your infrastructure costs will also increase over time. An elastic infrastructure can intelligently expand and contract as its capacity needs change.
Examples include the following:
• Increase the number of web servers when traffic spikes. • Lower write capacity on your database when that traffic goes down. • Handle the day-to-day fluctuation of demand throughout your architecture

--- 


![](image/Pasted%20image%2020231003133809.png)

In a traditional IT procurement model, to cope with this increase in demand, businesses must regularly invest up front in large purchases of infrastructure. They would continue to use this infrastructure until they needed more capacity, and then make another large investment.

----


![](image/Pasted%20image%2020231003133841.png)

However, demand is rarely linear or predictable. It is far more likely that workloads are spiky and variab

---
However, demand is rarely linear or predictable. It is far more likely that workloads are spiky and variab

![](image/Pasted%20image%2020231023121511.png)





---

![](image/Pasted%20image%2020231003133915.png)

The alternative is that a business underprovisions its infrastructure to save money or because it couldn’t have predicted a peak. It experiences a lost opportunity when demand outstrips the available environment. This situation can create a negative user experience. Consider the feeling of a website that crashes when you are trying to purchase newly released tickets to a popular show.


---

![](image/Pasted%20image%2020231003133944.png)

Using cloud technology, you can fit supply to demand through elastic cloud resources. Unlike traditional infrastructure, you don’t need to provision resources months in advance. You don’t need to keep resources that are not used, and you don’t need to worry as much about an inability to forecast customer demand.

## 1.2 Auyo Scaling components

![](image/Pasted%20image%2020231003134015.png)


Amazon EC2 Auto Scaling helps you to have the correct number of Amazon EC2 instances available to handle application load. You create collections of EC2 instances, called Auto Scaling groups. You can specify the minimum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling manages your group to never go below this size. You can specify the maximum number of instances in each Auto Scaling group, and Amazon EC2 Auto Scaling manages your group to never go above this size.
The graphic shows how to set up a group from start to finish. You learn about each of the three steps in the following slides.

---


![](image/Pasted%20image%2020231003134051.png)

Before you can create an Auto Scaling group using a launch template, you must create a launch template. This template includes the parameters required to launch an EC2 instance, such as the ID of the Amazon Machine Image (AMI) and an instance type. A launch template provides full functionality for Amazon EC2 Auto Scaling and also newer features of Amazon EC2. These features can include the current generation of Amazon EBS Provisioned IOPS volumes (io2), EBS volume tagging, T2 Unlimited instances, Elastic Inference, and Dedicated Hosts.
You are strongly encouraged to create Auto Scaling groups from launch templates to get the latest features from Amazon EC2. A launch configuration is an instance configuration template that an Auto Scaling group uses to launch EC2 instances. When you create a launch configuration, you must specify information about the EC2 instances to launch. Include the AMI, instance type, key pair, security groups, and block device mapping.
Alternatively, you can create a launch configuration by using attributes from a running EC2 instance.
For more information about templates, see "Create a launch template for an Auto Scaling group" in the Amazon EC2 Auto Scaling User Guide at https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-launch-template.html.
For more information about launch configurations, see "Create a launch configuration using an EC2 instance" in the Amazon EC2 Auto Scaling User Guide at https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-lc-with-instanceID.html.


---


![](image/Pasted%20image%2020231003134101.png)

## 1.3 

![](image/Pasted%20image%2020231003134150.png)

You can use the following tools to invoke scaling in your groups: • Health status checks – You can configure your group to maintain a specified number of running instances at all times. If an instance becomes unhealthy, the group terminates the unhealthy instance and launches another instance to replace it.
• CloudWatch alarms – A scaling policy instructs Amazon EC2 Auto Scaling to track a specific CloudWatch metric. It defines which action to take when the associated CloudWatch alarm is in the ALARM state.
• Schedules – You can scale by schedule. Actions are performed automatically as a function of time and date. Scaling by schedule is useful when you know exactly when to increase or decrease the number of instances in your group.
• Manual scaling – Manual scaling is the most basic way to scale your resources. Specify only the change in the maximum, minimum, or desired capacity of your group. Amazon EC2 Auto Scaling manages the process of creating or terminating instances to maintain the updated capacity.


---

health status check: 比如说 cpu 使用率过高 

![](image/Pasted%20image%2020231003134233.png)


--- 


![](image/Pasted%20image%2020231003134256.png)


With scheduled scaling, you can scale your application before known load changes. For example, every week, the traffic to your web application starts to increase on Wednesday, remains high on Thursday, and starts to decrease on Friday. You can plan your scaling activities based on the known traffic patterns of your web application.
With dynamic scaling, you define how to scale the capacity of your Amazon EC2 Auto Scaling group in response to changing demand. For example, suppose that you have a web application that currently runs on two instances. You want the CPU utilization of the group to stay at about 50 percent when the load on the application changes. As a result, you have extra capacity to handle traffic spikes without maintaining an excessive number of idle resources.

Use predictive scaling to increase the number of EC2 instances in your group in advance of daily and weekly
patterns in traffic flows. Predictive scaling is well suited for situations where you have:
• Cyclical traffic, such as high use of resources during regular business hours and low use of resources during evenings and weekends
• Recurring on-and-off workload patterns, such as batch processing, testing, or periodic data analysis 
• Applications that take a long time to initialize, which causes a noticeable latency impact on application performance during scale-out events

It is recommended that you scale out early and fast, while you scale in slowly over time


--- 


![](image/Pasted%20image%2020231003134347.png)

Amazon EC2 Auto Scaling supports multiple purchasing options within the same group. You can launch and automatically scale a fleet of On-Demand Instances and Spot Instances within a single Auto Scaling group. You can receive discounts for using Spot Instances. In addition, you can use Reserved Instances or a Savings Plan to receive discounted rates of the regular On-Demand Instance pricing. All of these factors combined help you to optimize your cost savings for EC2 instances, while ensuring that you obtain the desired scale and performance for your application.
Using Amazon EC2 Fleet, you can define a combination of EC2 instance types to make up the desired capacity of your group. This capacity is defined as a percentage of each type of purchasing option. Amazon EC2 Auto Scaling will maintain the desired cost optimization as your group scales in or out. Groups that are made up of mixed fleets still support the same lifecycle hooks, instance health checks, and scheduled scaling as a single-fleet group.
Learn more about optimizing cost. For more information, see “Auto Scaling groups with multiple instance types and purchase options” in the Amazon EC2 Auto Scaling User Guide at https://docs.aws.amazon.com/autoscaling/ec2/userguide/asg-purchase-options.html


# 2 Review 

![](image/Pasted%20image%2020231023122703.png)

Imagine that you are now ready to talk to the operations manager and present solutions that meet their architectural needs.
Think about how you would answer the questions from the beginning of the lesson.
Your answers should include the following solutions: 
• Use tools like CloudWatch metrics, CloudWatch Logs, CloudTrail, and VPC Flow Logs to monitor and log activity in your accounts.
• Configure CloudWatch alarms for existing metrics and use EventBridge to take action when a metric is in the ALARM state.
• Explore options available to you in Elastic Load Balancing. Choose either an Application Load Balancer, a Network Load Balancer, or a Gateway Load Balancer based on your use case.
• Prepare for changes in demand by using AWS Auto Scaling. For compute, use Amazon EC2 Auto Scaling to invoke scaling based on the expected demand for that workload. Use launch templates to build your configuration to support scaling in and out



# 3 Capstone Architecture 

At the end of this course is a Capstone Lab project. You will be provided a scenario and asked to build an architecture based on project data, best practices, and the Well-Architected Framework.


![](image/Pasted%20image%2020231003134450.png)


You notice that an ELB load balancer is added to balance the WordPress traffic across multiple EC2 instances. This arrangement also gives you fault-tolerance if one of your EC2 instances fails a health check for application traffic.
Your application servers that were added in the Compute module have been placed in an Amazon EC2 Auto Scaling group. This provision adds scalability to your application.
As your Auto Scaling group scales out, the launch template will use your AMI to launch application servers. User data in the launch template is processed during instance launch. You can use it to mount your Amazon Elastic File System (Amazon EFS) automatically at instance launch. The EC2 instances in the auto scaling group will launch with security groups that allow incoming traffic from the Amazon Aurora primary DB instance.
You have now learned about all of the services used in the Capstone Lab. You will revisit this architecture again on Day 3 to strengthen your knowledge on these topics.

Consider how you could continue expanding on this architecture by reviewing the following questions:
• How would you automate the creation of resources? 
• How would you duplicate this deployment in more than one account without manual effort?
• Can you use containers instead of virtual machines to control the application?
• Can you integrate this application with your on-premises network? 
• Do you need more than one account to be able to access this application? 
• What serverless strategies can you use to help with easy management of the application? 
• What is your disaster recovery strategy for this environment

# 4 Knowledge Check

a

![](image/Pasted%20image%2020231003134510.png)

The correct answer is A, Amazon EC2 instance.
A load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones to increase the availability of your application.


----

b 因为 只有这样 才能应对 unpredictable traffic 


![](image/Pasted%20image%2020231003134529.png)

The answer is B, dynamic.
This option gives you extra capacity to handle traffic spikes without maintaining an excessive number of idle resources.
Predictive scaling would be best for cyclical traffic, recurring on-and-off workload patterns, or applications that take a long time to initialize.


----

b

![](image/Pasted%20image%2020231003134644.png)

The correct answer is B, EventBridge.
EventBridge builds upon and extends CloudWatch Events. It uses the same service API and endpoint, and the same underlying service infrastructure. EventBridge reacts to events that other AWS services generate.

---


c d 

![](image/Pasted%20image%2020231003134717.png)

The correct answer is C and D, alarm and insufficient data. Amazon CloudWatch alarms have three possible states: OK, ALARM, and INSUFFICIENT_DATA.

----
a 不对 用 cloud watch 
b 是对的 
c 不对 因为 有application
d 是对的 
e 用 cloud watch 

![](image/Pasted%20image%2020231003134801.png)

The correct answer is B and D, store log data as a record of account usage and capture root login failures.
CloudTrail provides insight into who is doing what and when, by tracking user activity and API usage. CloudTrail does the following tasks: • Monitors and logs account activity across your AWS infrastructure • Records API call interactions for most AWS services • Automatically pushes logs to Amazon S3 • Captures root login failures



















