


![](image/Pasted%20image%2020231003111201.png)

Lab 3 uses a VPC across two Availability Zones with a private and public subnet in each. Each private subnet contains a t3 EC2 instance. One private subnet contains an Aurora DB instance, which connects to a target group that consists of the two EC2 instances. Inbound traffic routes through an internet gateway into an Application Load Balancer. The load balancer distributes traffic between the EC2 instance



![](image/Pasted%20image%2020231003111211.png)


![](image/Pasted%20image%2020231004132029.png)





