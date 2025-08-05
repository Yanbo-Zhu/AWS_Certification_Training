

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


## 1.1 ELB Load Balancer components 


![](image/Pasted%20image%2020231003132600.png) 

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


# 4 各个LB common feature and uncommon faeature


![](image/Pasted%20image%2020231003133117.png)



The table in the graphic outlines support for a set of load balancer features.
- If you need flexible application management, consider an Application Load Balancer. 
- If you need extreme performance and a static IP, consider a Network Load Balancer. 
- If you need to manage your third-party virtual appliances, consider a Gateway Load Balancer.


## 4.1 static ip addresse

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

## 4.2 SSL offloading

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




## 4.3 redirects: to another websites
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

# 5 NLB vs ALB

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

