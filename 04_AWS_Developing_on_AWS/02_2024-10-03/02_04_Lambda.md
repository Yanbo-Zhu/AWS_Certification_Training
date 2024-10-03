
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


![](image/Pasted%20image%2020241003152038.png)




![](image/Pasted%20image%2020241003152114.png)


role also has to be attach to a function 



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




# 5 ResourcePolicy And ExecutionRole


resource policy : who can execute lambda policy 
Execution Role role: decide what lamdba function can do 


![](image/Pasted%20image%2020241003164556.png)



# 6 Create Function 

![](image/Pasted%20image%2020241003152244.png)



![](image/Pasted%20image%2020241003152406.png)

![](image/Pasted%20image%2020241003152627.png)


![](image/Pasted%20image%2020241003152644.png)

why  lamdba needs a vpc : 
- when you want to runs windows , mac OS.
- vpc make a network , vpc provide 
- I can connect the lambda function, 这时候就需要vpc
    - 比如 prosgres 需要接触到 lambda function 

---


![](image/Pasted%20image%2020241003153321.png)




# 7 trigger

![](image/Pasted%20image%2020241003153441.png)


![](image/Pasted%20image%2020241003153501.png)


## 7.1 trigger : API Gateway 

![](image/Pasted%20image%2020241003154702.png)

click it 
[https://ytvzyh9za1.execute-api.eu-south-2.amazonaws.com/default/DemoDevOnAWS](https://ytvzyh9za1.execute-api.eu-south-2.amazonaws.com/default/DemoDevOnAWS "https://ytvzyh9za1.execute-api.eu-south-2.amazonaws.com/default/demodevonaws")
得到 
![](image/Pasted%20image%2020241003154803.png)


# 8 Test 
![](image/Pasted%20image%2020241003153723.png)

可以手动触发 一些 lambda function 

![](image/Pasted%20image%2020241003153748.png)


![](image/Pasted%20image%2020241003153811.png)


![](image/Pasted%20image%2020241003153822.png)




# 9 General configuration

![](image/Pasted%20image%2020241003155121.png)


Timout : 默认3秒 , 最大可以设置成 15min , 就是一个 inifinite loop  最长运行的时间,  if  lamdba fucntion doesn;t complete 15min , this lamdba fucntion will be interrupt automactically 
memeory : 默认是 128 MB,  go to 10G maximal , cost more mpney 

# 10 Concurrency 

就是有很多event invoke 同一个 lamdba function 的时候,  他们以怎么样的顺序 被执行 

当 my app cannot tolerate not even the first initial 200 millisecond 就开启这个Concurrency 

最大的 conccurey 允许的数值  在 unreserved account concurrency 处给出 
![](image/Pasted%20image%2020241003154430.png)




![](image/Pasted%20image%2020241003154930.png)



# 11 lambda_handler(event, context) Function


## 11.1 event 
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


## 11.2 context
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



## 11.3 Example

![](image/Pasted%20image%2020241003164435.png)

