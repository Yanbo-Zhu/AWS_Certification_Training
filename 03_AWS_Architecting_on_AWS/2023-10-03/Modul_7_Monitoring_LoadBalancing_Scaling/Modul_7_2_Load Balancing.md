

![](image/Pasted%20image%2020231003132018.png)


# 1 ELB: Elastic Load Balancing 

![](image/Pasted%20image%2020231003132153.png)


ELB is a highly available and scalable AWS service that automatically distributes incoming application traffic across multiple targets. Targets can be Amazon EC2 instances, containers, IP addresses, Lambda functions, and more. The targets can be in a single Availability Zone or multiple zones. With ELB, you would have two or more Amazon EC2 instances. If one instance stops responding, ELB will distribute the traffic to the other instances, without affecting your customers.
ELB uses heath checks to determine if a resource is available. The heath checks are indicated by an API response code. For example, if the code is 200 (OK), the resource is running without any issues. If the code is 503, the resource is unavailable, so ELB will route traffic to other available resources.

Elastic Load Balancing (ELB) makes up one of the most widely used AWS service categories. It has been adopted by organizations of all sizes, in all geographies, and across every industry. ELB load balancers are the only load balancers available on AWS that natively connect users to your EC2 instances, container deployments, and AWS Lambda functions. Some key feature sets include:
• High availability – ELB automatically distributes your traffic across multiple targets in a single Availability Zone or multiple Availability Zones. Examples of targets include EC2 instances, containers, and IP addresses.
• Layer 4 or Layer 7 HTTP and HTTPS load balancing – You can load balance your HTTP or HTTPS applications for Layer 7-specific features. Alternatively, you can use strict Layer 4 load balancing for applications that rely purely on the TCP.
• Security features – Use Amazon VPC to create and manage security groups that are associated with load balancers to provide additional networking and security options. You can also create an internal (non-internet-facing) load balancer.
• Health checks – ELB load balancers can detect unhealthy targets, stop sending traffic to them, and spread the load across the remaining healthy targets.
• Monitoring operations – To monitor real-time application performance, ELB integrates with CloudWatch metrics and provides request tracing.
In this example, the load balancer receives requests from desktop and mobile clients (users). There are two subnets in the same VPC, with two EC2 instances each. Each subnet is in a separate Availability Zone. All four EC2 instances are registered to the same load balancer and receive traf


ELB has a number of benefits, including:
• High availability and elasticity: ELB is an AWS managed service that supports your application in a Region. ELB automatically adds and removes capacity based on server usage.
• Security: ELB works with Amazon Virtual Private Cloud (VPC) to provide robust security features, including integrated certificate management, user-authentication, and SSL/TLS decryption.
• Feature breadth: ELB includes support for features needed in container-based workloads, including HTTP/S, gRPC, TLS offload, advanced rule-based routing, and integration with container services.
• Robust monitoring and visibility: ELB helps you to monitor the health of your applications and their performance in real time with Amazon CloudWatch metrics, logging, and request tracing. This improves visibility into your application’s performance.
• Integration and global reach: ELB is integrated with other AWS services, such as Amazon EC2, Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS), and more. ELB is available wherever you run your AWS workloads.


## 1.1 ELB Load Balancer components 


![](image/Pasted%20image%2020231003132600.png) 


![](image/Pasted%20image%2020231013115141.png)


Load balances can wotk with different services
Listeners:  LB ist load balancer
Tagrget groups:
Load balander rules:  form app2 , use tg 1 According to rule, load balancer decide to suer target froup s


Three main components of ELB are listeners, target groups, and rules.
• Listeners: A listener is a process that checks for connection requests. To define a listener, you configure a protocol and port, based on the ELB type. Customers connect to a listener, which is referred as client-side.
• Target groups: A target group is a collection of resources, such as Amazon EC2 instances, AWS Lambda function, or IP addresses, where you send traffic. Each target group must have health check definitions.
• Rules: Rules are sets of connection instructions that define the source IP addresses and resources in target groups. You configure rules to associate a target group with a listener.


An ELB load balancer distributes your incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones. In this way, it increases the availability of your application. Your load balancers are configured with listeners. You can have more than one listener per load balancer. Listeners have different functions for different types of load balancers. Your load balancer can forward requests to one or more target groups based on rules and settings that you define.
Each target group routes requests to one or more registered targets (for example, EC2 instances) by using the specified protocol and port number. You can register a target with multiple target groups.

