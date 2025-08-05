
![](image/Pasted%20image%2020241003151016.png)


# 1 其他 
## 1.1 EC2 Instnace


Spot Instance time is not granteteed 

![](image/Pasted%20image%2020241003151507.png)

![](image/Pasted%20image%2020241003151520.png)

![](image/Pasted%20image%2020241003151702.png)


## 1.2 AWS Batch 

if you have a workload 


![](image/Pasted%20image%2020241003151831.png)

![](image/Pasted%20image%2020241003151837.png)


## 1.3 Lightsail 


当你想造一个很轻量的 instance for 一个 light weight application , 就不用 ec instance, 用和这个好了 

![](image/Pasted%20image%2020241003153130.png)



# 2 Comparing 

![](image/Pasted%20image%2020241003152020.png)



# 3 Lambda function 

![](image/Pasted%20image%2020231010214108.png)


![](image/Pasted%20image%2020241003152038.png)




![](image/Pasted%20image%2020241003152114.png)


role also has to be attach to a function 


AWS Lambda is a compute service that helps you run code without provisioning or managing servers. You pay only for the compute time you consume – you incur no charges when your code is not running.
With AWS Lambda, you can run code for virtually any type of application or backend service, all with zero administration. You need only to upload your code and AWS Lambda manages everything required to run and scale your code with high availability. You can set up your code to automatically launch from other AWS services or call it directly from any web or mobile app.
Before using AWS Lambda, you must have an understanding of the following key Lambda concepts:
- Event source – what invokes the call 
- Language choice 
- Execution environment – permissions and resources
    - role also has to be attach to a function 


The code you run on AWS Lambda uploads as a Lambda function. Each function has associated configuration information, such as its name, description, entry point, and resource requirements. The code must be written in a “stateless” style, that is, it should assume that there is no affinity to the underlying compute infrastructure. Local file system access, child processes, and similar artifacts might not extend beyond the lifetime of the request, and any persistent state should be stored in Amazon S3, Amazon DynamoDB, or another internet-available storage service. Lambda functions can also can include libraries, including native ones.


# 4 function 被执行的时候 

lamdba function 在什么上面运行  what  被创造?  
答案是   virtuall machine,   not docker container.   
linux kvm 被使用 ,
Firecraker  被使用 (MircoVMs)

![](image/Pasted%20image%2020241003154110.png)


## 4.1 why mircoVM 被使用, 不是 container 

 原因是 a docker is not as isolated as a virtual machine.

![](image/Pasted%20image%2020241003154140.png)


## 4.2 Cold Start 


Remember, the cold start is the time it takes to initialize the Lambda function for the first time that you call the Lambda function, right?


# 5 Network

![[image/Pasted image 20250326161251.png]]


# 6 Resource-based policy And IAM Execution Role role


resource-based policy : who can execute lambda function  
Execution Role role: decide what lamdba function can do 


![](image/Pasted%20image%2020241003164556.png)



 Resource-based policy 的解释见 

