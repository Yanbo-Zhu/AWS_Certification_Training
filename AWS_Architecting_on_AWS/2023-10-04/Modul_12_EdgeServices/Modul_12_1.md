

# 1 #


![](image/Pasted%20image%2020231004110259.png)



# 2 #


![](image/Pasted%20image%2020231004110347.png)



![](image/Pasted%20image%2020231004110435.png)


# 3 Edge fundamentals

![](image/Pasted%20image%2020231004110448.png)


AWS edge computing services provide infrastructure and software that move data processing and analysis as close to the endpoint as necessary. This includes deploying AWS managed hardware and software to locations outside AWS data centers, and even onto customer-owned devices.
You can extend the cloud for a consistent hybrid experience using these AWS edge services related to locations: 
• AWS edge locations – Edge locations are connected to the AWS Regions through the AWS network backbone. Amazon CloudFront, AWS WAF, and AWS Shield are services you use here.
• AWS Local Zones – Local Zones are an extension of the AWS Cloud. They are located close to large population and industry centers. You learned about Local Zones in Module 1: Architecting Fundamentals.
• AWS Outposts – With AWS Outposts, you can run some AWS services on premises or at your own data center.
• AWS Snow Family – The Snow Family of products provides offline storage at the edge, which is used to deliver data back to AWS Regions.
You can use the same infrastructure, services, APIs, and tools for a consistent experience


--- 


![](image/Pasted%20image%2020231004110613.png)

Review the edge services architecture. A user sends a request to an application partly hosted on premises. The user’s request interacts with Amazon Route 53, AWS WAF, Amazon CloudFront, and AWS Outposts. The AWS services hosted in the cloud are protected with AWS Shield.
In this module, you learn about each of the services labeled in the example. 
1. First, you learn about Amazon Route 53 and how you can use it to direct traffic to your resources. Route 53 operates at edge locations around the world.
2. Next, you learn about the AWS content delivery network known as Amazon CloudFront. 3. Following CloudFront, you learn about AWS WAF and AWS Shield and how they relate to distributed denial of service (DDoS) protection.
4. Last, you discover how AWS Outposts brings the power of the AWS Cloud to your on-premises network.


# 4 Amazon Route 53

The network engineer asks, “Is there a DNS solution for AWS that is both highly available and scalable?”
The networking team must choose whether to host their own Domain Name System (DNS) or use another service. The company wants your advice about how to integrate DNS services into the other AWS services they are using


![](image/Pasted%20image%2020231004110651.png)


Domain Name System: domain name and the corresponding ip addresse 

Route 53 provides a DNS, domain name registration, and health checks. Route 53 was designed to give developers and businesses a reliable and cost-effective way to route end users to internet applications. It translates names like example.com into the numeric IP addresses that computers use to connect to each other.
With Route 53, you can purchase and manage domain names, such as example.com, and automatically configure DNS settings for your domains.
Route 53 effectively connects user requests to infrastructure running in AWS, such as Amazon Elastic Compute Cloud (Amazon EC2) instances, Elastic Load Balancing (ELB) load balancers, or Amazon Simple Storage Service (Amazon S3) buckets. You can also use it to route users to infrastructure outside of AWS.
You can configure an Amazon CloudWatch alarm to check on the state of your endpoints. Combine your DNS with health check metrics to monitor and route traffic to healthy endpoints.
For more information about Route 53 health checks, see "Monitoring health checks using CloudWatch" in the Amazon Route 53 Developer Guide (https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/monitoring-health-checks.html)


--- 



![](image/Pasted%20image%2020231004111029.png)

A hosted zone is a container for records. Records contain information about how you want to route traffic for a specific domain, such as example.com, and its subdomains, such as dev.example.com or mail.example.com. A hosted zone and the corresponding domain have the same name.
There are two types of hosted zones: 
• Public hosted zones contain records that specify how you want to route traffic on the internet.
    • For internet name resolution 
    • Delegation set: For authoritative name servers to be provided to the registrar or parent domain

• Private hosted zones contain records that specify how you want to route traffic in your Amazon Virtual Private Cloud (Amazon VPC).
    • For name resolution inside a VPC 
    • Can be associated with multiple VPCs and across accounts

For more information about working with hosted zones, see "Working with hosted zones" in the Amazon Route 53 Developer Guide (https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-working-with.html).

--- 


