
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
    - Client VPN - connecting a Client (ie users laptop) to your AWS network
- PrivateLinks (VPC Interface Endpoints) 
    - keeps traffic within the AWS network and not traverse the internet to keep traffic is secure.​


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

# 4 Security Groups vs NACLs
6:39:49 Security Groups vs NACLs

[Security groups for your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)

![](image/Pasted%20image%2020230513155137.png)

- Network Access Control Lists (NACLs)
    - Acts as a virtual firewall at the **subnet level**
    - You create **Allow and Deny rules**.
    - eg. Block a specific IP address known for abuse
- Security Groups
    - Acts as a virtual firewall at the **instance level**
    - Implicitly denies all traffic. You create **only Allow rules**.
    - eg. Allow EC2 instance access on port 22 for SSH
    - eg. You cannot block a single IP address.

## 4.1 Follow Along
6:41:07 Security Groups vs NACLs Follow Along

### 4.1.1 设置新的VPC and Subnet
![](image/Pasted%20image%2020230513160034.png)

![](image/Pasted%20image%2020230513160253.png)

![](image/Pasted%20image%2020230513160055.png)


### 4.1.2 设置新的 Internet Gateway 
![](image/Pasted%20image%2020230513160436.png)

### 4.1.3 新的Route Table
![](image/Pasted%20image%2020230513160503.png)

![](image/Pasted%20image%2020230513160642.png)


### 4.1.4 ###
给某个subnet 分配 他的 iPhonev addreasse 
![](image/Pasted%20image%2020230513161013.png)

### 4.1.5 生成新的 ec instacne , 让他run 在我们新的 subnet 中 

![](image/Pasted%20image%2020230513161703.png)

### 4.1.6 Security group

设置 一个 Security group 中的 allows 

![](image/Pasted%20image%2020230513162114.png)

![](image/Pasted%20image%2020230513162054.png)

并且将他赋给 某个 ec2 instance


### 4.1.7 Access Control Lists (NACLs)

![](image/Pasted%20image%2020230513162343.png)


# 5 AWS CloudFront (FA)
6:54:46 AWS CloudFront (FA)

cloudfront is a content delivery network and it's used to cache your data all over the place as you can 
用于缓存网络通信的内容 到 s3 bucket 中

![](image/Pasted%20image%2020230513162811.png)

![](image/Pasted%20image%2020230513163210.png)

