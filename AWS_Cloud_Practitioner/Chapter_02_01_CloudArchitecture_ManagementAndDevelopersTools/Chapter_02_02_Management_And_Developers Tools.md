
# 1 AWS API

AWS API is an HTTP APi and you can interract by sending https requests 
An API is software that allows two applications/services to talk to each other. The most common type of API is via HTTP/S requests.
AWS API is an HTTP API and you can interact by sending HTTPS requests, using an application interacting with APIs like Postman.
Each AWS Service has its own Service Endpoint which you send requests

GET / HTTP/1.1  
host: monitoring.us-east-1.amazonaws.com  
x-amz-target: GraniteServiceVersion20100801.GetMetricData  
x-amz-date: 20180112T092034Z  
Authorization: AWS4-HMAC-SHA256 Credential=REDACTEDREDACTED/20180411/…..  
Content-Type: application/json  
Accept: application/json  
Content-Encoding: amz-1.0  
Content-Length: 45  
Connection: keep-alive

To authorize use you will need generate a signed request You make a separate request with your AWS credentials and get back a token.
You need to also provide an ACTION and accompanying parameters as the payload
Rarely do users directly send HTTP requests directly to the AWS API. Its much easier to interact with the API via a variety of Developer Tools


在实际中 user 很少 send http request directly to aws api. 一般都是通过 一些 aws service 去跟aws api 互动 
- HTTP Request:
    - Directly interact with the AWS API
- AWS management Console 
    - A WISWIG Web Interface
- AWSSDK
    - Interact with the API using your favourite programming language
- AWS CLI
    - Interact with the API via a terminal/shell program


https://docs.aws.amazon.com/general/latest/gr/aws-apis.html

例子
https://docs.aws.amazon.com/general/latest/gr/aws-apis.html
![](image/Pasted%20image%2020230331195728.png)
![](image/Pasted%20image%2020230331200319.png)


## 1.1 如何实际用 postsman 和 AWS API 联系

1 
https://docs.aws.amazon.com/general/latest/gr/aws-service-information.html
https://docs.aws.amazon.com/general/latest/gr/ec2-service.html

复制 endpoint 的值
![](image/Pasted%20image%2020230331201216.png)


2 postsman 中 

![](image/Pasted%20image%2020230331201308.png)

填写 accessKey 和 secret key
![](image/Pasted%20image%2020230331201417.png)

填写 Body 
![](image/Pasted%20image%2020230331201447.png)

# 2 AWS Management Console

AWS management console is a web-based unified console to build manage and monitor everything from simple web apps to complex cloud deployments 
Point and Click to manually launch and configure AWS resources with limited programming knowledge.
This is known as “ClickOps” since you can perform all your system operations via clicks.
The AWS Management Console is located at: console.aws.amazon.com

https://aws.amazon.com/console/

![](image/Pasted%20image%2020230331202129.png)


# 3 每个 AWS Service 自己的 Console
AWS Service each have their own customized console. You can access these consoles by **searching** the service name

Some AWS Services Console will act as an umbrella console containing many AWS Services: e.g.
-   VPC Console
-   EC2 Console
-   Systems Manager Console
-   SageMaker Console
-   CloudWatch Console

# 4 AWS Account ID

Every AWS account has a unique Account ID

The **Account ID** can be easily found by dropping down the current user in the Global Navigation

The AWS Account ID is composed of 12 digits eg:
-   123456789012
-   121212121212
-   498241098510

The AWS Account ID is used
-   when logging in with a non-root user account
-   Cross-account roles
-   Support cases

It is generally good to keep your Account ID private as it is one of many components used to identify an account for the attack by a malicious actor.

![](image/Pasted%20image%2020230331232112.png)

例子:  在 IAM 中 create role 中可以用到 account iD
![](image/Pasted%20image%2020230331232310.png)

例子: 在 IAM 中 create policy  中可以用到 account iD
only from that account id is allowed 
![](image/Pasted%20image%2020230331232453.png)

![](image/Pasted%20image%2020230331232558.png)

 
# 5 AWS Tools for PowerShell

let you interact with the aws API via PowerShell Cmdlets 

What is PowerShell?
PowerShell is a task automation and configuration management framework.

A command-line shell and a scripting language
Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.

