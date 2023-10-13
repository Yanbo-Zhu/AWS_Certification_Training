
In this module, you will explore:
• Amazon CloudWatch monitoring capabilities • Elastic Load Balancing • Amazon Elastic Compute Cloud (Amazon EC2) Auto Scaling

In this module, you explored:
• Amazon CloudWatch monitoring capabilities • Elastic Load Balancing • Amazon EC2 Auto Scaling

In this module, you explored:
• Amazon CloudWatch monitoring capabilities • Elastic Load Balancing • Amazon EC2 Auto Scaling

![](image/Pasted%20image%2020231013113031.png)

# 1 Monitoring 


![](image/Pasted%20image%2020231013113337.png)

Monitoring is the process of collecting and analyzing data about the operational health and usage of your AWS resources. Each data point collected, also referred to as a resource metric, can be used to address overutilization, application flaws, misconfiguration, or security-related events in real time.

Monitoring your resources in real time helps you to:
• Respond to operation issues proactively instead of waiting for your end users to report the issues
• Improve performance and reliability by reducing performance bottlenecks and inefficient architectures
• Recognize security threats and events by identifying anomalies like unusual traffic spikes or unusual IP addresses accessing your resources
• Make data-driven decisions by analyzing the data you collect in a given time period 
• Create cost-effective solutions by analyzing, identifying, and applying a solution to address underused resources

![](image/Pasted%20image%2020231013113414.png)

Amazon CloudWatch is a monitoring and observability web service. It provides real-time data and actionable insights to help you monitor your applications, respond to system-wide performance changes, optimize resource usage, and see a unified view of operation health.
CloudWatch collects monitoring data in the form of metrics, logs, and events from your AWS and on-premises resources. After analyzing the data collected, you can set alarms to address anomalous behavior with your resources by automating fixes.
For example, you can monitor your Amazon Elastic Compute Cloud (Amazon EC2) instance CPU usage and disk reads and writes. From the data collected, you can determine if you should launch additional instances or stop underused instances.

## 1.1 CloudWatch metrics 

![](image/Pasted%20image%2020231013113436.png)

CloudWatch metrics are data about the performance of your systems.

By default, CloudWatch metrics are part of most AWS services, including Amazon EC2 instances, Amazon Elastic Block Store, Amazon Relational Database Service, and more. You can also enable additional metrics for your services and applications. CloudWatch loads all the metrics collected into your account, which provides an efficient way for you to navigate and search through the data. You can also graph and set alarms for your metrics.

Each metric in CloudWatch has a timestamp and is organized into containers, called namespaces. Metrics in different namespaces are isolated from each other. The AWS namespaces typically use AWS/service for naming convention. For example, for Amazon EC2, the naming convention would be AWS/EC2.

When a metric is sent to CloudWatch from an AWS service, a name/value identity key pair is attached to the metric. This key pair is called a dimension. Dimensions filter results that CloudWatch returns. For example, you can get statistics for a specific Amazon EC2 instance by specifying the instance ID dimension when you search for metrics.

To track website traffic or custom application behavior, you can publish your own metrics to CloudWatch using custom metrics. To gain more visibility, you can use high-resolution custom metrics. While you can publish data points with timestamps as granular as one-thousandth of a second, CloudWatch aggregates data to a minimum granularity of 1 second. You can read and retrieve it with a period of 1 second, 5 seconds, 10 seconds, 30 seconds, or any multiple of 60 seconds.


## 1.2 CloudWatch Logs 

assign repots to cloudwatch logs

![](image/Pasted%20image%2020231013113519.png)

Amazon CloudWatch Logs enable you to store, monitor, and access logs from your resources, such as Amazon EC2 instances, AWS Lambda functions, and more. CloudWatch Logs allow you to query and filter your log data.

By default, some AWS services, such as AWS Lambda, send logs to CloudWatch Logs with minimal effort. All you do is give the service the correct AWS Identity and Access Management (IAM) permission to post logs to CloudWatch Logs. Other services require additional work. For example, if you want an application running in your Amazon EC2 instance to send logs to CloudWatch Logs, you must first install CloudWatch 

Log agent on the Amazon EC2 instance. The agent includes:
• Plugin for the AWS Command Line Interface (AWS CLI) that pushes the log data to CloudWatch Logs
• Script that initiates the process to push data to CloudWatch Logs 
• cron job that ensures the daemon is always running

