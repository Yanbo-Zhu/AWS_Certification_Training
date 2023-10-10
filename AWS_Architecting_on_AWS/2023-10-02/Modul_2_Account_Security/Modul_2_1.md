
![](image/Pasted%20image%2020231002102157.png)

# 1 Business requests
![](image/Pasted%20image%2020231002102237.png)

The least privileged access or the least privileged principle

# 2 princple and identities of aws account 


## 2.1 root user 
![](image/Pasted%20image%2020231002102423.png)

## 2.2 IAM

![](image/Pasted%20image%2020231002102644.png)


## 2.3 principle 

![](image/Pasted%20image%2020231002103054.png)

谁 或者 什么 东西, 可以 提出 request. 这些东西 或者人, 已经被 authoricated or authendicated 

Federated user,

# 3 IAM 仔细介绍
## 3.1 IAM user
![](image/Pasted%20image%2020231002103249.png)

IAM user 自己的 credentials should never be shared to others

![](image/Pasted%20image%2020231002103703.png)

API: You just exposes resources for you to access any functionalities where it is accessed using a URL

![](image/Pasted%20image%2020231002104217.png)


## 3.2 IAM policy 

![](image/Pasted%20image%2020231002104426.png)

we have compromised on the best practice of the least privileged Principle 

## 3.3 IAM User groups

![](image/Pasted%20image%2020231002104816.png)


In IAM:   There is no nesting in groups . group of group  是不行的 没有这种可能.  no group is derived from another group 

## 3.4 IAM roles 

![](image/Pasted%20image%2020231002104805.png)

user assume a role 
不需要sahring credentials with other 

iam role can be assigned to ec2 instance (a aws services )

![](image/Pasted%20image%2020231002105919.png)


![](image/Pasted%20image%2020231002110116.png)


# 4 Security policies 

![](image/Pasted%20image%2020231002110354.png)

![](image/Pasted%20image%2020231002110623.png)


## 4.1 identity-based policy 
![](image/Pasted%20image%2020231002110653.png)


![](image/Pasted%20image%2020231002110834.png)

condition: 
resource : 可以作用于任何的 ex2 instance . 因为 写为了 instance/* 
yanbo only can start and stop instance which containce tag "owner", owner 的只 为 yanbo 的名字  


### 4.1.1 explicit allow and deny 以及他的优先级 

![](image/Pasted%20image%2020231002111319.png)

1 
to list this bucket
and download (Get-Object) the object from that bucket 


2 deny 的这个 policy, 拒绝 


如过 1+2 都 分配个了 我.  我将会不能访问 任何 资源 in ec2 and s3 

==One explicit deny policy at the bottom of the policy is stronger than 10000 allows policy on top of list ==


![](image/Pasted%20image%2020231002111830.png)

## 4.2 resourece -based policy

为什么 identity-based policy 没有 principal. 因为 principal 中是只能 this is attached to a user or iam user, acoount, not a iam user group . 
identity-based policy 已经指定了identity.  不需要在特别在 policy 中写出了 
但是 resourece -based policy 中 没有 指明 那个 对象有这个 polcy, 所以需要在 principla 中指出

principal 中是只能 this is attached to a user or iam user, acoount,
putObject: upload file 

![](image/Pasted%20image%2020231002111922.png)


这个 user 向往 folder245 中 放入个 材料也不行 因为没有 对应的 allow 

![](image/Pasted%20image%2020231002112444.png)

==root  user have an unlimited permissions on everything in their respective aws account in default, 他不需要 任何 polcy 就可以做到 ==
但是 iam user 如果没有任何 policy , 他就什么都做不了 

![](image/Pasted%20image%2020231002112551.png)


## 4.3 IAM permission boundareis 
需要重听 



![](image/Pasted%20image%2020231002113033.png)
就是已经付价格了 某个 user 很多的 policy了. 这时候 又添加了一个 自己设置的policy which owns a permission . 
这两块都被实施在某个 user 上面, 那么 这个 user 中能用 中间交集的 中的权利. 这是 aws default 默认的 
## 4.4 managing multiple accounts 

![](image/Pasted%20image%2020231002113051.png)

![](image/Pasted%20image%2020231002113231.png)

![](image/Pasted%20image%2020231002113524.png)

central aws acount: management acount . 可以产生 a consolidated bill 

![](image/Pasted%20image%2020231002113629.png)

scps: service control policy 被定义在 OU 中,  被实施在下属的所有的 acoount under an OU 


## 4.5 scp: service control polcyes 
==scp just filter the permission, scp does not grant permission ==

只有 inter
![](image/Pasted%20image%2020231002113938.png)

![](image/Pasted%20image%2020231002114354.png)

==identity based policies are influenced by SCP.==
==resource based policies are not influenced by SCP.==


![](image/Pasted%20image%2020231002114242.png)

![](image/Pasted%20image%2020231002114510.png)


### 4.5.1 4 scp 对应的 aws serivce 

![](image/Pasted%20image%2020231002115446.png)


![](image/Pasted%20image%2020231002115455.png)

![](image/Pasted%20image%2020231002115514.png)


![](image/Pasted%20image%2020231002115526.png)

![](image/Pasted%20image%2020231002115533.png)


# 5 review 

![](image/Pasted%20image%2020231002123240.png)

manage multipe accunts:  through aws organizasation, scps 


# 6 #

--- 
a 不对 located nor user , is resourrce 

d
![](image/Pasted%20image%2020231002123449.png)



---

c
![](image/Pasted%20image%2020231002123541.png)

---
![](image/Pasted%20image%2020231002123559.png)

bd

------

b

![](image/Pasted%20image%2020231002123912.png)



----

a
![](image/Pasted%20image%2020231002123931.png)


-----



----






