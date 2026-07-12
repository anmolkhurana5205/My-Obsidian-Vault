**Amazon SNS (Simple Notification Service)** is a **fully managed publish/subscribe (pub/sub) messaging service** used to **send notifications and events** to multiple subscribers **in real time**.

Amazon SNS enables:
- **Publishers** to send messages to a **topic**
- **Subscribers** to receive messages automatically
- **One-to-many communication**
In short: **SNS pushes messages to many consumers simultaneously.**

## Why SNS Exists
SNS solves:
- Tight coupling between systems
- Need for fan-out event delivery
- Real-time notifications
- Scalable event broadcasting

## Message Flow
`Publisher → SNS Topic → Subscribers`

## Core SNS Components
### 1. Topic
- Central communication channel
- Messages are published to topics
### 3.2 Publisher
- Service or application sending messages
- Example: EC2, Lambda, CloudWatch, custom apps
### 3.3 Subscriber
- Receives messages from topic
- Multiple subscribers per topic

## Subscription Types (Protocols)
SNS supports multiple delivery mechanisms.

| Protocol           | Description             |
| ------------------ | ----------------------- |
| HTTP / HTTPS       | Webhooks                |
| SQS                | Queue-based consumption |
| Lambda             | Serverless processing   |
| Email / Email-JSON | Notifications           |
| SMS                | Mobile messages         |
| Mobile Push        | iOS / Android           |
| Firehose           | Data ingestion          |

