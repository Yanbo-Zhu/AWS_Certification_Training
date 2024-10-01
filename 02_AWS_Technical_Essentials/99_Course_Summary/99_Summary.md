
![](image/Pasted%20image%2020231013144153.png)

In this course, you explored:
• Amazon Web Services, AWS security, and IAM
• AWS virtual servers, containers, and serverless computing 
• AWS private networks, public networks, and secure network traffic 
• AWS block, file, and object storage options 
• AWS SQL and NoSQL database services 
• AWS resource monitoring, load balancing, and scaling

![](image/Pasted%20image%2020231013144222.png)

Architecture diagram of Final Employee Directory application from hands-on lab. Refer to slide notes for information.
In the hands-on labs, you completed a number of tasks.
You launched:
• Amazon Virtual Private Cloud (Amazon VPC), with two Availability Zones and two public subnets (one in each AZ)
• Amazon Elastic Compute Cloud (Amazon EC2) instances in each subnet and configured a security group for each instance
• Employee Directory application in the EC2 instances

You created: 
• Amazon Simple Storage Service (Amazon S3) bucket to store employee photos for the Employee Directory application
• Amazon DynamoDB employee data table for the Employee Directory application

You added: 
• Application Load Balancer 
• Auto Scaling group



![](image/Pasted%20image%2020231013144327.png)

To modernize the Employee Directory application, you can use a 100 percent serverless solution by making a few adjustments. These adjustments are explained in the notes.

To modernize the Employee Directory application, you can use a 100 percent serverless solution by making a few adjustments.
• Use Amazon S3 buckets to store the employee photos and the static Employee Directory application website files (HTML, CSS, and JavaScript)
• Use Amazon DynamoDB tables for the employee data • Use AWS Lambda functions to create, retrieve, update, and delete employee data from S3 buckets and Amazon DynamoDB
• Connect to the S3 bucket hosting the Employee Directory application’s static website through Amazon Route 53 and Amazon CloudFront
• Make API calls to the AWS Lambda functions through the Amazon API Gateway • Use AWS SDKs to develop a mobile front end for the Employee Directory application • Use Amazon Cognito to add web or mobile authentication


Resource
To learn more about Amazon Route 53, Amazon CloudFront, AWS SDKs, and Amazon Cognito, visit the AWS documentation: https://docs.aws.amazon.com


![](image/Pasted%20image%2020231013144405.png)

Dive deep and learn about additional services, techniques, and design patterns:
• Architecting on AWS: Learn more about the fundamentals of building IT infrastructure in AWS Cloud using best practices and design patterns.
• Cloud operations on AWS: Learn more about installing, configuring, automating, monitoring, securing, maintaining, and troubleshooting the AWS services, networks, and systems that support business applications.
• Developing on AWS: Learn more about service authentication, how to use AWS SDKs, and how to use AI coding companion such as Amazon CodeWhisperer to develop scalable cloud applications faster and more securely.

Whatever role you are preparing for, it may be beneficial to take advantage of AWS CodeWhisperer to help in the creation of application and infrastructure code on AWS. The next two slides will discuss this tool briefly. Follow the links in those slides if you want to learn more.
Resource To find out more, see https://aws.amazon.com/training/learn-about/






![](image/Pasted%20image%2020231013144446.png)

Amazon CodeWhisperer analyzes your comments and code as you write them in your integrated development environment (IDE). It goes beyond code completion by using natural language processing to comprehend the comments in your code. By understanding English comments, CodeWhisperer generates complete functions and code blocks that align with your descriptions. CodeWhisperer also analyzes the surrounding code, ensuring the generated code matches your style and naming conventions and seamlessly integrates into the existing context.

When scanning for security vulnerabilities, CodeWhisperer assesses your code against multiple sets of standards and best practices. This includes the following: 
• Open Worldwide Application Security Project (OWASP) standards 
• Crypto library best practices 
• AWS security standards

