# System Design Fundamentals

## Overview
System design is the process of defining the architecture, components, modules, interfaces, and data for a system to satisfy specified requirements.


### System Design Study Plan
| 週次       | 主題                                       | 核心關鍵詞                                                             | 重點問題                  |
| -------- | ---------------------------------------- | ----------------------------------------------------------------- | --------------------- |
| Week 1   | [**Scalability & Load Balancer** ](./Scaling_And_LR.md)         | Vertical / Horizontal Scaling, Auto Scaling, Round Robin, IP Hash | 如何應對高併發？如何分散負載？       |
| Week 2   | [**Cache 設計與策略** ](./Cache.md)                         | Read-Through, Write-Through, TTL, LRU, Redis                      | 如何用 Cache 提高效能又保持一致性？ |
| Week 3   | **Database 選型與 Sharding**                | SQL vs NoSQL, Sharding, Replication, CAP                          | 什麼情況選 MySQL？什麼情況拆 DB？ |
| Week 4   | **Data Consistency & Message Queue**     | Eventual Consistency, Kafka, RabbitMQ, Idempotency Key            | 系統怎麼確保資料一致？怎麼防重複？     |
| Week 5   | **Rate Limiting & Circuit Breaker**      | Token Bucket, Leaky Bucket, Retry, Backoff, Hystrix               | 如何保護系統不被濫用或雪崩？        |
| Week 6   | **CDN & Global System Design**           | Cloudflare, Geo DNS, Edge Cache                                   | 如何設計給全球用戶？如何用 CDN 加速？ |
| Week 7   | **Monitoring & Reliability**             | SLA, SLO, SLI, Prometheus, Grafana, Healthcheck                   | 如何設計一個穩定且可觀察的系統？      |
| Week 8   | **Design Real Systems & Interview Case** | Design YouTube, Messenger, TinyURL, LLM Infra                     | 如何答出一個完整的系統設計題？       |

## Core Concepts

### 1. Scalability
The ability of a system to handle increased load by adding resources.

#### Vertical Scaling (Scale Up)
- **Definition**: Adding more resources to existing servers
- **Resources**: CPU, RAM, Disk, Network
- **Pros**: Simple to implement, no code changes needed
- **Cons**: Limited by hardware constraints, single point of failure

#### Horizontal Scaling (Scale Out)
- **Definition**: Adding more servers to distribute load
- **Types**:
  - **Software Scaling**: Load balancing, caching, database sharding
  - **Hardware Scaling**: Multiple servers, distributed systems
- **Pros**: Better fault tolerance, unlimited scaling potential
- **Cons**: More complex to implement, requires code changes

### 2. Reliability
- **Definition**: System's ability to function correctly under given conditions
- **Key Concerns**:
  - Server failures and recovery
  - Data loss prevention
  - Fault tolerance mechanisms

### 3. Availability
- **Definition**: Percentage of time the system is operational
- **Formula**: `Availability = (Total Time - Downtime) / Total Time`
- **Common Targets**:
  - 99.9% (Three nines) = 8.76 hours downtime/year
  - 99.99% (Four nines) = 52.56 minutes downtime/year
  - 99.999% (Five nines) = 5.26 minutes downtime/year

### 4. Efficiency
- **Latency**: Time delay for first response (measured in milliseconds)
- **Throughput**: Number of operations processed per time unit (requests/second)
- **Goal**: Balance between low latency and high throughput

## CAP Theorem
A fundamental theorem in distributed systems stating that it's impossible for a distributed data store to simultaneously provide more than two out of three guarantees:

### Consistency (C)
- All nodes see the same data at the same time
- Ensures data integrity across the system

### Availability (A)
- Every request receives a response (success or failure)
- System remains operational despite failures

### Partition Tolerance (P)
- System continues to operate despite network partitions
- Handles communication failures between nodes

**Trade-off**: You can only guarantee two out of three properties.

## Load Balancing
Distributes incoming network traffic across multiple servers to ensure no single server bears too much load.

### Algorithms
- **Round Robin**: Distributes requests sequentially
- **IP Hash**: Routes requests based on client IP address
- **Least Connections**: Sends to server with fewest active connections
- **Weighted Round Robin**: Assigns different weights to servers

### Benefits
- Improved response times
- Increased throughput
- Better resource utilization
- High availability

## Caching Strategies
Temporary storage of frequently accessed data to improve performance.

### Write Strategies
- **Write-Through**: Data written to cache and database simultaneously
- **Write-Around**: Data written directly to database, bypassing cache
- **Write-Back**: Data written to cache first, then to database later

### Eviction Policies
- **LRU (Least Recently Used)**: Removes least recently accessed items
- **FIFO (First In First Out)**: Removes oldest items first
- **LFU (Least Frequently Used)**: Removes least frequently accessed items

## Storage Solutions

### SQL Databases (Relational)
- **Structure**: Predefined schema with tables and relationships
- **Examples**: MySQL, PostgreSQL, Oracle, SQL Server
- **Use Cases**: ACID transactions, complex queries, data integrity

### NoSQL Databases (Non-Relational)
- **Structure**: Flexible data structures
- **Types**:
  - **Key-Value Stores**: Redis, DynamoDB
  - **Document Databases**: MongoDB, CouchDB
  - **Wide-Column Stores**: Cassandra, HBase
  - **Graph Databases**: Neo4j, Amazon Neptune
  - **Vector Databases**: Pinecone, Weaviate (for AI/ML applications)

## ACID Principles
Properties that guarantee reliable processing of database transactions.

### Atomicity
- All operations in a transaction succeed or fail together
- No partial updates

### Consistency
- Database remains in a valid state before and after transaction
- All constraints and rules are maintained

### Isolation
- Concurrent transactions don't interfere with each other
- Each transaction appears to run in isolation

### Durability
- Committed transactions persist even after system failures
- Data is permanently stored

## How to Choose the Right Solution

### Consider These Factors:
1. **Data Structure**: Structured vs unstructured data
2. **Query Patterns**: Simple lookups vs complex joins
3. **Scale Requirements**: Small dataset vs big data
4. **Consistency Needs**: Strong vs eventual consistency
5. **Performance Requirements**: Read-heavy vs write-heavy workloads
6. **Team Expertise**: Available skills and experience

### Decision Framework:
- **SQL**: When you need ACID compliance and complex relationships
- **NoSQL**: When you need flexibility, scalability, or specific data models
- **Cache**: When you need fast access to frequently used data
- **Load Balancer**: When you need high availability and scalability