AWS Tools for PowerShell lets you interact with the AWS API via PowerShell Cmdlets
Cmdlet is a special type of command in PowerShell in the form of capitalized verb-and-noun e.g. New-S3Bucket

![](image/Pasted%20image%2020230331232913.png)



## 5.1 安装和使用 AWS Tools fro PowerShell

1 cloud shell 打开 powershell 
打开 cloudshell 
![](image/Pasted%20image%2020230331233202.png)

cloudshell 中打开 powershell 模式 : 就是 输入 pwsh , 按回车 进入 powershell 模式 
![](image/Pasted%20image%2020230331233301.png)


2 本机中下载 aws powershell module
https://aws.amazon.com/powershell/
https://www.powershellgallery.com/packages/AWS.Tools.Common/4.1.303
https://docs.aws.amazon.com/powershell/latest/userguide/pstools-getting-started.html
https://docs.aws.amazon.com/powershell/latest/reference/

实际的安装步骤 
https://docs.aws.amazon.com/powershell/latest/userguide/pstools-getting-set-up-windows.html
执行Install-Module -Name AWS.Tools.Installer
![](image/Pasted%20image%2020230331234453.png)

然后 还要 安装 Install-AWSToolsModule AWS.Tools.EC2,AWS.Tools.S3 -CleanUp, 要不然没法使用 


3  执行 Get-S3BUCKET 和 New-S3Bucket -BucketName website-example -Region us-west-2



# 6 Amazon Resource Names (ARN)

Amazon Resourece Names (ARNs) uniquely identify AWS resources.  
ARNs are required to specify a resource unambiguously across all of aws 

Resource ARNs can include a path. Path can include a wildcard character, namely an asterisk (\*)
![](image/Pasted%20image%2020230401145401.png)

Format variationsn of ARN
![](image/Pasted%20image%2020230401144921.png)

The ARN has the following **format variations**
arn:**partition:service:region:account-id:resource-id**  
arn:**partition:service:region:account-id:resource-type/resource-id**  
arn:**partition:service:region:account-id:resource-type:resource-id**  

Partition
-   aws - AWS Regions
-   aws-cn - China Regions
-   aws-us-gov - AWS GovCloud (US) Regions

Service – Identifies the service
-   ec2
-   s3
-   iam

Region – which AWS resource
-   us-east-1
-   ca-central-1

Account ID
-   121212121212
-   123456789012

Resource ID

Could be a number name or path:
-   user/Bob
-   instance/i-1234567890abcdef0

In the AWS Management Console its common to be able to copy the ARN to your clipboard
arn:aws:s3:::my-bucket

**Paths in ARNs**
Resource ARNs can include a path Paths can include a wildcard character, namely an asterisk (*)