The security scan feature is continuously updated to help keep applications free from new security vulnerabilities.
- Compatibility – CodeWhisperer integrates with popular tools such as Visual Studio Code, JetBrains IDEs (IntelliJ IDEA, PyCharm, etc.), Amazon SageMaker Studio, JupyterLab, AWS Cloud9, and AWS Lambda console. 
- Support – CodeWhisperer supports a wide range of programming languages and development environments, including Python, Java, JavaScript, TypeScript, C#, Go, Rust, PHP, Ruby, Kotlin, C, C++, Shell scripting, structured query language (SQL), and Scala.
- Installation – You can access CodeWhisperer by downloading and installing the AWS Toolkit IDE extension/plugin. You can also activate CodeWhisperer from directly within the AWS Lambda and AWS Cloud9 console code editors.

Installation instructions vary depending on the environment. For more information, see “Getting started” in the CodeWhisperer User Guide at https://docs.aws.amazon.com/codewhisperer/latest/userguide/getting-started.htm




![](image/Pasted%20image%2020231013144647.png)


Automated code generation automates repetitive tasks and saves you time. It eliminates the need for you to invest excessive hours in exploring and learning new technologies. Instead, you can rely on high-quality code suggestions that match your coding style. This approach enhances your productivity so you can focus on critical tasks, which encourages innovation and progress in software development. With automated code generation, you can streamline your workflows and achieve significant time savings while ensuring the delivery of code that meets your standards.

CodeWhisperer code generation offers many benefits for software development organizations. It accelerates application development for faster delivery of software solutions. By automating repetitive tasks, it optimizes the use of developer time, so developers can focus on more critical aspects of the project. Additionally, code generation helps mitigate security vulnerabilities, safeguarding the integrity of the codebase.

CodeWhisperer also protects open source intellectual property by providing the open source reference tracker. CodeWhisperer enhances code quality and reliability, leading to robust and efficient applications. And it supports an efficient response to evolving software threats, keeping the codebase up to date with the latest security practices. CodeWhisperer has the potential to increase development speed, security, and the quality of software.


Resource: 
• “Getting started” at https://aws.amazon.com/codewhisperer/resources/ 
• Dive deep with the “Amazon CodeWhisperer – Getting Started” course on AWS Skill Builder at https://explore.skillbuilder.aws/learn/course/external/view/elearning/16405/amaz on-codewhisperer-getting-started
• Learn how to build an event-driven serverless app at https://catalog.us-east-1.prod.workshops.aws/workshops/a33a5d69-1417-4d5f-acc9-ae5c7fba665b/en-US/



![](image/Pasted%20image%2020231013144756.png)

AWS Certification helps learners to build credibility and confidence by validating their cloud expertise with an industry-recognized credential. Certification helps organizations to identify skilled professionals who can lead cloud initiatives by using Amazon Web Services (AWS).

The slide shows the AWS certifications that are currently available. To earn an AWS certification, you must earn a passing score on a proctored exam. Each certification level for role-based certifications provides a recommended experience level with AWS Cloud services as follows: • Professional – Two years of comprehensive experience designing, operating, and troubleshooting solutions by using the AWS Cloud
• Associate – One year of experience solving problems and implementing solutions by using the AWS Cloud
• Foundational – Six months of fundamental AWS Cloud and industry knowledge

Specialty certifications focus on a particular technical domain. The recommended experience for taking a specialty exam is technical experience in the domain as specified in the exam guide.

AWS does not publish a list of all services or features that are covered in a certification exam. However, the exam guide for each exam lists the current topic areas and objectives that the exam covers. For more information, the exam guides and other preparation materials are available on the AWS Certification exam preparation page at https://aws.amazon.com/certification/certification-prep/.

The information on this slide is current as of March 2023. However, exams are frequently updated, and the details regarding which exams are available—and what is tested by each exam—are subject to change. For more information about the latest AWS certification exam information, see the AWS Certification page at https://aws.amazon.com/certification/.
You are required to update your certification (or recertify) every 3 years. For more information, see the AWS Recertification page at https://aws.amazon.com/certification/recertification/.





![](image/Pasted%20image%2020231013144842.png)


