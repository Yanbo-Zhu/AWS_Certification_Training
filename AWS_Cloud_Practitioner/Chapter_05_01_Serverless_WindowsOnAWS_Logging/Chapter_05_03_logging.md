

# 1 Logging Service
10:16:53 Logging Service

Amazon Web Services (AWS) provides service-specific operational metrics and log files to give customers insight into how the service is operating.

## 1.1 CloudTrail

[**CloudTrail**](https://aws.amazon.com/cloudtrail/?nc2=type_a) - logs all `API calls`(SDK, CLI) between various `AWS services`

https://aws.amazon.com/cloudtrail/features/ "CloudTrail records user activity and API calls across AWS services as events. CloudTrail events help you answer the questions of "who did what, where, and when?""

**Questions that CloudTrail can answer:**
_Who create this bucket?_ - detect developer mis-configuration
_Who spun up that expensive EC2 instance?_ - Detect malicious actors
_Who launched this SageMaker notebook?_ - Automate responses

## 1.2 CloudWatch

[**CloudWatch**](https://aws.amazon.com/es/cloudwatch/) - is a collection of multiple services
-   CloudWatch **Logs** : Performance data about AWS Services eg. CPU Utilization, Memory, Network in Application Logs eg. Rails, Nginx Lambda Logs
-   CloudWatch **Metrics**: Represents a time-ordered set of data points. A variable to monitor
-   CloudWatch **Events**: trigger an event based on a condition eg. every hour take a snapshot of the server
-   CloudWatch **Alarms**: triggers notifications based on metrics
-   CloudWatch **Dashboard**: create visualizations based on metrics
    

## 1.3 X-Ray

[**AWS X-Ray**](https://docs.aws.amazon.com/xray/latest/devguide/aws-xray.html) is a distributed tracing system. You can use it to pinpoint issues with your microservices.​ See how data moves from one app to another, how long it took to move, and if it failed to move forward.

# 2 AWS Cloud Trail
10:20:07 AWS Cloud Trail

**AWS CloudTrail** is a service that enables governance, compliance, operational auditing, and risk auditing of your AWS account.
AWS CloudTrail is used to monitor API calls and Actions made on an AWS account.

Easily identify which users and accounts made the call to AWS eg.
-   **Where** — Source IP Address
-   **When** — EventTime
-   **Who** — User, UserAgent
-   **What** — Region, Resource, Action

CloudTrail is already logging by default and will collect logs for the **last 90 days** via **Event History**
If you need more than 90 days you need to create a **Trail**
Trails are output to S3 and do not have GUI like Event History. 
To analyze a Trail you’d have to use **Amazon Athena**.


![](image/Pasted%20image%2020230521111157.png)


![](image/Pasted%20image%2020230521111219.png)

# 3 CloudWatch Alarm
10:21:44 CloudWatch Alarm

**A CloudWatch Alarm** monitors a **CloudWatch Metric** based on **a defined threshold.**

When alarm breaches (goes outside the defined threshold) then it changes **state.**

**Metric Alarm States**
-   **OK** The metric or expression is **within** the defined threshold
-   **ALARM** The metric or expression is **outside** of the defined threshold
-   **INSUFFICIENT_DATA**
    -   The alarm has just started
    -   the metric is not available
    -   Not enough data is available

When it changes state we can define what **action it should trigger.**
-   Notification
-   Auto Scaling Group
-   EC2 Action

![](image/Pasted%20image%2020230521111455.png)

[Using Amazon CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)

# 4 Anatomy of an Alarm
10:22:42 Anatomy of an Alarm

- **Threshold Condition**
    - Defines when a datapoint is breached   在……上打开缺口
- **Evaluation Periods**
    - number of previous periods
- **Data point**
    - Represents the metric’s measurement at a given period
- **Metric**
    - The actual data we are measuring
- **Period**
    - How often it checks to evaluate the Alarm
- **NetworkIn**
    - The volume of incoming network traffic. measured in Bytes. When using 5min monitoring divide by 300 to get Bytes/second
- **Datapoints to alarm**
    - data point is breached in an evaluation period going back 4 periods. _This is what triggers the alarm_
    - define the number of datapoints within the evaluation period that must be breaching to cause the  alarm to go to ALARM state 
    - eg. 1 out of 4 ,  在  evaluation period 中  每次4 个, 每次各 datapoints 中 最后一个 的datapoint 的状态, 拿出来, 根据这个datapoint 的状态值 去 产生 对应的 alarm state 

![](image/Pasted%20image%2020230521112716.png)

[Using Amazon CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEm)
[What is Amazon EC2?](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/viewing_metrics_with_cloudwatch.htmlail.html)

# 5 Log Events
10:23:49 Log Events

## 5.1 **Log Streams**

A log stream represents a **sequence of events** from an **application or instance being monitored**.
You can create Log Streams manually but generally, this is automatically done by the service you are using

Here is a Log Group for a **Lambda function**
You can see here the Log Streams are named after the **running instance**. Lambdas frequency run on new instances so the stream streams contain timestamps

Here is a Log Group for an **application log running on EC2**. 
You can see here the Log Streams are named after the running instance’s Instance ID

Here is a Log Group for **AWS Glue**.
You can see here the Log Streams are named after the **Glue Jobs**.

![](image/Pasted%20image%2020230521112939.png)

## 5.2 aws服务: CloudWatch Logs — Log Events

**Log Events**
Represents a single event in a log file. Log events can be seen within a Log Stream.
You can use filter events to filter Out logs based on simple or  Pattern matching syntax:

![](image/Pasted%20image%2020230521113033.png)

# 6 Log Insights (log 分析工具 )
10:16:53 Log Insights

**CloudWatch Logs Insights** enables you to **interactively search and analyze your CloudWatch log data** and has the following advantages:
-   More robust filtering than using the simple Filter events in a Log Stream
-   Less burdensome than having to export logs to S3 and analyze them via Athena.

**CloudWatch Logs Insights** supports all types of logs.

CloudWatch Logs Insights is commonly used via the console to do ad-hoc queries against logs groups.

CloudWatch Insights has its own language called:
-   CloudWatch Logs Insights **Query Syntax**

其他 
-   A single request can query up to **20 log groups.**
-   Queries **time out after 15 minutes**, if they have not been completed.
-   Query results are **available for 7 days.**

![](image/Pasted%20image%2020230521113550.png)


----
AWS provides sample queries: 
AWS provides sample queries that can get you started for common tasks, And to ease learning the Query Syntax. 
A good example Is filtering VPC Flow Logs.
You can create and save your own queries to make future repetitive tasks easier.

![](image/Pasted%20image%2020230521113708.png)

# 7 CloudWatch Metrics  (指定使用 某个 Metrics 去 monitor 这个 metice 的 所代表的数据 )
10:26:47 CloudWatch Metrics

指定使用 某个 Metrics 去 monitor 这个 metice 的 所代表的数据 

**A CloudWatch Metric** represents a **time-ordered set of data points**
It's a **variable** that is **monitored over time**.
CloudWatch comes with many **predefined** metrics that are generally namespaced by AWS Service.

**EC2 Per-Instance Metrics**
-   CPUUtilization
-   DiskReadOps
-   DiskWriteOps
-   DiskReadBytes
-   DiskWriteBytes
-   NetworkIn
-   NetworkOut
-   NetworkPacketsIn
-   NetworkPacketsOut


![](image/Pasted%20image%2020230521113920.png)

# 8 AWS CloudTrail Follow Along
10:27:29 AWS CloudTrail Follow Along

要保存超过90天的 event history 就要产生一个 CloudTrail


create a Cloudtail 
![](image/Pasted%20image%2020230521115001.png)

通过 这个 Cloudtrail 产生的 log 都会存在某个 s3 Bucket 中

![](image/Pasted%20image%2020230521115054.png)



