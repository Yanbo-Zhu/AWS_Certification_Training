
# 2 Introduction to Shared Responsibility Model

Shared Responsibility Model: 
A cloud security framework that defines the security obligations of the customer versa the cloud service provider. e.g. AWS
Each CSP has its own variant of the Shared Responsibility Model but they are all generally the same.

**AWS Shared Responsibility Model**
The **type of cloud deployment model** and/or **the scope of the cloud service category** can result in specialized Shared Responsibility Models.

![](image/Pasted%20image%2020230401230740.png)

# 3 AWS Shared Responsibility Model

![](image/Pasted%20image%2020230401231226.png)

![](image/Pasted%20image%2020230401231259.png)


- Customer's responsibilities  
    - secure the data
        - if you don not turn on monitoring services to monitor sensitive data. It's your fault
    - Configuration
        - if you mis conifguration or dont use the 相应的 aws service to keep them in screct 

### 3.1.1 Customer

Configuration of Managed Services or Third-Party Software
-   Platforms
-   Applications
-   Identity and Access Management (IAM)

Configuration of Virtual Infrastructure and Systems
-   Operating System
-   Network
-   Firewall

Security Configuration of Data
-   Client-Side Data Encryption
-   Server-Side Encryption
-   Networking Traffic Protection
-   Customer Data

### 3.1.2 AWS

Software
-   Compute
-   Storage
-   Database
-   Networking

Hardware / Global Infrastructure
-   Regions
-   Availability Zones
-   Edge Locations
-   Physical Security


# 4 Types of Cloud Responsibilities

![](image/Pasted%20image%2020230401231541.png)

On-Premise 	Infrastructure as a Service 	Platform as a Service 	Software as a Service
Applications 	Applications 	Applications 	Applications
Data 	Data 	Data 	Data
Runtime 	Runtime 	Runtime 	Runtime
Middleware 	Middleware 	Middleware 	Middleware
OS 	OS 	OS 	OS
Virtualization 	Virtualization 	Virtualization 	Virtualization
Servers 	Servers 	Servers 	Servers
Storage 	Storage 	Storage 	Storage
Networking 	Networking 	Networking 	Networking

Legend: Customer is Responsible CSP is Responsible


# 5 Shared Responsibility for Compute

Compute as a comparision example of the shared responsibility Model 

![](image/Pasted%20image%2020230401232119.png)

1 Infrastructure as a Service (IaaS)

Bare Metal

EC2 Bare Metal Instance

Customer:

    The Host OS Configuration
    Hypervisor

AWS

    Physical machine

Virtual Machine

Elastic Cloud Compute (EC2)

Customer:

    The Guest OS Configuration
    Container Runtime

AWS

    Hypervisor, Physical machine

Containers

AWS Elastic Container Service(ECS)

Customer:

    Configuration of containers
    Deployment of Containers
    Storage of containers

AWS

    The OS, The Hypervisor, Container Runtime


2 
Platform as a Service (PaaS)

Managed Platform

AWS Elastic Beanstalk

Customer:

    Uploading your code
    Some configuration of environment
    Deployment strategies
    Configuration of associated services

AWS

    Servers, OS, Networking, Storage, Security


3 
Software as a Service (SaaS)

Content Collaboration

Amazon WorkDocs

Customer:

    Contents of documents
    Management of files
    Configuration of sharing access controls

AWS

    Servers, OS, Networking, Storage, Security

4 
Function as a Service (FaaS)

Functions

    AWS Lambda

Customer:

    Upload your code

AWS

    Deployment, Container Runtime, Networking, Storage, Security, Physical Machine, (basically everything)


![](image/Pasted%20image%2020230401232333.png)




![](image/Pasted%20image%2020230401234058.png)



# 6 Shared Responsibility Model Alternate

[Shared Responsibility: What This Means for You as a CISO (Cloud Next '19)](https://www.youtube.com/watch?v=D2zf0SgNdUw)
[Exploring container security: the shared responsibility model in GKE](https://cloud.google.com/blog/products/containers-kubernetes/exploring-container-security-the-shared-responsibility-model-in-gke-container-security-shared-responsibility-model-gke)
[Google Cloud Platform: Shared Responsibility Matrix](https://services.google.com/fh/files/misc/gcp_pci_srm__apr_2019.pdf)

Costumer 和 CSP Cloud service provider 到底各自负责什么 

the share responsibility model is a simple visualization that helps determine what the customer is responsible for and what the csp is responsible for

- The Customer
    - The Customer is responsible for the data and the configuration of access controls that resides in AWS 
    - The Customer is responsible fir the configuration of cloud services and grating access to users via permissions 
- The CSP is generally responsible for the underlying infrastructure 

Responsibility of in the cloud: If you can configure or store it, then you (the costumer) are responsible for it 
Responsibility of the cloud: If you can not configure , then you CSP is responsible for it 


![](image/Pasted%20image%2020230401234143.png)





# 7 Shared Responsibility Model Architecture

![](image/Pasted%20image%2020230401234927.png)

Less Responsibility ↑

Amplify Serverless Framework

Lambda Serverless Architecture

Fargate Serverless Containers

ECS/EKS Containers

Elastic Beanstalk  Platform as a Service 

EC2 Infrastructure as a Service

More Responsibility ↓

---

Serverless / Functions
No more servers, just worry about data and code

Microservices / Containers
Mix and match languages, better utilization of resources

Traditional / VMs
Global workforce is most familiar with this kind of architecture and lots of documentation, frameworks, and support.