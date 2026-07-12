**Amazon Virtual Private Cloud (VPC)** is a **logically isolated virtual network** within AWS where you launch and control AWS resources such as **EC2, RDS, ECS, EKS, and Load Balancers**.

Think of it as **your own private data center network inside AWS**.

## Why Amazon VPC Exists
VPC gives you:
- **Network isolation**
- **Full control over IP addressing**
- **Secure traffic routing**
- **Custom network architecture**
Without VPC, all resources would sit in a shared AWS network.

## Core VPC Concepts
### 1. CIDR Block
- Defines the IP address range of the VPC
- Example: `10.0.0.0/16`
- Cannot be changed after creation
### 2. Subnets
- Segments of a VPC
- Bound to **one Availability Zone**
- Types:
    - **Public subnet**
    - **Private subnet**
### 3. Route Tables
- Control traffic routing
- Each subnet is associated with a route table
### 4. Internet Gateway (IGW)
- Allows communication with the internet
- Required for public subnets
### 5. NAT Gateway / NAT Instance
- Enables private subnet resources to access the internet
- Prevents inbound internet traffic

## Security in VPC
### 1. Security Groups
- Stateful firewall
- Applied at **instance level**
- Allow rules only
### 2. Network ACLs (NACL)
- Stateless firewall
- Applied at **subnet level**
- Allow and deny rules

### Subnet
Subnets are used to organize your resources and can be made publicly or privately accessible. A private subnet is commonly used to contain resources like a database storing customer or transactional information. A public subnet is commonly used for resources like a customer-facing website.

![[Pasted image 20260118183152.png]]