![](image/Pasted%20image%2020231004111218.png)


When you create a record, you choose a routing policy, which determines how Amazon Route 53 responds to queries: 
• Simple routing policy – Use for a single resource that performs a given function for your domain. An example is a web server that serves content for the example.com website.
• Failover routing policy – Use when you want to configure active-passive failover.
• Geolocation routing policy – Use when you want to route traffic based on the location of your users. 
• Geoproximity routing policy – Use when you want to route traffic based on the location of your resources and, optionally, shift traffic from resources in one location to resources in another.
• Latency routing policy – Use when you have resources in multiple AWS Regions and you want to route traffic to the Region that provides the lowest latency with less round-trip time.
• Multivalue answer routing policy – Use when you want Route 53 to respond to DNS queries with up to eight healthy records selected at random.
• Weighted routing policy – Use to route traffic to multiple resources in proportions that you specify.

For more information about routing policies, see "Choosing a routing policy" in the Amazon Route 53 Developer Guide (https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html).



---


![](image/Pasted%20image%2020231004111552.png)

Simple routing lets you configure standard DNS records, with no special Route 53 routing such as weighted or latency. With simple routing, you typically route traffic to a single resource, for example, to a web server for your website.


--- 



if health check on 一个失败了, 就转向另一个 
One is supposed to be active, the other one is hot standby
![](image/Pasted%20image%2020231004111622.png)

Route 53 health checks monitor the health and performance of your web applications, web servers, and other resources.
Each health check that you create can monitor one of the following: • The health of a specified resource, such as a web server • The status of other health checks • The status of a CloudWatch alarm
After you create a health check, you can get the status of the health check, get notifications when the status changes, and configure DNS failover.


--- 
Using geolocation routing, you can choose the resources that serve your traffic based on the geographic location of your users, meaning the location that DNS queries originate from. For example, you might want all queries from Europe to be routed to an ELB load balancer in the London Region

![](image/Pasted%20image%2020231004111629.png)

---

Using geoproximity routing, Route 53 can route traffic to your resources based on the geographic location of your users and your resources. You can optionally choose to route more, or less, traffic to a given resource by specifying a value, known as a bias. A bias expands or shrinks the size of the geographic Region from which traffic is routed to a resource.
In this example, if you increase the bias of one of the Regions, its geographic boundary will increase. This will consequently decrease the boundaries of the surrounding Regions


![](image/Pasted%20image%2020231004111700.png)

---

If your application is hosted in multiple AWS Regions, you can improve performance for your users by serving their requests from the AWS Region that provides the lowest latency.
Data about the latency between users and your resources is based entirely on traffic between users and AWS data centers. If you aren't using resources in an AWS Region, the actual latency between your users and your resources can vary significantly from AWS latency data. This is true even if your resources are located in the same city as an AWS Region.


![](image/Pasted%20image%2020231004111806.png)

---



提供几个 healthy 选择给user, 让 user 自己选择去那个 地址 

![](image/Pasted%20image%2020231004111857.png)

With multivalue answer routing, you can configure Route 53 to return multiple values, such as IP addresses for your web servers, in response to DNS queries. You can specify multiple values for almost any record, but with multivalue answer routing, you can also check the health of each resource. Route 53 returns values only for healthy resources.
The ability to return multiple IP addresses whose health can be checked is a way for you to use DNS to improve availability and load balancing. However, it is not a substitute for a load balancer


--- 



![](image/Pasted%20image%2020231004111948.png)

With weighted routing, you can assign weights to a resource record set to specify the frequency with which different responses are served.
In this example of a blue/green deployment, a weighted routing policy is used to send a small amount of traffic to a new production environment. If the new environment is operating as intended, the amount of weighted traffic can be increased to confirm it can handle the increased load. If the test is successful, all traffic can be sent to the new environment.



# 5 Amazon CloudFront 

被用来 caching 

Cloud Delivery network 
It works perferctly with static object , So images, videos, songs
And when someone requests that content the first time, it's going to be read. then it will be cached. So the first client is served. Maybe not the best experience, but then the second and third and 4th there

We use Cloud front. This is called a Content Delivery Network CDN. So if you hear the term CDN, that's a Content Delivery Network

![](image/Pasted%20image%2020231023151314.png)

The network engineer asks, ”What service can provide the content delivery network that we need?”
The engineering team needs to speed up content delivery for customers. You should explore how AWS resources can be served by edge locations on the AWS network.


