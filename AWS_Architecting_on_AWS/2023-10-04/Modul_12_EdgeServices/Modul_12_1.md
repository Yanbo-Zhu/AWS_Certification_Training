

# 1 #


![](image/Pasted%20image%2020231004110259.png)



# 2 #


![](image/Pasted%20image%2020231004110347.png)



![](image/Pasted%20image%2020231004110435.png)


# 3 

![](image/Pasted%20image%2020231004110448.png)


![](image/Pasted%20image%2020231004110613.png)


# 4 Route 53


![](image/Pasted%20image%2020231004110651.png)


Domain Name System: domain name and the corresponding ip addresse 


![](image/Pasted%20image%2020231004111029.png)




![](image/Pasted%20image%2020231004111218.png)


![](image/Pasted%20image%2020231004111552.png)


if health check on 一个失败了, 就转向另一个 
One is supposed to be active, the other one is hot standby
![](image/Pasted%20image%2020231004111622.png)




![](image/Pasted%20image%2020231004111629.png)




![](image/Pasted%20image%2020231004111700.png)



![](image/Pasted%20image%2020231004111806.png)




提供几个 healthy 选择给user, 让 user 自己选择去那个 地址 

![](image/Pasted%20image%2020231004111857.png)



![](image/Pasted%20image%2020231004111948.png)


# 5 Amazon CloudFront 

被用来 caching 

Cloud Delivery network 
It works perferctly with static object , So images, videos, songs
And when someone requests that content the first time, it's going to be read. then it will be cached. So the first client is served. Maybe not the best experience, but then the second and third and 4th there

We use Cloud front. This is called a Content Delivery Network CDN. So if you hear the term CDN, that's a Content Delivery Network

![](image/Pasted%20image%2020231004112142.png)


![](image/Pasted%20image%2020231004112453.png)

![](image/Pasted%20image%2020231004112504.png)



![](image/Pasted%20image%2020231004112703.png)


![](image/Pasted%20image%2020231004112805.png)




CloudFront 

origin:  where to save the caching 

![](image/Pasted%20image%2020231004113127.png)





![](image/Pasted%20image%2020231004113151.png)

CloudFront Origin Shield 
- the Cloudfront Origin shield is going to be a third level of caching close to the origin.   
- third level caching it's like a third level of caching to ensure that if it's not in the edge cache or the regional edge cache then I'm going to go here as a Before I need to bother the the origin itself
- so it's it's shielding the origin from requests, but not secure



# 6 DDos attacks 

![](image/Pasted%20image%2020231004113726.png)



![](image/Pasted%20image%2020231004113740.png)



![](image/Pasted%20image%2020231004113853.png)

![](image/Pasted%20image%2020231004113902.png)



WAF: firewall 

if you have shield advance, use waf free

applied it in application layer, https 

![](image/Pasted%20image%2020231004114022.png)



![](image/Pasted%20image%2020231004114116.png)




![](image/Pasted%20image%2020231004114250.png)





WAF ist not inline 

![](image/Pasted%20image%2020231004114407.png)





# 7 aws firewall manager 

![](image/Pasted%20image%2020231004114604.png)

File Manager is a tool that you can use it in order to be able to configure, update and change lots of security services, even in an organ, instead of hopping into each one and working on it separately so it can help you configure the rules in Italy as well


![](image/Pasted%20image%2020231004114701.png)




# 8 DDos-resilient reference architecture 

![](image/Pasted%20image%2020231004114810.png)




# 9 AWS outposts 



![](image/Pasted%20image%2020231004114830.png)

![](image/Pasted%20image%2020231004114845.png)

data 仍需要放在 data center, 但是 他有需要 aws services 
if you are forced to have your data in house and not you not move it to a aWS and but you still you or you are allowed to aws, use aws outputs 

插入 Outposts chip 就行了 

![](image/Pasted%20image%2020231004114938.png)

physical host chip to your data center 




![](image/Pasted%20image%2020231004115036.png)


![](image/Pasted%20image%2020231004115133.png)




# 10 Knowledge 


d 
a 

![](image/Pasted%20image%2020231004115204.png)



-----

d e


![](image/Pasted%20image%2020231004115309.png)




-----

b

![](image/Pasted%20image%2020231004115407.png)



--------

when you have to use the Outpost serves not Outpost rack 

output servers

c


![](image/Pasted%20image%2020231004115424.png)


![](image/Pasted%20image%2020231004115547.png)




# 11 Lab 6


![](image/Pasted%20image%2020231004121204.png)
![](image/Pasted%20image%2020231004125215.png)



![](image/Pasted%20image%2020231004121129.png)


![](image/Pasted%20image%2020231004124754.png)



OAI  
Origin Access Identity(OAI) 源访问身份，简单来说，就是使终端用户只能通过CloudFront 访问您的文件，而不能直接从源站的URL或域名访问。 l OAI配置大幅提高源站的安全性，避免恶意流量绕过CloudFront对源站直接进行访问。




Distribution domain name: 
https://d3dbobrakoqvxk.cloudfront.net
https://d3dbobrakoqvxk.cloudfront.net/CachedObjects/logo.png



Origin domain 
LabELB-350140125.us-west-2.elb.amazonaws.com

labBucket6


Amazon S3 canonical user ID 
965f22d4a327a354e26de6f01368cad0cd168901b0fe752944ba45a2b6b27f372233971b4bc8cc86dab2b16c9c7f7c19

arn:aws:s3:::labbucket6secondary



