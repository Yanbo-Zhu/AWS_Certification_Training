


![](image/Pasted%20image%2020231003124018.png)


![](image/Pasted%20image%2020231003124127.png)

![](image/Pasted%20image%2020231003124159.png)


Imagine that your operations manager meets with you to discuss how to monitor resources and scale operations in your Amazon Web Services (AWS) accounts. Here are some questions that they are asking about monitoring and scaling.
At the end of this module, you meet with the operations manager and present some solutions. 

# 1 Monitoring 简介



![](image/Pasted%20image%2020231003124245.png)

The operations manager asks, “What tools and services are available to monitor and log activity in our AWS accounts?”
You and the operations team must examine tools that are used in monitoring activity so that you can help build an easy-to-manage architecture


![](image/Pasted%20image%2020231003124315.png)


Monitoring your environment is one of the most important things to think about when creating architecture. You will always need a way to keep track of how your resources are operating and performing. Monitoring gives you the information to answer the question: Does something need to change?

Here are a few points to remember:
• With monitoring, you gather information about resource utilization and application performance. Monitoring measures whether your infrastructure is satisfying demand. It helps you build an architecture that scales up for more demand and pulls back when there is less demand.
• This kind of scaling provides a better user experience for your customers and saves you money. 
• Monitoring is important for security. With parameters in place, you can see if and when users are accessing parts of your environment, and verify permissions.


# 2 Amazon CloudWatch

![](image/Pasted%20image%2020231003124419.png)

Amazon CloudWatch is an AWS service that provides a near-real-time stream of system events. The events describe changes to your AWS resources. With CloudWatch, you can respond quickly to operational changes and take corrective action. CloudWatch alarms send notifications or automatically make changes to the resources that you are monitoring based on rules that you define.
For example, you can monitor the CPU usage and disk reads and writes of your Amazon Elastic Compute Cloud (Amazon EC2) instances. This data can be used to determine whether you should launch additional instances to handle increased load. You can also use this data to stop underused instances to save money. Besides monitoring the built-in metrics that come with AWS, you can create and monitor custom metrics. With CloudWatch, you gain system-wide visibility into resource use, application performance, and operational health.
You can collect, access, and correlate this data in one place from across all of your AWS resources, applications, and services. CloudWatch also collects from on-premises servers. To optimize performance and resource use, CloudWatch provides automatic dashboards, data with one-second granularity, and up to 15 months of metrics storage and retention.
For more information about CloudWatch, see “What is Amazon CloudWatch?” in the Amazon CloudWatch User Guide at https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html.




dashboards: by default: 3 dashboards, 3 per month

![](image/Pasted%20image%2020231003124709.png)

Metrics are data about the performance of your systems. By default, many services provide you with metrics for resources. For example, these resources might include Amazon EC2 instances, Amazon Elastic Block Store (Amazon EBS) volumes, and Amazon Relational Database Service (Amazon RDS) DB instances. CloudWatch stores data about a metric as a series of data points. Each data point has an associated timestamp.

You can publish your own metrics to CloudWatch. Use the AWS Management Console to view statistical graphs of your published metrics.

You can also turn on detailed monitoring for some resources, such as your Amazon EC2 instances, or publish your own application metrics. Amazon CloudWatch can load all the metrics in your account (both AWS resource metrics and application metrics that you provide) for search, graphing, and alarms. Metric data is kept for 15 months, so you can view both up-to-the-minute data and historical data.

A CloudWatch metric includes the following components: 
• A namespace is a container for CloudWatch metrics. Metrics in different namespaces are isolated from each other so that metrics from different applications are not mistakenly aggregated into the same statistics. You can specify a namespace name when you create a metric. The AWS namespaces use the following naming convention: AWS/service. In the example, the namespace is AWS/EC2.
• A metric represents a time-ordered set of data points that are published to CloudWatch. Think of a metric as a variable to monitor, and the data points represent the values of that variable over time. Each metric data point must be associated with a timestamp. If you do not provide a timestamp, CloudWatch creates a timestamp for you based on the time that the data point was received.
• A dimension is a name-value pair that uniquely identifies a metric. You can assign up to 10 dimensions to a metric. Every metric has specific characteristics that describe it. You can think of dimensions as categories for those characteristics. In the example, the dimension is the instance ID.
To graph metrics in the console, you can use CloudWatch Metrics Insights, a high-performance structured query language (SQL) query engine. Use it to identify real-time trends and patterns within all of your met
# 3 Logging 


