# Amazon EKS

## What is it?

- EKS stands for **Elastic Kubernetes Service**.
- It is a managed Kubernetes service provided by AWS.
- It is used to run and manage containerized applications.
- AWS manages the Kubernetes control plane.

## Why use it?

- Run Docker containers using Kubernetes.
- Automatically scale applications.
- Provide high availability.
- Reduce Kubernetes control-plane management.
- Integrates with AWS services such as IAM, VPC, and CloudWatch.

## Key concepts

- **Cluster** - The Kubernetes environment.
- **Node** - A machine that runs application pods.
- **Pod** - The smallest deployable unit in Kubernetes.
- **Deployment** - Manages and updates pods.
- **Service** - Provides network access to pods.
- **Namespace** - Separates resources within a cluster.

## Important features

- Managed Kubernetes control plane
- Automatic scaling
- High availability
- IAM integration
- Load Balancer integration
- CloudWatch monitoring
- Supports EC2 and serverless **Fargate** workloads

## Real-world example

A company has a Node.js application running in Docker containers.

```text
User
 |
Load Balancer
 |
EKS Cluster
 |
Pods
 |
Docker Containers
 |
Node.js Application