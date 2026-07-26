# Amazon ECS (Elastic Container Service)

## What is ECS?

Amazon ECS (Elastic Container Service) is a fully managed AWS service used to run and manage Docker containers.

It helps you deploy, scale, and manage containerized applications without managing the underlying infrastructure.

---

## Why Use ECS?

- Run Docker containers easily
- Automatically scale applications
- Integrates with AWS services
- Secure container management
- Reduces server management work

---

# ECS Main Components

## 1. Cluster

A cluster is a logical group of resources where containers run.

Example:

```
Production Cluster
 |
 |-- Web Application Container
 |-- API Container
 |-- Worker Container
```

---

## 2. Task Definition

A Task Definition is a blueprint that describes how a container should run.

It contains:

- Docker image
- CPU and memory requirements
- Container ports
- Environment variables
- IAM roles

Example:

```json
{
  "family": "my-app",
  "containerDefinitions": [
    {
      "name": "backend",
      "image": "my-app:v1",
      "memory": 512,
      "portMappings": [
        {
          "containerPort": 3000
        }
      ]
    }
  ]
}
```

---

## 3. Task

A Task is a running instance of a Task Definition.

Example:

```
Task Definition
      |
      |
      ↓
Running Task

Node.js API Container
Port: 3000
Memory: 512MB
```

---

## 4. Service

A Service manages how many copies of a task should run.

Example:

```
ECS Service

Desired Tasks: 3

Running:

Task 1  ✓
Task 2  ✓
Task 3  ✓
```

If one task fails, ECS automatically starts a new one.

---

# ECS Launch Types

## 1. ECS on Fargate

Serverless option.

AWS manages:

- Servers
- Operating system
- Infrastructure

Example:

```
User
 |
Application Container
 |
AWS Fargate
 |
AWS Infrastructure
```

Use when:

- You don't want to manage servers
- Need quick deployments

---

## 2. ECS on EC2

You manage EC2 instances.

Example:

```
ECS Cluster

EC2 Instance
 |
 |-- Container 1
 |-- Container 2
 |-- Container 3
```

Use when:

- Need more control
- Have existing EC2 infrastructure

---

# ECS Architecture Example

Running a Node.js API:

```
User
 |
Route 53
 |
Application Load Balancer
 |
ECS Service
 |
-----------------
|               |
Task 1          Task 2
Node API        Node API
 |
RDS Database
```

---

# ECS with Docker Example

Dockerfile:

```dockerfile
FROM node:20

WORKDIR /app

COPY package*.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm","start"]
```

Build image:

```bash
docker build -t my-api .
```

Run locally:

```bash
docker run -p 3000:3000 my-api
```

Push image to Amazon ECR:

```bash
docker push my-api
```

Deploy image using ECS Task Definition.

---

# ECS Auto Scaling

ECS can automatically increase or decrease tasks.

Example:

Normal traffic:

```
2 Tasks
```

High traffic:

```
5 Tasks
```

Low traffic:

```
1 Task
```

Scaling can use:

- CPU usage
- Memory usage
- Request count

---

# ECS Networking

ECS usually runs inside an AWS VPC.

Components:

- VPC
- Subnets
- Security Groups
- Load Balancer

Example:

```
VPC

Public Subnet
 |
Load Balancer

Private Subnet
 |
ECS Containers
 |
RDS Database
```

---

# ECS Monitoring

Uses Amazon CloudWatch.

Monitor:

- CPU usage
- Memory usage
- Container logs
- Task failures

---

# ECS Advantages

- Easy Docker deployment
- Fully managed service
- Supports auto scaling
- Integrates with AWS services
- Secure with IAM

---

# ECS Limitations

- AWS-specific service
- Less portable than Kubernetes
- Requires AWS knowledge

---

# ECS vs EC2

| ECS | EC2 |
|---|---|
| Runs containers | Runs virtual machines |
| AWS manages containers | User manages servers |
| Good for microservices | General purpose computing |
| Supports Docker | Supports any application |

---

# ECS vs Kubernetes

| ECS | Kubernetes |
|---|---|
| AWS managed | Open source |
| Easier to learn | More complex |
| AWS focused | Multi-cloud |
| Less configuration | More flexibility |

---

# Best Practices

- Use Fargate for simple workloads
- Store images in Amazon ECR
- Use IAM roles for tasks
- Use Application Load Balancer
- Enable CloudWatch logging
- Use private subnets for containers
- Configure Auto Scaling
- Keep container images small

---

# Interview Questions

## What is Amazon ECS?

Amazon ECS is a managed AWS service for running and scaling Docker containers.

---

## What is the difference between Task and Service?

Task:
- A single running container instance

Service:
- Maintains the required number of running tasks

---

## What is Fargate?

Fargate is a serverless compute engine for running ECS containers without managing EC2 servers.

---

## What is a Task Definition?

A Task Definition is a configuration file that defines how a container should run.

---

## ECS Real World Example

A company runs an online shopping website:

```
Customer
 |
CloudFront
 |
Application Load Balancer
 |
ECS Fargate
 |
Node.js API Containers
 |
RDS Database
```

ECS automatically creates more containers during high shopping traffic.