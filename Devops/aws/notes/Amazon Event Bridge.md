**Amazon EventBridge** is a **serverless event bus service** that enables **event-driven, loosely coupled architectures** by routing events from sources to targets using rules.

EventBridge allows you to:
- Capture **events** from AWS services, SaaS apps, or custom apps
- **Filter and route** events in real time
- Trigger multiple **targets** without tight coupling
In short: **Event Bridge is the central nervous system for events in AWS.**

Event Bridge solves:
- Tight coupling between services
- Complex event routing logic
- Hard-coded integrations
- Scaling event consumers independently

## How EventBridge Works (Flow)
`Event Source → Event Bus → Rule → Target(s)`

## Core Components
### 1. Event
A JSON record describing **something that happened**.
Example:
```
{
  "source": "aws.ec2",
  "detail-type": "EC2 Instance State-change Notification",
  "detail": {
    "state": "running"
  }
}

```
### 3.2 Event Bus
A **channel** that receives events.
Types:
- **Default event bus** (AWS services)
- **Custom event bus** (your apps)
- **Partner event bus** (SaaS providers)
### 3.3 Rule
Defines:
- **Which events** to match
- **Where to send them**
Rules use **event patterns** or schedules.
### 3.4 Target
The destination for matched events.
Common targets:
- AWS Lambda
- SQS
- SNS
- Step Functions
- EC2 (via SSM)
- API Destinations

## Common Use Cases
- Microservices communication
- Infrastructure automation
- Audit & compliance workflows
- CI/CD triggers
- SaaS integrations
- Decoupled event-driven systems