![](image/Pasted%20image%2020231003124832.png)


log: it slides down what events happened

四种不同的 方式  侧重不同 


Plan for logging as you build. Review the following services to understand how they support logs: 
• Amazon CloudWatch Logs monitor, store, and access your log files from Amazon EC2 instances, AWS CloudTrail, Amazon Route 53, and other resources.
• AWS CloudTrail provides event history of your account activity, including actions taken through the console, AWS SDK, command line interface (CLI), and AWS services. This event history simplifies security analysis, resource change tracking, and troubleshooting. CloudTrail facilitates governance, compliance, and operational and risk auditing. With CloudTrail, you can log, continuously monitor, and retain account activity that is related to actions across your AWS infrastructure.
• VPC Flow Logs captures information about the IP traffic that goes to and from network interfaces in your virtual private cloud (VPC).
• Load balancing provides access logs that capture detailed information about requests that are sent to your load balancer. You can use custom logs from your applications.

For more information about logging and events, see “Logging and Events” in the AWS Technical Guide at https://docs.aws.amazon.com/whitepapers/latest/aws-security-incident-response-guide/logging-and-events.html.
For more information about application log files, see “Store and Monitor OS & Application Log Files with Amazon CloudWatch” on AWS News Blog at https://aws.amazon.com/blogs/aws/cloudwatch-log-service/.


---
## 3.1 CloudWatchLogs
- someone send log to here


![](image/Pasted%20image%2020231003125338.png)



这个例子中 , metric filter 只提取 error 的 log ,放到 metrics


The example shows two identical web servers that record data to the same log file, which is called server.log. One server is in Amazon EC2, and the other is a virtual machine on premises.
Both servers are able to publish events in the log file to a log stream. A log stream is a sequence of log events that share the same source. Each separate source of logs in CloudWatch Logs makes up a separate log stream.
Multiple log streams can be collected in a single log group. A log group shares the same retention, monitoring, and access control settings across all streams. You can define log groups and specify which streams to put into each group. There is no limit to the number of log streams that can belong to one log group.
After you create a log group, you can use metric filters to search for and match terms, phrases, or values in your log events. When a metric filter finds one of the terms, phrases, or values in your log events, you can increment the value of a CloudWatch metric. For example, you can count occurrences of a single term, such as the word error, in a metric called LogFile-ErrorCount.
Metrics can be monitored and invoke alarms, which is covered later in this module.
For more information about CloudWatch log functionality, see “Working with log groups and log streams” in the Amazon CloudWatch Logs User Guide at https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/Working-with-log-groups-and-streams.html.
Learn more about collecting metrics and logs. For more information, see “Collect metrics and logs from Amazon EC2 instances and on-premises servers with the CloudWatch agent” in Amazon CloudWatch User Guide at https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html.

## 3.2 AWS CloudTrail 

track user activity and api activity , api call 

![](image/Pasted%20image%2020231003125600.png)

![](image/Pasted%20image%2020231003125835.png)

Cloudtrail can send log into a Bucket in local server 


AWS CloudTrail provides insight into who did what and when by tracking user activity and API usage. With CloudTrail, you can get a history of AWS API calls in your account. These calls can be made through the console, AWS SDKs, CLI, and higher-level AWS services. CloudTrail records the AWS API calls and delivers the log files to you. The information includes the source IP address and identity of the API caller. It also includes the time of the call, the request parameters, and the response elements that the AWS service returns.
The AWS API call history that CloudTrail produces can facilitate security analysis, tracking of resource changes, and compliance auditing.
You turn on CloudTrail on a per-Region basis. If you use multiple Regions, you can choose where log files are delivered for each Region. CloudTrail saves the logs in your designated Amazon Simple Storage Service (Amazon S3) bucket. You might have a separate S3 bucket for each Region, or you can aggregate log files from all Regions into a single S3 bucket.

CloudTrail helps you answer questions that require detailed analysis. Store your CloudTrail API usage logs in an S3 bucket. You can analyze those logs later to answer compelling questions, for example:
• Why was a long-running instance terminated and who terminated it? (organizational traceability and accountability)
• Who changed a security group configuration? (accountability and security auditing) 
• What activities were denied due to lack of permissions? (potential internal or external attack against the network)

For more information about CloudTrail supported services and integrations, see “CloudTrail supported services and integrations” in the AWS CloudTrail User Guide at http://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-supported-services.html.

---



![](image/Pasted%20image%2020231003125907.png)


