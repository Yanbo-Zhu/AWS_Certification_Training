

![](image/Pasted%20image%2020231002153857.png)

Lab 2 uses a VPC across one Availability Zone with a public and private subnet. Each subnet contains a T3 EC2 instance. Separate security groups control the EC2 instances. You manage route tables separately for the public and private subnet. A NAT gateway in the public subnet receives traffic from the private subnet. An internet gateway receives traffic from the public subnet.
Review the diagram here, and then read the lab tasks on the following page

![](image/Pasted%20image%2020231002153943.png)


## 0.1 task 1 : testing connectivity to the private instance from the public instance 

加入一个 inbound rules for icmp, 因为 ping 用的是 ic,p protocol 

![](image/Pasted%20image%2020231002163107.png)


![](image/Pasted%20image%2020231002163224.png)


## 0.2 task 2: retrieving instance metadata 

![](image/Pasted%20image%2020231002163541.png)

![](image/Pasted%20image%2020231002163608.png)

```sh
TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` \
&& curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/
```

得到 
```http
sh-5.2$ TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` \
&& curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    56  100    56    0     0  38808      0 --:--:-- --:--:-- --:--:-- 56000
* processing: http://169.254.169.254/latest/meta-data/
*   Trying 169.254.169.254:80...
* Connected to 169.254.169.254 (169.254.169.254) port 80
> GET /latest/meta-data/ HTTP/1.1
> Host: 169.254.169.254
> User-Agent: curl/8.2.1
> Accept: */*
> X-aws-ec2-metadata-token: AQAEAJHtU0Tt2q3W6G9KqKpejCXBm3KCiisAAXE_S8JNQyx4SA6uEw==
>
< HTTP/1.1 200 OK
< X-Aws-Ec2-Metadata-Token-Ttl-Seconds: 21600
< Content-Type: text/plain
< Accept-Ranges: none
< Last-Modified: Mon, 02 Oct 2023 14:05:18 GMT
< Content-Length: 312
< Date: Mon, 02 Oct 2023 14:32:45 GMT
< Server: EC2ws
< Connection: close
<
ami-id
ami-launch-index
ami-manifest-path
block-device-mapping/
events/
hostname
iam/
identity-credentials/
instance-action
instance-id
instance-life-cycle
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
reservation-id
security-groups
services/
* Closing connection
systemsh-5.2$
```


---

输入
```sh
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-hostname
```

```http
sh-5.2$ curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-hostname
* processing: http://169.254.169.254/latest/meta-data/public-hostname
*   Trying 169.254.169.254:80...
* Connected to 169.254.169.254 (169.254.169.254) port 80
> GET /latest/meta-data/public-hostname HTTP/1.1
> Host: 169.254.169.254
> User-Agent: curl/8.2.1
> Accept: */*
> X-aws-ec2-metadata-token: AQAEAJHtU0Tt2q3W6G9KqKpejCXBm3KCiisAAXE_S8JNQyx4SA6uEw==
>
< HTTP/1.1 200 OK
< X-Aws-Ec2-Metadata-Token-Ttl-Seconds: 21575
< Content-Type: text/plain
< Accept-Ranges: none
< Last-Modified: Mon, 02 Oct 2023 14:05:18 GMT
< Content-Length: 53
< Date: Mon, 02 Oct 2023 14:33:10 GMT
< Server: EC2ws
< Connection: close
<
* Closing connection
ec2-35-183-235-141.ca-central-1.compute.amazonaws.comsh-5.2$
```