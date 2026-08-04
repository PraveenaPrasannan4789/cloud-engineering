# Amazon DynamoDB

## What is DynamoDB?

- Amazon DynamoDB is a fully managed **NoSQL database** service.
- It stores data as **key-value** and **document** data.
- It is designed for high performance and scalability.

---

## Why Use DynamoDB?

- Fast performance
- Automatic scaling
- Serverless
- Highly available
- Managed by AWS

---

## Common Use Cases

- E-commerce applications
- Gaming applications
- Shopping carts
- User profiles
- IoT applications

Example:

```
User

  |

Application

  |

DynamoDB
```

---

# Key Concepts

## Table

- A table stores data.
- Similar to a table in a relational database.

Example:

```
Users
```

---

## Item

- An item is a single record in a table.
- Similar to a row in SQL.

Example:

```
{
  "UserId": "101",
  "Name": "John",
  "Age": 25
}
```

---

## Attribute

- An attribute is a piece of information about an item.
- Similar to a column in SQL.

Example:

```
Name
Age
Email
```

---

## Primary Key

Every table must have a primary key.

Types:

### Partition Key

- A single unique key.

Example:

```
UserId
```

---

### Composite Key

- Combination of:
  - Partition Key
  - Sort Key

Example:

```
Partition Key : CustomerId

Sort Key : OrderId
```

---

# DynamoDB Features

## Automatic Scaling

- Automatically adjusts capacity based on traffic.

---

## High Availability

- Data is automatically replicated across multiple Availability Zones.

---

## Low Latency

- Reads and writes usually take only a few milliseconds.

---

## Backup and Restore

- Supports on-demand backups.
- Supports point-in-time recovery.

---

## Encryption

- Data is encrypted at rest.
- Supports AWS KMS.

---

# DynamoDB vs RDS

| DynamoDB | RDS |
|-----------|-----|
| NoSQL | Relational database |
| No SQL required | Uses SQL |
| Flexible schema | Fixed schema |
| Very fast | Standard performance |
| Automatically scales | Manual scaling (or autoscaling for supported engines) |

---

# Real World Example

Shopping cart application:

```
Customer

    |

Website

    |

DynamoDB

    |

Cart Items
```

---

# AWS CLI Example

## Create Table

```bash
aws dynamodb create-table \
  --table-name Users \
  --attribute-definitions AttributeName=UserId,AttributeType=S \
  --key-schema AttributeName=UserId,KeyType=HASH \
  --billing-mode PAY_PER_REQUEST
```

---

# Terraform Example

```hcl
resource "aws_dynamodb_table" "users" {
  name         = "Users"
  billing_mode = "PAY_PER_REQUEST"
  hash_key     = "UserId"

  attribute {
    name = "UserId"
    type = "S"
  }
}
```

---

# Advantages

- Fully managed
- Serverless
- Fast performance
- Automatic scaling
- High availability
- No infrastructure to manage

---

# Limitations

- No SQL joins
- Limited complex queries
- Data model must be planned carefully

---

# Interview Questions

### What is DynamoDB?

- A fully managed NoSQL database service provided by AWS.

---

### What is an Item?

- A single record stored in a DynamoDB table.

---

### What is an Attribute?

- A piece of data within an item.

---

### What is the difference between a Partition Key and a Composite Key?

Partition Key:
- Uses one unique key.

Composite Key:
- Uses a Partition Key and a Sort Key.

---

### Is DynamoDB serverless?

- Yes. AWS manages the infrastructure, scaling, and maintenance.

---

### When should you use DynamoDB?

- High-traffic applications
- Low-latency workloads
- Flexible or changing data structures
- Large-scale applications

---

# Best Practices

- Choose a good partition key
- Use on-demand backups
- Enable point-in-time recovery
- Encrypt data with AWS KMS
- Monitor with CloudWatch
- Use IAM to control access