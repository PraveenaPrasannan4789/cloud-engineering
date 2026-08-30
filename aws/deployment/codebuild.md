
---

### `codebuild.md`

```markdown
# AWS CodeBuild

## What is it?

- AWS CodeBuild is a **fully managed build service**.
- It compiles source code, runs tests, and creates build artifacts.

## Why use it?

- No build servers to manage
- Automatically scales
- Runs tests automatically
- Creates deployment artifacts

## Key Concepts

- **Build Project** - Defines how the application is built.
- **Build Environment** - Environment where the build runs.
- **Buildspec** - File containing build commands.
- **Artifact** - Output produced by the build.

## Important Features

- Supports multiple programming languages.
- Supports Docker builds.
- Integrates with CodePipeline.
- Can store artifacts in S3.

## Real-world Example

```text
GitHub
   |
   ↓
CodeBuild
   |
   ├── Install dependencies
   ├── Run tests
   ├── Build application
   |
   ↓
Build Artifact
   |
   ↓
S3