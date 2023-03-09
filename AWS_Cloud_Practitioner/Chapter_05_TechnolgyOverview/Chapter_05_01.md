# 1 AWS Organizations and Accounts

一个组织里面有 root account user 
若干个  Organization Units, 每个 unit 就是一个 aws accounts 
每个 Unit 具有 不同的 Permission, 能够使用的 aws service 也不同  
Services Control Polices  集中管控 这些  permiisions 


![](image/Pasted%20image%2020230308225805.png)



## 1.1 例子

对应的 aws 服务:  

### 1.1.1 Identity and Access Management (IAM ) -> Aws Organization :Organization Activity 
只有 root Account  才有这个权利 
![](image/Pasted%20image%2020230308230553.png)

### 1.1.2 AWS Organizations 
只有 root Account users 才有这个权利 
通过 这个 创立一个 新的 aws organizations 

![](image/Pasted%20image%2020230308230801.png)

![](image/Pasted%20image%2020230308230814.png)


2.1 Accounts 界面 
star 星标的 代表他为 root account 
![](image/Pasted%20image%2020230308231035.png)

![](image/Pasted%20image%2020230308231133.png) 

可以用来去 create new account 
![](image/Pasted%20image%2020230308231907.png)

 
delete aws acoount  per Root account
![](image/Pasted%20image%2020230308235146.png)

delete aws acount 在这个 aws non root account 自己的界面上 
![](image/Pasted%20image%2020230308235529.png)
![](image/Pasted%20image%2020230308235536.png)

2.2 Organize Accounts 界面 
如果你是 root aacounts  下, 就可以利用这个界面去 创造 organizational Unit 
![](image/Pasted%20image%2020230308231642.png)

![](image/Pasted%20image%2020230308231736.png)


将一个 accout 挪到 某个 Organizational units

![](image/Pasted%20image%2020230308232326.png)


2.3 Policies 界面 
![](image/Pasted%20image%2020230308232510.png)

create new policy allowEC2
![](image/Pasted%20image%2020230308234646.png)
![](image/Pasted%20image%2020230308234657.png)
![](image/Pasted%20image%2020230308234722.png)
![](image/Pasted%20image%2020230308234734.png)

Authorize  permission with a Organizational Unit through assign Policy (通过 attach button, 另外还有 deattch 操作  )
![](image/Pasted%20image%2020230308234836.png)
![](image/Pasted%20image%2020230308234845.png)



# 2 AWS Networking
# 3 Database Services
# 4 Provisioning Services
# 5 Computing Services
# 6 Storage Services
# 7 Business Centric Services
# 8 Enterprise Integration
# 9 Logging Services
# 10 Know your Initialisms