![](image/Pasted%20image%2020231004112453.png)

It’s not always possible to replicate your entire infrastructure across the globe when your web traffic is geo-dispersed. It is also not cost effective. With a content delivery network (CDN), you can use its global network of edge locations to deliver a cached copy of your web content to your customers.
To reduce response time, the CDN uses the nearest edge location to the customer or the originating request location. Using the nearest edge location dramatically increases throughput because the web assets are delivered from cache. For dynamic data, you can configure many CDNs to retrieve data from the origin servers.
Use Regional edge caches when you have content that is not accessed frequently enough to remain in an edge location. Regional edge caches absorb this content and provide an alternative to having to retrieve that content from the origin server.

---


![](image/Pasted%20image%2020231004112504.png)

Amazon CloudFront is a global CDN service that accelerates delivery of your websites, APIs, video content, or other web assets. It integrates with other AWS products to give developers and businesses a straightforward way to accelerate content to users. There are no minimum usage commitments.
CloudFront provides extensive flexibility for optimizing cache behavior, coupled with network-layer optimizations for latency and throughput. The CDN offers a multi-tier cache by default. It has Regional edge caches that improve latency and lower the load on your origin servers when the object is not already cached at the edge.
CloudFront supports real-time, bidirectional communication over the WebSocket protocol. With this persistent connection, clients and servers can send real-time data to one another without the overhead of repeatedly opening connections. This is especially useful for communications applications such as chat, collaboration, gaming, and financial trading.


---


![](image/Pasted%20image%2020231004112703.png)

Imagine you are serving an image from a traditional web server, not from CloudFront. You might serve an image named sunsetphoto.png using the URL http://example.com/sunsetphoto.png. Your users can easily navigate to this URL and see the image.
The users don't realize that their request was routed from one network to another (through the complex collection of interconnected networks that comprise the internet) until the image was found.
CloudFront speeds up the distribution of your content by routing each user request through the AWS backbone network to the edge location that can best serve your content. Typically, this is a CloudFront edge server that provides the fastest delivery to the viewer. Using the AWS network can dramatically reduce the number of networks your users' requests must pass through, which improves performance. Users get lower latency (the time it takes to load the first byte of the file) and higher data transfer rates. You also get increased reliability and availability because copies of your files (also called objects) are now held (or cached) in multiple edge locations around the world.


---


![](image/Pasted%20image%2020231004112805.png)

Review the steps to learn what happens when you request an object from an origin.
If content is already cached and its time-to-live (TTL) has not expired, steps 2 and 3 are skipped, and the data is transferred from the edge location to the content requester.

----


CloudFront 

origin:  where to save the caching 

![](image/Pasted%20image%2020231023151421.png)

![](image/Pasted%20image%2020231004113127.png)


To configure CloudFront, you specify an origin server from which CloudFront gets your files, for example, an S3 bucket or your HTTP server. These will be distributed from CloudFront edge locations all over the world.
• An origin server stores the original, definitive version of your objects. 
• If you are serving content over HTTP, your origin server is either an S3 bucket or an HTTP server, such as a web server.
• Your HTTP server can run on an EC2 instance or on an on-premises server that you manage. These servers are also known as custom origins.

Next, you create a CloudFront distribution. This tells CloudFront which origin servers to get your files from when users request the files through your website or application. At the same time, you specify details such as whether you want CloudFront to log all requests and whether you want the distribution to be activated as soon as it's created.
CloudFront assigns a domain name to your new distribution. The service sends your distribution's configuration, but not the content, to all of its edge locations.

--- 

![](image/Pasted%20image%2020231004113151.png)

CloudFront Origin Shield 
- the Cloudfront Origin shield is going to be a third level of caching close to the origin.   
- third level caching it's like a third level of caching to ensure that if it's not in the edge cache or the regional edge cache then I'm going to go here as a Before I need to bother the the origin itself
- so it's it's shielding the origin from requests, but not secure

Amazon CloudFront is a managed service. You should understand what services AWS provides to help you improve performance. You are also responsible for configuring CloudFront to optimize your application’s performance.
AWS provides features that improve the performance of your content delivery: 
• TCP optimization – CloudFront uses TCP optimization to observe how fast a network is already delivering
your traffic and the latency of your current round trips. It then uses that data as input to automatically improve performance.
• TLS 1.3 support – CloudFront supports TLS 1.3, which provides better performance with a simpler handshake process that requires fewer round trips. It also adds improved security features.
• Dynamic content placement – Serve dynamic content, such as web applications or APIs from ELB load balancers or Amazon EC2 instances, by using CloudFront. You can improve the performance, availability, and security of your content.

