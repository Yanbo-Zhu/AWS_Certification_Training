这个 Modul 的overview 

![](image/Pasted%20image%2020231002084512.png)




# 1 amazon web services 

![](image/Pasted%20image%2020231016200429.png)


![](image/Pasted%20image%2020231002084604.png)

![](image/Pasted%20image%2020231002084756.png)

orchestrate services in a huge IT environment
The white commercialize those services

AWS is the world’s most comprehensive and adopted cloud solution. AWS offers services such as compute, database, and storage. The AWS pay-as-you-go model, and its security practices, have made AWS the preferred cloud solution for businesses and public organizations.
AWS has been delivering cloud services to customers around the world by running a wide variety of use cases. AWS has the most operational experience of any cloud provider, and at a greater scale. AWS has unmatched experience, reliability, and performance, and an unmatched security record.
Millions of customers, small and large, are using AWS to lower costs, become more agile, and innovate faster. AWS is continually accelerating its pace of innovation to invent new technologies that you can use to transform your business.


## 1.1 benefit of aws 

![](image/Pasted%20image%2020231002084954.png)

scaleability 
avaialbilty 
you pay only  when you use: 被称作 OpEx model operational 

Customers move to AWS to increase agility. 
• Accelerate time to market – By spending less time acquiring and managing infrastructure, you can focus on developing features that deliver value to your customers.
• Increase innovation – You can speed up your digital transformation by using AWS, which provides tools to more easily access the latest technologies and best practices. For example, you can use AWS to develop automations, adopt containerization, and use machine learning.
• Scale seamlessly – You can provision additional resources to support new features and scale existing resources up or down to match demand.

Customers also move to AWS to reduce complexity and risk. 
• Optimize costs – You can reduce costs by paying for only what you use. Instead of paying for on-premises hardware, which you might not use at full capacity, you can pay for compute resources only while you’re using them.
• Minimize security vulnerabilities – Moving to AWS puts your applications and data behind the advanced physical security of the AWS data centers. With AWS, you have many tools to manage access to your resources.
• Reduce management complexity – Using AWS services can reduce the need to maintain physical data centers, perform hardware maintenance, and manage physical infrastructure.

For more information about the advantages of migrating your business to the cloud, see “The future of business is here” at https://aws.amazon.com/campaigns/migrating-to-the-cloud/.


## 1.2 我们学什么

![](image/Pasted%20image%2020231002085535.png)

AWS offers a broad set of global cloud-based products. They include compute, storage, database, analytics, networking, mobile, developer tools, management tools, Internet of Things (IoT), security, and enterprise applications. These services help organizations move faster, scale, and lower IT costs. AWS covers infrastructure, foundation, and application services.
This course focuses on the AWS services that are highlighted on this slide. These services are: Serverless, Networking and content delivery, Database, Security identity and compliance, Management and governance, Storage, AWS cost management, Compute, and Containers.
For more information, see AWS Cloud Products at https://aws.amazon.com/products/

# 2 AWS Infrasturcture 

“How is AWS global infrastructure organized?

![](image/Pasted%20image%2020231002085619.png)

n virgaina has 6 data center 


## 2.1 AWS Data Centers

![](image/Pasted%20image%2020231002090434.png)

AWS pioneered cloud computing in 2006 to provide rapid and secure infrastructure. AWS continuously innovates on the design and systems of data centers to protect them from man-made and natural risks. Today, AWS provides data centers at a large, global scale.
AWS implements controls, builds automated systems, and conducts third-party audits to confirm security and compliance. As a result, the most highly regulated organizations in the world trust AWS every day.
To learn how AWS secures the data centers, see “Our Data Centers” at https://aws.amazon.com/compliance/data-center/data-cente


## 2.2 Availability zones 

![](image/Pasted%20image%2020231002090453.png)

high availabailty: one region is broken. the data in another region is still in use 

A group of one or more data centers is called an Availability Zone.
An Availability Zone is one or more discrete data centers with redundant power, networking, and connectivity in an AWS Region. When you launch an instance, you can select an Availability Zone or let AWS choose one for you. If you distribute your instances across multiple Availability Zones and one instance fails, you can design your application so that an instance in another Availability Zone can handle requests.
For more information about Availability Zones, see “Global Infrastructure” at https://aws.amazon.com/about-aws/global-infrastructure/.


## 2.3 Region