Key CloudWatch Logs terms are log event, log stream, and log groups.
• Log event: Record of activity recorded by the application or resource being monitored. A log event has a timestamp and an event message.
• Log stream: Group of log events belonging to the same resource being monitored. 
• Log groups: Collection of log streams that share the same retention and permission settings.

![](image/Pasted%20image%2020231013113948.png)


## 1.3 Cloudwatch alarms 

Example:  alarms watch
Please send me the alram when  xxx
Task action send notifciation or an email to adminiostator

![](image/Pasted%20image%2020231013114107.png)

You can create CloudWatch alarms to automate actions based on sustained state changes of your metrics. You configure when alarms are triggered and the action that is performed.
For example, to add EC2 instances when your EC2 instance CPU goes over an 75 percent threshold for more than 10 minutes, you would create an alarm that would notify you and automatically launch additional instances.

To create an alarm, you need to choose the metric, threshold, and time period. The three states of a metric alarm are OK, ALARM, and INSUFFICIENT_DATA.

• OK: Metric or expression is within the defined threshold. 
• ALARM: Metric or expression is outside of the defined threshold. 
• INSUFFICIENT_DATA: Alarm has started, the metric is not available, or not enough data is available for the metric to determine the alarm state.

An alarm can be triggered when it transitions from one state to another. Once it is triggered, it can initiate an action, such as an Amazon EC2 action, an Auto Scaling action, or notification transmission.

## 1.4 CloudWatch Dashboard 

CloudWatch Dashboard
Create a dashboard based on xxx

![](image/Pasted%20image%2020231013114222.png)

Once your AWS services are provisioned and sending metrics to CloudWatch, you can visualize and review the data in CloudWatch dashboards. Dashboards are customizable pages that you use for data visualization for one or more metrics through the use of widgets, such as a graphs, charts, text, numbers, and tables.

You can build a variety of custom dashboards, each one focusing on a distinct view of your environment. You can also pull data from different Regions into a single dashboard to create a global view of your architecture.

CloudWatch aggregates statistics according to the time period you specify when you create a graph or request metrics. You can also choose whether your metric widgets display live data. Live data is data published within the last minute that has not been fully aggregated.


# 2 Load Balancing 

![](image/Pasted%20image%2020231013114356.png)

Once your web application is online and available to your customers, traffic to your website will increase over time. If you deployed your application on one Amazon EC2 instance, what would happen if the instance response time decreases or the instance stops responding? You would probably start getting numerous phone calls and email messages. To resolve the issue, you would have to review your logs, identify the issue, and launch another Amazon EC2 instance. During this response action, your customers would not be able to access your web application. To help avoid this situation, AWS offers Elastic Load Balancing.

ELB is a highly available and scalable AWS service that automatically distributes incoming application traffic across multiple targets. Targets can be Amazon EC2 instances, containers, IP addresses, Lambda functions, and more. The targets can be in a single Availability Zone or multiple zones. With ELB, you would have two or more Amazon EC2 instances. If one instance stops responding, ELB will distribute the traffic to the other instances, without affecting your customers.

ELB uses heath checks to determine if a resource is available. The heath checks are indicated by an API response code. For example, if the code is 200 (OK), the resource is running without any issues. If the code is 503, the resource is unavailable, so ELB will route traffic to other available resources.


![](image/Pasted%20image%2020231013115111.png)


ELB has a number of benefits, including:
• High availability and elasticity: ELB is an AWS managed service that supports your application in a Region. ELB automatically adds and removes capacity based on server usage.
• Security: ELB works with Amazon Virtual Private Cloud (VPC) to provide robust security features, including integrated certificate management, user-authentication, and SSL/TLS decryption.
• Feature breadth: ELB includes support for features needed in container-based workloads, including HTTP/S, gRPC, TLS offload, advanced rule-based routing, and integration with container services.
• Robust monitoring and visibility: ELB helps you to monitor the health of your applications and their performance in real time with Amazon CloudWatch metrics, logging, and request tracing. This improves visibility into your application’s performance.
• Integration and global reach: ELB is integrated with other AWS services, such as Amazon EC2, Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS), and more. ELB is available wherever you run your AWS workloads.

Resource To learn more about ELB, refer to the AWS product page: https://aws.amazon.com/elasticloadbalancing


![](image/Pasted%20image%2020231013115141.png)


Load balances can wotk with different services
Listeners:  LB ist load balancer
Tagrget groups:
Load balander rules:  form app2 , use tg 1
According to rule, load balancer decide to suer target froup s


