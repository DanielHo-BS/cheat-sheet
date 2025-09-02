# Database Design

## Overview

Databases store, manage, and serve application data. Choosing the right type directly affects performance, scalability, and reliability.

## SQL vs NoSQL Comparison

### Key differences

| Topic | SQL databases | NoSQL databases |
|------|---------------|-----------------|
| Data model | Structured tables (rows, columns) | Flexible models (JSON, key–value, graph, wide-column) |
| Consistency | Strong (ACID) | Often eventual or tunable |
| Query | Rich SQL, JOINs | Simple queries, usually no JOIN |
| Scaling | Primarily vertical | Horizontal by default/easier |
| Schema | Fixed, predefined | Schema-less or flexible |
| Common use | OLTP/transactions | Big data, caching, logs, content |

### SQL databases

**Key traits:**
- Relational (RDBMS)
- Use SQL
- ACID guarantees (atomicity, consistency, isolation, durability)

**Common products:**
- MySQL, PostgreSQL, Oracle, SQL Server

**Good for:**
- Strong consistency transactional systems
- Stable, well-defined schema
- Complex queries, reports, BI
- Small to medium systems or single-node deployments

### NoSQL database types

#### 1. Key–Value store
- **Products:** Redis, DynamoDB, Riak
- **Traits:** O(1) access by key, very high performance
- **Good for:** Cache, sessions, leaderboards

#### 2. Document store
- **Products:** MongoDB, CouchDB
- **Traits:** JSON/BSON documents, flexible schema
- **Good for:** Content management, API payload storage

#### 3. Wide-column store
- **Products:** Cassandra, HBase
- **Traits:** Column-family layout, large-scale data
- **Good for:** Big data analytics, time series

#### 4. Graph database
- **Products:** Neo4j, ArangoDB
- **Traits:** Nodes and edges, graph traversals
- **Good for:** Social graphs, recommendations, knowledge graphs

### When to choose SQL

- OLTP transactions with strong consistency
- Stable schema (e.g., users, inventory, finance)
- Complex joins and reporting
- Simple deployments with limited scale-out needs
- Mature ecosystem and team familiarity

### When to choose NoSQL

- Evolving or flexible schema (IoT, activity feeds)
- Fast iteration and MVPs
- Store JSON payloads directly
- Massive horizontal scale requirements
- High read/write concurrency, search/stream use cases

## Sharding

### What is sharding

Sharding splits a large database horizontally across multiple nodes to improve capacity and performance.

**Core ideas:**
- Break one large database into multiple smaller shards
- Each shard holds only a subset of data
- Distribute load via a shared-nothing architecture

### Why sharding

**Main drivers:**

1. **Single-node limits**
   - Data outgrows CPU, RAM, or disk on a single machine
   - Vertical scaling alone is insufficient

2. **Performance bottlenecks**
   - Queries slow down on one database
   - Write latency increases and impacts UX

3. **Horizontal scale needs**
   - Add machines to scale out
   - Not just upgrading hardware

### Sharding strategies

#### 1. Range-based sharding

**How it works:**
- Assign data by value ranges
- Example: user_id 1–1000 → shard1, 1001–2000 → shard2

**Pros:**
- Simple and intuitive
- Supports range queries (e.g., BETWEEN)

**Cons:**
- Hotspots form (new users cluster in one shard)
- Load becomes skewed over time

#### 2. Hash-based sharding

**How it works:**
- Hash a key (e.g., hash(user_id) % N → shardN)

**Pros:**
- Even distribution
- Avoids hotspots

**Cons:**
- Range queries require scanning all shards
- Rebalancing is nontrivial without consistent hashing

#### 3. Directory/lookup sharding

**How it works:**
- Maintain a routing table mapping keys to shards
- Example: user_id → shardX

**Pros:**
- Very flexible and reconfigurable
- Can support complex placement rules

**Cons:**
- Operate an extra routing service
- Potential single point of failure

### Sharding challenges

**Main challenges:**

1. **Cross-shard query complexity**
   - JOIN/COUNT/aggregations across shards are expensive
   - Higher latency and operational complexity

2. **Data consistency**
   - Distributed transactions are hard
   - Additional consistency controls are needed

3. **Operational overhead**
   - Resharding is complex
   - Backups, migrations, and monitoring are harder

### Common applications

**Where sharding fits well:**

1. **Large consumer web apps**
   - Social networks at massive scale
   - Single-node DB cannot cope

2. **E-commerce**
   - Large volumes of orders, users, catalog
   - High read/write concurrency

3. **Logs and time series**
   - Rapid growth
   - Requires horizontal scale

### Sharding support by database

| Database | Range-based | Hash-based | Directory-based | Notes |
|----------|-------------|------------|-----------------|-------|
| MySQL | Yes (app layer) | Yes (app layer) | Yes (Vitess, ShardingSphere) | No native sharding |
| MongoDB | Yes (native) | Yes (native) | Yes (Config Server + Mongos) | Sharding is core |
| Redis | No (poor for ranges) | Yes (Redis Cluster) | Caution (custom routing) | Best with hashing |
| Cassandra | Limited | Yes (consistent hashing) | No | Avoids hotspots by design |


