**Elastic Load Balancing (ELB)** is an AWS service that **automatically distributes incoming traffic** across multiple targets (EC2 instances, containers, IPs, Lambda) to ensure **high availability, fault tolerance, and scalability**.

## Why ELB Exists
ELB solves critical infrastructure problems:
- Prevents **single point of failure**
- Handles **traffic spikes**
- Improves **application availability**
- Integrates tightly with **Auto Scaling**

## 2. Core Functions of ELB
ELB:
- Distributes traffic evenly
- Performs **health checks**
- Routes traffic only to **healthy targets**
- Supports **automatic scaling**
- Works across **multiple Availability Zones**

## 3. Types of Elastic Load Balancers
AWS provides **three main ELB types**
### 3.1 Application Load Balancer (ALB)
**Layer:** 7 (HTTP/HTTPS)
**Best for:**
- Web applications
- REST APIs
- Microservices

**Key Features**
- Path-based routing (`/api`, `/images`)
- Host-based routing (`api.example.com`)
- Supports WebSockets
- Native HTTP/2
- Works with ECS, EKS, Lambda

**Example**
`/login  → Auth Service /orders → Order Service`

---

### 3.2 Network Load Balancer (NLB)
**Layer:** 4 (TCP/UDP/TLS)
**Best for:**
- High-performance applications
- Low-latency workloads
- Real-time systems

**Key Features**
- Handles millions of requests/sec
- Static IP support
- Preserves client IP
- Ultra-low latency

### 3.3 Gateway Load Balancer (GWLB)
**Layer:** 3/4
**Best for:**
- Network security appliances
- Firewalls, IDS/IPS

**Key Features**
- Transparent traffic routing
- Uses GENEVE protocol
- Centralized security control

## 4. Classic Load Balancer (CLB) — Legacy
Layer 4 & 7
- Limited features
- Not recommended for new systems

## 5. Integration with Auto Scaling
- ELB detects unhealthy instances
- ASG replaces them
- Traffic is routed only to healthy instances.
This enables **self-healing systems**.

## **Routing methods**

**Round Robin**  
Distributes traffic evenly across all available servers in a cyclic manner.

**Least Connections**  
Routes traffic to the server with the fewest active connections, maintaining a balanced load.

**IP Hash**
Uses the client’s IP address to consistently route traffic to the same server.

**Least Response Time**  
Directs traffic to the server with the fastest response time, minimizing latency.

![[Pasted image 20260117183957.png]]

![[Pasted image 20260117184012.png]]

![[Pasted image 20260117184023.png]]