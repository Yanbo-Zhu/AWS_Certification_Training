

# 1 IAM


IAM ist groble service,   iam 是无法选region,  globally valid 

刚开始要干什么 
1. stop use root, enable MFA
2. release least privilege
3. temporary access 

## 1.1 IAM_Terms_Concepts
- users 
    - attached with policys
- groups 
    - attached with policys
- roles
    - attached with policys
    - roles can not be attached with IAM user 
    - xx assmue a role 
    - metaphor: give carkey to costumer 
- policy 
    - what a role can do: trsut policy
    - who can assuame a role:  trust policy
        - The conditions on the role can determine which can assume the role because you remember that trust policy. I was not very specific.
    


![](image/Pasted%20image%2020241002135419.png)


![](image/Pasted%20image%2020241002111733.png)



### 1.1.1 Permission policy


example-role  ec2 

![](image/Pasted%20image%2020241002112658.png)


### 1.1.2 Trusted Entity  (Assume Role)

principal :  user , service is principal 
group it not a principle


在 IAM policy 中定义 Trusted Entity 
those Trusted Entities is able to assume this IAM role 
This aws iam Trusted Entity  can (with effect ) use  the action (  can assume this role ) 


![](image/Pasted%20image%2020241002113406.png)



## 1.2 IAM user 

![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002140129.png)

![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002140154.png)


## 1.3 IAM policy 


可以自定义自己的 customized IAM policy 

![](image/Pasted%20image%2020241002114009.png)


![](image/Pasted%20image%2020241002114020.png)


![](image/Pasted%20image%2020241002114027.png)


 From xx source ip 可以 access to xx S3 buckets  to do xx action 

![](image/Pasted%20image%2020241002114151.png)


---


this polcy give  a limeted read list read to a specify aws servcice of 421 aws services 
![](image/Pasted%20image%2020241002114043.png)

![](image/Pasted%20image%2020241002114113.png)



## 1.4 Setting up AWS permanent credentials 

aws configuration file 

![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002135438.png)

![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002133307.png)



## 1.5 attach IAM role to a ec2 instance profile

![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141023.png)


![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141057.png)


![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141212.png)


## 1.6 IAM role: Trust Relationships and permission 

1 
permission: rolle  can do what in permision defined 

![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141521.png)

---


2  Trust Relationships 
里面定义 to trust which entity 

only trusted entities  kann assume this role 


![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141546.png)



---


![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141629.png)


![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002141637.png)


![](../01_03_Accessing_AWS_Service/image/Pasted%20image%2020241002154344.png)





# 2 AWS CloudTrail 

AWS CloudTrail is a web service that records AWS API calls for your AWS account and delivers log files to an Amazon S3 bucket.

to see  what a service have exactly done 

![](image/Pasted%20image%2020241002114647.png)


Cloudtrail 通 trace  api record ,  to see which one has used xx 

![](image/Pasted%20image%2020241002115029.png)

![](image/Pasted%20image%2020241002115617.png)



# 3 secure account setup 

[https://d0.awsstatic.com/aws-answers/AWS_Secure_Account_Setup.pdf](https://d0.awsstatic.com/aws-answers/AWS_Secure_Account_Setup.pdf "https://d0.awsstatic.com/aws-answers/aws_secure_account_setup.pdf")   
![](image/Pasted%20image%2020241002120603.png)


# 4 cost watching 

https://aws.amazon.com/blogs/aws-cloud-financial-management/getting-started-with-aws-budgets/

## 4.1 billing alarm through alert fucntion in aws cloudwatch 


[https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html "https://docs.aws.amazon.com/amazoncloudwatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html")

Create billing alarm to monitor 
montoring  the aws cloudwath metric.  In cloudwoatch , you can setup biiling alarm/alert according to cloudwatch metric 



![](image/Pasted%20image%2020241002120418.png)



![](image/Pasted%20image%2020241002115428.png)


![](image/Pasted%20image%2020241002120519.png)


## 4.2 aws budgets 


[https://aws.amazon.com/fr/blogs/aws-cloud-financial-management/get-started-with-aws-budgets-actions/](https://aws.amazon.com/fr/blogs/aws-cloud-financial-management/get-started-with-aws-budgets-actions/ "https://aws.amazon.com/fr/blogs/aws-cloud-financial-management/get-started-with-aws-budgets-actions/")

AWS budgets  doesn't  have to work toegther with AWS Cloudwatch
configure budgets and also is able to  configure  budgets actions  to do something when xx happens 
budget actions: example: setup up a limt and then stop 

![](image/Pasted%20image%2020241002120108.png)

![](image/Pasted%20image%2020241002120128.png)



20000 budgets rule  ist fee 

![](image/Pasted%20image%2020241002115508.png)



