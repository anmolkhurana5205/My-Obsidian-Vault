**Containers** package applications with their dependencies, while **orchestration** manages how containers are deployed, scaled, networked, and healed. AWS provides multiple managed services to run containers at scale.

A **container** is a lightweight, portable unit that includes:
- Application code
- Runtime
- Libraries & dependencies
They share the host OS kernel (unlike VMs).
### Benefits
- Fast startup
- Consistent environments
- Efficient resource usage
- Easy scaling

## Containers vs Virtual Machines

|Feature|Containers|EC2 / VMs|
|---|---|---|
|OS|Shared kernel|Full OS per VM|
|Startup|Seconds|Minutes|
|Isolation|Process-level|Hardware-level|
|Portability|High|Medium|
|Overhead|Low|High|
**Orchestration** handles:
- Scheduling containers
- Scaling in/out
- Load balancing
- Service discovery
- Health checks
- Rolling updates
- Self-healing

## Container Services on AWS
AWS offers **three primary container platforms**.
### 1. Amazon ECS (Elastic Container Service)
**AWS-native container orchestrator**
#### Key Features
- Simple to use
- Deep AWS integration
- No control plane to manage
#### Launch Types
- **EC2 launch type** → you manage instances
- **Fargate launch type** → serverless containers
#### Use When
- You want simplicity
- AWS-only environment
- Tight AWS integration
### 2. Amazon EKS (Elastic Kubernetes Service)
**Managed Kubernetes on AWS**
#### Key Features
- Standard Kubernetes API
- Portable across clouds
- Rich ecosystem
#### Components
- Control plane managed by AWS
- Worker nodes on EC2 or Fargate
#### Use When
- You need Kubernetes
- Multi-cloud strategy
- Complex orchestration needs
### 3. AWS Fargate (Serverless Containers)
**Compute engine for ECS & EKS**
#### Characteristics
- No EC2 management
- Pay per container
- Automatic scaling
- Strong isolation
#### Best For
- Microservices
- Event-driven workloads
- Spiky traffic

## Supporting AWS Services
### Amazon ECR (Elastic Container Registry)
- Stores Docker images
- Integrated with ECS/EKS
- Secure and scalable
### Elastic Load Balancing
- ALB for HTTP services
- NLB for high performance
### Auto Scaling
- Scales tasks/pods
- Scales EC2 worker nodes (if used)

## Storage for Containers
- EBS (block storage)
- EFS (shared storage)
- S3 (object storage via apps)
## Common Architectures
### ECS + Fargate
`ALB → ECS Service → Containers`
### EKS
`Ingress → Kubernetes Services → Pods`

![[Pasted image 20260118160735.png]]