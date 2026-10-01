## Core Distributed Systems & Infrastructure Architecture

* **CAP Theorem & PACELC:** Understanding the fundamental constraints of distributed data and making explicit choices between Consistency, Availability, and Latency.
* **Database Scaling & Sharding:** Horizontal vs Vertical scaling. Designing shard keys to avoid hot partitions and utilizing consistent hashing to minimize data movement during node failures.
* **SQL vs. NoSQL Trade-offs:** When to enforce ACID transactions and relational integrity (PostgreSQL) versus relying on eventual consistency and high-write throughput (Cassandra, MongoDB, DynamoDB).
* **Caching Strategies:** Cache Aside, Read-Through, Write-Through, Write-Back. Understanding cache invalidation mechanisms and mitigating the Thundering Herd problem using jitter and probabilistic early expiration.
* **Message Queues & Event-Driven Architecture:** Decoupling services using Kafka, RabbitMQ, or SQS. Handling consumer group offsets, message ordering guarantees, and exactly-once delivery semantics.
* **Idempotency & Distributed Transactions:** Implementing Saga Patterns (Choreography vs Orchestration) and Two-Phase Commits to maintain data integrity across microservices without holding distributed locks.

## Cloud-Native & Golang/Python Service Patterns

* **Golang Concurrency Modeling:** Designing system throughput around the G-M-P (Goroutine-Machine-Processor) model. Using buffered channels for worker pools and the `context` package for cascading timeouts across microservices.
* **Python Async/Sync Trade-offs:** Knowing when Python's Global Interpreter Lock (GIL) bottlenecks high-throughput I/O. Architecting hybrid systems where Python handles ML/AI heavy lifting and Golang acts as the high-throughput API gateway.
* **API Gateways & Rate Limiting:** Centralizing authentication, SSL termination, and distributed rate-limiting (Token Bucket, Sliding Window Log) before traffic hits internal clusters.
* **Kubernetes (K8s) Topology:** Designing fault-tolerant cluster architectures. Choosing between NodePort, LoadBalancer, and Ingress. Managing stateful services using StatefulSets and Persistent Volume Claims (PVCs).
* **Observability & Telemetry:** Tracing distributed requests using OpenTelemetry/Jaeger. Tracking SLIs/SLOs to identify the source of tail latency and isolating slow database queries or failing dependencies.

## AI Backend & LLM System Design

* **RAG (Retrieval-Augmented Generation) Architecture:** Designing scalable end-to-end pipelines. Evaluating fixed-size versus semantic chunking, embedding generation strategies, and vector indexing algorithms like HNSW (Hierarchical Navigable Small World).
* **Vector Database Scaling:** Designing distributed vector stores (Milvus, Qdrant, pgvector) to handle millions of high-dimensional embeddings with sub-100ms similarity search latency.
* **LLM API Gateways & Routing:** Architecting resilient middleware to route prompts dynamically across multiple LLM providers (OpenAI, Anthropic, local OSS models) based on real-time token cost and latency thresholds.
* **Agentic Workflows & Tool Execution:** Designing state machines (e.g., LangGraph) where LLMs recursively plan, execute tools, and reflect. Securing the execution sandbox for LLM-generated code.
* **Asynchronous AI Processing:** Decoupling slow LLM generation from client connections using WebSockets or Server-Sent Events (SSE) combined with background worker queues.

## Top 10 High-Level Design Questions (Backend + AI)

1. **Design a Multi-Provider LLM Gateway:**
* *Tricky Scenario:* Handling rate limits (HTTP 429) from upstream providers gracefully. Implementing streaming responses (SSE) through multiple proxies without buffering the entire output in memory.


2. **Design an Enterprise RAG Document Ingestion Pipeline:**
* *Tricky Scenario:* Processing massive PDF uploads asynchronously. Handling chunking boundary overlaps to preserve semantic meaning, and designing a mechanism to update the vector index automatically when the source document changes.


3. **Design an Idempotent Payment/Billing System (Stripe/Razorpay):**
* *Tricky Scenario:* Preventing double-charging when the network drops mid-request. Safely processing delayed webhooks and implementing strict transaction boundaries.


4. **Design a Real-Time Ride-Matching System (Uber/Ola):**
* *Tricky Scenario:* Storing and querying high-frequency geographical locations (using Quadtrees or Geohashes) while managing concurrent driver dispatching and ETA calculation.


5. **Design an Agentic Memory Store:**
* *Tricky Scenario:* Semantic deduplication. Merging contradictory user facts automatically (e.g., replacing "User likes Python" with "User prefers Golang over Python") without inflating the vector database indefinitely.


6. **Design a High-Throughput Notification System:**
* *Tricky Scenario:* Prioritizing transactional OTPs over promotional emails. Designing a pluggable architecture to failover seamlessly between external providers (Twilio, Sendgrid) during outages.


7. **Design a URL Shortener (Bit.ly):**
* *Tricky Scenario:* Generating collision-free unique IDs at scale (using Base62 encoding via a Ticket Server or Twitter Snowflake) and implementing aggressive caching for viral links.


8. **Design a Distributed Rate Limiter:**
* *Tricky Scenario:* Synchronizing rate limit counters across multiple API Gateway nodes globally with minimal latency, typically using Redis with Lua scripts to ensure atomicity.


9. **Design an E-commerce Flash Sale Backend:**
* *Tricky Scenario:* Preventing inventory overselling during massive traffic spikes. Bypassing slow relational databases by using Redis for atomic decrements, followed by asynchronous database reconciliation.


10. **Design an Event Logging and Telemetry Service:**
* *Tricky Scenario:* Ingesting millions of events per second without degrading the performance of the core application. Batching events at the edge and flushing them to a scalable messaging broker like Kafka.



## Crucial Architectural Trade-offs for SDE 2

* **Microservices vs Monolith:** Recognizing when distributed systems add unnecessary operational complexity. A senior engineer identifies when a well-architected modular monolith is the superior, more maintainable choice.
* **Dual Writes & Data Consistency:** Handling scenarios where a service must update a database and publish a Kafka event simultaneously. Implementing the Outbox Pattern to avoid inconsistencies if one operation succeeds and the other fails.
* **Cascade Failures & Resilience:** Implementing Circuit Breakers, retries with exponential backoff, and bulkheads to prevent one slow downstream dependency from consuming all server resources and crashing the entire cluster.
* **Synchronous vs Asynchronous Communication:** Choosing between gRPC/REST for operations requiring immediate responses versus Message Queues for workloads that benefit from eventual consistency and decoupled execution.
