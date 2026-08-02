# Amazon RDS vs Amazon Aurora

| Feature | Amazon RDS | Amazon Aurora |
|---------|------------|---------------|
| What is it? | Managed relational database service | AWS-built relational database engine within RDS |
| Database Engines | MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, Aurora | MySQL-compatible, PostgreSQL-compatible |
| Performance | Standard database performance | Up to 5× faster than MySQL and 3× faster than PostgreSQL |
| Storage | Configure storage manually (autoscaling available for supported engines) | Automatically scales storage up to 128 TB |
| High Availability | Multi-AZ deployment | Built-in high availability across multiple AZs |
| Read Replicas | Supported (number depends on engine) | Up to 15 Aurora Replicas |
| Automatic Failover | Yes (with Multi-AZ) | Yes, faster failover |
| Backups | Automatic backups and snapshots | Automatic backups and snapshots |
| Maintenance | Managed by AWS | Managed by AWS |
| Cost | Lower | Higher |
| Best For | Small to medium applications | High-performance, enterprise applications |

---

## When to Choose Amazon RDS

Choose RDS if:

- You want a lower-cost managed database.
- Your application has moderate traffic.
- You need Oracle or SQL Server.
- Standard performance is sufficient.

Example:

- Company HR system
- Internal business application
- Small e-commerce website

---

## When to Choose Amazon Aurora

Choose Aurora if:

- You need very high performance.
- Your application receives millions of requests.
- You need fast failover.
- You need automatic storage scaling.
- You have read-heavy workloads.

Example:

- Amazon-like shopping website
- Banking application
- SaaS platform
- Gaming backend

---

# Simple Example

### Amazon RDS

```
Application
      |
      |
   RDS Database
```

Suitable for most business applications.

---

### Amazon Aurora

```
Application
      |
Primary Aurora
   /    |    \
Replica Replica Replica
```

Suitable for high-traffic applications requiring better performance and scalability.

---

# Interview Question

### Which is better, RDS or Aurora?

There is no universally "better" option.

- Choose **RDS** for cost-effective managed databases and support for multiple database engines.
- Choose **Aurora** when you need higher performance, greater scalability, and faster failover for MySQL- or PostgreSQL-compatible workloads.