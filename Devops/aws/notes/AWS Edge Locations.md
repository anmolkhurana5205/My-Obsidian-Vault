**AWS Edge Locations** are **globally distributed data centers** used by AWS to deliver **content, DNS, and edge computing services** with **low latency** to end users.

- They are a key part of **AWS’s global edge network**.

Edge Locations are **not full AWS Regions**.  
They are optimized sites that sit **physically close to users** and handle:
- Content delivery
- DNS resolution
- DDoS protection
- Edge compute execution
Primary goal: **reduce latency and improve performance**.

### Edge Location Architecture
```
User
 ↓
Nearest AWS Edge Location
 ↓
(Cache hit) → Response immediately
(Cache miss) → AWS Region (Origin)

```

