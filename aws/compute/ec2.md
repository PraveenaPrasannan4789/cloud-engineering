# Amazon EC2 (Elastic Compute Cloud)

## What is EC2?

Amazon EC2 (Elastic Compute Cloud) is a web service that provides secure, resizable virtual servers (called **instances**) in the AWS Cloud. It allows you to run applications without managing physical hardware.

---

## Why Use EC2?

- Launch virtual machines in minutes
- Scale resources up or down as needed
- Pay only for what you use
- Support a wide range of operating systems
- Full control over the server

---

## Common Use Cases

- Hosting web applications
- Running APIs and backend services
- Database servers
- Development and testing environments
- Batch processing
- Machine learning workloads

---

# EC2 Components

## 1. AMI (Amazon Machine Image)

An AMI is a template used to launch an EC2 instance.

It includes:
- Operating System
- Software packages
- Application code
- Configuration

Examples:

- Amazon Linux
- Ubuntu
- Windows Server
- Red Hat Enterprise Linux

---

## 2. Instance Type

The instance type determines the hardware configuration.

Examples:

| Type | Purpose |
|-------|----------|
| t2.micro | Free Tier, small workloads |
| t3.small | General purpose |
| m5.large | Balanced compute and memory |
| c5.large | Compute optimized |
| r5.large | Memory optimized |
| g4dn.xlarge | GPU workloads |

---

## 3. Key Pair

A key pair is used to securely connect to an EC2 instance.

Consists of:

- Public Key (stored by AWS)
- Private Key (.pem file stored by you)

Linux:

```bash
ssh -i my-key.pem ec2-user@public-ip
```

---

## 4. Security Group

A Security Group acts as a virtual firewall.

It controls:

- Inbound traffic
- Outbound traffic

Example:

| Port | Protocol | Purpose |
|------|----------|----------|
| 22 | SSH | Remote access |
| 80 | HTTP | Website |
| 443 | HTTPS | Secure website |

---

## 5. Elastic IP

An Elastic IP is a static public IPv4 address.

Benefits:

- Remains the same even if the instance stops
- Can be attached to another instance

---

## 6. EBS (Elastic Block Store)

Persistent storage attached to EC2.

Characteristics:

- Data survives instance restart
- Can create snapshots
- High performance SSD/HDD options

Common volume types:

- gp3
- io2
- st1
- sc1

---

## 7. Instance Store

Temporary storage attached to the physical host.

Characteristics:

- Very fast
- Data lost when instance stops or terminates
- Suitable for cache or temporary files

---

# EC2 Lifecycle

```
Launch
   ↓
Pending
   ↓
Running
   ↓
Stopping
   ↓
Stopped
   ↓
Starting
   ↓
Running
   ↓
Terminated
```

---

## Public vs Private IP

### Public IP

- Accessible from the internet
- Changes after stopping/starting (unless Elastic IP)

### Private IP

- Used inside the VPC
- Never changes while the instance exists

---

# Purchasing Options

## On-Demand

- Pay by the hour or second
- No commitment
- Best for short-term workloads

---

## Reserved Instances

- Commit for 1 or 3 years
- Lower cost
- Best for predictable workloads

---

## Spot Instances

- Use unused AWS capacity
- Up to 90% cheaper
- Can be interrupted by AWS

Best for:

- Batch jobs
- Testing
- Big data

---

## Dedicated Hosts

Physical server dedicated to one customer.

Used when:

- License compliance
- Regulatory requirements

---

# Auto Scaling

Automatically adjusts the number of EC2 instances.

Benefits:

- High availability
- Cost optimization
- Handles traffic spikes

Example:

Minimum: 2

Desired: 3

Maximum: 8

---

# Load Balancer

Distributes traffic across multiple EC2 instances.

Types:

- Application Load Balancer (ALB)
- Network Load Balancer (NLB)
- Gateway Load Balancer (GWLB)

Benefits:

- High availability
- Fault tolerance
- Better performance

---

# Monitoring

Amazon CloudWatch monitors EC2.

Common metrics:

- CPU Utilization
- Network In
- Network Out
- Disk Read
- Disk Write
- Status Check

---

# EC2 Pricing Factors

Pricing depends on:

- Instance type
- Region
- Operating system
- Storage
- Data transfer
- Purchasing option

---

# Advantages

- Fully scalable
- Flexible
- Multiple operating systems
- Secure
- Integrates with AWS services
- Pay-as-you-go

---

# Limitations

- Requires server management
- Responsible for OS updates
- Must configure backups
- Scaling requires planning (unless Auto Scaling)

---

# Best Practices

- Use IAM Roles instead of storing credentials
- Keep Security Groups restrictive
- Enable CloudWatch monitoring
- Use Auto Scaling for production
- Place instances behind a Load Balancer
- Regularly patch the operating system
- Use EBS snapshots for backups
- Stop unused instances to reduce costs
- Use the latest generation instance types
- Enable detailed monitoring when needed

---

# Related AWS Services

- Amazon VPC
- Amazon EBS
- Amazon S3
- Elastic Load Balancer (ELB)
- Auto Scaling
- CloudWatch
- IAM
- Route 53
- Systems Manager
- CloudTrail

---

# Interview Questions

### What is Amazon EC2?

A service that provides virtual servers in the AWS Cloud.

---

### What is an AMI?

A template containing an operating system and software used to launch EC2 instances.

---

### What is the difference between Security Groups and NACLs?

Security Groups:
- Instance level
- Stateful

Network ACLs:
- Subnet level
- Stateless

---

### What is an Elastic IP?

A static public IPv4 address that can be reassigned between EC2 instances.

---

### What is the difference between EBS and Instance Store?

EBS:
- Persistent
- Survives reboot
- Snapshot support

Instance Store:
- Temporary
- Lost after termination
- Faster local storage

---

### What is Auto Scaling?

A service that automatically increases or decreases EC2 instances based on demand.

---

### What is the difference between stopping and terminating an EC2 instance?

Stopping:
- Instance can be restarted
- EBS volumes remain

Terminating:
- Instance is permanently deleted
- Root EBS volume is deleted by default

---

### What is the Free Tier instance?

`t2.micro` (older) or `t3.micro` (region dependent), depending on the current AWS Free Tier offering.