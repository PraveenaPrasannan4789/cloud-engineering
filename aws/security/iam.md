# AWS IAM (Identity and Access Management)

## What is IAM?

- AWS IAM is a service used to control access to AWS resources.
- It manages **who can access AWS** and **what actions they can perform**.
- IAM is a global AWS service.

---

## Why Use IAM?

- Control user permissions
- Secure AWS resources
- Follow least privilege access
- Manage access for users, applications, and services

---

# Key Concepts

## User

- Represents a person or application that needs AWS access.

Example:

```
Developer User
      |
      |
Access AWS Console
```

---

## Group

- Collection of IAM users with common permissions.

Example:

```
Developers Group

Users:
- John
- Sarah

Permissions:
- Access EC2
- Access S3
```

---

## Role

- Provides temporary permissions to AWS services or users.
- Commonly used by AWS services.

Example:

```
EC2 Instance

     |

IAM Role

     |

Permission to access S3
```

---

## Policy

- A JSON document that defines permissions.

Example:

Allow reading S3 bucket:

```json
{
  "Effect": "Allow",
  "Action": "s3:GetObject",
  "Resource": "*"
}
```

---

# Authentication vs Authorization

## Authentication

- Who are you?

Example:

```
Login with username and password
```

## Authorization

- What can you do?

Example:

```
Can access S3?
Can create EC2?
```

---

# IAM Example

Scenario:

A developer needs access to upload files to S3.

```
Developer

   ↓

IAM User

   ↓

IAM Policy

   ↓

S3 Upload Permission

   ↓

S3 Bucket
```

---

# Best Practices

- Avoid using the root account
- Enable MFA
- Follow least privilege principle
- Use IAM Roles instead of access keys for AWS services
- Rotate access keys regularly
- Review permissions regularly

---

# Interview Questions

### What is IAM?

- AWS service used to manage access and permissions.

### Difference between IAM User and IAM Role?

User:
- Permanent identity
- Used by people/applications

Role:
- Temporary permissions
- Used by AWS services

### What is least privilege?

- Giving users only the permissions they need and nothing more.