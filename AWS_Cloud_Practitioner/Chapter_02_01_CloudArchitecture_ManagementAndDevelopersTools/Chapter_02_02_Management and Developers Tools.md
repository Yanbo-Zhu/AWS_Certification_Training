
# 1 AWS API

AWS API is an HTTP APi and you can interract by sending https requests 
在实际中 user 很少 send http request directly to aws api. 一般都是通过 一些 aws service 去跟aws api 互动 
- AWS management Console 
- AWSSDK
- AWS CLI

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

https://aws.amazon.com/console/

![](image/Pasted%20image%2020230331202129.png)


# 3 每个 AWS Service 自己的 Console
aws  services each have their own customized console 

# 4 AWS Account ID

![](image/Pasted%20image%2020230331232112.png)

例子:  在 IAM 中 create role 中可以用到 account iD
![](image/Pasted%20image%2020230331232310.png)

例子: 在 IAM 中 create policy  中可以用到 account iD
only from that account id is allowed 
![](image/Pasted%20image%2020230331232453.png)

![](image/Pasted%20image%2020230331232558.png)

 
# 5 AWS Tools for PowerShell

let you interact with the aws API via PowerShell Cmdlets 

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


# 7 AWS CLI

https://aws.amazon.com/cli/

CLI allows users to programmatically interact with the aws API via entering single or multi-line commands into a shell or terminal 
AWS CLI is Python executable programm 

![](image/Pasted%20image%2020230401151729.png)

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


# 8 AWS Software development Kit SDK
SDK: A Collection of software development tools in one installable package 

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

It is a brower-based shell built into the aws management Console 
- aws Cloudshell is scoped per region
- 1 GB storage free per aws region 
- 预装了 很多 tools
- seamlessly switch between Bash Powershell zsh 
- 某些 aws region 不支持 cloudshell
![](image/Pasted%20image%2020230401202831.png)

# 10 Infrastructure as Code (LaC)

Write a configuration script to automate creating, updating or destroying cloud infracture 
AWS CloudFormation and AWS Cloud Development Kit 

![](image/Pasted%20image%2020230401204728.png)

## 10.1 CloudFormation

write infrastructure as Code as a json or yaml file 
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

CDK  allows you to use your favorite programming language to implement the  infrastructure as code

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


# 12 Access Keys (就是 Aws credentials)

- An access key is a key and secret required to have pragmatic access to database resources when interacting with the awps api outside of the aws management console
- Access Keys ist Stored in ~/.aws/credentials 
    - Default profile 以及 其他的profile 
- access keys 通过 aws configure 去设置 


![](image/Pasted%20image%2020230401223017.png)

![](image/Pasted%20image%2020230401223335.png)



## 12.1 Access Keys 例子

iam 中的 user 的 access key 
![](image/Pasted%20image%2020230401223446.png)


# 13 AWS Documentation

![](image/Pasted%20image%2020230401223658.png)