This course includes content that might be related to an AWS Certification exam. To continue preparing for the exam, follow these core 4 steps.
For more information about each exam, you can scan the QR code to see “Explore AWS Certification exams” at https://aws.amazon.com/certification/exams/

![](image/Pasted%20image%2020231013144906.png)

Step one is getting to know the exam and exam-style questions.
You can review the exam guide for each exam by exploring the AWS Certification Exams page. For more information, see Explore all AWS Certification exams at https://aws.amazon.com/certification/exams/.
For sample exam questions, you can sign up on AWS Skill Builder. Within Skill builder, you can enroll in an Official Practice Question Set. For more information, see AWS Skill Builder: Your learning center to build in-demand cloud skills at https://explore.skillbuilder.aws/learn.
The questions in the practice sets are created by following the same process as questions that you will see on the actual AWS Certification exams. They include detailed feedback and recommended resources to help you prepare for your exam.


![](image/Pasted%20image%2020231013144910.png)

Step two is brushing up on exam topics.
In addition to the reviewing the exam guide and enrolling in self-paced courses on AWS Skill Builder, you can explore AWS Builder Labs to get hands-on experience with AWS.
For more information, see AWS Builder Labs: Learn cloud skills in a live AWS environment at https://aws.amazon.com/training/digital/aws-builder-labs/.

![](image/Pasted%20image%2020231013144931.png)

Next, you can take exam preparation courses in AWS Skill Builder.
Skill Builder also offers many resources that you can use to address any gaps in your knowledge that you discover. 
1. Skill Builder offers courses across all domains. 
2. There also are more than 150 self-paced labs. 
3. Finally, if you’d like to gain hands-on experience with AWS services by playing an actual game, try AWS Cloud Quest.
Note: Some of these resources require a digital subscript



![](image/Pasted%20image%2020231013144957.png)


Finally, determine your exam readiness by taking an official practice exam.
Each practice exam includes the same number of questions as the actual exam. The practice exams provide practice with the same question style, depth, and rigor as the certification exam. They include exam-style scoring and a pass or fail. You’ll also receive feedback on the answer choices for each question with recommended resources to deepen your understanding of key topics. You can determine whether you want to simulate the exam experience by taking a timed exam with answers only shown at the end. Or you can choose other options, like untimed, or with answers shown after submitting each question




![](image/Pasted%20image%2020231013145046.png)

AWS offers flexible, convenient options for taking exams. Explore the Schedule an Exam page to choose the exam option that works best for you. For more information, see Schedule an Exam: Find the testing option that works best for you at https://aws.amazon.com/certification/certification-prep/testing/



![](image/Pasted%20image%2020231013145101.png)

Continue your learning with AWS Skill Builder, our online learning center.
Are you ready to achieve your goals at your pace? Free digital training on AWS Skill Builder offers more than 500 on-demand courses and learning plans so you can build the skills that you need, your way.
Want to build problem-solving cloud skills in an interactive, engaging experience? A Skill Builder subscription offers access to self-paced labs, practice exams, role-based games, and real-world challenges to accelerate your learning.
For more information about how to learn more and get started, see AWS Skill Builder at https://aws.amazon.com/training/digital.

![](image/Pasted%20image%2020231013145118.png)

AWS Training and Certification is an organization dedicated to expanding and deepening knowledge of AWS, and driving proliferation in the use of AWS services. Our programs are designed for customers, AWS Partners, and AWS employees. Over the past several months, we have rolled out several new courses, training labs, and certifications to our customers and partners.
Expand your AWS Cloud skills. For more information, see the following resources: 
• Digital training – https://explore.skillbuilder.aws/ 
• Classroom training – https://aws.amazon.com/training 
• AWS Certification – https://aws.amazon.com/certification 
• AWS Workshops – https://workshops.aws/ 
• Tech Talks – https://aws.amazon.com/events/online-tech-talks/on-demand/ 
• AWS Ramp-Up Guides – https://aws.amazon.com/training/ramp-up-guides/





