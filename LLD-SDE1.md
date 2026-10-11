### Prerequisites Checklist for LLD

* [ ] **1. OOP Basics**
* **Core Concept:** Syntax & Mechanics
* **Specific Topics:** Classes, objects, constructors, field initializers, access modifiers (`public`, `private`, `protected`), `static` members, `readonly` (final equivalent), method overriding, function/method overloading.
* **TypeScript Nuances:** TypeScript function overloading signatures vs. single implementation signature; compile-time checks vs. runtime prototype emissions.


* [ ] **2. Four Pillars**
* **Core Concept:** Core Foundations
* **Specific Topics:** Encapsulation (data hiding, getters/setters), Abstraction (hiding implementation complexity), Inheritance (hierarchical sub-typing), Polymorphism (subtype polymorphism, method dispatch).
* **TypeScript Nuances:** Favor composition over deep inheritance hierarchies; prototype-chain mechanics behind TS classes.


* [ ] **3. Relationships**
* **Core Concept:** Object Coupling
* **Specific Topics:** Association (peer-to-peer "uses-a"), Aggregation (independent lifecycle "has-a"), Composition (dependent lifecycle "part-of", owner controls destruction).
* **TypeScript Nuances:** Expressing strong vs. weak ownership without manual memory management; managing garbage collection references in long-running Node.js processes.


* [ ] **4. SOLID Principles**
* **Core Concept:** Extensibility Rules
* **Specific Topics:** **S**: Single Responsibility; **O**: Open/Closed; **L**: Liskov Substitution; **I**: Interface Segregation; **D**: Dependency Inversion.
* **TypeScript Nuances:** Dependency injection via constructors/factories; avoiding tight coupling to third-party SDKs; keeping TS interfaces minimal and client-specific.


* [ ] **5. Interface vs. Abstract Class**
* **Core Concept:** Contract Design
* **Specific Topics:** Contracts vs. template implementations, when to pick an interface (pure signature, multiple inheritance), when to pick an abstract class (code reuse, default behavior).
* **TypeScript Nuances:** Interfaces evaporate completely at TS compile time (zero runtime bundle footprint), whereas abstract classes compile down to JavaScript constructor functions.


* [ ] **6. Design Patterns**
* **Core Concept:** Reusable Blueprints
* **Specific Topics:** Creational (Singleton, Factory, Builder), Structural (Adapter, Decorator, Proxy), Behavioral (Strategy, Observer, State, Command).
* **TypeScript Nuances:** Replacing certain classic patterns with native closures/functions when classes are unnecessary; implementing typed EventEmitters for Observer.


* [ ] **7. UML & Diagramming**
* **Core Concept:** Visual Architecture
* **Specific Topics:** **Class Diagrams:** Visibility notations, relationship arrows. **Sequence Diagrams:** Lifelines, activation bars, async calls.
* **TypeScript Nuances:** Translating asynchronous promises, microtasks, and event loops into accurate sequence diagrams.


* [ ] **8. Concurrency & Mechanics**
* **Core Concept:** Application Runtime
* **Specific Topics:** Single-threaded Event Loop, Macrotask vs. Microtask queue, Promise chaining, race condition mitigation in async/await, Idempotency keys.
* **TypeScript Nuances:** Deadlock prevention in async locks, Promise pooling, avoiding unhandled promise rejections.

---

### Top 10 General Backend & Fullstack LLD Problems

#### 1. Design a Parking Lot System

* **Tricky Scenario:** Finding the nearest available slot matching vehicle size (Bike, Car, Truck) with multiple gates operating concurrently.
* **Key Patterns & Structures:** Factory Pattern (Vehicle/Ticket creation), Strategy Pattern (Slot allocation & pricing algorithms), Min-Heap / Priority Queue (finding nearest slot by distance metric).
* **Tradeoffs:** In-memory tracking via Min-Heap offers $O(\log N)$ lookup but requires distributed synchronization/mutexes across multi-instance services. Relying purely on relational DB queries with `SELECT ... FOR UPDATE` trades lookup latency for transactional consistency.
* **Before You Code:** Clarify gate count, whether pricing is dynamic (hourly vs. flat), and whether spot allocation must be deterministic or best-effort under load.

#### 2. Design Splitwise (Expense Sharing)

* **Tricky Scenario:** Minimizing cash-flow transactions across $N$ users (Debt Simplification) and handling rounding precision errors across unequal splits.
* **Key Patterns & Structures:** Strategy Pattern (Split types: Equal, Percentage, Exact), Directed Graph with Greedy/Backtracking algorithms (settling debts with minimum transfers).
* **Tradeoffs:** Graph debt simplification reduces transaction steps from $O(N^2)$ to $O(N)$, but settling debts greedily makes audit logs harder to trace back to original transactions. Using raw IEEE-754 floats introduces fractional cent discrepancies; use integers (smallest currency unit, e.g., cents) or decimal libraries.
* **Before You Code:** Confirm if debt simplification is automatic or opt-in per group, and how split imbalances (e.g., $100 split among 3 people) should be assigned.

