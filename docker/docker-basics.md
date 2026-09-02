What is Docker?

Docker is a platform used to package and run applications inside containers.

A container includes the application and the dependencies it needs to run.

Without Docker:

My laptop
├── Node.js
├── npm
├── PostgreSQL
├── dependencies
└── Application

Another developer may have different versions, causing:

"It works on my machine!"

With Docker:

Docker Container
├── Application
├── Node.js
├── Dependencies
└── Configuration

The same container can run consistently on a developer laptop, server, or cloud environment.

Why use Docker?
Consistent environment
Easy application deployment
Lightweight compared with VMs
Isolates applications
Easy to scale
Works well with CI/CD
Commonly used with AWS ECS, EKS and ECR
Important Docker concepts
Concept	Meaning
Image	Template/package used to create a container
Container	Running instance of an image
Dockerfile	Instructions for building an image
Registry	Place where Docker images are stored
Volume	Persistent storage for containers
Network	Allows containers to communicate

The basic flow is:

Dockerfile
    ↓
Docker Image
    ↓
Docker Container
    ↓
Running Application
Simple example

Suppose you have a Node.js application.

Node.js Application
        ↓
    Dockerfile
        ↓
    Docker Image
        ↓
    Docker Container

You can then run that container on your laptop or deploy the image to AWS.

Useful commands
docker --version

Check Docker installation.

docker ps

Show running containers.

docker images

Show local images.

docker pull nginx

Download an image.

docker run nginx

Create and run a container from the nginx image.

Docker vs Virtual Machine

Virtual Machine:

Physical Server
 ├── VM
 │    ├── Guest OS
 │    └── Application
 └── VM
      ├── Guest OS
      └── Application

Docker:

Physical Server
 ├── Docker
 ├── Container
 │    └── Application
 └── Container
      └── Application

Containers share the host OS kernel, so they are generally lighter and faster to start than VMs.

Remember

Docker packages applications into containers so they can run consistently across different environments.