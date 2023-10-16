
![](image/Pasted%20image%2020231002102157.png)

# 1 Business requests
![](image/Pasted%20image%2020231002102237.png)

The least privileged access or the least privileged principle

Imagine that your security specialist meets with you to discuss how to start building accounts with least privilege in AWS. Here are some questions that they are asking about account security.
At the end of this module, you meet with the security specialist and present some solutions. 

# 2 Princple and identities of aws account 


![](image/Pasted%20image%2020231016202858.png)

The security specialist asks, “What are the best practices to manage access to AWS accounts and resources?” 
The security team must start setting up accounts. 
The company wants your advice for how to provide access.

## 2.1 root user 
![](image/Pasted%20image%2020231002102423.png)


When you first create an AWS account, you begin with a root user. This user has complete access to all AWS services and resources in the account. You access the root user identity by signing in with the email address and password, which were provided when you created the account. AWS strongly recommends that you not use root account credentials for day-to-day interactions with AWS. Create users for everyday tasks. You can manage and audit users with relative ease.
Create your additional users and assign permissions to these users by following the principle of least privilege. Grant users only the level of access that they require and nothing more. You can start by creating an administrator user. Manage the account with the administrator user instead of the root user.
As a best practice, require multi-factor authentication (MFA) for your root user. It provides you with an extra layer of security for your AWS accounts. Use your root user only for tasks that require it.

For more information about the root user, see “AWS account root user” in the AWS Identity and Access Management User Guide at https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html.

For more information about least privilege and IAM best practices, see “Grant least privilege” in the AWS Identity and Access Management User Guide at https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege

## 2.2 IAM

IAM is a web service that helps you securely control access to AWS resources. Use IAM to control who is authenticated (signed in) and authorized (has permissions) to use resources.
Think of IAM as the tool to centrally manage access to launching, configuring, managing, and terminating your resources. You have granular control over access permissions. This control is based on resources and helps you define who has permissions to which API calls.
You manage access in AWS by creating and using security policies. You learn about IAM users, IAM user groups, and roles in this section.
For more information about IAM, see “What is IAM?” in the AWS Identity and Access Management User Guide at https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html.
For more information about policy types and their uses, see “Policies and permissions in IAM” at https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html.


![](image/Pasted%20image%2020231002102644.png)


## 2.3 principle 

![](image/Pasted%20image%2020231002103054.png)

谁 或者 什么 东西, 可以 提出 request. 这些东西 或者人, 已经被 authoricated or authendicated 

Federated user,

A principal is an entity that can request an action or operation on an AWS resource. IAM users and IAM roles are the most common principals that you work with, and you learn about them in this lesson.

The principal can also be an AWS service, such as Amazon Elastic Compute Cloud (Amazon EC2), a Security Assertion Markup Language 2.0 (SAML 2.0) provider, or an identity provider (IdP). With an IdP, you manage identities outside IAM — for example, Login with Amazon, Facebook, or Google. You can give these external identities permissions to use AWS resources in your account.

Federated users are external identities that IAM does not manage directly.
For more information about federated users, see “Identity federation in AWS” at https://aws.amazon.com/identity/federation/.


# 3 IAM 仔细介绍
## 3.1 IAM user




![](image/Pasted%20image%2020231002103249.png)

By default, a new IAM user has no permissions to do anything. The user is not authorized to perform any AWS operations or access any AWS resources. An advantage of having individual IAM users is that you can assign permissions individually to each user.

For example, this diagram shows three IAM users — an administrator, developer, and auditor — and their permissions within an AWS account. The administrator has permissions to access an Amazon Simple Storage Service (Amazon S3) bucket, an EC2 instance, and a list of IAM users in your account. The auditor has read-only permissions to Amazon S3 and IAM, but not Amazon EC2. The developer only has permissions to the EC2 instance.

As a best practice, require multi-factor authentication (MFA) for your IAM users and set up an IAM user password policy.

For more information about IAM users, see “IAM users” in the AWS Identity and Access Management User Guide at https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html.

IAM user 自己的 credentials should never be shared to others

![](image/Pasted%20image%2020231002103703.png)


Provide the type of credentials that are required for the type of access that a user will need.

Ways to access AWS services include: 
• AWS Management Console access – Create a password for a user.
• Programmatic access – The IAM user might need to make API calls, use the AWS CLI, or use the AWS SDKs. In that case, you will create an access key (access key ID and a secret access key) for that user.

As a best practice, apply the principle of least privilege, which means that you create only the credentials that the user needs. For example, do not create access keys for a user who requires access only through the console.

AWS requires different types of security credentials, depending on how you access AWS.

For more information, see “Understanding and getting your AWS credentials” in the AWS General Reference at https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html.
For more information about password creation, see “Managing passwords for IAM users” in the AWS Identity Access and Management User Guide at https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_passwords_admin-change-user.html


API: You just exposes resources for you to access any functionalities where it is accessed using a URL

![](image/Pasted%20image%2020231002104217.png)

Programmatic access gives your IAM user the credentials to make API calls in the AWS CLI or AWS SDKs. AWS provides an SDK for programming languages such as Java, Python, and .NET.

When programmatic access is granted to your IAM user, it creates a unique key pair that comprises an access key ID and a secret access key. Use your key pair to configure the AWS CLI, or make API calls through an AWS SDK.

To set up AWS CLI in your client, enter the aws configure command. The example code shows the four elements that are required to configure your IAM user in AWS CLI: 
• AWS Access Key ID 
• AWS Secret Access Key 
• Default region name
• Default output format (json, yaml, yaml-stream, text, table)

For more information about configuring your key pair in AWS CLI, see “Configuration basics” in the AWS Command Line Interface User Guide at https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html
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






