# EC2 vs AWS Lambda

## Overview

Both Amazon EC2 and AWS Lambda are compute services used to run applications, but they work differently.

- **EC2** provides virtual servers where you manage the application environment.
- **Lambda** runs your code without managing servers (serverless).

---

# EC2 (Elastic Compute Cloud)

## What is EC2?

EC2 provides virtual machines in AWS where you have full control over:

- Operating system
- Installed software
- Server configuration
- Application deployment

Example:

```
User
 |
Application
 |
EC2 Instance
 |
Operating System
 |
AWS Hardware
```

---

## EC2 Example

Running a Node.js API:

```
EC2 Server

Ubuntu Linux
 |
Node.js
 |
Express API
 |
Application Code
```

You manage:

- Server updates
- Security patches
- Scaling
- Monitoring

---

# AWS Lambda

## What is Lambda?

Lambda is a serverless compute service that runs code only when triggered.

AWS manages:

- Servers
- Operating system
- Infrastructure
- Scaling

Example:

```
User Request
 |
API Gateway
 |
Lambda Function
 |
Database
```

---

## Lambda Example

A user uploads an image:

```
S3 Bucket
 |
Image Upload Event
 |
Lambda Function
 |
Resize Image
 |
Save Result
```

Lambda runs only when the upload happens.

---

# EC2 vs Lambda Comparison

| Feature | EC2 | Lambda |
|---|---|---|
| Type | Virtual Server | Serverless Function |
| Server Management | User manages | AWS manages |
| Running Time | Always running | Runs when triggered |
| Scaling | Manual/Auto Scaling | Automatic |
| Billing | Pay for server uptime | Pay for execution time |
| Startup Time | Faster after running | May have cold start |
| Control | Full control | Limited control |
| Best For | Long-running applications | Event-driven tasks |

---

# When to Use EC2?

Use EC2 when you need:

- Full server control
- Long-running applications
- Custom software installation
- Specific OS configuration
- Traditional web applications

Examples:

- Hosting websites
- Running backend APIs
- Database servers
- Enterprise applications

---

# When to Use Lambda?

Use Lambda when you need:

- Short-running tasks
- Automatic scaling
- Event-driven processing
- Serverless architecture

Examples:

- Image processing
- File processing
- Scheduled jobs
- API backend functions
- Data transformation

---

# Scaling Difference

## EC2 Scaling

You need Auto Scaling Groups.

Example:

```
Normal Traffic

EC2
 |
2 Instances


High Traffic

EC2
 |
10 Instances
```

---

## Lambda Scaling

AWS automatically creates more executions.

Example:

```
1000 Requests

Lambda

Function
Function
Function
Function

Automatically Scaled
```

---

# Cost Comparison

## EC2

You pay while the instance is running.

Example:

```
EC2 Instance Running:

8 hours/day
30 days/month

You pay for allocated resources
```

---

## Lambda

You pay only when code executes.

Example:

```
Function runs:

1000 requests
+
Execution time

You pay for usage
```

---

# Architecture Examples

## EC2 Application

```
Users
 |
Route 53
 |
Load Balancer
 |
EC2 Instances
 |
RDS Database
```

---

## Lambda Application

```
Users
 |
API Gateway
 |
Lambda
 |
DynamoDB
```

---

# Advantages

## EC2 Advantages

- Full control
- Supports any application
- Easy migration from traditional servers
- Custom configurations

## Lambda Advantages

- No server management
- Automatic scaling
- Cost efficient for small workloads
- Fast deployment

---

# Limitations

## EC2 Limitations

- Need server maintenance
- Scaling requires configuration
- Pay even when idle

## Lambda Limitations

- Maximum execution time limit
- Cold start delay
- Limited runtime control
- Not suitable for long-running applications

---

# Interview Questions

## What is the difference between EC2 and Lambda?

EC2 provides virtual servers that users manage, while Lambda runs code without requiring server management.

---

## Is Lambda cheaper than EC2?

It depends on workload.

- For occasional tasks, Lambda is usually cheaper.
- For applications running continuously, EC2 may be more cost-effective.

---

## Can Lambda replace EC2?

Not always.

Lambda is best for event-driven workloads, while EC2 is better for applications requiring full server control.

---

## Real World Example

### E-commerce Website

EC2:

```
Frontend + Backend API
        |
      EC2
        |
       RDS
```

Lambda:

```
Customer uploads image
        |
       S3
        |
     Lambda
        |
 Image Processing
```

---

# Summary

| Choose EC2 | Choose Lambda |
|---|---|
| Need full server control | Want serverless execution |
| Long-running application | Short tasks |
| Custom environment | Event-driven workloads |
| Predictable traffic | Variable traffic |
| Traditional applications | Modern cloud-native applications |