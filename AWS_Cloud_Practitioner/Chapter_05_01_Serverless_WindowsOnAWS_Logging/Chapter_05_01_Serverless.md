
# 1 What is Serverless
10:05:31 What is Serverless?

Serverless architecture generally describes fully managed cloud services.

The classification of a cloud service being serverless is not a Boolean answer (yes or no), but an answer on a scale where a cloud service has a degree of serverless.

A serverless service could have all or most of the following characteristics:
-   Highly elastic and scalable
-   Highly available
-   Highly durable
-   Secure by default
-  Abstracts away the underlying infrastructure and are billed based on the execution of your business task.
-  Serverless can **Scale-to-Zero** meaning when not in use the serverless resources cost nothing.
    - **Pay-for-Value** (you don’t pay for idle servers).

An analogy of serverless could be similar to an energy rating labels which allows consumers to compare the energy efficiency of a product. Some services are more serverless than others.

# 2 Serverless Services
10:07:51 Serverless Services

what ist Serverless Services: When the underlying servers, infrastructure, and Operating System (OS) is taken care of by the Cloud Service Provider (CSP).​
Serverless is generally by default highly available, scalable and cost-effective. 
You pay for what you use.​

- [**DynamoDB**](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html) 
    - is a serverless NoSQL key/value and document database. 
    - It is designed to scale to billions of records with guaranteed consistent data return in at least a second. You don’t have to worry about managing shards!​
- [**Simple Storage Service (S3)**](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html) 
    - is a serverless object storage service. 
    - You can upload very large and an unlimited amount of files. You pay for what you store. You don’t worry about the underlying file-system, or upgrading the disk size.​
- [**ECS Fargate**](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html) 
    - is serverless orchestration container service. 
    - It is the same as ECS except you pay-on-demand per running container (With ECS you have to keep an EC2 server running even if you have no containers running) AWS manages the underlying server, so you don’t have to scale or upgrade the EC2 server.​
- [**AWS Lambda**](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) 
    - is a serverless functions service. 
    - You can run code without provisioning or managing servers. You upload small pieces of code, choose how much memory, and how long the function is allowed to run before timing out. You a charged based on the runtime of the serverless function rounded to the nearest 100ms.​
- [**Step Functions**](https://aws.amazon.com/step-functions/) 
    - is a state machine service.
    - It coordinates multiple AWS services into serverless workflows. Easily share data among Lambdas. Have a group of lambdas wait for each other. Create logical steps. Also works with Fargate Tasks.​
- [**Aurora Serverless**](https://aws.amazon.com/rds/aurora/serverless/) 
    - is the serverless on-demand version of Aurora. 
    - When you want "most" of the benefits of Aurora but can trade to have cold-starts or you don't have lots of traffic demand