![](image/Pasted%20image%2020231002090847.png)
    - prone to the latency 
    - upload through the nearest AW point of presence and then it gets carried over the WS backbone
        - aws point of presence: a rack for cache ,  but it's not a full region or a full availability zone 

Each AWS Region consists of multiple isolated and physically separate Availability Zones within a geographic area. This arrangement achieves the greatest possible fault tolerance and stability. In your account, you determine which Regions you need.
Regions are isolated from each other, and AWS doesn’t automatically replicate resources across Regions. Therefore, when you view your resources, you see only the resources that are tied to the Region that you specify in the console.
You can run applications and workloads from a Region to reduce latency to end users. In this way, you avoid the upfront expenses, long-term commitments, and scaling challenges that are associated with maintaining and operating a global infrastructure.
For more information about AWS Regions, see Regions and Availability Zones at https://aws.amazon.com/about-aws/global-infrastructure/regions_az/

factors that impact region selection 
![](image/Pasted%20image%2020231002091149.png)

Governance : regulatory constraints, some regulations . in the government that allow or not allowed 

Choosing the right Region is important. You must determine the right Region for your services, applications, and data, based on the following factors:
• Governance and legal requirements – Consider any legal requirements based on data governance, sovereignty, or privacy laws.
• Latency – Close proximity to customers means better performance.
• Service availability – Not all AWS services are available in all Regions. 
• Cost – Different Regions have different costs. Research the pricing for the services that you plan to use and compare costs to make the best decision for your workloads.

## 2.4 Local zones

![](image/Pasted%20image%2020231002091537.png)

You can use AWS Local Zones for highly demanding applications that require single-digit millisecond latency to end users. Examples include:
• Media and entertainment content creation – Includes live production, video editing, and graphics-intensive virtual workstations for artists in geographic proximity
• Real-time multiplayer gaming – Includes real-time multiplayer game sessions, to maintain a reliable gameplay experience
• Machine learning hosting and training – For high-performance, low latency inferencing • Augmented reality (AR) and virtual reality (VR) – Includes immersive entertainment, data driven insights, and engaging virtual training experiences

Customers can innovate faster because chip designers and verification engineers solve complex, compute-intensive, and latency-sensitive problems by using application and desktop streaming services in AWS Local Zones.

For more information, see AWS Local Zones at https://aws.amazon.com/about-aws/global-infrastructure/localzones

- use local zones 
    - encounter the latency
    - a stretch of region closer to where the clients are
    - local zones is AWS facility, but it's not a full-fledged availability zone or a full-fledged pledge
- Edge Locations
    - so edge locations are meant to have caching of data and some accelerated services 

## 2.5 Edge location

![](image/Pasted%20image%2020231002091706.png)

An edge location is the nearest point to a requester of an AWS service. Edge locations are in major cities around the world. They receive requests and cache copies of your content for faster delivery.

To deliver content to end users with lower latency, you use a global network of edge locations that support AWS services. CloudFront delivers customer content through a worldwide network of point of presence (PoP) locations, which consists of edge locations and Regional edge cache servers.

Regional edge caches, used by default with CloudFront, are used when you have content that is not accessed frequently enough to remain in an edge location. Regional edge caches absorb this content and provide an alternative to the need to retrieve that content from the origin server.

For more information, see Amazon CloudFront Key Features at https://aws.amazon.com/cloudfront/feature

![](image/Pasted%20image%2020231016201428.png)

One common use for edge locations is to serve content closer to your customers. This diagram shows an example of a video file that is stored in Amazon Simple Storage Service (Amazon S3) in South America. The file is cached to an edge location near the customer to serve the video file faster to a customer in Asi

## 2.6 AWS local zones vs edge location 

AWS Local Zones address low-latency requirements in specific geographic areas, Edge Locations optimize content delivery and network performance**, and Outposts provide a hybrid cloud solution for on-premises environments with AWS services

![](image/Pasted%20image%2020231002091847.png)

When should you use AWS Local Zones?
You should use AWS Local Zones to deploy AWS compute, storage, database, and other services closer to your end users for low-latency requirements. With AWS Local Zones, you can use the same AWS infrastructure, services, APIs, and tool sets that you are familiar with in the cloud.

When should you use edge locations?
You should use edge locations for caching the data (content) to provide fast delivery of content for users. Using edge locations provides a better user experience, with faster delivery to users at any location




