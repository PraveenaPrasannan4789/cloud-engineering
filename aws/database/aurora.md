# Amazon Aurora

## What is Amazon Aurora?

- Amazon Aurora is a **fully managed relational database** service.
- It is built by AWS and is compatible with **MySQL** and **PostgreSQL**.
- It provides better performance and availability than standard MySQL and PostgreSQL.

---

## Why Use Aurora?

- High performance
- Automatic backups
- High availability
- Fault tolerant
- Automatic storage scaling
- Managed by AWS

---

## Aurora Compatible Databases

- Aurora MySQL
- Aurora PostgreSQL

You can migrate existing MySQL or PostgreSQL databases to Aurora with minimal changes.

---

## Common Use Cases

- E-commerce applications
- Banking systems
- SaaS applications
- Enterprise applications
- High-traffic websites

Example:

```
User
  |
Application
  |
Amazon Aurora
```

---

# Key Features

## High Performance

- Up to **5x faster** than standard MySQL.
- Up to **3x faster** than standard PostgreSQL.

---

## Automatic Storage Scaling

- Storage automatically grows as your data increases.
- No need to manually resize storage.

Example:

```
10 GB

↓

50 GB

↓

200 GB

↓

Automatically grows
```

---

## Multi-AZ Availability

- Aurora automatically stores copies of data across multiple Availability Zones.
- If one Availability Zone fails, Aurora continues running.

---

## Aurora Replicas

- Create up to **15 read replicas**.
- Used to improve read performance.
- Replicas can automatically become the primary database if needed.

Example:

```
Application

      |

Primary Aurora

   /     |      \

Replica Replica Replica
```

---

## Backups

- Automatic backups enabled by AWS.
- Point-in-time recovery supported.
- Manual snapshots are also available.

---

## Security

- Encryption at rest
- Encryption in transit
- IAM authentication
- Security Groups
- AWS Secrets Manager integration

---

## Monitoring

Use Amazon CloudWatch to monitor:

- CPU Utilization
- Database Connections
- Free Memory
- Read Latency
- Write Latency
- Storage Usage

---

# Aurora vs RDS

| Amazon Aurora | Amazon RDS |
|---------------|------------|
| AWS-built database | Managed database service |
| MySQL & PostgreSQL compatible | Supports multiple database engines |
| Higher performance | Standard performance |
| Automatic storage scaling | Storage configured by user (autoscaling available for supported engines) |
| Up to 15 read replicas | Fewer read replicas depending on engine |

---

# Aurora vs MySQL

| Aurora | MySQL |
|---------|--------|
| Managed by AWS | Self-managed or RDS |
| Faster performance | Standard performance |
| Automatic scaling | Manual scaling |
| High availability built in | Requires additional configuration |

---

# Real World Example

An online shopping website:

```
Customers

     |

Website

     |

Amazon Aurora

     |

Orders
Products
Payments
```

---

# AWS CLI Example

## Create an Aurora Cluster

```bash
aws rds create-db-cluster \
  --db-cluster-identifier my-aurora-cluster \
  --engine aurora-mysql \
  --master-username admin \
  --master-user-password password123
```

---

# Terraform Example

```hcl
resource "aws_rds_cluster" "aurora" {
  cluster_identifier = "my-aurora-cluster"
  engine             = "aurora-postgresql"
  master_username    = "admin"
  master_password    = "password123"
}
```

---

# Advantages

- High performance
- Automatic storage scaling
- High availability
- Automatic backups
- Easy maintenance
- Supports MySQL and PostgreSQL

---

# Limitations

- More expensive than standard RDS
- Supports only MySQL and PostgreSQL compatibility
- Not required for small or low-traffic applications

---

# Interview Questions

### What is Amazon Aurora?

- A fully managed relational database built by AWS, compatible with MySQL and PostgreSQL.

---

### Is Aurora part of Amazon RDS?

- Yes. Aurora is a database engine available within Amazon RDS.

---

### Which databases are compatible with Aurora?

- MySQL
- PostgreSQL

---

### What is an Aurora Replica?

- A read-only copy of the primary database used to improve read performance and provide high availability.

---

### Does Aurora automatically scale storage?

- Yes. Aurora automatically increases storage as the database grows.

---

### When should you choose Aurora instead of standard RDS?

- When you need:
  - High performance
  - High availability
  - Automatic storage scaling
  - Read-heavy workloads

---

# Best Practices

- Enable Multi-AZ deployment
- Enable automatic backups
- Use Aurora Replicas for read-heavy workloads
- Enable encryption
- Store credentials in AWS Secrets Manager
- Monitor using CloudWatch
- Use IAM authentication where appropriate
- Schedule maintenance during low-traffic periods