Three main components of ELB are listeners, target groups, and rules.
• Listeners: A listener is a process that checks for connection requests. To define a listener, you configure a protocol and port, based on the ELB type. Customers connect to a listener, which is referred as client-side.
• Target groups: A target group is a collection of resources, such as Amazon EC2 instances, AWS Lambda function, or IP addresses, where you send traffic. Each target group must have health check definitions.
• Rules: Rules are sets of connection instructions that define the source IP addresses and resources in target groups. You configure rules to associate a target group with a listener.


![](image/Pasted%20image%2020231013115217.png)

Classic load
Classica load balancer will be abondened in the future, so don’t use it analymore

The four ELB types are Application Load Balancer, Network Load Balancer, Gateway Load Balancer, and Classic Load Balancer. A load balancer serves as the single point of contact for clients. The load balancer distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, in multiple Availability Zones.

## 2.1 Application Load Balancer 

![](image/Pasted%20image%2020231013115653.png)

![](image/Pasted%20image%2020231013115734.png)


Application Load Balancer is ideal for load balancing HTTP and HTTPS traffic. It operates at the request level (layer 7), routing traffic to targets (Amazon EC2 instances, containers, IP addresses, and AWS Lambda functions) based on the request content.

Application Load Balancer has a number of primary features.
• Security: You can create and manage security groups associated with ELB to provide additional networking and security options inside your Amazon VPC. Application Load Balancer supports desync protections implementation based on the http_desync_guardian library, where customer applications are protected from HTTP vulnerabilities.
• TLS offloading: Application Load Balancer supports client TLS session termination. You can create an HTTPS listener, which enables traffic encryption between your load balancer and the clients that initiate SSL or TLS sessions. 
    Load balander cajnd0 the decryption  and encyrtion  for ec2 instances . So do not do decryption  and encyrtion  in ec2 instances  solelt
• Sticky sessions: Application Load Balancer supports both duration-based and application-based cookies, enabling nearly continuous request routing from the same client to the same target.
• Redirects: Application Load Balancer can redirect an incoming request from one URL, such as HTTP, to another URL, such as HTTPS, helping you to achieve security compliance.
• Fixed response: Application Load Balancer can control which client requests are served by your application, enabling it to respond to requests before they reach your applications.
• Content-based routing: Application Load Balancer can route a request to a service based on the content of the request, such as Host field, Path URL, HTTP header, HTTP method, Query string, or source IP address.

Resource To learn more about Application Load Balancer features, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/application-load-balance

## 2.2 Network Load Balancer 

![](image/Pasted%20image%2020231013115751.png)


![](image/Pasted%20image%2020231013115756.png)


You cann asssigne a public a static ip for by using elastic newtwork load balance

Example 
Route S3 in dbs service
Can be only  done by  network load balancer, not be done by application load balancer
需要重听

---


