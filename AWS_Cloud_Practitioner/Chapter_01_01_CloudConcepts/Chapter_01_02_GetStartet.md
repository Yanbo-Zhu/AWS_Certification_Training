46:57 Create an AWS Account
48:42 Create IAM User
56:23 AWS Region Selector
58:26 Overbilling Story
1:02:37 AWS Budgets
1:06:56 AWS Free Tier
1:09:43 Billing Alarm
1:14:23 Turning on MFA

# 1 Create AWS Accout and Root user 

# 2 Create IAM user and user group

## 2.1 IAM USER

Access keys
Use access keys to send programmatic calls to AWS from the AWS CLI, AWS Tools for PowerShell, AWS SDKs, or direct AWS API calls. You can have a maximum of two access keys (active or inactive) at a time. Learn more 

![](image/Pasted%20image%2020230319131747.png)


# 3 AWS Region Selector 

Some AWS Services 是没有 region dependent的, 不用选 Region , 像是 Cloud Front 
Some  AWS Services 是=有 region 之分: EC2, S3


# 4 AWS Budgets
services name 就是 AWS Budgets
The first 2 Budgets which you set  are free 
在 设定 budget 的时候 ,就可以设置 alert 功能,  这样 就会 定期收到 账单 在邮箱里面 

![](image/Pasted%20image%2020230319134854.png)
![](image/Pasted%20image%2020230319134733.png)

![](image/Pasted%20image%2020230319135054.png)



# 5 AWS Free Tier
Free Tier  is available to you uh for the first 12 months of a new abs account and allows you to utilize the services without incurring any cost to you and so it's in your advantage to utilize this free tier

就是 这里面有很多的 免费大礼包 

https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all
![](image/Pasted%20image%2020230319135357.png)


Billing 中设置 收到 free tier usage Alerts 的提醒
![](image/Pasted%20image%2020230319135639.png)



# 6 Billing Alarm (via cloudWatch)

a old new before aws budgets
使用 cloudWatch  这 Aws services 
You get 10 free alarms with a thousand free email notifications each month as part of the free tier


![](image/Pasted%20image%2020230319140956.png)

![](image/Pasted%20image%2020230319141104.png)
![](image/Pasted%20image%2020230319141023.png)


 Auto Scaling action: 一旦超过了 预设的 花钱的值, 会自动 做一些 action, 比图说 shutdown or delete the machine 

# 7 Turning on MFA (Multi Factor Authentification)  (via IAM)

![](image/Pasted%20image%2020230319141821.png)


有三种验证方法
![](image/Pasted%20image%2020230319141833.png)

Virtual MFA: 手机 装个 app. 用它来验证. 
![](image/Pasted%20image%2020230319142217.png)



