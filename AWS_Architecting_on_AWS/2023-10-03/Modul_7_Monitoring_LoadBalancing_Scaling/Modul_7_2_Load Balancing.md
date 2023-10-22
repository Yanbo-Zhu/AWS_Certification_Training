

![](image/Pasted%20image%2020231003132018.png)


# 1 ELB: Elastic Load Balancing 

![](image/Pasted%20image%2020231003132153.png)


Elastic Load Balancing (ELB) makes up one of the most widely used AWS service categories. It has been adopted by organizations of all sizes, in all geographies, and across every industry. ELB load balancers are the only load balancers available on AWS that natively connect users to your EC2 instances, container deployments, and AWS Lambda functions. Some key feature sets include:
• High availability – ELB automatically distributes your traffic across multiple targets in a single Availability Zone or multiple Availability Zones. Examples of targets include EC2 instances, containers, and IP addresses.
• Layer 4 or Layer 7 HTTP and HTTPS load balancing – You can load balance your HTTP or HTTPS applications for Layer 7-specific features. Alternatively, you can use strict Layer 4 load balancing for applications that rely purely on the TCP.
• Security features – Use Amazon VPC to create and manage security groups that are associated with load balancers to provide additional networking and security options. You can also create an internal (non-internet-facing) load balancer.
• Health checks – ELB load balancers can detect unhealthy targets, stop sending traffic to them, and spread the load across the remaining healthy targets.
• Monitoring operations – To monitor real-time application performance, ELB integrates with CloudWatch metrics and provides request tracing.
In this example, the load balancer receives requests from desktop and mobile clients (users). There are two subnets in the same VPC, with two EC2 instances each. Each subnet is in a separate Availability Zone. All four EC2 instances are registered to the same load balancer and receive traf


![](image/Pasted%20image%2020231003132335.png)


Gateway load balancer:  more secutriry only 
其他两个 loadbalacer : normal workload 

Types of load balancers available for you to use include:
• Application Load Balancer – This load balancer functions at the application layer, the seventh layer of the Open Systems Interconnection (OSI) model. Application Load Balancer supports content-based routing, applications that run in containers, and open standard protocols (WebSocket and HTTP/2). This type of balancer is ideal for advanced load balancing of HTTP and HTTPS traffic.
• Network Load Balancer – This load balancer is designed to handle tens of millions of requests per second while maintaining high throughput at ultra-low latency. Network Load Balancer operates at the transport layer (Layer 4), and routes connections to targets based on IP protocol data. Targets include EC2 instances, containers, and IP addresses. It is ideal for balancing TCP and User Diagram Protocol (UDP) traffic.
• Gateway Load Balancer – You can use this load balancer to deploy, scale, and manage your third-party virtual appliances. It provides one gateway for distributing traffic across multiple virtual appliances, and scales them up or down, based on demand. This distribution reduces potential points of failure in your network and increases availability. Gateway Load Balancer passes all Layer 3 traffic transparently through third-party virtual appliances. It is invisible to the source and destination.
• Classic Load Balancer – This previous-generation load balancer is not discussed deeply in this course.


----


![](image/Pasted%20image%2020231003132600.png) 



![](image/Pasted%20image%2020231003132645.png)


ssl: for network \
https: for a loader blanace 

什么事 SSL offloading ? 

preserve source ip address: 因为某些国家 要 阻挡 某个货架的访问 
redirects: to another websites

An ELB load balancer distributes your incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones. In this way, it increases the availability of your application. Your load balancers are configured with listeners. You can have more than one listener per load balancer. Listeners have different functions for different types of load balancers. Your load balancer can forward requests to one or more target groups based on rules and settings that you define.
Each target group routes requests to one or more registered targets (for example, EC2 instances) by using the specified protocol and port number. You can register a target with multiple target groups.
In the example, a load balancer has two listeners. Listener 1 has one target group called target group 1, with two registered targets. A second listener in the same load balancer has one target group with three different registered targets.

--- 

![](image/Pasted%20image%2020231003132905.png)



![](image/Pasted%20image%2020231003133117.png)

static ip addresse: fix the ip address that used in alb 

![](image/Pasted%20image%2020231003133208.png)



The table in the graphic outlines support for a set of load balancer features.
If you need flexible application management, consider an Application Load Balancer. If you need extreme performance and a static IP, consider a Network Load Balancer. If you need to manage your third-party virtual appliances, consider a Gateway Load Balancer.
**Elastic Load Balancing now supports forwarding traffic directly from Network Load Balancer to Application Load Balancer. With this feature, you can use AWS PrivateLink and expose static IP addresses for applications that are built on Application Load Balancer.
For more information and a full, up-to-date comparison of ELB products, see “Elastic Load Balancing features” at https://aws.amazon.com/elasticloadbalancing/features/?nc=sn&loc=2.
Learn more about exposing static IP addresses for applications that are built on Application Load Balancer. For more information, see “Application Load Balancer now enables AWS PrivateLink and static IP addresses by direct integration with Network Load Balancer” at https://aws.amazon.com/about-aws/whats-new/2021/09/application-load-balancer-aws-privatelink-static-ip-addresses-network-load-balancer/.