[[../../03_AWS_Architecting_on_AWS/2023-10-02/Modul_2_Account_Security/Modul_2_1#4.2 Ressource-based policy]]

# 7 Create Function 

![](image/Pasted%20image%2020241003152244.png)



![](image/Pasted%20image%2020241003152406.png)

![](image/Pasted%20image%2020241003152627.png)


![](image/Pasted%20image%2020241003152644.png)

why  lamdba needs a vpc : 
- when you want to runs windows , mac OS.
- vpc make a network , vpc provide 
- I can connect the lambda function, 这时候就需要vpc
    - 比如 prosgres 需要接触到 lambda function 



# 8 trigger

![](image/Pasted%20image%2020250326151406.png)

![](image/Pasted%20image%2020241003153441.png)


![](image/Pasted%20image%2020241003153501.png)


## 8.1 Trigger的类型 


From Chapter_04_02_ApplicationIntegration , AWS 的 Application Integration Services
From [[../../03_AWS_Architecting_on_AWS/2023-10-02/Modul_4_Compute/Modul_4_1_Compute|Modul_4_1_Compute]]

A Lambda function can be invoked manually or by an AWS service. Some of these services are covered in more detail later in this course.
If you want a way to configure an HTTPS endpoint in front of your function, consider using AWS Lambda Function URLs.
For more information about Lambda Function URLs, see “Announcing AWS Lambda Function URLs: Built-in HTTPS Endpoints for Single-Function Microservices” in the AWS News Blog at https://aws.amazon.com/blogs/aws/announcing-aws-lambda-function-urls-built-in-https-endpoints-for-single-function-microservices/.


AWS 的 Application Integration Services

- **Simple Notification Service (SNS)** - a **pub-sub messaging system**. Sends notifications via various formats such as Plain-text **Email**, HTTP/s (**webhooks**) SMS (**text messages**), **SQS** and **Lambda**. Push messages which then are sent to subscribers
- **Simple Queue Service (SQS)** is a queueing messaging service. Send events to a queue. Other applications pull the queue for messages. Commonly used for background jobs.
- **Step Functions** is a **state machine service**. It coordinates multiple AWS services into serverless workflows. Easily share data among Lambdas. Have a group of lambdas wait for each other. Create logical steps. Also works with Fargate Tasks.
- **EventBridge (CloudWatch Events)** is a **serverless event bus** that makes it easy to connect applications together from your own application, third-party services, and AWS services.
- **Kinesis** is a **real-time streaming data service**. Create **Producers** which send data to a stream. **Multiple Consumers** can consume data within a stream. Use for real-time analytics, click streams, ingesting data from a fleet of IoT Devices
- **Amazon MQ** is a **managed message broker service** that uses **Apache ActiveMQ**
- **Managed Kafka Service (MSK)** a **fully managed Apache Kafka service**. Kafka is an open-source platform for building real-time streaming data pipelines and applications. Similar to Kinesis but more robust
- **API Gateway** is a fully-managed service for developers to create, publish, maintain, monitor, and secure APIs. You can create API endpoints and route them to AWS services.
- **AppSync** is a **fully managed GraphQL service**. GraphQL is an open-source agnostic query adaptor that allows you to query data from many different data sources.

![](image/Pasted%20image%2020230515174407.png)


![](image/Pasted%20image%2020231002153514.png)
## 8.2 trigger : API Gateway 

![](image/Pasted%20image%2020241003154702.png)

click it 
[https://ytvzyh9za1.execute-api.eu-south-2.amazonaws.com/default/DemoDevOnAWS](https://ytvzyh9za1.execute-api.eu-south-2.amazonaws.com/default/DemoDevOnAWS "https://ytvzyh9za1.execute-api.eu-south-2.amazonaws.com/default/demodevonaws")
得到 
![](image/Pasted%20image%2020241003154803.png)




# 9 Code Source : lambda_handler(event, context) Function

![](image/Pasted%20image%2020241003153321.png)


## 9.1 event 

定义一个 event  在这个event 中 写下一些内容,    这个event 用来触发 lambdafucntion 

**user parameters **needed for the Lambda function are declared and retrieved from the event 

When you inspect the handler function, notice that it first prints the event, which helps to troubleshoot if you have an issue. Next, all of the user parameters needed for the Lambda function are declared and retrieved from the event and environment.

```
    # Extract the user parameters from the event and environment
    UserId = event["UserId"]
    NoteId = event["NoteId"]
    VoiceId = event['VoiceId']
    mp3Bucket = os.environ['MP3_BUCKET_NAME']
    ddbTable = os.environ['TABLE_NAME']
```


## 9.2 context
context  做什么用的
context where the lambda funciton is running   (**runtime parameter **)

AWS Lambda, the `context` parameter in the `lambda_handler` function provides runtime information about the invocation, function, and environment. It contains useful metadata that can be helpful in handling or debugging your Lambda function.

Here are some key attributes available within the `context` object:

1. **`context.aws_request_id`**
    
    - A unique identifier for the request. Useful for tracking and correlating logs.
2. **`context.function_name`**
    
    - The name of the Lambda function.
3. **`context.function_version`**
    
    - The version of the Lambda function that is being executed.
4. **`context.invoked_function_arn`**
    
    - The Amazon Resource Name (ARN) of the function, showing which resource triggered the invocation.
5. **`context.memory_limit_in_mb`**
    
    - The memory size configured for the Lambda function (in MB).
6. **`context.log_group_name`** and **`context.log_stream_name`**
    
    - The CloudWatch log group and log stream associated with the function execution.
7. **`context.get_remaining_time_in_millis()`**
    
    - A method that returns the amount of time (in milliseconds) before the function times out. Useful for ensuring tasks are completed within the function’s timeout limits.
8. **`context.client_context`**
    
    - Provides information about the client application if invoked from a mobile app via AWS Mobile SDK.
9. **`context.identity`**
    
    - Information about the Amazon Cognito identity provider, if invoked through that service.

In summary, the `context` parameter gives you access to useful runtime data that can help you monitor, debug, or modify the behavior of your AWS Lambda function.



## 9.3 Example

![](image/Pasted%20image%2020241003164435.png)




# 10 Test 
![](image/Pasted%20image%2020241003153723.png)

可以手动触发 一些 lambda function 

![](image/Pasted%20image%2020241003153748.png)


![](image/Pasted%20image%2020241003153811.png)


![](image/Pasted%20image%2020241003153822.png)




# 11 logs to AWS Cloudwatch 

 通过 lambda 产生很多 console logs, 然后把pass 这些 console logs to cloud watch. let's say you're using lambda, you would, you can put within your  functions, a lot of console log calls. And so that would then pass that on to cloud watch. And that is just in itself, application logs for lambdas.  


![](image/Pasted%20image%2020250326152745.png)

# 12 General configuration

![](image/Pasted%20image%2020241003155121.png)


Timout : 默认3秒 , 最大可以设置成 15min , 就是一个 inifinite loop  最长运行的时间,  if  lamdba fucntion doesn;t complete 15min , this lamdba fucntion will be interrupt automactically 
memeory : 默认是 128 MB,  go to 10G maximal , cost more mpney 

## 12.1 trigger 

![](image/Pasted%20image%2020250326151406.png)


## 12.2 Concurrency 

就是有很多event invoke 同一个 lamdba function 的时候,  他们以怎么样的顺序 被执行 

当 my app cannot tolerate not even the first initial 200 millisecond 就开启这个Concurrency 

最大的 conccurey 允许的数值  在 unreserved account concurrency 处给出 
![](image/Pasted%20image%2020241003154430.png)




![](image/Pasted%20image%2020241003154930.png)



# 13 例子

## 13.1 from Chapter_03_01_compute   3.2 lambda 


![](image/Pasted%20image%2020230402100031.png)

![](image/Pasted%20image%2020230402100100.png)

![](image/Pasted%20image%2020230402100113.png)

create a new test event
![](image/Pasted%20image%2020230402100221.png)

点击 test
![](image/Pasted%20image%2020230402100311.png)

![](image/Pasted%20image%2020230402100341.png)

 

