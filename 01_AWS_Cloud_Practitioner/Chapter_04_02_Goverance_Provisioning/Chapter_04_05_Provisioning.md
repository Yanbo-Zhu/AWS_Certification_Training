
# 1 Provisioning Services
9:44:37 Provisioning Services

`Provisioning` is the allocation or creation of resources and services to a customer. ​ AWS Provisioning Services is responsible for setting up and then managing those AWS Services

**Types of Services:**

![](image/Pasted%20image%2020230520203722.png)

-   [**Elastic Beanstalk**](https://aws.amazon.com/elasticbeanstalk/?nc2=type_a) 
    - an easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and Internet Information Services (IIS).
    - EB will provision various AWS services, including EC2 S3, Simple Notification Sercvice (SNS), Cloudwatch, EC2 AutoScaling groups, and Elastic load balancers 
    - euqivalent Heroku 
-   [**OpWorks**](https://aws.amazon.com/opsworks/)
    - configuration management service 
    - provides managed instances of **Chef** and **Puppet**
-   [**CloudFormation**](https://aws.amazon.com/cloudformation/?nc2=type_a) 
    - lets you deploy your cloud resources using infrastructure-as-code with **JSON** and **YAML** templates
    - is known as Infrasturcture as Code (IaC)
-   [**AWS Partner Solutions**](https://aws.amazon.com/quickstart/?quickstart-all.sort-by=item.additionalFields.updateDate&quickstart-all.sort-order=desc) (formerly AWS QuickStarts) 
    - pre-made packages that can launch and configure your AWS compute, network, storage, and other services required to deploy a workload on AWS 
-   [**AWS Marketplace**](https://aws.amazon.com/marketplace) 
    - a digital catalogue containing **thousands** of software listings from independent software vendors you can use to find, buy, test, and deploy software.
-   [**AWS Amplify**](https://docs.aws.amazon.com/amplify/) 
    - is a mobile and web application framework, that will provision multiple AWS services as your backend.​
-   [**AWS App Runner**](https://aws.amazon.com/apprunner/) (for container )
    - a fully managed service that makes it easy for developers to quickly deploy containerized web applications and APIs, at scale and with no prior infrastructure experience required.
-   [**AWS Copilot**](https://aws.amazon.com/containers/copilot/) (for container)
    - AWS Copilot is a command-line interface (CLI) that enables customers to quickly launch and easily manage containerized applications on AWS
-   [**AWS CodeStar**](https://aws.amazon.com/codestar/) 
    - provides a unified user interface, enabling you to easily manage your software development activities in one place. Easily launch common types of stacks eg LAMP
-   [**AWS Cloud Development Kit (CDK)**](https://aws.amazon.com/cdk/) 
    - an Infrastructure as Code (IaC) tool. Allows you to use your favourite programming language. Generates out CloudFormation templates as the means for IaC

# 2 AWS Elastic Beanstalk

9:47:21 AWS Elastic Beanstalk

**What is Platform as a Service? (PaaS)**
- a PaaS allows customers to develop, run, and manage applications without the complexity of building and maintaining the infrastructure typically associated with developing and launching an app

**Elastic Beanstalk** 
- is a PaaS for deploying web applications with little-to-no knowledge of the underlying infrastructure so you can focus on writing application code instead of setting up an automated deployment pipeline and DevOps tasks.
- Choose a platform, upload your code and it runs with little knowledge of the infrastructure.
- Not Recommended for **“Production”** applications (large Production companies )
    - AWS is talking about enterprises, large companies.

Elastic Beanstalk is powered by a CloudFormation template and **setups** for you:
-   Elastic Load Balancer
-   Autoscaling Groups
-   RDS Database
-   EC2 Instance preconfigured (or custom ) platforms
-   Monitoring (CloudWatch, SNS)
-   In-Place and Blue/Green deployment methodologies
-   Security (Rotates passwords)
-   Can run **Dockerized** environments

![](image/Pasted%20image%2020230520204303.png)

Reference

[AWS OpWorks](https://aws.amazon.com/opsworks/)
[AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/)
[AWS CloudFormation](https://aws.amazon.com/cloudformation/)
[AWS AppSync](https://aws.amazon.com/appsync/)
[Amplify Framework Documentation](https://aws-amplify.github.io/)
[AWS Quick Starts](https://aws.amazon.com/quickstart/)


# 3 AWS Elastic Beanstalk Follow Along
9 :48:52 AWS Elastic Beanstalk Follow Along

## 3.1 创造一个 environment per Elastic Beanstalk 
在创建一个新的  environment per Elastic Beanstalk , 就要去选择好很多东西, 比如 load balancer, database, 如果你需要的话 

![](image/Pasted%20image%2020230520205854.png)


Myapp-env 自己刚才新造的 env
![](image/Pasted%20image%2020230520210339.png)

这个 env 的 log
![](image/Pasted%20image%2020230520210435.png)

这 env 的 monitoring
![](image/Pasted%20image%2020230520210454.png)

这个 env 的 sample application
![](image/Pasted%20image%2020230520210613.png)

![](image/Pasted%20image%2020230520210624.png)

## 3.2 创造一个新的 Development environment per Cloud9 这个 aws service , 用它来 去编辑 sample application 中的code 

就是早出一个 类似于 IDE 的环境 

![](image/Pasted%20image%2020230520210855.png)

![](image/Pasted%20image%2020230520211115.png)


![](image/Pasted%20image%2020230520211258.png)

把整理好的 code , zip into a achrive file 
然后把这个 archive file 上床到 通过 elastick beanstalk 新造的 env 中  作为 新的 sample application 的源代码 
![](image/Pasted%20image%2020230520211637.png)



## 3.3 上传新的 zip file 到 作为新的 sample application 的代码

可以到新 这个  zip file 到 作为新的 sample application 的代码 所生成的 webseite 上有写, 这是 second aws elastic beanstalk Ruby application. 


![](image/Pasted%20image%2020230520211824.png)