In the example, a load balancer has two listeners. Listener 1 has one target group called target group 1, with two registered targets. A second listener in the same load balancer has one target group with three different registered targets.



![](image/Pasted%20image%2020231003132645.png)


# 2 Load Balancer types

![](image/Pasted%20image%2020231003132335.png)


Gateway load balancer:  more secutriry only 
其他两个 loadbalacer : normal workload 

Types of load balancers available for you to use include:
• Application Load Balancer – This load balancer functions at the application layer, the seventh layer of the Open Systems Interconnection (OSI) model. Application Load Balancer supports content-based routing, applications that run in containers, and open standard protocols (WebSocket and HTTP/2). This type of balancer is ideal for advanced load balancing of HTTP and HTTPS traffic.
• Network Load Balancer – This load balancer is designed to handle tens of millions of requests per second while maintaining high throughput at ultra-low latency. Network Load Balancer operates at the transport layer (Layer 4), and routes connections to targets based on IP protocol data. Targets include EC2 instances, containers, and IP addresses. It is ideal for balancing TCP and User Diagram Protocol (UDP) traffic.
• Gateway Load Balancer – You can use this load balancer to deploy, scale, and manage your third-party virtual appliances. It provides one gateway for distributing traffic across multiple virtual appliances, and scales them up or down, based on demand. This distribution reduces potential points of failure in your network and increases availability. Gateway Load Balancer passes all Layer 3 traffic transparently through third-party virtual appliances. It is invisible to the source and destination.
• Classic Load Balancer – This previous-generation load balancer is not discussed deeply in this course.


|类型|OSI 层|协议|主要用途|
|---|---|---|---|
|**CLB**|L4 + L7|TCP, HTTP, HTTPS|旧版本，功能有限，现在基本不推荐新建|
|**ALB**|L7|HTTP, HTTPS, gRPC|需要基于 URL、Host 的路由（Web 应用）|
|**NLB**|L4|TCP, UDP, TLS|高性能、低延迟的网络流量（数据库、gRPC、MQTT、游戏服务器等）|


# 3 ALB 

![](image/Pasted%20image%2020231013115653.png)

pplication Load Balancer is ideal for load balancing HTTP and HTTPS traffic. It operates at the request level (layer 7), routing traffic to targets (Amazon EC2 instances, containers, IP addresses, and AWS Lambda functions) based on the request content.

Application Load Balancer has a number of primary features.
• Security: You can create and manage security groups associated with ELB to provide additional networking and security options inside your Amazon VPC. Application Load Balancer supports desync protections implementation based on the http_desync_guardian library, where customer applications are protected from HTTP vulnerabilities.
• TLS offloading: Application Load Balancer supports client TLS session termination. You can create an HTTPS listener, which enables traffic encryption between your load balancer and the clients that initiate SSL or TLS sessions. 
    Load balander cajnd0 the decryption  and encyrtion  for ec2 instances . So do not do decryption  and encyrtion  in ec2 instances  solelt
• Sticky sessions: Application Load Balancer supports both duration-based and application-based cookies, enabling nearly continuous request routing from the same client to the same target.
• Redirects: Application Load Balancer can redirect an incoming request from one URL, such as HTTP, to another URL, such as HTTPS, helping you to achieve security compliance.
• Fixed response: Application Load Balancer can control which client requests are served by your application, enabling it to respond to requests before they reach your applications.
• Content-based routing: Application Load Balancer can route a request to a service based on the content of the request, such as Host field, Path URL, HTTP header, HTTP method, Query string, or source IP address.

Resource To learn more about Application Load Balancer features, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/application-load-balance


## 3.1 **ALB is Multi-Tenant (several dynamical IP)


ALB 是 AWS 的 **多租户全托管服务**，它的入口是由 AWS 管理的一组动态 IP，AWS 可能会因为扩容、维护等原因随时更换这些 IP。 详细解释一下
 ALB is a **multi-tenant, fully managed service** in AWS. Its entry point uses a set of **dynamic IP addresses** managed by AWS.  These IPs can change at any time (due to scaling, maintenance, failover, etc.).

