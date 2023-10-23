
![](image/Pasted%20image%2020231004095814.png)

In this lab, you create a serverless architecture. When a user adds an image to an Amazon S3 bucket, the event is published to an SNS topic. Three SQS queues are subscribed to the topic. Each queue has a Lambda function that is invoked when its SQS queue sends a message. Each Lambda function resizes the image and adds it to another S3 bucket. These events are logged in Amazon CloudWatch.


![](image/Pasted%20image%2020231023150602.png)