#### 3. Design BookMyShow (Seat Booking)

* **Tricky Scenario:** Multiple users attempting to book the exact same high-demand seats simultaneously during payment gateway redirects.
* **Key Patterns & Structures:** State Pattern (`AVAILABLE`, `LOCKED`, `BOOKED`), Strategy Pattern (Seat tier pricing), Distributed Lock / TTL Cache (Redis with auto-expiring keys).
* **Tradeoffs:** Pessimistic DB locking blocks database rows and creates query bottlenecks. Distributed locks with a time-to-live (e.g., 5-minute hold) improve throughput, but require fallback webhooks to restore availability if the user abandons the payment window.
* **Before You Code:** Ask about hold duration, whether seat reservations are temporary holds or final purchases, and how checkout failures are reconciled.

#### 4. Design a Digital Wallet (Payment / Ledger System)

* **Tricky Scenario:** Maintaining strict double-entry ledger balance without race conditions or duplicate deductions when network retries occur.
* **Key Patterns & Structures:** Command Pattern (Encapsulating debit/credit transactions), State Pattern (Transaction state machine: `INITIATED`, `PENDING`, `COMPLETED`, `FAILED`), Idempotency Key storage.
* **Tradeoffs:** Single-entry accounting balances are simpler to query, but double-entry accounting (every debit has an equal credit) provides absolute auditability at the cost of double the row writes.
* **Before You Code:** Clarify overdraft rules, currency conversions, and idempotency guarantees for transient failures.

#### 5. Design a Distributed Rate Limiter

* **Tricky Scenario:** Throttling high-volume API consumers across clustered instances without introducing high database latency or race conditions.
* **Key Patterns & Structures:** Strategy Pattern (Token Bucket, Leaky Bucket, Sliding Window Log, Sliding Window Counter), Decorator / Middleware Pattern.
* **Tradeoffs:** Sliding Window Log gives 100% precision but consumes high memory per user. Sliding Window Counter or Token Bucket uses minimal fixed memory, trading fractional boundary precision for high performance.
* **Before You Code:** Clarify granularity (per-user IP, API token, or route), burst tolerance, and whether response headers must return remaining quota.

#### 6. Design an In-Memory Cache (LRU / LFU)

* **Tricky Scenario:** Achieving strict $O(1)$ operations for both `get` and `put` while handling thread/async concurrency and capacity evictions.
* **Key Patterns & Structures:** Doubly Linked List + Hash Map (for LRU); Hash Map + Frequency-Bucketed Doubly Linked Lists (for LFU).
* **Tradeoffs:** LRU is simple and computationally lightweight, but vulnerable to scans clearing out hot keys. LFU tracks actual popularity better, but adds operational overhead to maintain frequency counts and clear stale historical keys.
* **Before You Code:** Confirm eviction metric (LRU vs. LFU), whether time-based TTL expiration is required, and maximum capacity behavior.

#### 7. Design a Task Management System (Jira / Trello)

* **Tricky Scenario:** Complex workflow transitions with conditional rules (e.g., a card cannot be moved to "Done" unless all subtasks/QA checks are resolved).
* **Key Patterns & Structures:** State Pattern (Workflow states), Observer Pattern (Webhook triggers, notification updates), Composite Pattern (Tasks containing subtasks and checklists).
* **Tradeoffs:** Hardcoding transitions in an enum is fast to develop, but implementing a dynamic state engine with custom board rules requires a flexible graph-based transition schema that adds validation overhead.
* **Before You Code:** Establish whether workflows are fixed or user-customizable, and identify how notifications should be routed.

#### 8. Design an Elevator Control System

* **Tricky Scenario:** Efficient multi-car dispatching under varying peak loads (morning up-peak vs. evening down-peak) using SCAN/LOOK scheduling algorithms.
* **Key Patterns & Structures:** State Pattern (Elevator state: `MOVING_UP`, `MOVING_DOWN`, `IDLE`), Strategy Pattern (Dispatching algorithm), Observer Pattern (Hall button events).
* **Tradeoffs:** A basic First-Come-First-Served approach is trivial to code but terribly inefficient. LOOK/SCAN algorithms maximize throughput and minimize motor wear, but can lead to starvation for calls in opposite directions during heavy traffic.
* **Before You Code:** Clarify number of cars, building height, capacity limits, and emergency/maintenance mode requirements.

#### 9. Design a Vending Machine

