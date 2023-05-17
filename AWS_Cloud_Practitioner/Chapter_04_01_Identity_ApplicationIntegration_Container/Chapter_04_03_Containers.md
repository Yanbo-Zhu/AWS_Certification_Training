
# 1 基础知识 
## 1.1 VMs vs Containers
9:05:22 VMs vs Containers

![](image/Pasted%20image%2020230515174854.png)

VMs do not make the best use of space.
Apps are not isolated which could cause config conflicts, security problems, or resource hogging.
Containers allow you to run multiple apps which are virtually isolated from each other.
Launch new containers and configure OS Dependencies per container.

## 1.2 Microservices
9:07:49 What are Microservices?

- Monolithic Architec ture
    - One app which is responsible for everything 
    - Functionality is tightly coupled
- Microservices Architecture
    - Multiple apps are each responsible for one thing 
    - Functionality is isolated and stateless

![](image/Pasted%20image%2020230515175327.png)

## 1.3 Kuberenetes
9:09:21 Kuberenetes

Kubernetes is an open-source container orchestration system for automating deployment, scaling, and management of containers.
Originally created by Google and now maintained by the Cloud Native Computing Foundation (CNCF)

Kubernetes is commonly called K8s
    The 8 represent the remaining letters “ubernete”

The advantage of Kubernetes over Docker is the ability to run containers distributed across **multiple VMs**
A unique component of Kubernetes are Pods.
A pod is a group of one more containers with shared storage, network resources, and other shared settings.
Kubernetes is ideally for micro-service architectures where a company has tens to hundreds of services they need to manage

![](image/Pasted%20image%2020230515175730.png)

## 1.4 Docker
9:10:41 Docker

[Docker (software)](https://en.wikipedia.org/wiki/Docker_(software))
[Open Container Initiative](https://opencontainers.org/)

**Docker** is a set of Platform as a Service (PaaS) products that use OS-level virtualization to deliver software in packages called containers.
Docker was the earliest popularized open-source container platform.
When people think of containers, they think of Docker.

**Docker CLI** – CLI commands to download, upload, build run and debug containers
**Dockerfile** – a configuration file on how to provision a container
**Docker Compose** – is a tool and configuration file when working with multiple containers
**Docker Swarm** – An orchestration tool for managing deployed multi-containers architectures
**Dockerhub** – a public online repository for containers published by the community for download

**The Open Container Initiative (OCI)** is an open governance structure for creating open industry standards around container formats and runtime. Docker established the OCI and it is now maintained by the Linux Foundation.

Docker has been losing favor with developers due to their handling of introducing a paid open-source model and alternatives like Podman are growing.


## 1.5 Podman, Builddah, Skpeo
9:12:21 Podman

**Podman** is a container engine that is OCI-compliant and is a drop-in replacement for Docker.
-   Podman is daemon-less where Docker uses a container deamon
-   Podman allows you to create pods like K8, Docker does not have pods
-   Podman only replaces one part of Docker. Podman is to be used alongside Buildah and Skopeo

**Buildah** is a tool used to build OCI Images
**Skopeo** is a tool for moving container images between different types of container storages

![](image/Pasted%20image%2020230515180252.png)

# 2 AWS 中Container Services
9:13:23 Container Services

![](image/Pasted%20image%2020230515180929.png)

1 
1. **Primary Services**
    - **Elastic Container Service (ECS)**
        -   No Cold Starts
    -   Self-Managed EC2
- **AWS Fargate**
    -   More Robust Than Lambda
    -   Scale to Zero Cost
    -   AWS-Managed EC2
- **Elastic Kubernetes Services (EKS)**
    -   Open Source
    -   Avoid Vendor Lock-In
- **AWS Lambda**
    -   Only think about code
    -   Short running tasks
    -   Can deploy custom containers
2.  **Provisioning and Deployment**
    - **Elastic Beanstalk (EB)**
        -   ECS on training wheels
        -   Platform as a Service
    - **App Runner**
        - Platform as a Service specifically for containers
    - **AWS Copilot CLI**
        - build, release and operate production-ready containerized applications on AWS App Runner, Amazon ECS, and AWS Fargate
3. **Supporting Services**
    1. **Elastic Container Registry (ECR)**
        1. Repos for your Docker Images
    2. **X-Ray**
    -   Analyze and debug between microservices
    3. **Step Functions**
        -   Stitch together Lambdas and ECS tasks