Network Load Balancer is ideal for load balancing TCP and UDP traffic. It operates at the connection level (layer 4), routing connections to targets (Amazon EC2 instances, microservices, and containers) in Amazon VPC, based on IP protocol data.
Some of the primary features of Network Load Balancer are:
• Sticky sessions: Requests are routed from the same client to the same target by a sticky session defined at the target group level.
• Low latency: Network Load Balancer offers low latencies for latency-sensitive applications. • Preserve source IP address: Network Load Balancer preserves the client-side source IP address and allows the backend to see the client’s IP address.
• Static IP support: Network Load Balancer automatically provides a static IP address per Availability Zone (subnet) that can be used by applications as the load balancer’s front-end IP.
• Elastic IP address support: You can assign an Elastic IP address per AZ (subnet and have your own fixed IP.
• DNS failover: If no healthy targets are registered with the Network Load Balancer or the Network Load Balancer nodes in a zone are unhealthy, Amazon Route 53 will direct traffic to load balancer nodes in other Availability Zones.

Resource 
To learn more about Network Load Balancer, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/network-load-balancer/




## 2.3 Gateway Load Balancer 

![](image/Pasted%20image%2020231013115909.png)


Gateway Load Balancer helps you to deploy, scale, and manage your third-party virtual appliances. It provides a gateway for distributing traffic across multiple virtual appliances, while scaling them up and down based on demand.

Some of the primary features of Gateway Load Balancer are:
• Bring higher-availability to third-party virtual appliances: Gateway Load Balancer ensures high availability and reliability by routing traffic through healthy virtual appliances and rerouting flows when a virtual appliance becomes unhealthy.
• Monitor health and performance metrics: You can monitor your Gateway Load Balancer using Amazon CloudWatch per Availability Zone metrics.
• Streamline deployment with AWS Marketplace: Deploying a new virtual appliance can be as straightforward as selecting it in AWS Marketplace.
• Ensure private connectivity in the AWS Cloud with Gateway Load Balancer endpoints: Gateway Load Balancer connects internet gateways, VPCs, and other network resources over a private connection. Your traffic flows in the AWS Cloud, which protects your data from being exposed on the internet.

Resource
To learn more about Gateway Load Balancer, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/gateway-load-balancer


## 2.4 Classic Load Balancer 

![](image/Pasted%20image%2020231013115916.png)

Classic Load Balancer is intended for applications built for Amazon EC2-Classic. It provides load balancing across multiple Amazon EC2 instances and operates at both the request and connection levels.

Classic Load Balancer has two primary features.
• SSL offloading: Classic Load Balancer supports SSL termination, including offloading SSL for backend application instances, centralized management of SSL certificates, and re-encryption to backend instances with optional public key authentication.
• IPv6 support: Classic Load Balancer supports the use of both the Internet Protocol version 4 and 6 (IPv4 and IPv6) for Amazon EC2-Classic solutions.

Resource
To learn more about Classic Load Balancer, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/classic-load-balancer

# 3 Scaling 

Vertical scaling is the process of upgrading or downgrading server capacity (such as memory, hard disk space, and more) of an Amazon EC2 instance depending on the demand traffic. This is accomplished by selecting a different Amazon EC2 family size or type.

To vertically scale an Amazon EC2 instance, you must complete three steps.
1. Stop the instance. 
2. Make the desired change to the instance size or type. 
3. Start the instance.

This manual process can become challenging when you have multiple instances to manage or you are limited on the instance scalability.

Horizontal scaling is the process of adding or removing Amazon EC2 instances depending on the traffic demands. This process can be automated using the Amazon EC2 Auto Scaling service. With horizontal scaling, you can add an unlimited number of instances.

![](image/Pasted%20image%2020231013120246.png)

Lower costs: 因为我们可以控制规模

Amazon EC2 Auto Scaling helps you increase application availability and lower your cost of infrastructure by automatically adding and removing Amazon EC2 instances. You can use the Amazon EC2 Auto Scaling fleet management feature to improve fault tolerance by maintaining the health and availability of your fleet of instances. When EC2 Auto Scaling detects an unhealthy instance, it terminates and replaces the instance with a new one.

The ELB services integrates seamlessly with Amazon EC2 Auto Scaling. If an Amazon EC2 instance becomes unhealthy, ELB routes the traffic to the remaining healthy instances. Meanwhile, Amazon EC2 Auto Scaling launches a new instance and notifies ELB when the instance is ready. Then, ELB adds the instance to the target group for traffic routing.

Resource
To learn more about EC2 Auto Scaling, visit the AWS service page: https://aws.amazon.com/ec2/autoscaling

![](image/Pasted%20image%2020231013120329.png)

在 auto scaling 创立 temple, 可以创立 新的 template

When you create an Amazon EC2 instance, the Amazon Machine Image (AMI) ID, instance type, security group, storage volumes, and other parameters are required. If you must launch additional instances with the same configuration, a launch template can be used to save the parameters for reuse. Amazon EC2 Auto Scaling uses launch templates when it launches additional instances during the scaling out process.

To create a launch template, you can create the template from scratch, create a new version of an existing template, or copy the parameters from a running instance or other template.

Launch templates support versioning. Instances can be launched from different versions of configurations. For example, if a current version causes issues, the previous version can be used for launching additional instances


![](image/Pasted%20image%2020231013120538.png)

An Amazon EC2 Auto Scaling group helps you to define where Amazon EC2 Auto Scaling deploys resources. In an Auto Scaling group, you specify the Amazon VPC and subnets for your Amazon EC2 instance deployed by Amazon EC2 Auto Scaling. You must select at least two subnets across different Availability Zones.
Auto Scaling groups help you choose Amazon EC2 instance types. You can choose On-Demand Instances, Spot Instances, or both.

The number of instances running in an Auto Scaling group are controlled by three settings – minimum, maximum, and desired capacity.
• Minimum: Ensures that you always have a certain number of Amazon EC2 instances running at all times.
• Maximum: Lets Amazon EC2 Auto Scaling scale out the number of Amazon EC2 instances as needed to handle an increase in demand.
• Desired capacity: Must be greater than or equal to the minimum limit and less than or equal to the maximum limit. Causing the Auto Scaling group to launch or terminate instances is like changing the desired capacity. Its value is usually set by an automated process, such as an Auto Scaling policy, Auto Scaling event, or a Lambda function, but it can be directly edited in the console, where you can observe the effects.


![](image/Pasted%20image%2020231013121009.png)

![](image/Pasted%20image%2020231013120605.png)


1 Simple scaling policy
Cpu > 75: Cpu 数量 1变2

2 Step scaling policy
Cpu > 75: 1变2
Cpu < 25: 2 变1

3 Target tracking scaling policy
Just set : I wanna average cpu ist 75%, 你怎么你变 cpu 是你自己的事情, 你随便去变吧
Leave much more automation on auto sacling 机制


Scaling policies use Amazon CloudWatch metrics and alarms to trigger an action. For example, suppose you set a CloudWatch alarm for your Amazon EC2 instances to maintain the CPU usage below 70 percent. Once the CPU usage surpasses 70 percent, it triggers a scaling policy to add an Amazon EC2 instance.
The three types of scaling policies are simple, step, and target tracking.
• Simple scaling policy: This policy increases or decreases the group current capacity based on a single scaling adjustment. After a scaling activity starts, the policy waits for the scaling activity to finish and the cooldown period to expire before responding to additional alarms.
• Step scaling policy: This policy increases or decreases the group current capacity based on a set of scaling adjustments, known as step adjustments. Unlike the simple scaling policy, you can respond to additional alarms, even while a scaling activity is in progress.
• Target tracking scaling policy: This policy increases or decreases the group current capacity based on a target value for a specific metric. Once a specific target value is set in the scaling metric, Amazon EC2 Auto Scaling creates and manages the CloudWatch alarm to make sure capacity adjusted to keep the metric tracking the specified target value.

Resource 
To learn more about scaling policies, refer to the AWS documentation: https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scale-based-on-demand.html


![](image/Pasted%20image%2020231013121030.png)


Multiple purchase options: can choose lower ec2 instance type

Amazon EC2 Auto Scaling is a robust service with a variety of features.
• Automatically scale in and out: Automate launching new Amazon EC2 instances when demand increases, and terminate instances when demand decreases.
• Choose when and how to scale: Scale dynamically by using Amazon CloudWatch metrics and alarms. The alarms can initiate Amazon EC2 Auto Scaling actions, such as launching a new instance to replace an unhealthy one.
• Fleet management: Through automation, Amazon EC2 Auto Scaling automatically replaces unresponsive instances to maintain application availability by monitoring the heath on all instances.
• Predictive scaling: By detecting daily and weekly change patterns with machine learning, Amazon EC2 Auto Scaling assists in maintaining the right level of Amazon EC2 instances needed to maintain availability.
• Support for multiple purchase models, instance types, and Availability Zones: To optimize scale, performance, and cost, you can automatically scale instances across purchase options, Availability Zones, and instance families in a single application.
• Included with Amazon EC2: When you sign up for an Amazon EC2 service, Amazon EC2 Auto Scaling is included with the service.


# 4 Summary 

![](image/Pasted%20image%2020231013143734.png)


# 5 Knowledge Check 

![](image/Pasted%20image%2020231013143817.png)

What are the three components of Amazon EC2 Auto Scaling?
A. Scaling policies, security group, Amazon EC2 Auto Scaling group 
B. Launch template, scaling policies, Amazon EC2 Auto Scaling group 
C. Security group, instance type, key pair 
D. AMI ID, instance type, storage

The correct response option is B. Launch template, scaling policies, Amazon EC2 Auto Scaling group.

Explanation: Amazon EC2 Auto Scaling requires you to specify three main components.
• Launch template or a launch configuration as a configuration template for the Amazon EC2 instances
• Scaling policies that allow you to configure a group to scale based on the occurrence of specified conditions or on a schedule
• Amazon EC2 Auto Scaling group that allows you to specify your minimum, maximum, and desired capacity of your instances

---


![](image/Pasted%20image%2020231013143827.png)


Which load balancer should be used for an application that requires a target group selection by using a rule based on website domains? A. Classic Load Balancer B. Application Load Balancer C. Network Load Balancer D. Gateway Load Balancer

The correct response option is B. Application Load Balancer.
Explanation: Application Load Balancer is a layer 7 load balancer that routes HTTP and HTTPs traffic, with support for rules.

----

