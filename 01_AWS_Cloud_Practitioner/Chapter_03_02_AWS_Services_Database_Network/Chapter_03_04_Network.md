
# 1 Cloud-Native Networking Services
6:35:39 Cloud-Native Networking Services

[Internetwork traffic privacy in Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html)
[VPC networking components](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Networking.html)

![](image/Pasted%20image%2020230513153709.png)
 
![](image/Pasted%20image%2020230513154007.png)

**Key definitions:**
- [**Region**](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/) - the geographical location of your network
- [**Virtual Private Cloud (VPC)**](https://docs.aws.amazon.com/vpc/latest/userguide/how-it-works.html)- a logically isolated section of the AWS Cloud where you can launch AWS resources
- [**Availability Zone** (**AZ)**](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/) - a data center containing your AWS resources
- **[Subnets](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html)**- a logical partition of an IP network into multiple, smaller network segments
- **[Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)**- Act as firewall at the instance level

- [**Internet Gateway**](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)- enables access to the Internet for your VPC
- **[Route Tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)**- determines where network traffic from your subnets are directed
- **[NACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html)**- _Network Access Control Lists._ Act as a firewall at the subnet level

- **Availability Zones:**
    - Availability Zones are the **data centers** where you launch your AWS resources into
    - Each AZs is associated with a specific `region`
- **Key VPC Components:**
    - A virtual private cloud (VPC) network is your own personal isolated section of the AWS cloud.
    - A `route table` contains a set of rules (called routes), that are used to determine where network traffic from your subnet or gateway is directed.
- **Internet Gateway**
    - Allows you to grant internet access to resources inside of your VPC. But you also need a **route table** which routes the traffic from the VPC network out to the IGW
    - You can think of it as a door from your `VPC` outward.

# 2 Enterprise/Hybrid Networking Services
6:37:07 Enterprise/Hybrid Networking Services

![](image/Pasted%20image%2020230513154344.png)


- Direct Connect
    - is a dedicated Gigabit network connection from your premises location to AWS. Provides a direct fiber optic cable running straight to the AWS network
- VPN - establishes a secure connection to your AWS network
    - Site-to-Site VPN - connecting your on-premise to your AWS network
        -  Which of the following are components of an AWS Site-to-Site VPN connection? (Choose two.): Virtual private gateway and Customer gateway 
        - The VPC has an attached virtual private gateway, and your on-premises (remote) network includes a customer gateway device, which you must configure to enable the Site-to-Site VPN connection. You set up the routing so that any traffic from the VPC bound for your network is routed to the virtual private gateway.
    - Client VPN - connecting a Client (ie users laptop) to your AWS network
- VPC Private Links (VPC Interface Endpoints) 
    - keeps traffic within the AWS network and not traverse the internet to keep traffic is secure.​
    - AWS PrivateLink provides private connectivity between virtual private clouds (VPCs), supported AWS services, and your on-premises networks without exposing your traffic to the public internet.
    - VPC Private Link is a way of making your service available to set of consumers. You can expose a service and the consumers can consume your service by creating an endpoint for your service.  With PrivateLink, endpoints are instead created directly inside of your VPC, using Elastic Network Interfaces (ENIs) and IP addresses in your VPC's subnets. 
    - To use AWS PrivateLink, create a VPC endpoint in your VPC, specifying the name of the service and a subnet. This creates an elastic network interface in the subnet that serves as an entry point for traffic destined to the service. The service is now in your VPC, enabling connectivity to AWS services via private IP addresses.
- AWS Transit Gateway
    - A large enterprise with multiple VPCs in several AWS Regions around the world needs to connect and centrally manage network connectivity between its VPCs. Which AWS service or feature meets these requirements? use AWS Transit Gateway
        - AWS Transit Gateway is a service that simplifies network connectivity between VPCs, VPNs, and on-premises networks. It allows the company to centrally connect to multiple VPCs in different AWS regions using a single gateway, making it easier to manage large-scale network connectivity.


# 3 Virtual Private Cloud (VPC) & Subnets
6:38:13 Virtual Private Cloud (VPC) & Subnets

![](image/Pasted%20image%2020230513155006.png)

- Virtual Private Cloud (VPC) 
    - is a logically isolated section of the AWS Network where you launch your AWS resources. 
    - You choose a range of IPs using CIDR Range
        - CIDR Range of 10.0.0.0/16 = 65,536 IP Addresses
        - CORRECTION: The CIDR Range for the Private Subnet should be 10.0.1.0/24, not 10.0.0.0/24
- Subnets 
    - a logical partition of an IP network into multiple smaller network segments. 
    - You are breaking up your IP range for VPC into smaller networks.
    - Subnets need to have a smaller CIDR range than to the VPC represent their portion.​ eg Subnet CIDR Range 10.0.0.0/24 = 256 IP Addresses

Public vs Private Subnets:
- Public subnet is one that can reach the Internet. Public subnet are generally used for placing resources which are accessible on the internet
- Private subnet is one that can not reach the internet. Private subnet are used when you need resources to be more secured and only accessible through tightly filtered traffic into the subnet

## 3.1 VPC peeruing 

You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The VPCs can be in different Regions. AWS uses the existing infrastructure of a VPC to create a VPC peering connection.   Answer = Peering

VPC peering can be used to establish a connection between two VPCs located in different AWS Regions while using their existing infrastructure. VPC peering allows traffic to flow between the two VPCs privately using AWS' network. This can be useful for scenarios where there is a need to transfer data between VPCs in different regions without exposing the data to the public internet.



# 4 Security Groups vs NACLs (Network Access Control Lists)
6:39:49 Security Groups vs NACLs

[Security groups for your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)

Security Groups and NACLs are all within the VPC. But the utility of these are slightly different.
So in that diagram, you can see that all those instances are contained within a security group,   and they can span multiple subnets. Whereas the  NACLs sit in front of the subnets. 
And NACLs gonna control access in and out from subnets.  

![](../Chapter_06_02_Security/image/Pasted%20image%2020230316093259.png)

![](image/Pasted%20image%2020230513155137.png)

## 4.1 NACLs
- NACLs act as a firewall at the subnet level.  
- <mark> 通过 Security Groups  只能定义 deny rules </mark>. Via NACLs, you can allow the deny rules.
    - Example (block a specific IP address to access your a specific Subnet ): The real utility of NACLs is that you can block a specific IP address known for abuse. Because you can have deny rules. And you can say exactly, I want to  deny exactly this IP address. 
    - ==Network ACLs are stateless, which means that responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).  These are stateless, meaning any change applied to an incoming rule isn't automatically applied to an outgoing rule==
    - Rules are evaluated starting with the lowest numbered rule. As soon as a rule matches traffic, it's applied regardless of any higher-numbered rule that might contradict it.