* **Tricky Scenario:** Handling state rollbacks when out-of-stock items are selected, change cannot be made, or user cancels transaction mid-payment.
* **Key Patterns & Structures:** State Pattern (`NoCoinState`, `HasCoinState`, `DispensingState`, `SoldOutState`), Strategy Pattern (Cash vs. Card payment), Greedy/Dynamic Programming (Optimal coin change algorithm).
* **Tradeoffs:** Pre-allocating inventory holds upon coin entry avoids dispensing failures, but blocks slots if the user aborts. Returning change via a simple greedy approach fails if denominations are non-standard, requiring DP at the cost of slight compute overhead.
* **Before You Code:** Confirm supported payment methods, exact change requirements, and edge cases when items get stuck or inventory runs empty.

#### 10. Design a Ride-Sharing Matching System (Uber Lite)

* **Tricky Scenario:** Matching riders to nearest available drivers while accounting for driver accept/reject timeouts and real-time location pings.
* **Key Patterns & Structures:** Strategy Pattern (Driver matching algorithm, Surge pricing calculation), Observer Pattern (Driver location updates), Spatial Indexing / Geohash.
* **Tradeoffs:** Polling relational databases for driver coordinates creates extreme I/O load. Using in-memory spatial indexes (QuadTrees or Geohash buckets in Redis) provides fast coordinate range lookups, but requires handling cross-cell boundary edge cases.
* **Before You Code:** Clarify vehicle tiers, matching radius criteria, and driver response timeouts.

---

### Top 10 AI Engineer Specific LLD Problems

#### 1. Design an LLM Gateway & Multi-Provider Router

* **Tricky Scenario:** Seamless fallback across providers (OpenAI, Anthropic, local vLLM) when encountering HTTP 429 rate limits or context length errors, translating schemas dynamically.
* **Key Patterns & Structures:** Strategy Pattern (Model routing: cost-optimized vs. latency-optimized), Adapter Pattern (Normalizing payload/response schemas across different vendor formats), Circuit Breaker Pattern.
* **Tradeoffs:** Standardizing payloads through an internal unified schema adds transformation latency and can obscure vendor-specific unique features (e.g., Anthropic prompt caching or OpenAI reasoning controls).
* **Before You Code:** Establish supported models, fallback criteria, rate-limiting policies, and streaming (SSE) support requirements.

#### 2. Design a Token-Streaming Parser & SSE Handler

* **Tricky Scenario:** Receiving partial token chunks from an LLM stream and parsing embedded JSON or structured output fragments before the complete string is received.
* **Key Patterns & Structures:** Stream Processing Pipeline, Observer Pattern (Emitter pushing tokens to client), State Machine (Lexing and parsing incomplete JSON tokens).
* **Tradeoffs:** Buffering until valid JSON blocks arrive guarantees client-side parser safety, but introduces perceivable latency. Streaming raw text instantly minimizes Time-To-First-Token (TTFT), but forces frontend clients to handle malformed partial JSON strings.
* **Before You Code:** Determine if the stream output contains raw Markdown, structured tools/JSON, or server-sent events, and define error handling on connection drops.

#### 3. Design an Agentic Memory Store (Short-Term & Long-Term)

* **Tricky Scenario:** Managing conversational history within token limits while extracting, deduplicating, and persisting relevant facts to long-term vector storage.
* **Key Patterns & Structures:** Strategy Pattern (Summarization vs. Sliding window pruning), Decorator Pattern (Injecting recalled memory into prompt templates), Repository Pattern (Vector + Relational DB sync).
* **Tradeoffs:** Sliding window pruning is fast and deterministic, but drops critical context older than $N$ turns. LLM-based summarization preserves core facts, but incurs additional API latency and token costs on every turn.
* **Before You Code:** Clarify token limits, persistence requirements, memory retrieval mechanisms (hybrid keyword + vector), and fact conflict resolution strategies.

#### 4. Design a Document Ingestion Pipeline for RAG

* **Tricky Scenario:** Ingesting diverse file types (PDF, Markdown, HTML), segmenting them into semantically cohesive chunks, generating embeddings, and bulk indexing without hitting rate limits.
* **Key Patterns & Structures:** Pipeline / Chain of Responsibility Pattern (Extract $\to$ Normalize $\to$ Chunk $\to$ Embed $\to$ Store), Factory Pattern (Document loaders), Strategy Pattern (Chunking algorithms: fixed-size vs. recursive character vs. semantic sentence boundaries).
* **Tradeoffs:** Fixed-size chunking with overlaps is computationally cheap, but cuts sentences and breaks tabular data. Semantic chunking yields superior retrieval precision, but requires extra inference overhead during ingestion.
* **Before You Code:** Clarify input formats, chunking boundaries, metadata tagging requirements, and rate limit protections for embedding APIs.

#### 5. Design an AI Tool/Function Execution Engine

