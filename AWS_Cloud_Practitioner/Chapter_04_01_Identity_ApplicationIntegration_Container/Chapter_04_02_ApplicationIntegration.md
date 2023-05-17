
Application Integration

# 1 Introduction to Application Integration
8:53:53 Introduction to Application Integration

Application Integration is the process of letting two independent applications communicate and work with each other, commonly facilitated by an intermediate system.

Cloud workloads encourage systems and services to be loosely coupled and so AWS has many services for the specific purpose of application integration.

The common systems or design patterns utilized for Application Integration generally are:
-   Queueing
-   Streaming
-   Pub/Sub
-   API Gateways
-   State Machine
-   Event Bus

# 2 Queueing and SQS
8:54:37 Queueing and SQS

Messaging System
- Used to provide asynchronous communication and decouple processes via messages/events From a sender and receiver ( producer and consumer)

Queueing System
- A Queueing system is a messaging system that generally will delete messages once they are consumed. Simple communication. <mark>**Not Real-time** </mark>. Have to pull. Not reactive.

AWS 的服务: Simple Queueing Service (SQS)
Fully managed **queuing service** that enables you to decouple and scale microservices, distributed systems, and serverless applications
Use Case: You need to queue up transaction emails to be sent e.g. Signup, Reset Password.

# 3 Streaming and Kinesis
8:55:46 Streaming and Kinesis

- streaming
    - Multiple consumers can react to events (messages)
    - Events live in the stream for long periods of time, so complex operations can be applied.<mark> Real-time </mark>

Amazon Kinesis 服务: 
Amazon Kinesis is the AWS fully managed solution for collecting, processing, and analyzing streaming data in the cloud. 

![](image/Pasted%20image%2020230514212955.png)

# 4 Pub-Sub and SNS
8:57:02 Pub-Sub and SNS

Publish–subscribe: 
Publish–subscribe pattern commonly implemented in **messaging systems**.  
In a pub/sub system the sender of messages (**publishers**) do not send their messages directly to receivers.  
They instead send their messages to an **event bus**. The event bus categorizes their messages into groups.  
Then receivers of messages (**subscribers**) subscribe to these groups.  
Whenever new messages appear within their subscription the messages are immediately delivered to them.  

![](image/Pasted%20image%2020230514213519.png)

-   Publisher have no knowledge of who their subscribers are.
-   Subscribers do **not pull** for messages.
-   Messages are instead automatically and immediately **pushed** to subscribers.
-   Messages and events are interchangeable terms in pub/sub

Use Case: a real-time chat system. A web-hook system

## 4.1 AWS 服务: **Simple Notification Service (SNS)**
SNS is a highly available, durable, secure, fully managed **pub/sub messaging** service that enables you to **decouple** microservices, distributed systems, and serverless applications.

![](image/Pasted%20image%2020230514213606.png)

# 5 API Gateway and Amazon API Gateway
8:59:08 API Gateway and Amazon API Gateway

An API Gateway is a program that sits between a single-entry point and multiple backends.
API Gateway allows for throttling, logging, routing logic, or formatting of the request and response

Amazon API Gateway (一种 aws 服务 ) is a solution for creating secure APIs in your cloud environment at any scale.
Create APIs that act as a front door for applications to access data, business logic, or functionality from back-end services.

![](image/Pasted%20image%2020230514213841.png)

# 6 State Machines and AWS Step Functions
9:00:27 State Machines and AWS Step Functions

A state machine is an abstract model which decides how one state moves to another based on a series of conditions. 
**Think of a state machine like a flow chart**.

AWS Step Functions (一种服务)
-   Coordinate multiple AWS Services into a serverless workflow
-   A graphical console to visualize the components of your application as a series of steps.
-   Automatically triggers and tracks each step, and retries when there are errors, so your application executes in order and as expected, every time
-   logs the state of each step, so when things go wrong, you can diagnose and debug problems quickly

![](image/Pasted%20image%2020230515172458.png)

# 7 Event Bus and Amazon Event Bridge
9:01:23 Event Bus and Amazon Event Bridge

EventBus and EventBridge
- An event bus **receives events** from a **source** and **routes events** to a **target** based on **rules**

![](image/Pasted%20image%2020230515173122.png)


## 7.1 Amazon Event Bridge (一种服务)

- **EventBridge** is a **serverless** event bus service that is used for application integration by **streaming real-time** data to your applications
- **EventBridge** was formerly called **Amazon CloudWatch** Events.

![](image/Pasted%20image%2020230515173508.png)
 
- **Event Bus**
    - Holds event data, defines rules on an event bus to react to events.
    - **Default Event Bus** — An AWS account has a default event bus  
    - **Custom Event Bus** — Scoped to multiple accounts or other AWS accounts  
    - **SaaS Event Bus** — Scoped to with Third-party SaaS Providers
- **Producers**
    - AWS Services that emit events
- **Partner Sources**
    - Are third-party apps that can emit events to an event bus
- **Rules**
    - Determines what events to capture and pass to targets. (100 Rules per bus)
- **Targets**
    - AWS Services that consume events (5 targets per rule)
- **Events**
    - Data emitted by services. JSON objects that travel (stream) within the event bus.

# 8 AWS 的 Application Integration Services
9:03:17 Application Integration Services

**Simple Notification Service (SNS)** - a **pub-sub messaging system**. Sends notifications via various formats such as Plain-text **Email**, HTTP/s (**webhooks**) SMS (**text messages**), **SQS** and **Lambda**. Push messages which then are sent to subscribers

**Simple Queue Service (SQS)** is a queueing messaging service. Send events to a queue. Other applications pull the queue for messages. Commonly used for background jobs.

**Step Functions** is a **state machine service**. It coordinates multiple AWS services into serverless workflows. Easily share data among Lambdas. Have a group of lambdas wait for each other. Create logical steps. Also works with Fargate Tasks.

**EventBridge (CloudWatch Events)** is a **serverless event bus** that makes it easy to connect applications together from your own application, third-party services, and AWS services.

**Kinesis** is a **real-time streaming data service**. Create **Producers** which send data to a stream. **Multiple Consumers** can consume data within a stream. Use for real-time analytics, click streams, ingesting data from a fleet of IoT Devices

**Amazon MQ** is a **managed message broker service** that uses **Apache ActiveMQ**

**Managed Kafka Service (MSK)** a **fully managed Apache Kafka service**. Kafka is an open-source platform for building real-time streaming data pipelines and applications. Similar to Kinesis but more robust

**API Gateway** is a fully-managed service for developers to create, publish, maintain, monitor, and secure APIs. You can create API endpoints and route them to AWS services.

**AppSync** is a **fully managed GraphQL service**. GraphQL is an open-source agnostic query adaptor that allows you to query data from many different data sources.

![](image/Pasted%20image%2020230515174407.png)