## 4.2 Security Groups
- They act as a firewall at the instance level 
- <mark> 通过 Security Groups  只能定义 allow rules </mark>
- 默认情况下关闭所有的交通, 通过 Security Groups  定义 rules. 这些 rules 指定打开那些交通. Security Groups implicitly deny all traffic, and so you have to create allow rules  to get access to things. And so that's  both for inbound and outbound. . 
    - Example if you wanted to open up Port 22. So you could SSH into an instance, that's an allow  rule you'd create on that security group

## 4.3 Security Groups vs NACLs 比较 
- they act as a firewall at the instance level, whereas  knackles act as a firewall at the sub net level.  
- Example (block a specific IP address to access your a specific Subnet  and the )
    - The real utility of NACLs is that you can block a specific IP address known for abuse. Because you can have deny rules. And you can say exactly, I want to  deny exactly this IP address. 
    - So the reason you can't do this with security groups is that, because the rules, which are defined in security group,  implicitly denies everything in order for you to deny a single IP and allow everything else,  imagine all the IP addresses in the world, you'd have to create allow rules (via Security Groups) for everything  for those IP addresses, and just exclude that  one IP address, which is like almost impossible.  
    - So for NACLs, the best use case here is again,  block a specific IP address known for abuse. 


- Network Access Control Lists (NACLs)
    - stateless
    - Acts as a virtual firewall at the **subnet level**
    - You create **Allow and Deny rules**.
    - eg. Block a specific IP address known for abuse
- Security Groups
    - stateful
    - Acts as a virtual firewall at the **instance level**
    - Implicitly denies all traffic. You create **only Allow rules**.
    - eg. Allow EC2 instance access on port 22 for SSH
    - eg. You cannot block a single IP address.

## 4.4 Follow Along
6:41:07 Security Groups vs NACLs Follow Along

### 4.4.1 设置新的VPC and Subnet
![](image/Pasted%20image%2020230513160034.png)

![](image/Pasted%20image%2020230513160253.png)

![](image/Pasted%20image%2020230513160055.png)


### 4.4.2 设置新的 Internet Gateway 
![](image/Pasted%20image%2020230513160436.png)

### 4.4.3 新的Route Table
![](image/Pasted%20image%2020230513160503.png)

![](image/Pasted%20image%2020230513160642.png)


### 4.4.4 ###
给某个subnet 分配 他的 iPhonev addreasse 
![](image/Pasted%20image%2020230513161013.png)

### 4.4.5 生成新的 ec instacne , 让他run 在我们新的 subnet 中 

![](image/Pasted%20image%2020230513161703.png)

### 4.4.6 Security group

设置 一个 Security group 中的 allows 

![](image/Pasted%20image%2020230513162114.png)

![](image/Pasted%20image%2020230513162054.png)

并且将他赋给 某个 ec2 instance


### 4.4.7 Access Control Lists (NACLs)

![](image/Pasted%20image%2020230513162343.png)


# 5 AWS CloudFront (FA)
6:54:46 AWS CloudFront (FA)

cloudfront is a content delivery network and it's used to cache your data all over the place as you can 
用于缓存网络通信的内容 到 s3 bucket 中
The best option for the company to ensure that users can view videos with low latency would be to use Amazon CloudFront. CloudFront is a content delivery network (CDN) that speeds up the delivery of static and dynamic web content, such as HTML, CSS, JavaScript, and images, as well as videos.

![](image/Pasted%20image%2020230513162811.png)

![](image/Pasted%20image%2020230513163210.png)