### Handling JOINs after sharding

**Context:**
- Single-node: SQL engine performs JOINs
- After sharding: data lives on different nodes; JOINs become distributed

**Approaches:**

#### 1. Avoid cross-shard JOINs (recommended)

**How:**
- Avoid JOIN dependencies at schema design time
- Co-locate related entities in the same shard
- Example: shard by user_id so users and orders live together

**Best for:**
- User-centric data (accounts, orders, carts)
- Entities sharing the same sharding key

#### 2. Denormalization

**How:**
- Duplicate frequently needed related fields
- Example: store user_name directly in orders to avoid JOIN to users

**Pros:**
- Faster reads
- Fewer cross-shard lookups

**Cons:**
- More storage
- Data synchronization required

**Best for:**
- Read-dominant workloads
- Infrequently changing reference data

#### 3. Application-side JOIN

**How:**
- Implement JOIN logic in the app
- Fetch primary records, then fetch related ones by IDs

**Pros:**
- Clear and controllable logic
- Tunable per use case

**Cons:**
- More network round-trips
- Slower than single-node JOINs

#### 4. Distributed SQL engines

**Tools:**
- ShardingSphere, Vitess, TiDB, Presto, SparkSQL

**Pros:**
- Transparent to the application
- Lets you write SQL as usual

**Cons:**
- Higher operational cost
- Slower than single-node JOINs

**Best practices:**
- Design for co-location
- Prefer denormalization and app-side assembly
- Minimize cross-shard queries

## Replication

### What is replication

Replication copies data from a primary (master) to one or more replicas (slaves/secondaries).

**Goals:**
- High availability
- Read/write splitting
- Fault tolerance
- Higher read throughput

### Replication modes

#### 1. Master–Slave

**How it works:**
- One primary handles writes
- Multiple replicas handle reads
- Data streams from primary to replicas

**Pros:**
- Simple
- Great for read-heavy workloads

**Cons:**
- Failover requires promotion
- Primary becomes a write bottleneck

**Examples:** MySQL master–slave, Redis replication

#### 2. Multi-master

**How it works:**
- Multiple primaries accept writes and sync with each other

**Pros:**
- Scales writes
- Higher availability

**Cons:**
- Conflict resolution is complex
- Consistency is harder to guarantee

**Examples:** MySQL Group Replication, CouchDB

#### 3. Synchronous replication

**How it works:**
- Primary waits for all replicas to commit before ACK

**Pros:**
- Strong consistency
- Minimal data-loss risk

**Cons:**
- Higher latency, lower throughput
- Any replica issue impacts writes

#### 4. Asynchronous replication

**How it works:**
- Primary ACKs immediately; replicas catch up later

**Pros:**
- Low latency, high throughput
- Writes unaffected by replica lag

**Cons:**
- Replica lag; possible data loss on failover

#### 5. Semi-synchronous

**How it works:**
- Primary waits for at least one replica

**Pros:**
- Balance between consistency and performance

**Cons:**
- Some latency; more moving parts

### Replication in common databases

- MySQL: asynchronous by default; master–slave common
- PostgreSQL: supports synchronous and asynchronous modes
- MongoDB: replica sets with automatic elections
- Redis: master–replica with Sentinel and Cluster mode

### Replication challenges

1. **Consistency under async replication**
   - Force reads to primary for strict consistency
   - Read-your-write: route user reads to primary after a write
   - Session stickiness: pin a session to a single node
   - Semi-sync: wait for at least one ACK
   - Version/timestamp checks: ensure read version ≥ last write

2. **Failover**
   - Manual promotion of a replica
   - Automatic failover/election
   - VIP/proxy switching (HAProxy, ProxySQL)
   - Avoid split-brain (Raft, Paxos, ZooKeeper, etcd)

3. **Write bottlenecks**
   - Vertical scale-up
   - Sharding (horizontal scale)
   - Multi-master architecture

4. **Network latency**
   - Semi-sync within a region
   - Local read replicas
   - Async cross-region with eventual consistency
   - Compression and batched transfer

## CAP Theorem

CAP states that a distributed data store can provide at most two of three guarantees: Consistency, Availability, and Partition tolerance.

1. **Consistency (C)**
   - Every read sees the most recent write (e.g., bank balance updates immediately)

2. **Availability (A)**
   - Every request receives a response, even during failures

3. **Partition tolerance (P)**
   - The system continues operating despite network partitions

### Common combinations

| Choice | Properties | Examples | Notes |
|--------|-----------|----------|-------|
| CA | Consistency + Availability (no partitions assumed) | Single-node SQL (MySQL, PostgreSQL) | Valid only when partitions are out of scope |
| CP | Consistency + Partition tolerance | HBase, MongoDB (primary–secondary) | May reject requests during partitions to keep consistency |
| AP | Availability + Partition tolerance | Cassandra, DynamoDB, Riak, Redis Cluster | Serve during partitions; converge eventually |

### When to prefer CA/CP/AP
- CA: single-node or same-DC deployments; strong consistency
- CP: financial/orders; reject requests under partitions
- AP: large-scale internet systems; accept temporary inconsistency for availability

