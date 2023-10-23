


![](image/Pasted%20image%2020231023154702.png)

The capstone lab is the final project for this course.
During the lab, you are provided with a scenario that discusses a business need. Review the requirements and use what you have learned in this course to complete the list of tasks.




---


![](image/Pasted%20image%2020231004151518.png)


Find the capstone lab in the same place in which you completed labs 1–6.
The capstone lab is organized into the following sections: 
• Lab overview – Introduction to the lab.
• Objectives – Learning objectives of the capstone lab. 
• Start lab – Instructions to begin the lab. 
• Section 1: High-level instructions – The primary instructions for the capstone lab. The instructions have an open-ended structure to attempt to challenge you and assess what you learned in this course.
• Section 2: Detailed instructions – In-depth instructions for each task in the lab. Use the step-by-step instructions to complete that task only if necessary, and then move back to the next task in the high-level instructions.
Use the navigation menu on the right side of the screen to move between sections




![](image/Pasted%20image%2020231004151651.png)




![](image/Pasted%20image%2020231004151852.png)

This is the multi-tier architecture you build in the capstone lab. Review the lab tasks on the next page. Details on each task step are available to you in the lab environment.
**Image description: The diagram shows a single AWS Region with one virtual private cloud (VPC) and two Availability Zones. Each Availability Zone contains a public subnet, an app subnet, and a database subnet. An bi-directional arrow outside the VPC routes through an internet gateway, to an Application Load Balancer. The Application Load Balancer is not in a subnet or an Availability Zone. The arrow continues to the Auto Scaling group that has app servers in the app subnets of both Availability Zones. Each app server communicates with an EFS mount target in its own subnet to reach the EFS file system, which is not inside an Availability Zone. All app servers communicate with an Amazon Aurora primary DB instance in one of the database subnets. The other database subnet holds the Aurora replica. A two-sided arrow points between the Aurora primary and Aurora replica. A bi-directional arrow points from the app servers and travels through each Availability Zone’s NAT gateway. The NAT gateways are in the public subnet of each Availability Zone. The arrows travel through each NAT gateway, and exit the VPC through the internet gateway. End description.



---

![](image/Pasted%20image%2020231023154851.png)

The lab is organized into six tasks. Remember that you can view the more detailed instructions if you need more assistance with a task step.
Begin reading the instructions for the capstone lab and have fun building

--- 

这两个 section 都是一样的 , 只不过 section 1 解释的很抽象. section 2 解释的 比较具体 

Section 1 
only give you the high-level instruction 

section 2
如果你想节省时间 做2 


![](image/Pasted%20image%2020231004151527.png)


endpoint of database 

mydbcluster.cluster-cthvawfj8tqy.us-west-2.rds.amazonaws.com
mydbcluster.cluster-ro-cthvawfj8tqy.us-west-2.rds.amazonaws.com