You can also adjust the configuration of your CloudFront distribution to accommodate for better performance: 
• Define your caching strategy – Choosing an appropriate TTL is important. In addition, consider caching based on things like query string parameters, cookies, or request headers.
• Improve your cache hit ratio – You can view the percentage of viewer requests that are hits, misses, and errors in the CloudFront console. Make changes to your distribution based on statistics collected in the CloudFront cache statistics report.
• Use CloudFront Origin Shield – Get an additional layer of caching between the regional edge caches and your origin. It is not always a best fit for your use case, but it can be beneficial for viewers that are spread across geographic regions or on-premises origins with capacity or bandwidth constraints.

For more information about dynamic content delivery, see “Amazon CloudFront Dynamic Content Delivery” (https://aws.amazon.com/cloudfront/dynamic-content/).
For more information about improving caching and availability in your distributions, see “Optimizing caching and availability” in the Amazon CloudFront Developer Guide (https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ConfiguringCaching.html ).



# 6 DDos attacks 

The network engineer asks, “How can we protect public-facing applications?”
The engineering team needs to prepare for distributed denial-of-service (DDoS) attacks. They want you to explain to them the best practices for protecting AWS services at the edge.

![](image/Pasted%20image%2020231004113726.png)

A DDoS attack is an attack in which multiple compromised systems attempt to flood a target, such as a network or web application, with traffic. A DDoS attack can prevent legitimate users from accessing a service and can cause the system to crash because of the overwhelming traffic volume.
The general concept of a DDoS attack is to use additional hosts to amplify the requests made to the target, rendering them at full capacity and unavailable. In the diagram, a single attacker uses three bot primaries. Each bot primary controls multiple bots that all attack the same target.

--- 


![](image/Pasted%20image%2020231004113740.png)


In general, DDoS attacks can be isolated by the Open Systems Interconnection (OSI) model layer they attack. They are most common at the Network (Layer 3), Transport (Layer 4), Presentation (Layer 6), and Application (Layer 7) layers.
Infrastructure layer attacks Attacks at Layer 3 and Layer 4 are typically categorized as infrastructure layer attacks. These are also the most common type of DDoS attack and include vectors such as synchronized (SYN) floods and other reflection attacks such as User Datagram Protocol (UDP) packet floods. These attacks are usually large in volume and aim to overload the capacity of the network or the application servers. Fortunately, these are also the type of attacks that have clear signatures and are easier to detect.
Application layer attacks An attacker might target the application itself by using a Layer 7, or Application layer, attack. In these attacks, similar to SYN flood infrastructure attacks, the attacker attempts to overload specific functions of an application to make the application unavailable or extremely unresponsive to legitimate users.




--- 


![](image/Pasted%20image%2020231004113853.png)

AWS Shield is a managed DDoS protection service that safeguards your applications running on AWS. It provides dynamic detection and automatic inline mitigations that minimize application downtime and latency. There are two tiers of AWS Shield: Shield Standard and Shield Advanced.
AWS Shield Standard provides protection against some of the most common and frequently occurring infrastructure (Layer 3 and 4) attacks. This includes SYN/UDP floods and reflection attacks. Shield Standard improves availability of your applications on AWS. The service applies a combination of traffic signatures, anomaly algorithms, and other analysis techniques. Shield Standard detects malicious traffic and it provides real-time issue mitigation. You are protected by Shield Standard at no additional charge.
If you need even more protection from DDoS attacks on your applications, consider using Shield Advanced. You get additional detection and mitigation against large and sophisticated DDoS attacks, near real-time visibility, and integration with AWS WAF, a web application firewall.
For more information, see “How AWS Shield works” in the AWS WAF, AWS Firewall Manager, and AWS Shield Advanced Developer Guide (https://docs.aws.amazon.com/waf/latest/developerguide/ddos-overview.html).


![](image/Pasted%20image%2020231004113902.png)






--- 




![](image/Pasted%20image%2020231004114022.png)



![](image/Pasted%20image%2020231004114116.png)





WAF: firewall 
if you have shield advance, use waf free
applied it in application layer, https 



AWS WAF is a web application firewall that helps protect your web applications or APIs against common web exploits and bots. AWS WAF gives you control over how traffic reaches your applications. Create security rules that control bot traffic and block common attack patterns, such as SQL injection (SQLi) or cross-site scripting (XSS). You can also monitor HTTP(S) requests that are forwarded to your compatible AWS services.
In the diagram, a client sends an inbound request to one of the five supported services: CloudFront, Application Load Balancer, Amazon API Gateway, AWS AppSync, or Amazon Cognito user pools. The traffic is evaluated against web access control lists (web ACLs) before it reaches the destination. If the traffic passes all web ACLs without a deny, it is sent to the destination AWS service.
For more information about AWS WAF, see “Getting started with AWS WAF” (https://docs.aws.amazon.com/waf/latest/developerguide/getting-started.html).


--- 


![](image/Pasted%20image%2020231004114250.png)

Before configuring AWS WAF, you should understand the components used to control access to your AWS resources. 
• Web ACLs – You use a web ACL to protect a set of AWS resources. You create a web ACL and define its protection strategy by adding rules.
• Rules – Rules define criteria for inspecting web requests and specify how to handle requests that match the criteria.
• Rule groups – You can use rules individually or in reusable rule groups. AWS Managed Rules for AWS AWF and AWS Marketplace sellers provide managed rule groups for your use. You can also define your own rule groups.
• Rule statements – This is the part of a rule that tells AWS WAF how to inspect a web request. When AWS WAF finds the inspection criteria in a web request, we say that the web request matches the statement.
• IP set – This is a collection of IP addresses and IP address ranges that you want to use together in a rule statement. IP sets are AWS resources.
• Regex pattern set – This is a collection of regular expressions that you want to use together in a rule statement. Regex pattern sets are AWS resources.
• Monitoring and logging – You can monitor web requests, web ACLs, and rules using CloudWatch. You can also activate logging to get detailed information about traffic that is analyzed by your web ACL. You choose where to send your logs: CloudWatch Logs, Amazon S3, or Amazon Kinesis Data Firehose.


--- 


WAF ist not inline 

![](image/Pasted%20image%2020231004114407.png)


Rule statements are the part of a rule that tells AWS WAF how to inspect a web request. When AWS WAF finds the inspection criteria in a web request, we say that the web request matches the statement.
Every rule statement does the following:
• Specifies what to look for and how, according to the statement type
• Has a single top-level rule statement that can contain other statements

Rule statements can be very simple. For example, you could have a statement that provides a set of originating countries for which you should check web requests. Rule statements can also be very complex. Examples include statements that combine many other statements with logical AND, OR, and NOT statements.
Web ACLs can contain rule statements that reference rule groups. On the console, you don't see these represented as rule statements. Every web ACL has a JSON format representation. In the JSON, you can see these special types of rule statements. For rules of any complexity, manage your web ACL with the JSON editor.
AWS WAF supports nesting for many rule statements. For example, use nesting to control the rate of requests coming from a specific geographic area. Use a rate-based rule and nest a geographic match rule inside it to narrow the scope.
For more information, see “AWS WAF rule statements” in the AWS WAF, AWS Firewall Manager, and AWS Shield Advanced Developer Guide (https://docs.aws.amazon.com/waf/latest/developerguide/waf-rule-statements.html).


# 7 AWS  firewall manager 

![](image/Pasted%20image%2020231004114604.png)

File Manager is a tool that you can use it in order to be able to configure, update and change lots of security services, even in an organ, instead of hopping into each one and working on it separately so it can help you configure the rules in Italy as well

AWS Firewall Manager simplifies the administration and maintenance tasks of your AWS WAF and Amazon VPC security groups. Set up your AWS WAF firewall rules, Shield protections, and Amazon VPC security groups once. The service automatically applies the rules and protections across your accounts and resources, even as you add new resources.

Firewall Manager helps you do the following: • Simplify rule management across applications and accounts. • Automatically discover new accounts and remediate noncompliant events. • Deploy AWS WAF rules from AWS Marketplace. • Activate rapid response to attacks across all accounts.

As new applications are created, Firewall Manager also facilitates bringing new applications and resources into compliance with a common set of security rules from day one. Now you have a single service to build firewall rules, create security policies, and enforce them in a consistent, hierarchical manner across your entire AWS infrastructure.
There are three prerequisites for using it: activate AWS Organizations with full features, use AWS Config, and have an assigned user as the Firewall Manager administrator.
For more information, see “Use AWS Firewall Manager to deploy protection at scale in AWS Organizations” on the AWS Security Blog (https://aws.amazon.com/blogs/security/use-aws-firewall-manager-to-deploy-protection-at-scale-in-aws-organizations/).



--- 



![](image/Pasted%20image%2020231004114701.png)

As your number of applications in the AWS Cloud grows, you should be familiar with how to manage compliance at scale.
Some of the challenges you will face include the following: 
• Large number of accounts and resources – It is hard to manage security policies centrally across all accounts and resources.
• New applications created all the time – It is difficult to be sure all applications are consistently protected on day one.
• Organization-wide visibility into threats – There is no single place to monitor and respond to any threats across the organization.
Use AWS Firewall Manager to scale up cloud security and monitoring in your environments.

For more information, see “Centrally manage AWS WAF (API v2) and AWS Managed Rules at scale with Firewall Manager” on the AWS Security Blog (https://aws.amazon.com/blogs/security/centrally-manage-aws-waf-api-v2-and-aws-managed-rules-at-scale-with-firewall-manager/)


# 8 DDos-resilient reference architecture 

![](image/Pasted%20image%2020231004114810.png)


In the diagram, AWS Shield and WAF sit on the edge of the architecture and act as gatekeepers, allowing or denying traffic. Recall that Shield protects common Layer 3 and Layer 4 infrastructure attacks. AWS WAF protects Layer 7, the application layer.
You keep bad traffic at the edge by using services such as Route 53 and CloudFront with AWS WAF and Shield. In this architecture, auto scaling is a last line of defense. Each of these AWS services, depending on the attacks, catch attacks and block them before they reach your VPC.
Services that are available in AWS edge locations, such as CloudFront, AWS WAF, and Route 53, take advantage of a global network of edge locations. Multiple edge locations provide applications with greater fault tolerance and increased scale for managing larger volumes of traffic.
In a traditional data center environment, you can mitigate infrastructure-layer DDoS attacks. You can use techniques like overprovisioning capacity, deploying DDoS mitigation systems, or scrubbing traffic with the help of DDoS mitigation services. On AWS, DDoS mitigation capabilities are automatically provided. You can optimize your application’s DDoS resilience by making architecture choices that best use those capabilities and give you the ability to scale for excess traffic.
For more information, see the AWS Whitepaper, “AWS Best Practices for DDoS Resiliency” (https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/welcome.html).


# 9 AWS outposts 



![](image/Pasted%20image%2020231004114830.png)

The network engineer asks, “Does AWS support any services running on premises to meet our latency and residency requirements?”
The engineering team must keep certain applications in their own data center for compliance and performance. The engineer wants you to explain how they can manage local resources using the same services that exist in the AWS Cloud.



![](image/Pasted%20image%2020231004114845.png)

data 仍需要放在 data center, 但是 他有需要 aws services 
if you are forced to have your data in house and not you not move it to a aWS and but you still you or you are allowed to aws, use aws outputs 

插入 Outposts chip 就行了 


To best understand AWS Outposts, consider this challenge: As you migrate applications to AWS, are there any applications that must remain on premises?
These applications might need to generate near real-time responses to end-user applications. Or they might need to communicate with other on-premises systems or control on-site equipment. Examples include workloads running on factory floors for automated operations in manufacturing, real-time patient diagnosis or medical imaging, and content and media streaming.
You need a solution to securely store and process customer data that must remain on premises or in countries outside of an AWS Region. You need to run data-intensive workloads and process data locally, or when you want closer controls on data analysis, backup, and restore.


--- 



![](image/Pasted%20image%2020231004114938.png)

physical host chip to your data center 

With Outposts, you can extend the AWS Cloud to an on-premises data center. Outposts come in different form factors, each with separate requirements. Verify that your site meets the requirements for the form factor that you're ordering.
When you order an Outposts rack, you can choose from a variety of Outposts configurations. Each configuration provides a mix of EC2 instance types and Amazon Elastic Block Store (Amazon EBS) volumes.
To fulfill the Outposts rack order, AWS will schedule a date and time with you. You will also receive a checklist of items to verify or provide before the installation. The team will roll the rack to the identified position, and your electrician can power the rack. The team will establish network connectivity for the rack over the uplink that you provide, and they will configure the rack's capacity.
With Outposts servers, you can order hardware at a smaller scale while still providing you AWS services on premises. You can choose from ARM-based or Intel-based options. Not all services available in Outposts racks are supported in Outposts servers.
Outposts servers are delivered directly to you and installed by either your own onsite personnel or a third-party vendor. Once connected to your network, AWS will remotely provision compute and storage resources.
For more information about Outpost site requirements, see “Outpost site requirements” in the AWS Outposts User Guide (https://docs.aws.amazon.com/outposts/latest/userguide/outposts-requirements.html).



---



![](image/Pasted%20image%2020231004115036.png)

A virtual private cloud (VPC) spans all Availability Zones in its AWS Region. You can extend any VPC in the Region to your Outpost by adding an Outpost subnet.
The diagram shows the relation between your Outposts and the AWS Cloud. Your Outposts family device (Outposts rack or Outposts server) is configured on premises on your network. Other on-premises devices such as a local server can communicate with Outposts. Your Outposts device is linked to a specific Availability Zone—in this case, ap-northeast-3a. The subnets have been removed from the diagram for simplicity. Adding an Outposts subnet extends your VPC to your on-premises network.
Outposts support multiple subnets. You choose the EC2 instance subnet when you launch the EC2 instance in your Outpost. You cannot choose the underlying hardware where the instance is deployed, because the Outpost is a pool of AWS compute and storage capacity.
Each Outpost can support multiple VPCs that can have one or more Outpost subnets. You create Outpost subnets from the VPC CIDR range where you created the Outpost. You can use the Outpost address ranges for resources, such as EC2 instances that reside in the Outpost subnet. AWS does not directly advertise the VPC CIDR, or the Outpost subnet range, to your on-premises location


---

![](image/Pasted%20image%2020231004115133.png)


You can create resources on your Outpost to support low-latency workloads that must run in close proximity to on-premises data and applications.
For more information about the full list of services available on Outposts, see “AWS resources on Outposts” in the AWS Outposts User Guide (https://docs.aws.amazon.com/outposts/latest/userguide/what-is-outposts.html#services).


# 10 Review 

![](image/Pasted%20image%2020231023152300.png)

![](image/Pasted%20image%2020231023152312.png)


You can create resources on your Outpost to support low-latency workloads that must run in close proximity to on-premises data and applications.
For more information about the full list of services available on Outposts, see “AWS resources on Outposts” in the AWS Outposts User Guide (https://docs.aws.amazon.com/outposts/latest/userguide/what-is-outposts.html#services).


# 11 Knowledge Check 


d 
a 

![](image/Pasted%20image%2020231004115204.png)

The answer is A and D, increased application security and reduced latency for access to application content.
CloudFront has built-in integrations with AWS Shield and AWS WAF, providing DDoS protection. CloudFront is a global content delivery network (CDN) service that accelerates delivery of your websites, APIs, video content, or other web assets.

-----

d e


![](image/Pasted%20image%2020231004115309.png)

The answer is D and E, AWS Shield and AWS WAF.
AWS Shield – AWS provides AWS Shield Standard and AWS Shield Advanced for protection against DDoS attacks. AWS Shield Standard is automatically included at no extra cost beyond what you already pay for AWS WAF and your other AWS services.
For more information, see “AWS Shield” in the AWS WAF, AWS Firewall Manager, and AWS Shield Advanced Developer Guide (https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html).
AWS WAF – Use AWS WAF web ACLs to help minimize the effects of a DDoS attack.
For more information, see “AWS WAF” in the AWS WAF, AWS Firewall Manager, and AWS Shield Advanced Developer Guide (https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)


-----

b

![](image/Pasted%20image%2020231004115407.png)

The answer is B, Weighted routing.
With weighted routing, you can assign weights to a resource record set to specify the frequency with which different responses are served.


--------

when you have to use the Outpost serves not Outpost rack 

output servers

c


![](image/Pasted%20image%2020231004115424.png)


![](image/Pasted%20image%2020231004115547.png)

The answer is C, A rack-mountable server is available in a location with space constraints.
AWS will deliver Outposts servers directly to you, and you can either have your onsite personnel or an AWS preferred third-party contractor install them. After the Outposts servers are connected to your network, AWS will remotely provision compute and storage resources so you can start launching applications







