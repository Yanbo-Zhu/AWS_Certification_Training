
# 1 

![](image/Pasted%20image%2020231003144657.png)


![](image/Pasted%20image%2020231003150041.png)

![](image/Pasted%20image%2020231023123505.png)

Imagine that your chief technology officer meets with you to discuss how to automate deployments and operations in the cloud. Here are some questions that they are asking.
At the end of this module, you meet with the chief technology officer and present some solutions

# 2 AWS CloudFormation overview

The chief technology officer asks, “How can we simplify our cloud infrastructure build?”
The infrastructure team would like to create environments that can be deployed, updated, and taken down in an uncomplicated way. The company wants you to identify tools that automate infrastructure deployment.


![](image/Pasted%20image%2020231003144912.png)


You can simplify the deployment of your Amazon Web Services (AWS) resources by using infrastructure as code (IaC). With IaC, you use code to define, deploy, configure, update, and remove infrastructure.
A template is a text file that describes and defines the resources to be deployed in your environment. This template is then processed by an engine that provisions the specified resources.
• Define an entire application stack (all resources required for your application) in a JSON or YAML template file. Treat the template as code and manage it using a version control system.
• Define runtime parameters for a template, such as the Amazon Elastic Compute Cloud (Amazon EC2) instance size, and Amazon EC2 key pair.
• The IaC solution provisions the resources that are defined in the template.

IaC has the following benefits: • Speed and safety – Your infrastructure is built programmatically, which makes it faster than manual deployment and makes errors less likely.
• Reusability – You can organize your infrastructure into reusable modules. 
• Documentation and version control – Your templates document your deployed resources, and version control provides a history of your infrastructure over time. You can also roll back to a previous working version of your infrastructure in the event of error.
• Validation – You perform code review on your templates, which decreases the chances of errors.

Learn more about creating a continuous integration and delivery (CI/CD) pipeline in the AWS Cloud. For more information, see “Complete CI/CD with AWS CodeCommit, AWS CodeBuild, AWS CodeDeploy, and AWS CodePipeline” in the AWS DevOps Blog at https://aws.amazon.com/blogs/devops/complete-ci-cd-with-aws-codecommit-aws-codebuild-aws-codedeploy-and-aws-codepipeline/.



---


![](image/Pasted%20image%2020231003145107.png)

一旦有变化, 通过 drift 改变 LaC Solution 


--- 

![](image/Pasted%20image%2020231003145251.png)

If you build infrastructure with code, you gain the benefits of repeatability and reusability while building your environments. Build the same complex environments with one template, or a combination of templates. This example uses the architecture template to create identical resources in different AWS Regions. One is the development environment, and the other is the production environment.
For builds to match a specific context, create environments dependent on conditions. For example, a template can be designed so that different Amazon Machine Images (AMIs) are used in the development or the production environments.


---

![](image/Pasted%20image%2020231023131215.png)


In this scenario, the template has been updated to add new security groups to the instance stacks.
With one change to the template that is used to launch these environments, all environments add the new security group resource.
This feature makes resource maintenance less complicated, provides consistency, and reduces effort through parallelization.

# 3 AWS CloudFormation

![](image/Pasted%20image%2020231003145427.png)

