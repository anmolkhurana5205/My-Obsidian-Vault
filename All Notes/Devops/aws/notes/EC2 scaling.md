### A.1 Vertical Scaling (Scale Up / Scale Down)
**Definition:**  
Increase or decrease the **size of a single EC2 instance**.
**How it works:**
- Change instance type (e.g., `t3.medium → m5.large`)
- Usually requires **stop → modify → start**
**Advantages**
- Simple
- No application redesign required
**Limitations**
- Downtime involved
- Upper hardware limit
- No fault tolerance
**Typical Use Cases**
- Databases
- Legacy applications
- Low-traffic systems
### A.2 Horizontal Scaling (Scale Out / Scale In)
**Definition:**  
Increase or decrease the **number of EC2 instances**.
**How it works:**
- Add or remove instances dynamically
- Uses **Auto Scaling Groups**
**Advantages**
- High availability
- No downtime
- Cloud-native approach
**Limitations**
- Requires stateless application design
- Slightly more complex
**Typical Use Cases**
- Web servers
- APIs
- Microservices
### B. Auto Scaling Group (ASG)
An **Auto Scaling Group** ensures the **right number of EC2 instances** are running at all times.
### Core Parameters
- **Minimum capacity**
- **Desired capacity**
- **Maximum capacity**
### Launch Configuration
Defined via **Launch Template**:
- AMI
- Instance type(s)
- Key pair
- Security groups
- User data scripts
### C. Scaling Policies (How AWS Decides to Scale)
#### 3.1 Target Tracking Scaling (Most Common)
Maintains a target metric value.
Example:
`Keep average CPU utilization at 50%`
#### 3.2 Step Scaling
Scales based on metric thresholds.
Example:

| CPU Usage | Action       |
| --------- | ------------ |
| > 70%     | +1 instance  |
| > 85%     | +3 instances |
#### 3.3 Simple Scaling (Legacy)
- One scaling action per alarm
- Uses cooldowns
- Rarely used now
#### 3.4 Scheduled Scaling
Scale based on **time**.
Example:
- Scale out at 9 AM
- Scale in at 6 PM
#### 3.5 Predictive Scaling
- Uses machine learning
- Forecasts traffic
- Scales in advance