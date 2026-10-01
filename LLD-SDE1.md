## Essential LLD & System Design

To pass machine coding and LLD rounds, you must master how to translate business requirements into working, modular code—specifically utilizing TypeScript interfaces, classes, and async paradigms.

### 1. Object-Oriented & Functional Design

* **SOLID Principles:**
* *Single Responsibility:* A class/module should do one thing.
* *Open/Closed:* Use TypeScript interfaces to extend behavior without modifying existing core logic.
* *Liskov Substitution:* Subclasses must behave exactly like their base classes.
* *Interface Segregation:* Break large monolithic interfaces into smaller, specific ones.
* *Dependency Inversion:* Inject dependencies (like database clients or LLM providers) rather than hardcoding them.


* **Design Patterns:**
* *Creational:* Factory (generating different LLM clients or game pieces), Singleton (database connection pool), Builder.
* *Structural:* Decorator (adding rate limiting to routes), Adapter (normalizing API responses).
* *Behavioral:* Strategy (pricing algorithms, routing logic), Observer (Event Emitters, Pub/Sub), State (order/workflow transitions).



### 2. Database & Data Modeling

* **Entity-Relationship (ER) Modeling:** Identifying entities, their attributes, and relationships (1:1, 1:N, M:N).
* **Normalization:** 1NF, 2NF, 3NF to eliminate data redundancy. Understand when to purposely *denormalize* for read performance.
* **Database Concurrency:** ACID properties, transaction isolation levels, Optimistic vs. Pessimistic locking (critical for booking systems and wallets).
* **Indexing strategies:** B-Trees, Hash indexes, and Vector indexes (HNSW for AI embeddings).

### 3. Diagramming & Architecture

* **UML Diagrams:**
* *Class Diagrams:* Map out classes, interfaces, inheritance, and composition.
* *Sequence Diagrams:* Trace the flow of asynchronous API calls across services.
* *State Diagrams:* Map out transitions (e.g., Order Placed -> Paid -> Shipped).



### 4. Application Mechanics

