**Amazon SQS** is a **fully managed message queuing service** that enables **decoupling**, **scaling**, and **fault tolerance** between distributed application components.

Amazon SQS allows components of a system to:
- Send messages to a **queue**
- Store messages **reliably**
- Process messages **asynchronously**
- Scale producers and consumers **independently**
In short: **SQS acts as a buffer between services.**

SQS solves common distributed-system problems:
- Tight coupling between services
- Traffic spikes overwhelming downstream systems
- Message loss during failures
- Complex queue management

## Types of SQS Queues
AWS provides **two queue types**.
### 1. Standard Queue (Default)
**Characteristics**
- Nearly unlimited throughput
- **At-least-once delivery**
- **Best-effort ordering**
- Possible duplicate messages
**Use Cases**
- Event processing
- Background jobs
- Log processing
### 2. FIFO Queue
**Characteristics**
- **Exactly-once processing**
- **First-In-First-Out order**
- Limited throughput (compared to standard)
**Key Concepts**
- Message Group ID
- Deduplication ID
**Use Cases**
- Financial transactions
- Order processing
- Inventory updates

## Message Lifecycle
`Producer → SQS Queue → Consumer`

### Message
- Up to **256 KB**
- Contains body + attributes

### Queue
- Stores messages until consumed
- Redundantly stored across AZs

### Producer
- Sends messages to SQS

### Consumer
- Polls and processes messages

## Dead-Letter Queue (DLQ)
- Stores messages that fail processing multiple times
- Configured using **maxReceiveCount**
- Helps debugging and isolation of failures

