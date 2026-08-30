
---

### `codedeploy.md`

```markdown
# AWS CodeDeploy

## What is it?

- AWS CodeDeploy is a service that **automates application deployments**.
- It can deploy applications to:
  - EC2
  - Lambda
  - ECS

## Why use it?

- Automate deployments
- Reduce deployment errors
- Support deployment strategies
- Easy rollback

## Key Concepts

- **Application** - The application being deployed.
- **Deployment Group** - Defines where the application is deployed.
- **Deployment** - Process of releasing a new application version.
- **AppSpec File** - Defines deployment instructions.

## Important Features

- In-place deployments
- Blue/Green deployments
- Automatic rollback
- Deployment monitoring
- Integration with CodePipeline

## Real-world Example

```text
CodePipeline
     |
     ↓
CodeBuild
     |
     ↓
CodeDeploy
     |
     ↓
EC2
     |
     ↓
New Application Version