Client -> DNS Resolve ALB hostname -> AWS returns healthy ALB node IPs -> ALB nodes may change IPs due to scaling/failover/maintenance -> ALB Listener (in this ALB node) --> Backend

Entry via AWS-Managed Dynamic IPs
When you create an ALB, AWS gives you a DNS name like: `my-alb-1234567890.us-east-1.elb.amazonaws.com`
==这很重要: ==
- That DNS record is managed by AWS Route 53 internally.
- ==When a client resolves this DNS name, AWS returns one or more **public IP addresses** for ALB nodes.==
- ==These IP addresses belong to AWS’s public IP pool and **can change**==.


**ALB is Multi-Tenant & Fully Managed**
- **Multi-tenant**
    - Your ALB is not running as a dedicated VM or network device only for you.
    - ==AWS hosts many customers’ ALBs on a **shared fleet of load balancer infrastructure** in each AWS region.==
    - Even though logically it’s “your ALB,” physically AWS runs it in a shared system that dynamically allocates resources.
- **Fully managed**
    - You don’t manage the hardware, OS, or scaling.
    - AWS decides when and where to add or remove ALB nodes (for scaling, failover, or maintenance).


**Why IPs Can Change Anytime**
==ALB is not bound to fixed ENIs (like NLB)==. Instead:
- **Scaling events** — When traffic increases, AWS may add new ALB nodes with new IPs.
- **Failover** — If a node becomes unhealthy, AWS removes it and replaces it with another one (new IP).
- **Maintenance** — AWS may patch or upgrade ALB nodes, replacing them with new machines.
- **Regional optimization** — AWS may change ALB nodes to optimize latency or load.
If you hardcode ALB’s current IP in your firewall, it might break after AWS changes the IPs.

**How AWS Makes This Work**
- AWS ensures **high availability** by putting **multiple ALB nodes in multiple AZs**.
- The DNS name for your ALB always resolves to the **current set of healthy nodes’ IP addresses**.
- TTL (time-to-live) for these DNS records is short (usually 60 seconds), so clients can quickly pick up new IPs.

**Why ALB Can’t Have a Static IP**
- Giving each ALB a dedicated fixed public IP would:
    - Reduce AWS’s flexibility in scaling and failover.
    - Waste IP addresses when ALBs scale down.
- Instead, AWS recommends:
    - ==Use **Route 53 Alias record** to map your domain to the ALB’s DNS name==.
    - If you absolutely need a static IP, put **AWS Global Accelerator** in front of the ALB (Global Accelerator provides fixed Anycast IPs).


# 4 NLB


![](image/Pasted%20image%2020231013115756.png)


