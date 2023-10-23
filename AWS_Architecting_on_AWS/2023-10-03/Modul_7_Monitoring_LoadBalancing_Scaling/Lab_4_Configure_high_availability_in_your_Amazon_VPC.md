

![](image/Pasted%20image%2020231003140836.png)


![](image/Pasted%20image%2020231003135050.png)


# 1 #


![](image/Pasted%20image%2020231003134936.png)


![](image/Pasted%20image%2020231003135010.png)


![](image/Pasted%20image%2020231003135022.png)


Lab 4 uses a VPC across two Availability Zones with a public and private subnet in each. Each private subnet contains an app server in the same Auto Scaling group. Private subnet 1 has an Aurora primary DB instance, and private subnet 2 has an Aurora replica. The primary DB instance and replica communicate with each other across Availability Zones. Each public subnet has a NAT gateway. An Application Load Balancer is in the VPC.




















