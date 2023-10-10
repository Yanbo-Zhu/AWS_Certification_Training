

# 1 xx

![](image/Pasted%20image%2020231003124018.png)


![](image/Pasted%20image%2020231003124127.png)

![](image/Pasted%20image%2020231003124159.png)


# 2 Monitoring 简介



![](image/Pasted%20image%2020231003124245.png)


![](image/Pasted%20image%2020231003124315.png)

# 3 Amazon CloudWatch

![](image/Pasted%20image%2020231003124419.png)


dashboards: by default: 3 dashboards, 3 per month

![](image/Pasted%20image%2020231003124709.png)


# 4 Logging 


![](image/Pasted%20image%2020231003124832.png)
![](image/Pasted%20image%2020231003124832.png)

log: it slides down what events happened

四种不同的 方式  侧重不同 



---
## 4.1 CloudWatchLogs
- someone send log to here


![](image/Pasted%20image%2020231003125338.png)



这个例子中 , metric filter 只提取 error 的 log ,放到 metrics


---


## 4.2 AWS CloudTrail 

track user activity and api activity , api call 

![](image/Pasted%20image%2020231003125600.png)


Cloudtrail can send log into a Bucket in local server 

![](image/Pasted%20image%2020231003125835.png)




![](image/Pasted%20image%2020231003125907.png)


![](image/Pasted%20image%2020231003125948.png)




![](image/Pasted%20image%2020231003130003.png)


![](image/Pasted%20image%2020231003130046.png)


create a new CloudTrail 

![](image/Pasted%20image%2020231003130201.png)


![](image/Pasted%20image%2020231003130242.png)

![](image/Pasted%20image%2020231003130250.png)

![](image/Pasted%20image%2020231003130259.png)



only the call to aws services will be logged 
 the call to aws ec2 instance will be logged 



## 4.3 VPC FLOW Logs 


![](image/Pasted%20image%2020231003130347.png)




![](image/Pasted%20image%2020231003130415.png)


# 5 CloudWatch alarms 



![](image/Pasted%20image%2020231003130600.png)


![](image/Pasted%20image%2020231003130844.png)


insufficient data: 就是没有给alram 足够的 条件, 不知道什么时候出发 


alarm 有延后性


![](image/Pasted%20image%2020231003130937.png)



# 6 cloud WatchEvent/  EventBridge 

eventbridge can track lambda function 


![](image/Pasted%20image%2020231003131106.png)


靠 cloudWatch alram 出发 eventBridge 

![](image/Pasted%20image%2020231003131420.png)


## 6.1 实战

create threshold 


![](image/Pasted%20image%2020231003131645.png)


![](image/Pasted%20image%2020231003131658.png)


![](image/Pasted%20image%2020231003131824.png)


alarm 触发后, 什么action 被采取 

![](image/Pasted%20image%2020231003131928.png)



![](image/Pasted%20image%2020231003132002.png)



