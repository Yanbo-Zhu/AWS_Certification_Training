# 1 AWS Well-Architected Framework

10:52:48 AWS Well-Architected Framework

-   [AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/)
-   [New Sustainability Pillar for the AWS Well-Architected Framework](https://aws.amazon.com/about-aws/whats-new/2021/12/new-sustainability-pillar-aws-well-architected-framework/)

0.1.1 Note: On Dec 2, 2021, AWS introduced a new AWS Well-Architected Sustainability Pillar to help organizations learn, measure, and improve workloads using environmental best practices for cloud computing.

The AWS Well-Architected Framework is a Whitepaper created by AWS to help customers build using best practices defined by AWS.
aws.amazon.com/architecture/well-architected

The framework is divided into ~~5~~ 6 sections called pillars which address different aspects of “lenses” that can be applied to a cloud workload.
 
1. **Your Cloud Workload**
2. **AWS Well-Architected Framework**
    -   General Definitions
    -   General Design Principles
    -   The Review Process
- If the Foundation is Not Solid Structural **Problems** will Arise

![](image/Pasted%20image%2020230521181957.png)

## 1.1 AWS Well-Architected Sustainability Pillar (一些特性)
Pillar  支柱

一些特性
-   Operational Excellence
-   Security
-   Reliability
-   Performance Efficiency
-   Cost Optimization
-   **[New] Sustainability**

# 2 General Defintions

10:54:21 General Defintions

Six Pillar
*Trade-Off Pillars Based on Business Context
- **Operational Excellent Pillar**    — Run and monitor systems
- **Security Pillar**                            — Protect data and systems, mitigate risk
- **Reliability Pillar**                          — Mitigate and recover from disruptions
- **Performance Efficiency Pillar**  — Use computing resources effectively 
  **Cost Optimization Pillar**           — Get the lowest price
  **[New] Sustainability**                — Use environmental best practices

--- 
**General Definitions**

**Component**     — Code, Configuration, and AWS Resource against a requirement
**Workload**        — A set of components that work together to deliver business value
**Milestones**      — Key changes of your architecture through product life cycle
**Architecture**   — **How** components work together **in a** workload
**Technology Portfolio**  — A collection of workloads required for the business to operate

# 3 On Architecture
10:55:38 On Architecture

The AWS Well-Architected Framework is designed around a different kind of team structure.
Enterprises generally have centralized teams with specific roles whereas AWS has distributed teams with flexible roles.
Distributed teams can come with new risks, AWS mitigates these with Practices, Mechanisms, and Leadership Principles


![](image/Pasted%20image%2020230521182558.png)

-----
1 **On-Premise Enterprise**

**Centralized** team consisting of:
-   Technical Architect (infrastructure)
-   Solution Architect (software)
-   Data Architect
-   Networking Architect
-   Security Architect

Managed by either TOGAF or Zachman Framework

---
2 **Amazon Web Services**

**Distributed teams** consisting of:
-   Practices
    -   Team Experts (Raise the Bar)
-   Mechanisms
    -   Automated Checks for Standards
-   *Amazon Leadership Principle

Supported by a virtual community of **SMEs, Principle Engineers**, eg. lunchtime talks - recycled into onboarding material

# 4 Amazon Leadership Principles
10:57:35 Amazon Leadership Principles

The **Amazon Leadership Principles are a set of principles** used during the company **decision-making, problem-solving, simple brainstorming, and hiring**.

1.  Customer Obsession
2.  Ownership
3.  Invent and Simplify
4.  Are Right, A Lot
5.  Learn and Be Curious
6.  Hire and Develop the Best
7.  Insist on the Highest Standards
8.  Think Big
9.  Bias for Action
10.  Frugality 俭省，节俭  frugal
11.  Earn Trust
12.  Dive Deep
13.  Have Backbone; Disagree and Commit
14.  Deliver Results
15.  Strive to be Earth’s Best Employer
16.  Success and Scale Bring Broad Responsibility

You can read in detail about all 16 here:
[https://www.amazon.jobs/en/principles](https://www.amazon.jobs/en/principles)
[Leadership Principles](https://www.amazon.jobs/en/principles)


# 5 General Design Principles
10:59:05 General Design Principles

[AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/)

使用 aws 你获得好处 

- **Stop guessing your capacity needs**
    - eg. Cloud computing you use as little or much-based **on demand**.
- **Test systems at production scale**
    - eg.  Clone production env to testing, Teardown testing not in use to save money.
- **Automate to make architectural experimentation easier**
    - eg. Using CloudFormation with ChangeSets, StackUpdate, and Drift Detection
- **Allow for evolutionary architectures**
    - eg. CI/CD, rapid or nightly releases, Lambdas deprecating run-times forcing you to evolve
- **Drive architectures using data**
    - eg. CloudWatch, Cloud Trail automatically turned on collecting data
- **Improve through game days**
    - eg. simulate traffic on production or purposely kill EC2 instances to see test recovery 


# 6 Anatomy of a Pillar
11:00:54 Anatomy of a Pillar

![](image/Pasted%20image%2020230521183159.png)

A Pillar of the Well-Architected Framework is **structured** as follows:
-   Design Principles
    -   A list of design principles that need to be considered during implementation
-   Definition
    -   overview of the best practice categories
-   Best Practices
    -   detailed information about each best practice with AWS Services
-   Resources
    -   Additional documentation, whitepapers, and videos to implement this pillar

# 7 AWS Well-Architected Design Principles (介绍每个 pillar )

## 7.1 Operational Excellence
11:01:59 Operational Excellence

**Operational Excellence Design Principles**

- **Perform operations as code**
    - Apply the same engineering discipline you would to application code to your cloud infrastructure. By treating your operations as code you can limit human error and enable consistent responses to events.
    - eg. Infrastructure as Code
- **Make frequent, small, reversible changes**
    - Design workloads to allow components to be updated regularly.
    - eg. rollbacks, incremental changes, Blue/Green, CI/CD
- **Refine operations procedures frequently**
    - Look for continuous opportunities to improve your operations
    - eg. Use game days to simulate traffic or event failure on your production workloads
- **Anticipate failure**
    - Perform post-mortems on system failures to better improve, write test code, kill production serves to test recovery
- **Learn from all operational failures**
    - share lessons learned in a knowledge base for operational events and failures across your entire organization

## 7.2 Security
11:03:17 Security

**Security Design Principles**

- **Implement a strong identity foundation**
    - Implement the Principle of Least Privilege (PoLP). Use Centralized identity. Avoid Long-lived credentials
- **Enable traceability**
    - Monitor alert and audit actions and changes to your environment in real-time Integrate log and metric collection and automate investigation and remediation
- **Apply security at all layers**
    - Take Defense-in-depth approach with multiple security controls for everything eg. Edge Network, VPC, Load Balancing Instances, OS, Application Code
- **Automate security best practices**
- **Protect data in transit and at rest**
- **Keep people away from data**
- **Prepare for security events**
    - Incident management systems and investigation policy and processes. Tools to detect, investigate and recover from incidences

## 7.3 Reliability
11:04:47 Reliability

**Reliability Design Principles**

- **Automatically recover from failure**
    - Monitor Key Performance Indicators (KPIs) and trigger automation when a threshold is breached.
- **Test recovery procedures**
    - Test how your workload fails, and you validate your recovery procedures. You can use automation to simulate different failures or to recreate scenarios that led to failures before.
- **Scale horizontally to increase aggregate system availability**
    - Replace one large resource with multiple small resources to reduce the impact of a single failure on the overall workload. Distribute requests across multiple, smaller resources to ensure that they don’t share a common point of failure.
- **Stop guessing capacity**
    - In on-premise it takes a lot of guesswork to determine the elasticity of your workload demands. With Cloud, you don’t need to guess how much you need because you can request the right size of resources on-demand.
- **Manage change in automation**
    - Making changes via Infrastructure as Code will allow for a formal process to track and review infrastructure

## 7.4 Performance Efficiency
11:05:54 Performance Efficiency

**Performance Efficiency Design Principles**

- **Democratize advanced technologies:**  使民主化
    - Focus on product development rather than procurement, provisioning, and management of services. Take advantage of advanced technology specialized and optimized for your use-case with on-demand cloud services.
- **Go global in minutes**
    - Deploying your workload in multiple AWS Regions around the world allows you to provide lower latency and a better experience for your customers at minimal cost.
- **Use serverless architectures:**
    - Serverless architectures remove the need for you to run and maintain physical servers for traditional compute activities. Removes the operational burden of managing physical servers, and can lower transactional costs because managed services operate at cloud scale.
- **Experiment more often:**
    - With virtual and automatable resources, you can quickly carry out comparative testing using different types of instances, storage, or configurations.
- **Consider mechanical sympathy**
    - Understand how cloud services are consumed and always use the technology approach that aligns best with your workload goals. For example, consider data access patterns when you select database or storage approaches.

## 7.5 Cost Optimization
11:07:22 Cost Optimization

**Cost Optimization Design Principles**

- **Implement Cloud Financial Management:**
    - Dedicate time and resources to build capability Cloud Financial Management and Cost Optimization tooling.
- **Adopt a consumption model**
    - Pay only for the computing resources that you require and increase or decrease usage depending on business requirements
- **Measure overall efficiency**
    - Measure the business output of the workload and the costs associated with delivering it. Use this measure to know the gains you make from increasing output and reducing costs.
- **Stop spending money on undifferentiated heavy lifting**
    - AWS does the heavy lifting of data center operations like racking, stacking, and powering servers. It also removes the operational burden 负担  of managing operating systems and applications with managed services. This allows you to focus on your customers and business projects rather than on IT infrastructure.
- **Analyze and attribute expenditure** 经费 消耗
    - The cloud makes it easier to accurately identify the usage and cost of systems, which then allows transparent attribution of IT costs to individual workload owners. This helps measure return on investment (ROI) and gives workload owners an opportunity to optimize their resources and reduce costs.

# 8 AWS Well-Architected-Tool
11:08:49 AWS Well-Architected-Tool

The Well-Architected Tool is **an auditing tool** to be used to asset your cloud workloads for alignment with the AWS Well-Architected Framework.
Its essentially **a checklist**, with nearby references to help you assemble a report to share with executives and key stakeholders
然后 通过 这个 checklist 你就可以产生一个 report, 然后 用这个 report 去和别人证明 How Well Architected of your programm 

![](image/Pasted%20image%2020230521185649.png)

[AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc)

## 8.1 Well-Architected Framework and Tool- Follow Along
11:09:31 Well-Architected Framework and Tool- Follow Along


Whitepaper
![](image/Pasted%20image%2020230521185841.png)


Well-Architected Tool
create a workload 
![](image/Pasted%20image%2020230521190003.png)

![](image/Pasted%20image%2020230521190122.png)

start a reviewing
![](image/Pasted%20image%2020230521190138.png)

![](image/Pasted%20image%2020230521190159.png)

# 9 AWS Architecture Center
11:13:28 AWS Architecture Center

The AWS Architecture Center is a web portal that contains **best practices** and **reference architectures** for a variety of different workloads.
aws.amazon.com/architecture

[AWS Architecture Center](https://aws.amazon.com/architecture/)

![](image/Pasted%20image%2020230521190340.png)
