


![](image/Pasted%20image%2020241002152103.png)


# 1 EBS

create EBS volume  with EC2 instance

![](image/Pasted%20image%2020241002152347.png)

# 2 EFS

shared NFS Volume 

![](image/Pasted%20image%2020241002152753.png)



# 3 S3


![](image/Pasted%20image%2020241002153012.png)



## 3.1 limitation: maximal size of object   5TB 
- single pull: maximal 2 GB 

Movie movie is 2 terabytes , but  maximal size of single pull ist 2GB,  how to address this problem :  S3 called Multipart upload
-  2 tB file into seraval parts and send each parts in prallier  


![](image/Pasted%20image%2020241002153648.png)


---

Standard S3 会将上传的文件 自动 上传到 3个不同的 AZ in the same region 
 S3 不会 自动 copy data between regions, 因为需要客户自己选择 到那个region 去保存. 如果客户想要保存 信息in serveral different regions , through replication feature in s3 

![](image/Pasted%20image%2020241002153839.png)


![](image/Pasted%20image%2020241002153914.png)

---




## 3.2 Entity Tag of object in s3 : 校验文件的intergrity 

![](image/Pasted%20image%2020241002154517.png)

Entity Tag的value ist MD5, ist hash code 
MD5消息摘要算法，一种被广泛使用的密码散列函数，可以产生出一个128位的散列值，用于确保信息传输完整一致。


Why we need thies entity Tag: 
- Because what you should do before downloading a file is get this value, download the file and when the file arrives to your machine, if there is any corruption in  transport and you run another MD5, the value will not be the same.
- Now if there was corruption on the way to the cloud, you can regocinze it 
- so, we can we help you depends which API you are using.


get md5, download file from s3 , check the file with md5 



![](image/Pasted%20image%2020241002154828.png)


![](image/Pasted%20image%2020241002160204.png)


![](image/Pasted%20image%2020241002160214.png)



## 3.3 prefixes and deleimiers in S3


![](image/Pasted%20image%2020241002153012.png)

![](image/Pasted%20image%2020241002160523.png)


![](image/Pasted%20image%2020241002160631.png)


## 3.4 version 

![](image/Pasted%20image%2020241002160720.png)



----

删除了某个 object , 但是通过 show version , 基础删除了, 他还会显现出来 

![](image/Pasted%20image%2020241002160816.png)



![](image/Pasted%20image%2020241002160822.png)


## 3.5 lifecycle rules 

![](image/Pasted%20image%2020241002160913.png)


## 3.6 replicate objects across bucket

![](image/Pasted%20image%2020241002160943.png)


## 3.7 immutable object: Object Lock 

[https://aws.amazon.com/blogs/storage/protecting-data-with-amazon-s3-object-lock/](https://aws.amazon.com/blogs/storage/protecting-data-with-amazon-s3-object-lock/ "https://aws.amazon.com/blogs/storage/protecting-data-with-amazon-s3-object-lock/")

protect s3 object from root user and any user 
就是谁都改写不了这个 object 了 

enable Object Lock 

![](image/Pasted%20image%2020241002161700.png)
![](image/Pasted%20image%2020241002161856.png)



## 3.8 static Website hosting 



![](image/Pasted%20image%2020241002161927.png)


![](image/Pasted%20image%2020241002161934.png)



![](image/Pasted%20image%2020241002161956.png)

会自动产生一个 endpoint 
![](image/Pasted%20image%2020241002162002.png)


[http://brussels-cafe.s3-website-sa-east-1.amazonaws.com](http://brussels-cafe.s3-website-sa-east-1.amazonaws.com "http://brussels-cafe.s3-website-sa-east-1.amazonaws.com/")



# 4 AWS S3 CLI


![](image/Pasted%20image%2020241002160328.png)
.  代表 source,   就是 current directory , 在 current directotory 下同步一个 s3 bucekt 