This example log file shows that an AWS Identity and Access Management (IAM) user named Alice called the EC2 StopInstances action. Alice used the ec2-stop-instances command in AWS Command Line Interface (AWS CLI). In this section of the log, you get information about who made the request.


![](image/Pasted%20image%2020231003125948.png)




![](image/Pasted%20image%2020231003130003.png)


![](image/Pasted%20image%2020231003130046.png)


create a new CloudTrail 

![](image/Pasted%20image%2020231003130201.png)

---


![](image/Pasted%20image%2020231003130242.png)
In this section of the script, you get information about the focus of the request. In this case, the focus of the request was an instance, and you can see the instance ID: i-abcdefg01234567890.


---


![](image/Pasted%20image%2020231003130250.png)

This section of the script can tell you when the API call occurred, what the API call was (StopInstances), and in what Region it occurred

---

![](image/Pasted%20image%2020231003130259.png)

In this section of the script, you get information about the response. In this case, the instance was stopped.

only the call to aws services will be logged 
 the call to aws ec2 instance will be logged 



## 3.3 VPC FLOW Logs 


![](image/Pasted%20image%2020231003130347.png)


VPC Flow Logs capture IP traffic information to and from VPC network interfaces. • They can be configured to record traffic per VPC, subnet, or network interface. 
• You can view information about your flow logs in the Amazon EC2 and Amazon VPC consoles by choosing the Flow Logs tab for a specific resource.
• Flow logs are turned off by default. You must opt in to collect flow log data.
Flow logs are published to either Amazon S3 buckets or CloudWatch log groups. Data is collected outside the path of your network traffic, and therefore does not affect network throughput or latency. Flow logs can help
you perform several tasks, such as: • Diagnose overly restrictive security group rules. • Monitor the traffic that is reaching your instance. • Determine the direction of the traffic to and from the network interfaces.

For more information about flow logs, see “Logging IP traffic using VPC Flow Logs” in the Amazon VPC User Guide at https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html.
Learn about improving security by analyzing VPC flow logs. For more information, see “Improve security by analyzing VPC flow logs with Amazon CloudWatch Contributor Insights” in the AWS Cloud Operations & Migrations Blog at https://aws.amazon.com/blogs/mt/improve-security-by-analyzing-vpc-flow-logs-with-amazon-cloudwatch-contributor-insights/


---



![](image/Pasted%20image%2020231003130415.png)

Each record captures a network IP traffic flow for a specific capture window and contains five different values, also known as a 5-tuple. A record includes different components of IP flow, such as the source, destination, and protocol. You can create alarms that will activate if certain types of traffic are detected, and metrics to help you identify trends and patterns.
The information includes an ACCEPT or REJECT action, based on security group and network access control list (network ACL) rules. It also includes source and destination IP addresses, ports, and the Internet Assigned Numbers Authority (IANA) protocol number. In addition, it includes packet and byte counts (a time interval during which the flow was observed).
Flow logs don’t capture everything in your network. VPC logging does not include Domain Name System (DNS) traffic or Dynamic Host Configuration Protocol (DHCP) requests and responses. If you’re running your own DNS server, you can log request resolution traffic. But many users rely on internal AWS DNS servers, and VPC Flow Logs will not capture activity between the servers and AWS DNS services. DHCP traffic is also not recorde




# 4 Alarms: CloudWatch alarms 

The operations manager asks, “How can we set thresholds and be alerted to changes in our infrastructure?” The operations team must examine AWS services that are used to help automate actions based on ev

![](image/Pasted%20image%2020231003130600.png)

A metric alarm watches a single CloudWatch metric. The alarm performs one or more actions based on the value of the metric relative to a threshold over a number of time periods. The action can be an Amazon EC2 action, an auto scaling action, or a notification sent to an Amazon Simple Notification Service (Amazon SNS) topic.


---


![](image/Pasted%20image%2020231003130844.png)


An alarm has three possible states:
• OK – The metric is within the defined threshold. 
• ALARM – The metric is outside the defined threshold.
• INSUFFICIENT_DATA – The alarm has started, the metric is not available, or not enough data is available for the metric to determine the alarm state.

ALARM is only a name that is given to the state and does not necessarily signal an emergency condition that requires immediate attention. It means that the monitored metric is equal to, greater than, or less than a specified threshold value. You could, for example, define an alarm that tells you when your CPU utilization for a given EC2 instance is too high. You might process this notification programmatically to suspend a CPU-intensive job on the instance. You can also send a notification to take action to notify the application owner.

