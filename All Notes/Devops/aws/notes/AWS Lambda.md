**AWS Lambda** is a **serverless compute service** that lets you run code **without provisioning or managing servers**. You upload your code, define when it should run, and AWS handles **execution, scaling, availability, and infrastructure**.

Lambda allows you to:
- Run code in response to **events**
- Automatically **scale from zero to thousands** of executions
- Pay **only for execution time**
- Focus purely on **business logic**
In short: **write code → trigger it → AWS runs and scales it.**

Lambda solves:
- Server provisioning and maintenance
- Over/under-provisioning
- Idle infrastructure cost
- Scaling complexity
It is a core building block for **event-driven and microservices architectures**.

## Key Concept
### 1. Function
- A Lambda **function** is your code + configuration
- Runs in an isolated execution environment
### 2. Event Source
Triggers Lambda execution.
Common sources:
- S3 (object upload)
- API Gateway
- EventBridge
- SQS
- SNS
- DynamoDB Streams
- CloudWatch schedules
### 3. Handler
Entry point of your function.
Example (Node.js):
```
exports.handler = async (event) => {
  return "Hello from Lambda";
};
```

## Supported Runtimes
- Node.js
- Python
- Java
- Go
- .NET
- Ruby
- Custom runtimes (via container images)

## Resource Configuration
Each function can configure:
- Memory (128 MB → 10 GB)
- CPU (proportional to memory)
- Timeout (up to 15 minutes)
- Ephemeral storage (up to 10 GB)

## Lambda vs EC2 (Quick Comparison)

|Feature|Lambda|EC2|
|---|---|---|
|Server management|None|Required|
|Scaling|Automatic|Manual/ASG|
|Billing|Per execution|Per hour|
|Execution limit|15 minutes|Unlimited|
|Use case|Event-driven|Long-running apps|

## Lambda Limitations
- Max execution time: **15 minutes**
- Cold start latency
- Not ideal for long-running processes
- Limited local disk (ephemeral)

## Cold Start vs Warm Start
### Cold Start
- New execution environment created
- Slight latency increase
### Warm Start
- Existing environment reused
- Faster execution
Provisioned Concurrency minimizes cold starts.
## Scaling Behavior
- Automatically scales **per request**
- Handles thousands of concurrent executions
- No load balancers or auto scaling groups required
## How Lambda Works (Execution Flow)
`Event → Lambda → Code Execution → Response`