* **Concurrency in Single-Threaded Environments:** Mastering the Event Loop, handling race conditions in async/await workflows, and managing Promise pooling.
* **Idempotency:** Ensuring retried network calls (like payments) do not result in duplicate actions.
* **Clean Code Practices:** DRY (Don't Repeat Yourself), intuitive variable naming, and rigorous error handling (try/catch blocks with custom error classes).

---

## Top 20 LLD Problems for SDE-1 (General & AI)

### General Backend & Fullstack (1-15)

1. **Design a Parking Lot**
* **Tricky Scenario:** Concurrency when two cars enter opposite gates simultaneously targeting the last available spot. Implementing a nearest-spot allocation strategy efficiently.


2. **Design Splitwise (Expense Sharing)**
* **Tricky Scenario:** The debt simplification algorithm. If A owes B, B owes C, and C owes A, the system must resolve this to minimize total transactions using a greedy algorithm or graph traversal. Precision errors in floating-point currency splits.


3. **Design an E-Commerce Checkout / Inventory System**
* **Tricky Scenario:** Handling inventory reservations. If a user adds an item to their cart, do you deduct inventory immediately or at payment? Managing lock timeouts so abandoned carts return items to the pool.


4. **Design a Digital Wallet (PhonePe/Paytm)**
* **Tricky Scenario:** Ensuring strict ACID compliance during a transfer between two users. Handling network timeouts where the money leaves User A but the API crashes before reaching User B (requires Idempotency keys and robust retry logic).


5. **Design a Rate Limiter**
* **Tricky Scenario:** Implementing Sliding Window or Token Bucket algorithms in memory. Handling high-throughput concurrent requests without creating race conditions that bypass the limit.


6. **Design BookMyShow (Seat Booking)**
* **Tricky Scenario:** Preventing double-booking. You must implement a distributed lock or pessimistic row lock on the seat while the user is on the payment gateway, and release it exactly after 5 minutes if unpaid.


7. **Design an In-Memory Cache (LRU/LFU)**
* **Tricky Scenario:** Achieving O(1) time complexity for both `get` and `put` operations. Requires combining a Hash Map with a Doubly Linked List, and managing garbage collection/eviction accurately.


8. **Design a Task Management System (Jira/Trello)**
* **Tricky Scenario:** Implementing a flexible state machine where rules govern transitions (e.g., a ticket cannot move to "Done" unless the "QA" subtask is closed). Designing the Observer pattern to notify assignees on changes.


9. **Design Snake and Ladders**
* **Tricky Scenario:** Handling infinite loops (a snake taking you to a ladder that takes you back to the snake). Extending the game to handle $N$ players and $M$ dice seamlessly.


10. **Design an Elevator System**
* **Tricky Scenario:** The dispatch algorithm (SCAN or LOOK algorithm). If an elevator is going up to floor 10 and someone presses "Up" on floor 5, the elevator should stop on the way, rather than finishing its trip and coming back.


11. **Design a Vending Machine**
* **Tricky Scenario:** The State pattern. Transitioning correctly between `Idle`, `HasMoney`, `Dispensing`, and `Refunding`. Calculating optimal exact change using dynamic programming (Coin Change problem).


12. **Design a Notification Service**
* **Tricky Scenario:** Deduplication and priority routing. If a user triggers 5 actions that send an email, batch them into one. Fallback logic: if the SMS gateway fails, immediately try the Push Notification gateway.


13. **Design a Chess Game Validator**
* **Tricky Scenario:** Validating complex moves like Castling, En Passant, and Pawn Promotion. The toughest edge case is verifying if a requested move leaves the player's *own* King in check (which makes the move illegal).


14. **Design a Ride-Sharing System (Uber Matching)**
* **Tricky Scenario:** Managing the dynamic state of drivers (Offline, Available, In-Trip). Calculating surge pricing based on real-time geofenced demand and supply using the Strategy pattern.


15. **Design a Message Queue (Kafka/RabbitMQ lite)**
* **Tricky Scenario:** Handling consumer offsets. If a consumer crashes halfway through processing a batch of messages, the system must know exactly which messages were successfully processed and which need redelivery.



### AI Engineer Specific (16-20)

16. **Design an LLM API Gateway & Router**
* **Tricky Scenario:** Fallback routing. If the primary OpenAI endpoint hits a rate limit (429) or times out, the system must seamlessly rewrite the prompt format and route the request to a fallback Anthropic or local model without failing the user request.


17. **Design an Agentic Memory Store**
* **Tricky Scenario:** Semantic deduplication. If the store already has "User likes React", and a new input says "User prefers React over Vue", the system must merge/update the vector rather than storing two conflicting redundant facts.


18. **Design a Document Ingestion Pipeline for RAG**
* **Tricky Scenario:** Chunking boundaries. If you split a PDF strictly by character count, you might slice a sentence in half, destroying its semantic meaning. Designing a strategy to chunk by semantic paragraphs with dynamic overlap.


19. **Design an AI Tool Execution Engine**
* **Tricky Scenario:** Security and sandboxing. If an LLM generates a Python script to solve a math problem, designing the execution environment to run that script safely without exposing the host system to infinite loops or malicious code.


20. **Design a Prompt Management System**
* **Tricky Scenario:** Version control for prompts. Treating prompts like code variables—allowing A/B testing of two different system prompts simultaneously and tracking which one yields a lower hallucination rate or higher user satisfaction.



---

## 1-Month SDE 1 Accelerated Roadmap

* Week 1: Language Core & LLD Fundamentals
**Focus:** Mastering the runtime, async paradigms, and design patterns.

* **Concepts:** Deep dive into the JavaScript Event Loop, Promises, `async/await`, Closures, and Prototypal Inheritance.
* **TypeScript:** Interfaces, Generics, Enums, and Utility Types (`Partial`, `Pick`, `Omit`).
* **LLD:** Implement basic design patterns (Singleton, Factory, Observer, Strategy) in plain TypeScript.
* **Practice:** Code purely in-memory solutions for **Snake & Ladders** and **In-Memory Cache (LRU)**. Focus on clean class structures and DRY principles.


* Week 2: Backend Engineering & Databases
**Focus:** APIs, state persistence, and concurrency control.

* **Backend:** Setup production-ready Express or Fastify servers. Implement middlewares, error boundaries, and rate limiting.
* **Databases:** Relational modeling with PostgreSQL. Understand 1NF-3NF, indexing, and ACID transactions.
* **Advanced DB:** Implement pessimistic locking for concurrent requests (e.g., `SELECT ... FOR UPDATE`).
* **Practice:** Build the backend for **BookMyShow** or a **Digital Wallet**. Write raw SQL queries to handle concurrent bookings or money transfers safely.


* Week 3: AI Integration & System Orchestration
**Focus:** Integrating LLMs, vector databases, and real-time streaming.

* **AI Engineering:** Work with LiteLLM or direct SDKs. Master function calling (tool use) and structured JSON outputs from LLMs.
* **Vector Data:** Setup `pgvector` locally. Learn text chunking, embedding generation, and cosine similarity search.
* **Real-time:** Implement Server-Sent Events (SSE) or WebSockets to stream LLM responses token-by-token to a client.
* **Practice:** Build the **LLM API Gateway** or the **Agentic Memory Store** problem, utilizing TypeScript to manage strict interfaces for API requests and LLM tool schemas.


* Week 4: Infrastructure, Containers & Mock Interviews
**Focus:** Packaging the code for production and machine coding constraints.

* **Docker:** Write multi-stage Dockerfiles. Understand image layers, `.dockerignore`, and keeping image sizes small. Use Docker Compose to spin up your backend, Postgres, and Redis simultaneously.
* **Kubernetes (KinD):** Deploy your containerized app to a local KinD cluster. Write manifests for Deployments, Services, and ConfigMaps.
* **Testing:** Write unit tests using Jest or Vitest to prove your LLD business logic works under edge cases.
* **Practice:** Time-box yourself. Pick 3 complex problems (e.g., **Parking Lot**, **Splitwise**, **Task Tracker**) and build fully working, modular, and testable CLI or API versions in exactly 90 minutes each.
