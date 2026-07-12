- Amazon EC2 (Elastic Compute Cloud)
- Amazon **EC2** is AWS’s core **compute service**

**Amazon EC2** allows you to:
- Launch **virtual machines (instances)** on demand
- Choose **CPU, memory, storage, and networking**
- Scale **up, down, or out** as needed
- Pay only for the **capacity you use**
Think of EC2 as **renting servers in AWS data centers**, but with automation and elasticity.

Core EC2 Components
AMI (Amazon Machine Image) - An **AMI** is a template used to create EC2 instances.
- Includes:
  - Operating system (Linux, Windows, etc.)
  - Preinstalled software
  - Configuration settings
- Types:
  - AWS-provided AMIs
  - Marketplace AMIs
  - Custom AMIs (your own)
Instance - An **instance** is a running virtual server created from an AMI.
- ``` sql
  Launch → Running → Stop/Start → Terminate
  ```

Instance Types - Define **hardware configuration**.

| Family                   | Purpose                    |
| ------------------------ | -------------------------- |
| General Purpose (t, m)   | Balanced workloads         |
| Compute Optimized (c)    | CPU-intensive              |
| Memory Optimized (r, x)  | RAM-heavy workloads        |
| Storage Optimized (i, d) | High I/O                   |
| Accelerated (p, g, inf)  | GPU / ML / AI              |
| Bare Metal (metal)       | No virtualization overhead |