



![](image/Pasted%20image%2020231004121204.png)

![](image/Pasted%20image%2020231004125215.png)

![](image/Pasted%20image%2020231004121129.png)


![](image/Pasted%20image%2020231004124754.png)


Lab 6 uses one Region and one VPC. There is a public and private subnet in each of two Availability Zones. Each public subnet has a NAT gateway. A user outside the Region interacts with CloudFront distributions. One distribution delivers content from an Auto Scaling group through an Application Load Balancer. The group’s EC2 instances are launched in two private subnets. A second CloudFront distribution delivers content with an origin of an S3 bucket.




---- 


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

