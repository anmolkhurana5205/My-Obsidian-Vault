- AWS infrastructure is built on **virtualization**, and the **hypervisor** is the core component that enables it.
A **hypervisor** is a low-level software layer that:
- **Creates and manages virtual machines (VMs)** on a physical server
- **Allocates hardware resources** (CPU, memory, storage, network) to each VM
- **Isolates VMs** so workloads from different customers cannot interfere
- **Enables multi-tenancy**, allowing many EC2 instances to run on the same hardware securely
- it allows AWS to run many EC2 instances safely on shared physical machines.