INSUFFICIENT_DATA can be returned when no data exists for a given metric. An example is the depth of an empty Amazon Simple Queue Service (Amazon SQS) queue. It can also be an indicator that something is wrong in your system.

insufficient data: 就是没有给alram 足够的 条件, 不知道什么时候出发 
alarm 有延后性


--- 

![](image/Pasted%20image%2020231003130937.png)

To create an alarm based on a metric math expression, choose one or more CloudWatch metrics to use in the expression. Then, specify the expression, threshold, and evaluation periods.
• Statistics are metric data aggregations over specified periods of time. For a metric alarm, it is evaluated on one statistic. Some of the most common statistics that you can choose are sample count, sum, average, maximum, minimum, and percentile.
• Period is the length of time to evaluate the metric or expression to create each individual data point for an alarm. It is expressed in seconds. If you choose one minute as the period, the alarm evaluates the metric once per minute.
• Evaluation Periods is the number of the most recent periods, or data points, to evaluate when determining the alarm state. In the example table, this number is the second number in the 2 of 2 value.
• Datapoints to Alarm is the number of data points within the Evaluation Periods that must be breaching to cause the alarm to reach ALARM state. The breaching data points don't need to be consecutive. However, they must all be within the last number of data points equal to the Evaluation Period.

In the example, the alarm threshold is set to 25 percent and the minimum breach is two periods. That is, the alarm state changes, and it invokes its action only when the threshold is breached for two consecutive periods. You control this value. You can also set how the alarm treats missing data points. In some cases, you might want to build your alarm to go to the INSUFFICIENT_DATA state for missing data rather than an ALARM state.
In the metric graph, this circumstance happens with the third through fourth and fifth periods. The alarm's state is set to ALARM at 1:20 PM. At period six, the value dips below the threshold and the state reverts to OK at 1:25 PM.
For more information about CloudWatch alarms, see “Using Amazon CloudWatch alarms” in the Amazon CloudWatch User Guide at https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html.

# 5 Event: Amazon EventBridge 

eventbridge can track lambda function 
靠 cloudWatch alram 发出 eventBridge 

![](image/Pasted%20image%2020231003131106.png)


Amazon EventBridge removes the friction of writing point-to-point integrations. You can access changes in data that occur in both AWS and software as a service (SaaS) applications through a highly scalable, central stream of events.
EventBridge is the preferred way to manage your events that are captured in CloudWatch. CloudWatch Events and EventBridge are the same underlying service and API, but EventBridge provides more features. Changes that you make in either CloudWatch or EventBridge will appear in each console.
With EventBridge, you get a simple programming model where event publishers are decoupled from event subscribers. You can build loosely coupled, independently scaled, and highly reusable event-driven applications.
Because it’s fully managed, it handles everything from event ingestion and delivery to security, authorization, and error-handling, so you can build scalable, event-driven applications. EventBridge is serverless, so you have no infrastructure to manage and you only pay for the events that you consume.
You only pay for events that your own applications or SaaS applications generate.


--- 


![](image/Pasted%20image%2020231003131420.png)

In the example, an EC2 instance reports the CPUUtilization metric data to CloudWatch. A custom alarm is created and configured, called CPUAbove90Percent, so that you will know when the EC2 instance is being overused.
EventBridge rules are built to notify your support team when the CPUAbove90Percent alarm is in ALARM state, so that they can investigate and take action. EventBridge takes two actions. It sends an email to subscribed recipients by using the Amazon SNS topic, and sends a rich notification to the operation team’s third-party monitoring tool.

Think about how you could take this further. 
• What other actions could you invoke by using EventBridge that could automate a response to high CPU utilization on the EC2 instance?
• Are tools available in AWS services that can help you redirect traffic while you take action?
• How could you scale out to prevent an event that is caused by overutilized CPU?

In this course, you learn how to build architectures that support your operations team to maintain a healthy environment.
For more information about EventBridge integrations, see “Amazon EventBridge Integrations” at https://aws.amazon.com/eventbridge/integrations/.

## 5.1 实战

create threshold 


![](image/Pasted%20image%2020231003131645.png)


![](image/Pasted%20image%2020231003131658.png)


![](image/Pasted%20image%2020231003131824.png)


alarm 触发后, 什么action 被采取 

![](image/Pasted%20image%2020231003131928.png)



![](image/Pasted%20image%2020231003132002.png)



