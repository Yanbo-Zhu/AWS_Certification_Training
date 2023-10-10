


![](image/Pasted%20image%2020231003081412.png)


![](image/Pasted%20image%2020231003081438.png)


# 1 Storage service


![](image/Pasted%20image%2020231003081520.png)

Block Storage: 
used it for database 
we'll save them and index them 

File Storage:
they can collaborate or applications

Object storage: 
S3
each object will be saved individually 


![](image/Pasted%20image%2020231003081738.png)


S3: for hot data
S3 Glacier for achive data 

## 1.1 S3

![](image/Pasted%20image%2020231003081826.png)


![](image/Pasted%20image%2020231003081935.png)


static  website :  no interaction with 
Dynamic  website:  with kommunication with back in 


![](image/Pasted%20image%2020231003082152.png)

no folder in S3 bucekt , but you can mimic folder using prefixes 
by default the bucekt ist private. no one can access the bucket but the owner 

![](image/Pasted%20image%2020231003082422.png)


Resource-based policy hast prinpcle attirbue . 
princple 中不能有 regex, 但可以用 ${variable}
![](image/Pasted%20image%2020231003082522.png)


![](image/Pasted%20image%2020231003082828.png)

resource 的路径
arn
aws: aws, or aws-ch or aws-us
s3: Region: aws aoccunt:filename 

![](image/Pasted%20image%2020231003082934.png)
listBucekt 对应 Resource 中的第一项
GetObject 对应 resource 中 第二项为作用项


![](image/Pasted%20image%2020231003083051.png)


![](image/Pasted%20image%2020231003083214.png)


![](image/Pasted%20image%2020231003083513.png)


1 Bucket policy kann not more 20kb 
2 each access point has own acces Point policy  
3 使用 access point 去分割 那些人 可以接触到那些资源



![](image/Pasted%20image%2020231003083725.png)





EBS 中
encryted value will be 解密 在 physicale host 然后 被给 instance 
![](image/Pasted%20image%2020231003084021.png)



S3
Server side encryption 
s3 中 encryption 发生在 server side 
![](image/Pasted%20image%2020231003084205.png)

sse: server-side encryption

sse-s3: 
s3 will So S3 will generate a data key for each object that needs to be encrypt


sse-kms

sse-c
client side encryption means the data is going to be encrypted before it is uploaded into s3 
s3 提供key, 但是加密要你自己来 


![](image/Pasted%20image%2020231003084622.png)

一般是 
主要的bucket 用 s3 bucket 
第一个backup of  用 s3 standard-IA , 
第二个backuo 用 s3 one zone-IA



自动帮你变更 access pattern 
一旦 你开始访问了, 又会便回到 Frequent access tier 
![](image/Pasted%20image%2020231003085200.png)

![](image/Pasted%20image%2020231003085343.png)



![](image/Pasted%20image%2020231003085425.png)


![](image/Pasted%20image%2020231003085557.png)

upload the same file again, help your visioning this file 

hacker of version and multiple copy: more cost if version by used  
versioning feature ist by default 

Object lock: WORM, no one can delete it and 

object key is the the only sole factor that s3 will consider whether the same file ist uploaded . 
如果 versioning freature 没有被开启,  文件会被覆盖, 只剩下新的文件 
如果 versioning freature 被开启.  新的 version 会被 产生, 只要 object key (文件名 文件 extension 加 路径 一样 ) 一样 


---
expiration action 

![](image/Pasted%20image%2020231003090444.png)

lifecycle polices : user define  多少天后 变
intelligent tier : s3 决定多少天后 变. 

can hat mulitple lifecycle polices in the same bucket 
lifecycle polices can befinded on the bucket level, 也可定义 subnet of prefix 有这个 policy

同样的 bucket 不同的object 可以拥有不同 的 storage class  

== ==

----

![](image/Pasted%20image%2020231003091251.png)

![](image/Pasted%20image%2020231003091533.png)




----

if file ist more than more 5 gb 
the s3 will take the large file , then cut it off into segments and then upload it paraellel , using multiport , 不同的 request 
如果 其中一个失败了 -> 需要重听 

![](image/Pasted%20image%2020231003091545.png)


With a multipart upload, you can consistently upload large objects in manageable parts. This process involves three steps: • Initiating the upload • Uploading the object parts • Completing the multipart upload
When the multipart upload request is completed, Amazon S3 will recreate the full object from the individual pieces.
Improve the upload process of larger objects with the following features:
• Improved throughput – You can upload parts in parallel to improve throughput. • Quick recovery from any network issues – Smaller part sizes minimize the impact of restarting a failed upload due to a network error.
• Pausing and resuming object uploads – You can upload object parts over time. When you have initiated a multipart upload, there is no expiration. You must explicitly complete or cancel the multipart upload.
• Beginning an upload before you know the final object size – You can upload an object as you are creating it. • Uploading large objects – Using the multipart upload API, you can upload large objects, up to 5 TB.
Note: You cannot perform multipart uploads manually by using the console.
For more information about multipart uploads, see “Uploading and copying ob

----

使用 edge location , caching, 然后加速 

![](image/Pasted%20image%2020231003091814.png)


![](image/Pasted%20image%2020231003092047.png)


![](image/Pasted%20image%2020231003092115.png)




![](image/Pasted%20image%2020231003092224.png)



![](image/Pasted%20image%2020231003092355.png)


![](image/Pasted%20image%2020231003092538.png)


## 1.2 Shared file systems overview


![](image/Pasted%20image%2020231003092621.png)


![](image/Pasted%20image%2020231003092644.png)

### 1.2.1 EFS (only for linux)

![](image/Pasted%20image%2020231003092745.png)

security gourp should alow the mount target via  protocal 2049  nfsv4


File locking: 

![](image/Pasted%20image%2020231003093035.png)


efs can shrink or grow based on data 



### 1.2.2 Fsx (for Windows File Server)

![](image/Pasted%20image%2020231003093135.png)



can be mounted to server 

SMB: server managment block , mount the fsx with several instance 

nfs: use it in client comunicated client  


# 2 Dara migration tools 

![](image/Pasted%20image%2020231003093402.png)



![](image/Pasted%20image%2020231003093428.png)


![](image/Pasted%20image%2020231003093641.png)




![](image/Pasted%20image%2020231003093926.png)

![](image/Pasted%20image%2020231003094021.png)

smb 
fns 
每一个需要配一个独立的  file gateway 



后两个用 isito 


## 2.1 
两种 传输形式的区别 

![](image/Pasted%20image%2020231003094052.png)



![](image/Pasted%20image%2020231003094122.png)


## 2.2 offline data migration 



![](image/Pasted%20image%2020231003094431.png)

![](image/Pasted%20image%2020231003094638.png)

snowball  上传速率更大 



# 3 Review


![](image/Pasted%20image%2020231003094714.png)


![](image/Pasted%20image%2020231003094749.png)



# 4 #


d

![](image/Pasted%20image%2020231003094804.png)




---

b

![](image/Pasted%20image%2020231003094822.png)

----
d

![](image/Pasted%20image%2020231003094849.png)





------

c: for server , when it 
b
e



![](image/Pasted%20image%2020231003094916.png)

