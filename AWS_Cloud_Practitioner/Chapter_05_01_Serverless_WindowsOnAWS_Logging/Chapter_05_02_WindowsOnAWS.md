
# 1 Windows on AWS
10:10:01 Windows on AWS

AWS hat multiple cloud services and tools to make it easy for you run Windows workloads on AWS 

[**Windows Servers on EC2**](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/EC2_GetStarted.html) - You can select from a number of Windows Server versions including t- he latest version, Windows Server 2019​
[**SQL Server on RDS**](https://aws.amazon.com/rds/sqlserver/) - You can select from a number of SQL Server database versions​
[**AWS Directory Service**](https://aws.amazon.com/directoryservice/) - lets you run *Microsoft Active Directory (AD)* as a managed service​
[**AWS License Manager**](https://aws.amazon.com/license-manager/) makes it easier to manage your software licenses from software vendors such as Microsoft.​
[**Amazon FSx for Windows File Server**](https://aws.amazon.com/fsx/windows/) - is a fully managed scalable storage built for Windows.​
[**AWS Software Development Kit (SDK)**](https://aws.amazon.com/tools/) - allows you to write code in your favorite language to interact with AWS API.​ The SDK supports *.NET* a language favorite for Windows Developers​
[**Amazon WorkSpaces**](https://aws.amazon.com/workspaces/?workspaces-blogs.sort-by=item.additionalFields.createdDate&workspaces-blogs.sort-order=desc) allows you to run a virtual desktop. You can launch a *Windows 10 desktop* to a provide secure and durable workstation that is accessible from wherever you have an internet connection.​
AWS lambdas supports Powershell as a programming language to write your serverless functions 
[**AWS Migration Acceleration Program (MAP)**](https://aws.amazon.com/migration-acceleration-program/) - for Windows is a migration methodology from moving large enterprise.​ AWS has Amazon Partners that specialize in providing professional services for MAP.​

# 2 EC2 Windows Follow Along
10:11:45 EC2 Windows Follow Along

windows 的 AMI 为 Free Tier
![](image/Pasted%20image%2020230521092858.png)

![](image/Pasted%20image%2020230521093415.png)

# 3 AWS License Manager
10:16:53 AWS License Manager

![](image/Pasted%20image%2020230521093841.png)

1 **What is Bring-Your-Own-License? (BYOL)**
就是 你公司已经买了 某个 software licence on-premises environments, 你也可以 使用同样的license 在 cloud vendor's computing service, 只要这个 software vendor 提供云版本的 service 
The process of reusing an existing software license to run vendor software on a cloud vendor’s computing service. BYOL allows companies to save money since they may have purchased the license in bulk or at a time that provided a greater discount than if purchased again.
eg. **License Mobility** is Microsoft Volume Licensing customers with eligible server applications covered by active Microsoft Software Assurance (SA


2 **AWS License Manager** 
is a service that makes it easier for you to manage your software licenses from software vendors centrally across AWS and your on-premises environments.

**AWS Licence Manager** software that is licensed based on **virtual cores (vCPUs), physical cores, sockets, or number of machines**. This includes a variety of software products from Microsoft, IBM, SAP, Oracle, and other vendors


AWS License Manager works with:
-   EC2 – Dedicated Instances, Dedicated Hosts, Spot Instances
-   RDS – (Only for Oracle databases)

For **Microsoft Windows Server** and **Microsoft SQL Server license**, you generally need to use a **Dedicated Host**

### 3.1.1 Reference

[AWS License Manager](https://aws.amazon.com/license-manager/)

[Bring your own license](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-hosts-overview.html#dedicated-hosts-BYOL)