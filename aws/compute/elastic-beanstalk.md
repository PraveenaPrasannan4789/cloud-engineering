# AWS Elastic Beanstalk

## What is it?

- Elastic Beanstalk is a **managed service for deploying applications**.
- It automatically handles infrastructure such as:
  - EC2
  - Load Balancer
  - Auto Scaling
  - CloudWatch
- You upload your application, and Elastic Beanstalk manages the infrastructure.

## Why use it?

- Easy application deployment
- No need to manually configure EC2 servers
- Automatic scaling
- Built-in load balancing
- Easy monitoring
- Supports multiple programming languages

## Key concepts

- **Application** - Your application in Elastic Beanstalk.
- **Environment** - The infrastructure where your application runs.
- **Application Version** - A specific version of your application code.
- **Environment Configuration** - Settings for the environment, such as instance type and scaling.

## Important features

- Automatic deployment
- Auto Scaling
- Load balancing
- Health monitoring
- Easy application version management
- Supports rolling and immutable deployments
- Supports Docker containers

## Real-world example

A company has a Node.js web application.

```text
Developer
    |
    | Deploy application
    ↓
Elastic Beanstalk
    |
    ├── EC2
    ├── Load Balancer
    ├── Auto Scaling
    └── CloudWatch