Network Load Balancer is ideal for load balancing TCP and UDP traffic. It operates at the connection level (layer 4), routing connections to targets (Amazon EC2 instances, microservices, and containers) in Amazon VPC, based on IP protocol data.
Some of the primary features of Network Load Balancer are:
• Sticky sessions: Requests are routed from the same client to the same target by a sticky session defined at the target group level.
• Low latency: Network Load Balancer offers low latencies for latency-sensitive applications. • Preserve source IP address: Network Load Balancer preserves the client-side source IP address and allows the backend to see the client’s IP address.
• Static IP support: Network Load Balancer automatically provides a static IP address per Availability Zone (subnet) that can be used by applications as the load balancer’s front-end IP.
• Elastic IP address support: You can assign an Elastic IP address per AZ (subnet and have your own fixed IP.
• DNS failover: If no healthy targets are registered with the Network Load Balancer or the Network Load Balancer nodes in a zone are unhealthy, Amazon Route 53 will direct traffic to load balancer nodes in other Availability Zones.

Resource 
To learn more about Network Load Balancer, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/network-load-balancer/




# 5 Gateway Load Balancer 

![](image/Pasted%20image%2020231013115909.png)


Gateway Load Balancer helps you to deploy, scale, and manage your third-party virtual appliances. It provides a gateway for distributing traffic across multiple virtual appliances, while scaling them up and down based on demand.

Some of the primary features of Gateway Load Balancer are:
• Bring higher-availability to third-party virtual appliances: Gateway Load Balancer ensures high availability and reliability by routing traffic through healthy virtual appliances and rerouting flows when a virtual appliance becomes unhealthy.
• Monitor health and performance metrics: You can monitor your Gateway Load Balancer using Amazon CloudWatch per Availability Zone metrics.
• Streamline deployment with AWS Marketplace: Deploying a new virtual appliance can be as straightforward as selecting it in AWS Marketplace.
• Ensure private connectivity in the AWS Cloud with Gateway Load Balancer endpoints: Gateway Load Balancer connects internet gateways, VPCs, and other network resources over a private connection. Your traffic flows in the AWS Cloud, which protects your data from being exposed on the internet.

Resource
To learn more about Gateway Load Balancer, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/gateway-load-balancer


# 6 Classic Load Balancer 

![](image/Pasted%20image%2020231013115916.png)

Classic Load Balancer is intended for applications built for Amazon EC2-Classic. It provides load balancing across multiple Amazon EC2 instances and operates at both the request and connection levels.

Classic Load Balancer has two primary features.
• SSL offloading: Classic Load Balancer supports SSL termination, including offloading SSL for backend application instances, centralized management of SSL certificates, and re-encryption to backend instances with optional public key authentication.
• IPv6 support: Classic Load Balancer supports the use of both the Internet Protocol version 4 and 6 (IPv4 and IPv6) for Amazon EC2-Classic solutions.

Resource
To learn more about Classic Load Balancer, refer to the AWS service page: https://aws.amazon.com/elasticloadbalancing/classic-load-balancer

# 7 各个LB common feature and uncommon faeature


Elastic Load Balancer (ELB) has 4 different types of possible load balancers.
ALB: Applikation Loadbalancer 
NLB: Network Loadbalancer
CLB: Classic Loadbalancer 
GWLB: Gateway Load Balancer 

application load balancer  and network load balancer  are specialized for their  individual use case. 
All thos Loadbalancer you can attch the amazon certification manager so you can apply ssl certificate



![](image/Pasted%20image%2020230317173623.png)

![](image/Pasted%20image%2020230522144042.png)

- CLB Classic Load Balancer 
    -  Layer 3,4 and 7 
    - does not use target groups. 
    - it's  intended for applications that were built within  the **EC two classic network** in mind,
    - Retires on Aug 15, 2022
- ALB Application Load Balancer
    - works in Application Layer Layer 7 - HTTP/S 
    - So prior to  this, if you needed a load bouncer for subdomain,  you'd have to launch a load bouncer for each one.  But now you with routing rules, you can route all  subdomains to the single load balancer and make  sure that it goes to the right instances that you  want to target.
    - Can attach WAF (web application firewall)
    -  Routing Rules:    create rules to change routing based on information found in an HTTP/S request
- NLB Network Load Balancer 
    - works in Transport layer .  Layer 3 and 4 – TCP and UDP
        - thie layer is dealing with IP protocol data. So this is where  you are dealing with TCP and TLS traffic where extreme performance ist required 
    - Example:  video , games ,  real time. So think about handling  millions of requests per second will maintain  **ultra low latency**
    - It's also optimized  for sudden and volatile traffic patterns. 
    - Optimized for **sudden and volatile traffic** patterns while using a single static IP address per Availability Zone
    - Capable of handling millions of requests per second while maintaining ultra-low latencies
- **Gateway Load Balancer (GWLB)**
    - When you need to deploy a fleet of third-party virtual appliances that support GENEVE





![](image/Pasted%20image%2020231003133117.png)



The table in the graphic outlines support for a set of load balancer features.
- If you need flexible application management, consider an Application Load Balancer. 
- If you need extreme performance and a static IP, consider a Network Load Balancer. 
- If you need to manage your third-party virtual appliances, consider a Gateway Load Balancer.





## 7.1 static ip addresse

fix the ip address that used in alb 

![](image/Pasted%20image%2020231003133208.png)

**Elastic Load Balancing now supports forwarding traffic directly from Network Load Balancer to Application Load Balancer. With this feature, you can use AWS PrivateLink and expose static IP addresses for applications that are built on Application Load Balancer.
For more information and a full, up-to-date comparison of ELB products, see “Elastic Load Balancing features” at https://aws.amazon.com/elasticloadbalancing/features/?nc=sn&loc=2.
Learn more about exposing static IP addresses for applications that are built on Application Load Balancer. For more information, see “Application Load Balancer now enables AWS PrivateLink and static IP addresses by direct integration with Network Load Balancer” at https://aws.amazon.com/about-aws/whats-new/2021/09/application-load-balancer-aws-privatelink-static-ip-addresses-network-load-balancer/.

==NLB 能用静态 IP 是因为它直接绑定 VPC 内的 ENI，而 ALB 是多租户共享架构，AWS 必须动态管理其 IP，所以不允许你固定 IP。==
==NLB can use static IPs because it’s directly tied to ENIs in your VPC.   ALB can’t because AWS dynamically manages its IP pool for scalability and redundancy.==

NLB 支持静态 IP 地址的原因
- **NLB 是 L4 负载均衡器**（基于 TCP/UDP 层）。
- 它直接在 **VPC 子网中分配 ENI（Elastic Network Interface）**，每个 ENI 都有固定的私有 IP，可以绑定 **EIP（Elastic IP）**，因此对外可以提供 **固定的公网 IP**。
- 因为工作在传输层，它不需要 AWS 的全局 DNS 解析来分配入口流量，所以固定 IP 是可行的。
- **NLB (Network Load Balancer)** is a **Layer 4** load balancer (TCP/UDP).
- It directly allocates **ENIs (Elastic Network Interfaces)** inside your **VPC subnets**.
- Each ENI has a fixed private IP and can be assigned an **Elastic IP (EIP)**, so you can have a **static public IP**.
- Since it operates at the transport layer, it doesn’t rely on AWS’s global DNS layer for routing, so static IPs are possible.


**原理：** `Client --> 固定 EIP --> NLB ENI --> 目标节点`


ALB 不支持静态 IP 的原因
- **ALB 是 L7 负载均衡器**（基于 HTTP/HTTPS 层）。
- ALB 是 AWS 的 **多租户全托管服务**，它的入口是由 AWS 管理的一组动态 IP，AWS 可能会因为扩容、维护等原因随时更换这些 IP。
- ALB 通过 **DNS 名称（如 my-alb-1234567890.us-east-1.elb.amazonaws.com）** 暴露服务，DNS 记录里可能有多个 A 记录，这些a记录的IP 会随时间变化。 每个ip address 都是 public IP address for ALB nodes 
- AWS 官方推荐使用 **Route 53 + CNAME** 或 **Alias Record** 绑定到 ALB，而不是直接用 IP。
- **ALB (Application Load Balancer)** is a **Layer 7** load balancer (HTTP/HTTPS).    
- ALB is a **multi-tenant, fully managed service** in AWS.
- Its entry point uses a set of **dynamic IP addresses** managed by AWS.  
    These IPs can change at any time (due to scaling, maintenance, failover, etc.).
- ALB is exposed via a **DNS name** (e.g., `my-alb-1234567890.us-east-1.elb.amazonaws.com`), which can resolve to multiple IP addresses that change over time.
- AWS recommends using **Route 53 + CNAME** or **Alias records** to ==map a domain to an ALB== instead of relying on a fixed IP.

`Client --> DNS 解析 ALB 域名 --> AWS 动态分配 IP --> ALB Listener --> 后端`
`Client --> DNS resolves ALB hostname --> AWS dynamically assigns IP --> ALB Listener --> Backend`


|功能|NLB（L4）|ALB（L7）|
|---|---|---|
|支持静态 IP|✅（绑定 EIP）|❌（仅支持 DNS 名称）|
|协议层|TCP/UDP|HTTP/HTTPS/WebSocket|
|性能|极高（低延迟）|高（有应用层处理开销）|
|适用场景|游戏、VoIP、固定入口|Web 应用、API 网关、HTTPS|

## 7.2 SSL offloading

==SSL Offloading 就是**把 SSL 处理工作交给负载均衡器**，让后端只处理明文 HTTP 请求，从而提升性能、简化证书管理。==

SSL（Secure Sockets Layer，安全套接字层）是一种用于在网络通信中 加密数据传输 的安全协议。
在网络架构中，由负载均衡器（如 AWS ALB、NLB + TLS、NGINX Ingress Controller）来处理 **SSL/TLS 加密与解密**，而不是由后端应用服务器自己处理。


**工作原理**
1. 客户端（浏览器、App）发起 **HTTPS** 请求。
2. 负载均衡器使用配置的 SSL 证书 **解密** 数据（TLS handshake）。
3. 解密后的数据以 **HTTP**（非加密）协议转发到后端应用服务器。
4. 应用返回响应，负载均衡器再 **加密**（可选）并发回给客户端。

**主要作用**
- **减轻后端压力**：后端不再处理 SSL 加解密的 CPU 开销。
- **统一证书管理**：证书只需要在负载均衡器上配置，不需要在每台后端机器上部署。
- **提高性能**：特别是高并发环境下，可以减少服务器 CPU 占用。

 **典型场景**
- **AWS ALB / ELB SSL Offloading**
    - ALB 监听 **HTTPS:443**，与客户端建立 TLS 连接。
    - ALB 解密后，把流量用 **HTTP:80** 发给 EC2 / Kubernetes Pod。
- **NGINX Ingress Controller SSL Termination**
    - Ingress Controller 处理 TLS，然后用 HTTP 给后端 Service。


 **注意事项**
- 如果使用 SSL Offloading，**客户端和负载均衡器之间是加密的**，但 **负载均衡器到后端是明文**，需要确保它们之间的网络是可信（比如同一个 VPC 内）。
- 如果后端也需要加密，可以使用 **SSL Pass-through** 或 **Re-encryption**（SSL → 解密 → 再加密）。




## 7.3 redirects: to another websites
==“ALB 支持 redirect” 就是说你可以直接在 ALB 里做 URL/协议/端口/路径跳转，不需要后端应用自己返回 301/302，节省了后端的处理逻辑。==

你可以在 **ALB 的监听器规则（Listener Rules）** 中配置 **重定向（Redirect Action）**，把收到的请求自动跳转到另一个 URL、协议、端口或路径。

常见用途
- **HTTP → HTTPS 重定向**（最常见）
    - 强制所有用户走 HTTPS。
- **域名跳转**
    - `example.com` → `www.example.com`
- **路径重定向**
    - `/old-page` → `/new-page`
- **端口重定向**
    - `http://example.com:8080` → `https://example.com:443`


AWS 控制台 / Terraform / CloudFormation 中可以这样设置：
这个例子会把所有 HTTP 请求重定向到 HTTPS，保持原有路径和查询参数。
```
{
  "Type": "redirect",
  "RedirectConfig": {
    "Protocol": "HTTPS",
    "Port": "443",
    "Host": "#{host}",
    "Path": "/#{path}",
    "Query": "#{query}",
    "StatusCode": "HTTP_301"
  }
}
```

# 8 NLB vs ALB

| 对比项         | **NLB**                                   | **ALB**                      |
| ----------- | ----------------------------------------- | ---------------------------- |
| **工作层级**    | 传输层（Layer 4）                              | 应用层（Layer 7）                 |
| **路由能力**    | 基于 IP/端口，不能解析 HTTP                        | 基于 Host、Path、Header、Method 等 |
| **性能**      | 高吞吐量、低延迟（百万 TPS 级别）                       | 较高延迟（需解析 HTTP 请求）            |
| **协议支持**    | TCP、UDP、TLS                               | HTTP、HTTPS、gRPC              |
| **静态 IP**   | 支持（可分配 EIP）                               | 不支持（ALB 是 DNS 名称）            |
| **跨 AZ 转发** | 支持本地 AZ 优先（优化流量）                          | 会跨 AZ 转发（有延迟+跨 AZ 费用）        |
| **典型场景**    | 数据库代理、MQTT、游戏、视频流、Ingress Controller (L4) | Web 应用、微服务 API 网关            |

- **NLB**：快、硬核、L4 传输层、支持 TCP/UDP、高并发、静态 IP，适合后端服务或网关入口。
- **ALB**：聪明、灵活、L7 应用层、支持 HTTP/HTTPS 路由，适合 Web/API 网关。


什么时候选 NLB？
✅ 适合：
- 需要超低延迟、百万级并发
- TCP/UDP 流量（非 HTTP）
- 需要静态 IP（EIP）
- Kubernetes Ingress Controller 做 L4 转发（比如 NGINX Ingress、Envoy）


什么时候选 ALB？
✅ 适合：
- HTTP/HTTPS 流量
- 需要基于 URL 路径、域名路由
- Web API / 前后端分离
- 想直接用 AWS WAF、安全组、Cognito 认证等 ALB 的 L7 功能