**IAM Policy ARN Path**
arn:aws:iam::123456789012:user/Development/product_1234/*

**S3 ARN Path**
arn:aws:s3:::my_corporate_bucket/Development/*


# 7 AWS CLI

https://aws.amazon.com/cli/

CLI allows users to programmatically interact with the aws API via entering single or multi-line commands into a shell or terminal 
AWS CLI is Python executable programm 
The AWS CLI can be installed on Windows, Mac or Linux/Unix
The name of the CLI program is aws

![](image/Pasted%20image%2020230401151729.png)

What is a CLI?
A Command Line Interface (CLI) processes commands to a computer program in the form of lines of text.
Operating systems implement a command-line interface in a shell.

What is a Terminal?
A terminal is a text only interface (input/output environment)

What is a Console?
A console is a physical computer to physically input information into a terminal

What is a Shell?
A shell is the command line program that users interact with to input commands. Popular shell programs:
    Bash
    Zsh
    PowerShell


## 7.1 CLI Terminal Console Shell 

![](image/Pasted%20image%2020230401151629.png)

## 7.2 安装 aws CLI

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

in Windows 
![](image/Pasted%20image%2020230401152523.png)

## 7.3 本机中 植入 aws access  credentials 

![](image/Pasted%20image%2020230401153651.png)

![](image/Pasted%20image%2020230401153951.png)

1 输入 aws configure, 回车, 然后 让你 输入 access key id 和 对应的 screat key value 
2 从哪里能获得 accesskey 
IAM -> user  -> create access key 
![](image/Pasted%20image%2020230401153822.png)

 3 Default region name:  自己选一个  , lke us-east-1
 4 default output format:  可以不选 可以选 json oder 其他的format

### 7.3.1 文件位置 
以上的这些 credential 信息 都 储存在 ~/.aws/credentials 或者在 config  文件中
![](image/Pasted%20image%2020230401154458.png)

### 7.3.2 multiple credential 
~/.aws/credentials 中  放置 两个 profile , 有不一样的 credential 

![](image/Pasted%20image%2020230401154801.png)

在 aws command 中 指定使用 某个 profile 中的 credential 信息
aws s3 ls --profile exampro 

### 7.3.3 使用 
https://docs.aws.amazon.com/cli/latest/reference/
https://docs.aws.amazon.com/cli/latest/reference/s3/index.html
aws s3 help
aws s3 ls


# 8 AWS SDK Software development Kit 

[Software Development Kit (SDK)](https://en.wikipedia.org/wiki/Software_development_kit)

A Software Development Kit (SDK) is a **collection of software development tools** in **one installable package**.
You can use the **AWS SDK** to programmatically create, modify, delete or interact with AWS resources.

AWS SDK is offered in various programming languages:
-   Java
-   Python
-   Node.js
-   Ruby
-   Go
-   .NET
-   PHP
-   JavaScript
-   C++

![](image/Pasted%20image%2020230401155402.png)


## 8.1 使用 sdk  
https://aws.amazon.com/developer/tools/

1 使用 aws cloud 9 去 建一个 environments
cloud 9 ist a cloud-based  ide for writing runing and debugging code 

![](image/Pasted%20image%2020230401155629.png)

建好的 一个新的 cloud9 environment
![](image/Pasted%20image%2020230401160534.png)

2 
安装gem aws-sdk 在这个 新建的 cloud9 环境里面 
gem 'aws-sdk' 或者 gem 'aws-sdk-s3' 写入 gemfile 中
然后 执行 bundle install : 这样会按照 gemfile 中的内容 执行,  执行 gem 'aws-sdk-s3'. 这样 就会安装 aws-sdk-s3 了

![](image/Pasted%20image%2020230401160658.png)

![](image/Pasted%20image%2020230401160830.png)


![](image/Pasted%20image%2020230401193815.png)

然后 在example.rb 中 输入下面的代码. 这个代码. 会 列出 s3 中的 you呢些 buckets (参考 https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/S3/Client.html)
然后 bundle exec ruby example.rb , 以此来执行 exampl.rb 这个脚本

![](image/Pasted%20image%2020230401194736.png)

![](image/Pasted%20image%2020230401194805.png)

3  setting credentials using aws.config 
![](image/Pasted%20image%2020230401195719.png)

![](image/Pasted%20image%2020230401195757.png)

或者
![](image/Pasted%20image%2020230401200108.png)

然后在 console 中 通过 export AWS_ACCESS_KEY_ID=sfdassfdasdfadfs  给出 值, 是的 在运行 example.rb 的时候这个AWS_ACCESS_KEY_ID 值 被得到 
![](image/Pasted%20image%2020230401200244.png)

credentials 藏在了  ~/.aws/credentials 中 
![](image/Pasted%20image%2020230401195907.png)

3 紧接上上面 使用 pry

![](image/Pasted%20image%2020230401194938.png)

![](image/Pasted%20image%2020230401194947.png)

![](image/Pasted%20image%2020230401195013.png)

![](image/Pasted%20image%2020230401195039.png)

![](image/Pasted%20image%2020230401195112.png)

4 create bucket with ruby 
https://docs.aws.amazon.com/sdk-for-ruby/v3/api/Aws/S3/Client.html#create_bucket-instance_method



# 9 AWS CloudShell

[What is AWS CloudShell?](https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html)

It is a brower-based shell built into the aws management Console 
AWS CloudShell is scoped per region, Same credentials as logged in user. Free Service!
- aws Cloudshell is scoped per region
- 1 GB storage free per aws region 
- 预装了 很多 tools
- seamlessly switch between Bash Powershell zsh 
- 某些 aws region 不支持 cloudshell
![](image/Pasted%20image%2020230401202831.png)


**Preinstalled Tools**
AWS CLI, Python, Node.js git, make, pip, sudo, tar, tmux, vim, wget, and zip and more

**Storage included**
1 GB of storage free per AWS region

**Saved files and settings**
Files saved in your home directory are available in future sessions for the same AWS region

**Shell Environments**
Seamlessly switch between
-   Bash
-   PowerShell
-   Zsh

# 10 Infrastructure as Code (LaC)

Write a configuration script to automate creating, updating or destroying cloud infracture 
-   IaC is a blueprint of your infrastructure.
-   IaC allows you to easily share, version, or inventory your cloud infrastructure.

AWS has two offerings for writing Infrastructure as Code: 
AWS CloudFormation and AWS Cloud Development Kit 
**AWS CloudFormation (CFN)**
CFN is a Declarative IaC tool

**AWS Cloud Development Kit (CDK)**
CDK is an Imperative IaC tool.

![](image/Pasted%20image%2020230401204728.png)



**Declarative**
-   You say what you want, and the rest is filled in. ~~Implicit~~ Explicit
-   More verbose, but zero chance of misconfiguration
-   Uses scripting languages eg. JSON, YAML, XML

**Imperative**
-   What you see is what you get. ~~Explicit~~ Implicit
-   Less verbose, you could end up with misconfiguration
-   Does more than Declarative
-   Uses programming languages eg. Python, Ruby, JavaScript

## 10.1 CloudFormation

write infrastructure as Code as a json or yaml file 


AWS CloudFormation allows you to write Infrastructure as Code (IaC) as either a JSON or YAML file.
CloudFormation is simple but it can lead to large files or is limited in some regard to creating dynamic or repeatable infrastructure compared to CDK.
CloudFormation can be easier for DevOps Engineers who do not have a background in web programming languages.
Since CDK generates out CloudFormation it's still important to be able to read and understand CloudFormation in order to debug IaC stacks.

![](image/Pasted%20image%2020230401205047.png)

### 10.1.1 CloudFormation 例子
https://docs.aws.amazon.com/cloudformation/index.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.Walkthrough.html
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-ec2-instance.html
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/index.html

例子1 cloud9 中 建立一个 yaml file , 这个用来 创造一个 新的 s3 bucket , 
然后 在 cloud9 中 , 使用  command  , 来运行这个yaml file , 从而创建 s3 buckt 
![](image/Pasted%20image%2020230401210754.png)

使用 aws cli cloudformation 来创造一个 new  stack in cloudformation
https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-cli.html

template 中 
![](image/Pasted%20image%2020230401213756.png)

使用 如下命令 aws cli cloudformation
![](image/Pasted%20image%2020230401213715.png)


2  create a new stack in CloudFormation
CloudFormation 中 建立一个 yaml file , 这个用来 创造一个 新的 s3 bucket , 
然后 把这个 yaml file 保存在 s3 中
然后 在 CloudFormation 中 , 使用  这个 yaml file in S3 
运行这个yaml file , 从而创建 s3 buckt 
![](image/Pasted%20image%2020230401210848.png)

在下面输入yaml 文件的内筒, 然后按下右上的 refresh button, 就会有 hello bucket 的图标产生. 

![](image/Pasted%20image%2020230401211113.png)

然后再按下左上面的 储存 button, 将这个  yaml file 储存到 s3 中
![](image/Pasted%20image%2020230401211348.png)

然后create stack with the yaml file in S3
![](image/Pasted%20image%2020230401211549.png)

![](image/Pasted%20image%2020230401211633.png)

## 10.2 Cloud Development kit (CDK) 

[Construct Hub](https://constructs.dev/)
[CDK Pipelines: Continuous delivery for AWS CDK applications](https://aws.amazon.com/blogs/developer/cdk-pipelines-continuous-delivery-for-aws-cdk-applications/)

CDK  allows you to use your favorite programming language to implement the  infrastructure as code
    TypeScript NodeJS Python Java ASP.NET

-   CDK is powered by CloudFormation (it generates out CloudFormation templates)
-   CDK has a large library of reusable cloud components called CDK Construct [https://constructs.dev](https://constructs.dev)
-   CDK comes with its own CLI
-   CDK Pipelines to quickly set up CI/CD pipelines for CDK projects
-   CDK has a testing framework for Unit and Integration Testing

AWS SDK looks similar, but the key difference is CDK ensures Idempotent of your Infrastructure

![](image/Pasted%20image%2020230401215533.png)

CDK generated our CloudFormation Templates

### 10.2.1 AWS CDK 和 SDK 的区别
AWS CDK 和 SDK 的区别: CDK ensures Idempotent of your infrastucture (等幂性). 就是 说 用 CDK 创造出来的 server 都是 with same state of file . 但是用 SDK 不能保证 每个创造出来的 server 都是一样的 


### 10.2.2 CDK 例子 
https://github.com/aws/aws-cdk
https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html

0  创造一个 new Cloud9 environment , 在 这个 envorment 中 进行 如下操作 

1  安装cdk 
https://github.com/aws/aws-cdk

Install or update the [AWS CDK CLI](https://docs.aws.amazon.com/cdk/latest/guide/tools.html) from npm (requires [Node.js ≥ 14.15.0](https://nodejs.org/download/release/latest-v14.x/)). We recommend using a version in [Active LTS](https://nodejs.org/en/about/releases/)
    npm i -g aws-cdk
(See [Manual Installation](https://github.com/aws/aws-cdk/blob/main/MANUAL_INSTALLATION.md) for installing the CDK from a signed .zip file).


2 Initialize a project:

mkdir hello-cdk
cd hello-cdk
cdk init sample-app --language=typescript   之后产生了一些文件 

![](image/Pasted%20image%2020230401221820.png)

3  Deploy this to your account:

cdk deploy

Use the cdk command-line toolkit to interact with your project:

    cdk deploy: deploys your app into an AWS account
    cdk synth: synthesizes an AWS CloudFormation template for your app
    cdk diff: compares your app with the deployed stack


4 最终会产生一个新的 stack in Cloudformation.
通过 cloudformation 的 console 可以看见这个新的 stack 


5 执行 cdk destory 来 删除 这个 新产生的 stack 
![](image/Pasted%20image%2020230401222524.png)

6 cdk  命令大全 
https://docs.aws.amazon.com/cdk/v2/guide/cli.html



# 11 AWS Toolkit for VSCode

![](image/Pasted%20image%2020230401222854.png)

AWS Toolkit is an open-source plugin for VSCode to create, debug, deploy AWS resources
[Working with AWS Services](https://docs.aws.amazon.com/toolkit-for-vscode/latest/userguide/working-with-aws.html)

**1. AWS Explorer**
Explore a wide range of AWS resources to your linked AWS Account

**2. AWS CDK Explorer**
Allows you to explore your stacks defined by CDK.

**3. Amazon Elastic Container Service**
Provides IntelliSense for ECS task-definitions files

**4. Serverless Applications**
Create, debug and deploy serverless applications via SAM and CFN

# 12 Access Keys (就是 Aws credentials)

- Access key is a key and secret required to have pragmatic access to database resources when interacting with the awps api outside of the aws management console
- Access Keys ist Stored in ~/.aws/credentials 
    - Default profile 以及 其他的profile 
- access keys 通过 aws configure 去设置 

A user must be **granted access** to use Access Keys
-   Never share your access keys
-   Never commit access keys to a codebase
-   You can have two active Access Keys
-   You can deactivate Access Keys
-   Access Keys have whatever access a user has to AWS resources.

Access Keys are to be store in ~/.aws/credentials and follow a TOML file format
**Default** will be the access key used when no profile is specified.
You can store multiple access keys by giving the **profile** names.
You can use the **aws configure** CLI command to populate the credential file.
The AWS SDK will automatically read from these environment variables.
This is the safe way of using an Access Key within your code.

![](image/Pasted%20image%2020230401223017.png)

![](image/Pasted%20image%2020230401223335.png)



## 12.1 Access Keys 例子

iam 中的 user 的 access key 
![](image/Pasted%20image%2020230401223446.png)


# 13 AWS Documentation

AWS Documentation is a large collection of technical documentation on how to use AWS Services.
docs.aws.amazon.com
AWS is very good about providing detailed information about every AWS service.
The basis of this course and for any AWS Certification will derive mostly from the AWS Documentation

![](image/Pasted%20image%2020230401223658.png)


