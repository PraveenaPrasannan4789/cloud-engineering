# Amazon RDS (Relational Database Service)

## What is Amazon RDS?

- Amazon RDS is a managed relational database service.
- AWS handles database administration tasks.
- You focus on your application instead of managing the database server.

---

## Why Use RDS?

- Easy to set up
- Automatic backups
- Automatic software patching
- High availability
- Scalable storage and compute
- Built-in monitoring

---

## Supported Database Engines

- MySQL
- PostgreSQL
- MariaDB
- Oracle
- Microsoft SQL Server
- Amazon Aurora

---

## Common Use Cases

- Web applications
- E-commerce websites
- Banking applications
- Business applications
- Content Management Systems (CMS)

Example:

```
User
  |
Application (EC2)
  |
Amazon RDS (PostgreSQL)
```

---

# Key Components

## DB Instance

- A database server running in AWS.
- You choose:
  - Database engine
  - Instance size
  - Storage

Example:

```
db.t3.micro
PostgreSQL
20 GB Storage
```

---

## Storage

RDS supports:

- General Purpose SSD (gp3)
- Provisioned IOPS SSD (io2)

Storage can be increased when needed.

---

## Multi-AZ Deployment

- Creates a standby database in another Availability Zone.
- Used for **high availability**.
- AWS automatically switches to the standby if the primary fails.

Example:

```
Primary DB (AZ-A)

        |

Automatic Replication

        |

Standby DB (AZ-B)
```

---

## Read Replica

- A copy of the primary database.
- Used to handle **read-only traffic**.
- Improves application performance.

Example:

```
Application

      |

Primary DB
      |
---------------------
|                   |
Read Replica 1   Read Replica 2
```

---

## Automated Backups

- AWS automatically backs up the database.
- Backups are stored securely.
- Can restore to a specific point in time.

Example:

Backup retention:

```
7 Days
```

---

## Snapshots

- Manual backups.
- Stored until you delete them.

Useful before:

- Upgrading
- Major changes
- Database migration

---

## Storage Autoscaling

Automatically increases storage when space is running low.

Example:

```
Allocated Storage:
100 GB

Maximum Storage:
300 GB

Current Usage:
95 GB

↓

AWS automatically increases storage.
```

---

## Monitoring

Amazon CloudWatch provides metrics such as:

- CPU Utilization
- Free Storage Space
- Database Connections
- Read IOPS
- Write IOPS
- Free Memory

---

# Security

Best practices:

- Keep database private
- Use Security Groups
- Enable encryption
- Enable automatic backups
- Rotate passwords
- Store credentials in AWS Secrets Manager

---

# RDS vs EC2 Database

| Amazon RDS | Database on EC2 |
|------------|-----------------|
| Managed by AWS | Managed by you |
| Automatic backups | Manual backups |
| Automatic patching | Manual patching |
| Easy scaling | Manual scaling |
| Less maintenance | More maintenance |

---

# RDS vs DynamoDB

| Amazon RDS | DynamoDB |
|------------|-----------|
| Relational database | NoSQL database |
| Uses SQL | No SQL |
| Fixed schema | Flexible schema |
| Best for structured data | Best for high-speed applications |

---

# Real World Example

An online shopping website:

```
Customer

    |

Website

    |

Amazon RDS (MySQL)

    |

Product & Order Data
```

---

# AWS CLI Example

## Create an RDS Instance

```bash
aws rds create-db-instance \
  --db-instance-identifier mydb \
  --engine postgres \
  --db-instance-class db.t3.micro \
  --allocated-storage 20
```

---

# Terraform Example

```hcl
resource "aws_db_instance" "example" {
  identifier         = "mydb"
  engine             = "postgres"
  instance_class     = "db.t3.micro"
  allocated_storage  = 20
  username           = "admin"
  password           = "password123"
  skip_final_snapshot = true
}
```

---

# Interview Questions

### What is Amazon RDS?

- A managed relational database service provided by AWS.

---

### What databases does RDS support?

- MySQL
- PostgreSQL
- MariaDB
- Oracle
- SQL Server
- Amazon Aurora

---

### What is Multi-AZ?

- A standby database in another Availability Zone for high availability and automatic failover.

---

### What is a Read Replica?

- A read-only copy of the primary database used to improve read performance.

---

### What is the difference between Multi-AZ and Read Replica?

| Multi-AZ | Read Replica |
|-----------|--------------|
| High availability | Improve read performance |
| Automatic failover | No automatic failover |
| Standby copy | Read-only copy |

---

### What is Storage Autoscaling?

- Automatically increases database storage when it starts running out of space.

---

### What is the difference between an automated backup and a snapshot?

Automated Backup:
- Created automatically
- Used for point-in-time recovery
- Deleted when the DB is deleted (unless retained)

Snapshot:
- Created manually
- Kept until you delete it
- Useful before upgrades or migrations

---

# Best Practices

- Enable Multi-AZ for production
- Enable automatic backups
- Enable storage autoscaling
- Enable encryption
- Use Read Replicas for heavy read workloads
- Keep the database in a private subnet
- Monitor with CloudWatch
- Store passwords in Secrets Manager
- Regularly apply updates during maintenance windows