* **Tricky Scenario:** Sandboxed, safe execution of LLM-invoked external functions (e.g., Python scripts, SQL queries, REST calls) with strict timeout and access controls.
* **Key Patterns & Structures:** Command Pattern (Encapsulating tool calls), Registry Pattern (Dynamic lookup and schema emission for tools), Proxy Pattern (Enforcing permissions and rate limits).
* **Tradeoffs:** Running code in local worker threads is fast with low overhead, but insecure. Containerized sandboxes (Docker/gVisor/WASM) guarantee security, but introduce container startup latency and resource constraints.
* **Before You Code:** Clarify the supported tool types (predefined typed methods vs. arbitrary user-generated scripts), authentication scope, and safety constraints.

#### 6. Design an Evaluation & Ground-Truth Scoring Framework (LLM-as-a-Judge)

* **Tricky Scenario:** Evaluating model outputs against metrics (Hallucination, ROUGE, Semantic Similarity, Toxicity) asynchronously across thousands of test runs.
* **Key Patterns & Structures:** Strategy Pattern (Evaluation metrics), Worker Queue / Producer-Consumer Pattern (Parallel batch runs), Observer Pattern (Progress and metric tracking).
* **Tradeoffs:** Deterministic heuristic metrics (BLEU, ROUGE) run instantly for free, but correlate poorly with actual human reasoning. LLM-as-a-judge provides nuanced reasoning, but costs money, adds latency, and suffers from self-preference bias.
* **Before You Code:** Clarify whether evaluations are synchronous (pre-deployment guardrails) or asynchronous (batch regression suites), and define custom grading rubrics.

#### 7. Design a Prompt Management & Version Control System

* **Tricky Scenario:** Managing prompt templates with variable injection, schema versioning, A/B rollout testing, and prompt regression tracking.
* **Key Patterns & Structures:** Template Method Pattern (Prompt construction and parameter binding), Factory Pattern (Hydrating prompts for target models), Strategy Pattern (Traffic splitting for A/B testing).
* **Tradeoffs:** Storing prompts directly in code keeps revisions aligned with Git commits, but requires a full deployment to change simple text. Storing them in a dynamic service allows zero-downtime hot updates, but introduces runtime fetching overhead and potential schema mismatches.
* **Before You Code:** Clarify parameter validation, template engines (Mustache vs. string interpolation), and whether rollback mechanisms must be automated.

#### 8. Design a Multi-Agent Orchestration Framework

* **Tricky Scenario:** Coordinating multiple specialized agents (e.g., Researcher, Coder, Critic) in sequential, hierarchical, or round-robin execution loops while preventing infinite loops.
* **Key Patterns & Structures:** Mediator Pattern (Orchestrator controlling inter-agent messaging), State Pattern (Execution graph states), Command Pattern (Task handoffs).
* **Tradeoffs:** Hierarchical topologies (manager delegating to workers) keep reasoning structured, but create single-point bottlenecks at the supervisor. Peer-to-peer communication offers dynamic flexibility, but increases the risk of hallucination loops and runaway token usage.
* **Before You Code:** Confirm agent communication topologies (directed acyclic graph vs. state machine), termination criteria, and message passing structure.

#### 9. Design a Semantic Caching Engine

* **Tricky Scenario:** Caching LLM query responses using vector embeddings to return cached answers for semantically equivalent prompts above a confidence threshold.
* **Key Patterns & Structures:** Decorator / Proxy Pattern (Intercepting calls before the LLM gateway), Strategy Pattern (Similarity calculation: Cosine vs. Dot product; threshold tuning).
* **Tradeoffs:** Exact-match key hashing (Redis) is microsecond-fast, but fails on simple rephrasings. Vector similarity caching intercepts similar queries to save tokens, but introduces vector search latency and the risk of returning stale/misaligned responses if similarity thresholds are set too low.
* **Before You Code:** Clarify similarity score threshold cutoffs, cache invalidation policies, and tenant isolation to avoid leaking sensitive cached responses across users.

#### 10. Design a Guardrails & Content Moderation Engine

* **Tricky Scenario:** Inspecting inputs and outputs in real time for PII leaks, prompt injections, and banned topics without adding latency bottlenecks to streaming responses.
* **Key Patterns & Structures:** Chain of Responsibility Pattern (Sequential validator interceptors), Strategy Pattern (Regex matching vs. Local small-model classifiers vs. Remote moderation APIs).
* **Tradeoffs:** Processing through remote moderation APIs provides high precision, but doubles response latency. Fast heuristic filters (regex and local embeddings) add sub-millisecond overhead, but are vulnerable to novel prompt injection techniques.
* **Before You Code:** Define failure actions (fail-open vs. fail-closed), stream-level scanning capabilities, and whether sanitization (masking PII) or full rejection is expected.
