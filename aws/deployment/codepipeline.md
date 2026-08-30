# AWS CodePipeline

## What is it?

- AWS CodePipeline is a **CI/CD service**.
- It automates the process of building, testing, and deploying applications.
- It connects different stages of the software delivery process.

## Why use it?

- Automate deployments
- Automate testing
- Reduce manual work
- Create repeatable deployment processes

## Key Concepts

- **Pipeline** - Complete CI/CD workflow.
- **Stage** - A step in the pipeline.
- **Action** - Task performed in a stage.
- **Source** - Where the application code comes from.
- **Build** - Compiles and tests the application.
- **Deploy** - Deploys the application.

## Important Features

- Integrates with GitHub, S3, CodeCommit, etc.
- Integrates with CodeBuild and CodeDeploy.
- Supports automated deployments.
- Supports manual approval actions.

## Real-world Example

```text
Developer
   |
   ↓
GitHub
   |
   ↓
CodePipeline
   |
   ├── Build → CodeBuild
   |
   ├── Test
   |
   └── Deploy → CodeDeploy  ->  EC2