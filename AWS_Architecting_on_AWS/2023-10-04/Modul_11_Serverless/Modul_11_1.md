

![](image/Pasted%20image%2020231004090427.png)

![](image/Pasted%20image%2020231004090524.png)


# 1 what is serverless


![](image/Pasted%20image%2020231004090624.png)



![](image/Pasted%20image%2020231004090833.png)




![](image/Pasted%20image%2020231004090900.png)





# 2 Amaozn API Gateway 

![](image/Pasted%20image%2020231004091049.png)


API: it's a way to expose you our application to the customer without the need to expose the whole complixity of application 

![](image/Pasted%20image%2020231004091802.png)


![](image/Pasted%20image%2020231004091818.png)



![](image/Pasted%20image%2020231004091912.png)



![](image/Pasted%20image%2020231004092101.png)






# 3 sqs



![](image/Pasted%20image%2020231004092205.png)


mediator 


![](image/Pasted%20image%2020231004092518.png)


![](image/Pasted%20image%2020231004092543.png)


precoder send the data into queue 
consumer pick the message form queue and then storage it into rds 



![](image/Pasted%20image%2020231004092754.png)


![](image/Pasted%20image%2020231004092957.png)


3000 per 

![](image/Pasted%20image%2020231004093113.png)



![](image/Pasted%20image%2020231004093138.png)


tune your visibility timeout 部分重听 


long pilling,  等一会, 看看 之前收到request 有没有回复 

![](image/Pasted%20image%2020231004093443.png)


![](image/Pasted%20image%2020231004093628.png)




sqs ist cloud native 



# 4 sns 

how can i give our applications the ability to send push notifications 



![](image/Pasted%20image%2020231004093735.png)


![](image/Pasted%20image%2020231004093824.png)





![](image/Pasted%20image%2020231004094053.png)



![](image/Pasted%20image%2020231004094112.png)


![](image/Pasted%20image%2020231004094144.png)


Fan out:   
-  在 sns 自动复制 , 发送给个个 queue 
- one to many 
- The Fanout scenario is when a message published to an SNS topic is replicated and pushed to multiple endpoints, such as Kinesis Data Firehose delivery ...



![](image/Pasted%20image%2020231004094710.png)


# 5 amazon kenesis 


![](image/Pasted%20image%2020231004094952.png)


Streaming data 
- Data streaming is when there is a continuous, constant flow of data being generated and processed. 


# 6 kinesis data streams 

![](image/Pasted%20image%2020231004095034.png)




# 7 Kinesis Data Firehose 

![](image/Pasted%20image%2020231004095159.png)



# 8 AWS Step Functions

![](image/Pasted%20image%2020231004095343.png)


![](image/Pasted%20image%2020231004095355.png)



![](image/Pasted%20image%2020231004095448.png)



# 9 Review


![](image/Pasted%20image%2020231004095635.png)




# 10 #


b

![](image/Pasted%20image%2020231004095648.png)



----

c

it reduce, beacuse we send th less mesage and 

![](image/Pasted%20image%2020231004095704.png)


----


c

![](image/Pasted%20image%2020231004095749.png)




# 11 



![](image/Pasted%20image%2020231004095814.png)