as result ist a stack (one Unit of resource 
CloudFormation translate the template and call the api to deploy the infrasture

Essentially, CloudFormation is an API wrapper. When you create an EC2 instance in the AWS Management Console, you initiate an API call to the Amazon EC2 service. The information that you enter through the wizard is passed on as parameters.
CloudFormation uses those APIs. The resources that you define in your CloudFormation template become API calls to AWS services, just like in the AWS Management Console. CloudFormation manages the dependencies and relationships.
Author your CloudFormation template with any code editor and then check it in to a version control system such as GitHub or CodeCommit. Review files before deploying.
CloudFormation is available in all AWS Regions, and you pay for only the resources that you use


---

![](image/Pasted%20image%2020231023131322.png)

Additional points for a CloudFormation template are as follows: 
• You can manage it by using your choice of version control — for example, Git or Subversion (SVN). 
• Define an entire application stack (all resources that your application requires) in a JSON template file. 
• Define runtime parameters for a template (EC2 instance size, Amazon EC2 key pair, and others). 
• If you created an AWS resource outside CloudFormation management, you can bring this existing resource into CloudFormation management by using resource import.

YAML formatted CloudFormation templates follow the same anatomy as existing JSON formatted templates and support all the same features.



---

![](image/Pasted%20image%2020231003145632.png)


cross-stack:  that stack 
- From that stack I may reference output of other stacks into a new stack


All resources in a stack are defined by the stack’s CloudFormation template. You can manage a collection of resources by creating, updating, or deleting stacks. For example, a stack can include all resources that are required to run a web application, including a web server, database, and networking rules. If you no longer require that web application, you can delete the stack, which deletes all of its related resources.
CloudFormation treats the stack resources as a single unit. They must all be created or deleted successfully for the stack to be created or deleted. If a resource can't be created, CloudFormation rolls the stack back and deletes any resources that were created. If a resource can't be deleted, CloudFormation retains any remaining resources until the entire stack can be successfully deleted.
When you must make changes to a stack's settings or change its resources, you update the stack instead of deleting it and creating a new stack. To change a running stack, submit the changes that you want to make by providing a modified template, new input parameter values, or both. CloudFormation generates a change set by comparing your stack with the changes that you submitted.
You can create cross-stack references so that you can share outputs from one stack with another stack.
For more information about cross-stack references, see "Walkthrough: Refer to resource outputs in another AWS CloudFormation stack" in the AWS CloudFormation User Guide at https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/walkthrough-crossstackref.html.



---


![](image/Pasted%20image%2020231003145908.png)



---

![](image/Pasted%20image%2020231003145916.png)

A layered architecture organizes stacks into multiple horizontal layers that build on top of one another. Each layer has a dependency on the layer directly under it. You can have one or more stacks in each layer, but within each layer, your stacks should have AWS resources with similar lifecycles and ownership.
For more information about a layered architecture, see "AWS CloudFormation best practices" in the AWS CloudFormation User Guide at https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html.

--- 


![](image/Pasted%20image%2020231003150006.png)



# 4 Infrastructure management 

![](image/Pasted%20image%2020231003150124.png)

The chief technology officer asks, “How can we deploy, maintain, and scale applications in the cloud?”
The operations team is looking for tools that can automate the deployment of infrastructure and help them manage resources after they are deployed.


![](image/Pasted%20image%2020231003150222.png)

![](image/Pasted%20image%2020231003150424.png)

Elastic Beanstalk: 
The concept is similar to Lambda, but it is server based, not serverless

AWS CDK:  
user 写成 python 语言, 然后 会翻译成 aws cloudformation 


When choosing infrastructure deployment tools, you must find a balance between convenience and control. Some tools give you complete control and have you choose every component and configuration. Though you can customize your deployment to fit your business needs, this method requires greater expertise and more resources to manage and maintain. Other tools are designed for convenience and include preconfigured infrastructure templates for common solutions. Though these tools are less complicated to use and require less maintenance, you do not always have the ability to customize your infrastructure components. You can automate your infrastructure deployments by using the following tools:
• AWS Elastic Beanstalk – Elastic Beanstalk integrates with developer tools and provides a one-stop experience to manage the application lifecycle. Elastic Beanstalk provisions and manages application infrastructure to support your application.
• AWS Solutions Library – AWS Solutions Library carries solutions that AWS and AWS Partners have built for a broad range of industry and technology use cases. These solutions include the tools that you need to get started quickly, such as CloudFormation templates, scripts, and reference architectures.
• AWS Cloud Development Kit (AWS CDK) – AWS CDK is an open-source software development framework to model and provision your application resources by using common programming languages. AWS CDK simplifies the creation and deployment of CloudFormation templates. It offers infrastructure components and groups of components that are preconfigured according to best practices. However, you can still customize your components and their settings.
• AWS CloudFormation – With CloudFormation, you define every resource and its configuration. You have granular control over every component of your infrastructure.
With AWS Systems Manager, you can view and control your infrastructure on AWS. You can automate or schedule a variety of maintenance and deployment tasks.




# 5 AWS Elastic Beankstalk 


![](image/Pasted%20image%2020231003150518.png)

The goal of Elastic Beanstalk is to help developers deploy and maintain scalable web applications and services in the cloud without worrying about underlying infrastructure. Elastic Beanstalk configures each EC2 instance in your environment with the components necessary to run applications for the selected application type. You don’t need to worry about logging into instances to install and configure your application stack. With Elastic Beanstalk, you can provision infrastructure to support common application designs, such as web applications and worker services.



![](image/Pasted%20image%2020231003150630.png)

![](image/Pasted%20image%2020231003150742.png)

左边是 前面, 右边是 后端 

# 6 其他 

![](image/Pasted%20image%2020231003150859.png)

AWS Solutions Library helps you solve common problems and build faster by using AWS. Solutions are vetted by AWS architects and are designed to be operationally effective, reliable, secure, and cost efficient. Many AWS solutions come with prebuilt CloudFormation templates. They can also include a detailed architecture, a deployment guide, and instructions for automated and manual deployment. You will be charged for the resources that you use to create and run this environment.
For more information, see “AWS Solutions Library” at https://aws.amazon.com/solutions/


---


![](image/Pasted%20image%2020231003150927.png)

AWS CDK is a software development framework that defines your cloud application resources by using a declarative model and familiar programming languages. AWS CDK includes a library of customizable constructs, which are building blocks that consist of one or more resources and include common configurations. You can use AWS CDK to generate CloudFormation templates and deploy your infrastructure along with your application runtime assets.
You can use AWS CDK with common programming languages such as Python, JavaScript, TypeScript, Java, or C


--- 

![](image/Pasted%20image%2020231003151045.png)
agent 安装在 xx 上. ssm 去管理它

aws systemer manager : It does require an agent on the managed resources on premises


When designing infrastructure, you must plan for its management. This planning affects your infrastructure deployments because you must grant the correct security policies to your management tools. You might also need to install management agents on your instances.
AWS Systems Manager provides a central place to view and manage your AWS resources, so you can have complete visibility and control over your operations.
With Systems Manager, you can: 
• Create logical groups of resources such as applications, different layers of an application stack, or development and production environments.
• Select a resource group and view its recent API activity, resource configuration changes, related notifications, operational alerts, software inventory, and patch compliance status.
• Take action on each resource group depending on your operational needs.
• Centralize operational data from multiple AWS services and automate tasks across your AWS resources.

You can open Systems Manager from the Amazon EC2 console. You select the instances that you want to manage and define the management tasks that you want to perform. Systems Manager is available at no cost to manage your Amazon EC2 and on-premises resources.
For more information about Systems Manager, see “What is AWS Systems Manager?” in the AWS Systems Manager User Guide at https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html

# 7 Amazon CodeWhisperer 

![](image/Pasted%20image%2020231003151136.png)

Amazon CodeWhisperer provides artificial intelligence (AI) powered code suggestions in your IDE for multiple programming languages. You can use CodeWhisperer to write the code needed to deploy and manage your infrastructure. CodeWhisperer suggestions are optimized for AWS APIs and work with AWS SDKs and AWS CDK



![](image/Pasted%20image%2020231003151217.png)


Amazon CodeWhisperer analyzes your comments and code as you write them in your integrated development environment (IDE). It goes beyond code completion by using natural language processing to comprehend the comments in your code. By understanding English comments, CodeWhisperer generates complete functions and code blocks that align with your descriptions. CodeWhisperer also analyzes the surrounding code, ensuring the generated code matches your style and naming conventions and seamlessly integrates into the existing context.

When scanning for security vulnerabilities, CodeWhisperer assesses your code against multiple sets of standards and best practices. This includes the following: 
• Open Worldwide Application Security Project (OWASP) standards 
• Crypto library best practices
• AWS security standards

The security scan feature is continuously updated to help keep applications free from new security vulnerabilities.
Compatibility – CodeWhisperer integrates with popular tools such as Visual Studio Code, JetBrains IDEs (IntelliJ IDEA, PyCharm, etc.), Amazon SageMaker Studio, JupyterLab, AWS Cloud9, and AWS Lambda console. Support – CodeWhisperer supports a wide range of programming languages and development environments, including Python, Java, JavaScript, TypeScript, C#, Go, Rust, PHP, Ruby, Kotlin, C, C++, Shell scripting, structured query language (SQL), and Scala. Installation – You can access CodeWhisperer by downloading and installing the AWS Toolkit IDE extension/plugin. You can also activate CodeWhisperer from directly within the AWS Lambda and AWS Cloud9 console code editors.
Installation instructions vary depending on the environment. For more information, see “Getting started” in the CodeWhisperer User Guide at https://docs.aws.amazon.com/codewhisperer/latest/userguide/getting-started.html




![](image/Pasted%20image%2020231003151257.png)

The code generation feature of CodeWhisperer offers code suggestions in real time in your development environment. It automatically offers code completion and code generation suggestions. It uses natural language processing of English comments in your code and an understanding of surrounding code to suggest whole lines of code, complete functions, and logical blocks of code. The generated code is aligned with your coding style and naming conventions. CodeWhisperer prioritizes secure coding and responsible artificial intelligence (responsible AI) practices. It is optimized for Amazon APIs and trained extensively on Amazon and open-source code. You have the option to accept the first suggestion, explore more suggestions, or continue writing your own code. It is important to review each code suggestion before accepting it, because you might need to make edits to ensure the suggestion aligns with your intended functionality.

User actions 
• Previous and next suggestion: Use the left arrow and right arrow. 
- Accept a suggestion: Press Tab.
• Reject a suggestion: Press Esc.
• Manually trigger code generation when typing a comment: On MacOS, press Option+C, and on Windows, press Alt+C.

Open Code Reference Log 
CodeWhisperer learns from open-source projects and the code it suggests might occasionally resemble code samples from the training data. With the reference log, you can view references to code suggestions that are similar to the training data. When such occurrences happen, CodeWhisperer notifies you and provides repository and licensing information. Use this information to make decisions about whether to use the code in your project and properly attribute the source code as desired.






![](image/Pasted%20image%2020231003151340.png)

The security scanning feature of CodeWhisperer detects security vulnerabilities in both code generated by CodeWhisperer and code written by developers. It scans the code to identify potential vulnerabilities and provides suggestions for remediation. This includes scanning for hard-to-find vulnerabilities that might be overlooked. The security scan is compatible with popular IDEs such as VS Code and JetBrains. It supports Python, Java, and JavaScript


--- 


![](image/Pasted%20image%2020231003151405.png)

Automated code generation automates repetitive tasks and saves you time. It eliminates the need for you to invest excessive hours in exploring and learning new technologies. Instead, you can rely on high-quality code suggestions that match your coding style. This approach enhances your productivity so you can focus on critical tasks, which encourages innovation and progress in software development. With automated code generation, you can streamline your workflows and achieve significant time savings while ensuring the delivery of code that meets your standards.

CodeWhisperer code generation offers many benefits for software development organizations. It accelerates application development for faster delivery of software solutions. By automating repetitive tasks, it optimizes the use of developer time, so developers can focus on more critical aspects of the project. Additionally, code generation helps mitigate security vulnerabilities, safeguarding the integrity of the codebase.

CodeWhisperer also protects open source intellectual property by providing the open source reference tracker. CodeWhisperer enhances code quality and reliability, leading to robust and efficient applications. It also supports an efficient response to evolving software threats, keeping the codebase up to date with the latest security practices. CodeWhisperer has the potential to increase development speed, security, and the quality of software.

Resources: 
• “Getting started” at https://aws.amazon.com/codewhisperer/resources/ 
• Dive deep with the “Amazon CodeWhisperer – Getting Started” course on AWS Skill Builder at https://explore.skillbuilder.aws/learn/course/external/view/elearning/16405/amazon-codewhisperer-getting-started
• Learn how to build an event-driven serverless app at https://catalog.us-east-1.prod.workshops.aws/workshops/a33a5d69-1417-4d5f-acc9-ae5c7fba665b/en-US/


Cost oaf CodeWhisperer

看你需要什么功能 

# 8 Review 

![](image/Pasted%20image%2020231023132529.png)

Imagine that you are now ready to talk to the chief technology officer and present solutions that meet their architectural needs.
Think about how you would answer the questions from the beginning of the lesson.
Your answers should include the following solutions: • You can use AWS CloudFormation to simplify your infrastructure with an infrastructure as code (IaC) approach.
• You can deploy and maintain your infrastructure by using AWS CDK, solutions from the AWS Solutions Library, and AWS Elastic Beanstalk. You can use AWS Systems Manager to automate infrastructure management.



![](image/Pasted%20image%2020231003151602.png)




# 9 Knowledge Check

a
![](image/Pasted%20image%2020231003151613.png)

The correct answer is A, all of the provisioned resources that are defined in a CloudFormation template.
A stack is a collection of AWS resources that a CloudFormation template generates, and it is managed as a single unit



-----

a 
c

![](image/Pasted%20image%2020231003151639.png)

![](image/Pasted%20image%2020231003151721.png)


The correct answers are A and C, developers can use common programming languages and developers can call preconfigured resources with proven defaults.
AWS CDK is a software development framework that you can use to define your cloud application resources. It can be used with familiar programming languages such as TypeScript, Python, Java, and .NET. AWS CDK offers different cloud components that include configuration detail, boilerplate, and glue logic for using one or multiple AWS services.
For more information about the features of AWS CDK, see “AWS Cloud Development Kit features” at https://aws.amazon.com/cdk/features/.














