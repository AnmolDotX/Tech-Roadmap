# Backend Engineering Fundamentals

A structured roadmap of the concepts a software engineer should understand to become a capable **Backend Engineer**, with enough frontend knowledge to build and understand complete web applications.

The focus is on fundamentals, practical implementation, and engineering trade-offs rather than memorizing technologies.

## 1. Programming Language Fundamentals

Choose one primary language and become comfortable building production-style applications with it.

- [ ] Syntax, variables, data types, operators, and control flow
- [ ] Functions, scope, closures, and recursion
- [ ] Arrays, strings, hash maps, sets, stacks, and queues
- [ ] Object-oriented programming (OOP)
- [ ] Functional programming fundamentals
- [ ] Error handling and exception propagation
- [ ] Modules, packages, imports, and exports
- [ ] Generics, interfaces, and type systems where applicable
- [ ] Memory management, stack vs heap, and garbage collection
- [ ] Concurrency, parallelism, and asynchronous programming
- [ ] Promises, async/await, event loops, and callbacks where applicable
- [ ] File handling, environment variables, and command-line arguments
- [ ] Dependency management and package managers
- [ ] Debugging, logging, and writing maintainable code
- [ ] Unit testing and language-specific testing tools

**Choose one:** TypeScript/JavaScript with Node.js, Python, Go, or Java.

## 2. Computer Science Fundamentals

- [ ] Data structures and their time/space complexity
- [ ] Big O notation and complexity analysis
- [ ] Common algorithms: searching, sorting, recursion, and hashing
- [ ] Operating system fundamentals
- [ ] Processes vs threads
- [ ] Context switching and scheduling
- [ ] Concurrency, race conditions, and deadlocks
- [ ] Mutexes, locks, and synchronization
- [ ] Memory allocation and virtual memory
- [ ] Filesystems and file permissions
- [ ] Linux command line and shell scripting
- [ ] Basic data representation: binary, hexadecimal, and encoding

## 3. Internet and Networking Fundamentals

Understand what happens when a client communicates with a server.

- [ ] How the internet works
- [ ] Client-server architecture
- [ ] IP addresses: IPv4 and IPv6
- [ ] Public vs private IP addresses
- [ ] Ports and sockets
- [ ] DNS resolution
- [ ] TCP vs UDP
- [ ] TCP handshake, connection termination, and reliability
- [ ] HTTP request/response lifecycle
- [ ] HTTP methods, status codes, and headers
- [ ] HTTP/1.1 vs HTTP/2 vs HTTP/3
- [ ] HTTPS, TLS, and certificates
- [ ] Cookies, sessions, and browser storage
- [ ] Same-origin policy and CORS
- [ ] WebSockets and Server-Sent Events (SSE)
- [ ] Proxies, reverse proxies, and load balancers
- [ ] Latency, bandwidth, packet loss, and timeouts

## 4. Backend Development and API Design

Learn to design, implement, test, and maintain backend services.

- [ ] What a web server and application server do
- [ ] Request lifecycle: routing, middleware, handlers, and responses
- [ ] REST API principles and resource modeling
- [ ] HTTP methods and appropriate status codes
- [ ] Request validation and data sanitization
- [ ] Query parameters, path parameters, headers, and request bodies
- [ ] Pagination, filtering, sorting, and search
- [ ] Consistent API response and error formats
- [ ] Middleware and request lifecycle hooks
- [ ] Centralized error handling
- [ ] API versioning and backward compatibility
- [ ] API documentation with OpenAPI/Swagger
- [ ] File uploads, downloads, and streaming
- [ ] Idempotency and safe retry behavior
- [ ] Rate limiting and request throttling
- [ ] Synchronous vs asynchronous processing
- [ ] Webhooks and webhook verification
- [ ] API testing and integration testing
- [ ] Input validation at system boundaries

### Frameworks and libraries

Learn one framework well instead of learning all of them.

- **Node.js:** Express, Fastify, or NestJS
- **Python:** FastAPI or Django
- **Go:** net/http, Gin, or Fiber
- **Java:** Spring Boot

Also understand the underlying HTTP server, routing, middleware, and request handling concepts independently of the framework.

## 5. Authentication and Authorization

- [ ] Authentication vs authorization
- [ ] Password hashing and salting
- [ ] Sessions and cookie-based authentication
- [ ] JWT: structure, validation, expiry, and limitations
- [ ] Access tokens and refresh tokens
- [ ] OAuth 2.0 and OpenID Connect fundamentals
- [ ] Role-based access control (RBAC)
- [ ] Permission checks and resource ownership
- [ ] Secure password reset and email verification flows
- [ ] Multi-factor authentication fundamentals
- [ ] CSRF, XSS, SQL injection, and SSRF
- [ ] Secrets management and secure configuration
- [ ] HTTPS, security headers, and least privilege
- [ ] OWASP Top 10 awareness

## 6. Database Fundamentals

### Relational databases and SQL

- [ ] Tables, rows, columns, schemas, and data types
- [ ] Primary keys, foreign keys, and constraints
- [ ] CRUD operations
- [ ] SELECT, INSERT, UPDATE, and DELETE
- [ ] JOINs: INNER, LEFT, RIGHT, and FULL
- [ ] GROUP BY, HAVING, aggregate functions, and subqueries
- [ ] Common Table Expressions (CTEs)
- [ ] Indexes and how they improve query performance
- [ ] Composite indexes and index selectivity
- [ ] Query execution plans and EXPLAIN
- [ ] Database normalization and denormalization
- [ ] One-to-one, one-to-many, and many-to-many relationships
- [ ] Transactions and ACID properties
- [ ] Isolation levels and transaction anomalies
- [ ] Locks, deadlocks, and concurrency control
- [ ] Migrations, schema evolution, and seed data
- [ ] Connection pooling
- [ ] Backups, restores, and disaster recovery

### NoSQL databases

- [ ] Relational vs non-relational data modeling
- [ ] Document databases and MongoDB
- [ ] Key-value databases and Redis
- [ ] Document structure, embedding, and referencing
- [ ] Denormalization and access-pattern-driven design
- [ ] Indexing in NoSQL databases
- [ ] Consistency and atomicity guarantees
- [ ] When to choose SQL vs NoSQL

### ORM and database access

- [ ] What an ORM does and its trade-offs
- [ ] Raw SQL vs ORM queries
- [ ] Relationships and eager vs lazy loading
- [ ] The N+1 query problem
- [ ] Transactions through an ORM
- [ ] Connection lifecycle and pooling
- [ ] Query optimization and parameterized queries

**Primary recommendation:** Start with PostgreSQL and SQL before adding MongoDB or other databases.

## 7. Caching and Performance

- [ ] What caching is and why it works
- [ ] Client-side, CDN, application, and database caching
- [ ] Cache-aside, write-through, and write-behind
- [ ] Cache hit ratio and eviction policies
- [ ] TTL and cache invalidation
- [ ] Redis data structures and common use cases
- [ ] Cache stampedes and cache penetration
- [ ] Database query optimization
- [ ] N+1 queries and connection pool saturation
- [ ] Pagination strategies: offset vs cursor
- [ ] Compression and payload-size optimization
- [ ] Profiling, benchmarking, and load testing
- [ ] Latency percentiles: p50, p95, and p99

## 8. Asynchronous Processing and Messaging

- [ ] Why background jobs are needed
- [ ] Job queues and worker processes
- [ ] Producers, consumers, and brokers
- [ ] Message acknowledgment and retry policies
- [ ] Dead-letter queues
- [ ] At-most-once, at-least-once, and exactly-once processing claims
- [ ] Idempotent consumers and duplicate message handling
- [ ] Scheduled and delayed jobs
- [ ] Event-driven architecture
- [ ] Pub/sub messaging
- [ ] RabbitMQ vs Kafka: fundamental differences
- [ ] Kafka topics, partitions, offsets, and consumer groups
- [ ] Eventual consistency and asynchronous workflows
- [ ] Transactional outbox pattern fundamentals

Learn a simple queue and worker system before introducing Kafka.

## 9. Web Server, Reverse Proxy, and CDN

- [ ] What a web server does
- [ ] Static file serving vs dynamic request handling
- [ ] Apache HTTP Server and Nginx fundamentals
- [ ] Reverse proxy configuration
- [ ] Load balancing algorithms
- [ ] TLS termination
- [ ] Virtual hosts and domain routing
- [ ] DNS records and domain configuration
- [ ] Content Delivery Networks (CDNs)
- [ ] Edge caching and cache-control headers
- [ ] Compression and static asset optimization
- [ ] Request buffering, timeouts, and body-size limits
- [ ] Health checks and upstream failure handling
- [ ] Horizontal vs vertical scaling

## 10. Frontend Fundamentals for Backend Engineers

You do not need to become a frontend specialist, but you should understand how your APIs are consumed.

### Browser and web fundamentals

- [ ] How a browser loads a website
- [ ] DNS lookup, TCP/TLS connection, and HTTP requests
- [ ] HTML parsing, CSSOM, DOM, and rendering
- [ ] JavaScript execution and the browser event loop
- [ ] Critical rendering path and page performance
- [ ] Browser caching and storage
- [ ] Cookies, sessions, and same-origin policy
- [ ] CORS and preflight requests
- [ ] Client-side vs server-side rendering
- [ ] Static site generation and hydration
- [ ] Responsive design and accessibility fundamentals
- [ ] Network tab, browser DevTools, and request debugging

### JavaScript and TypeScript

- [ ] Scope, closures, prototypes, and `this`
- [ ] Promises and async/await
- [ ] Event loop and microtask/macrotask queues
- [ ] ES modules and CommonJS
- [ ] TypeScript types, interfaces, unions, and generics
- [ ] Fetch API and HTTP error handling
- [ ] JSON serialization and deserialization

### React fundamentals

- [ ] Components, props, and state
- [ ] Rendering and reconciliation
- [ ] Hooks and component lifecycle concepts
- [ ] State management and data flow
- [ ] Forms and validation
- [ ] API integration and loading/error states
- [ ] Client-side routing
- [ ] Authentication flows in a frontend application
- [ ] Code splitting and lazy loading
- [ ] Server Components and Client Components (Next.js)
- [ ] SSR, SSG, and hydration
- [ ] Frontend testing fundamentals

### Frontend tooling and architecture

- [ ] Bundlers and build tools: Vite, webpack, or similar
- [ ] Transpilation and minification
- [ ] Tree shaking and code splitting
- [ ] Dependency management
- [ ] Environment-specific configuration
- [ ] Microfrontends: purpose, trade-offs, and when to use them
- [ ] Monolithic frontend vs microfrontend architecture
- [ ] Browser performance and Core Web Vitals awareness

Microfrontends and deep React internals are useful specialization topics, not prerequisites for a fresher backend role.

## 11. Software Architecture and Design

- [ ] Layered architecture and separation of concerns
- [ ] Controller-service-repository patterns
- [ ] Modular monoliths
- [ ] Monolith vs microservices
- [ ] Domain modeling and domain boundaries
- [ ] SOLID principles
- [ ] Dependency injection and inversion of control
- [ ] Composition vs inheritance
- [ ] Design patterns commonly used in backend systems
- [ ] DTOs, entities, and domain models
- [ ] Configuration management
- [ ] Clean architecture fundamentals
- [ ] API contracts and service boundaries
- [ ] UML and sequence diagrams
- [ ] ER diagrams and schema design
- [ ] Refactoring and technical debt
- [ ] Design trade-offs and engineering decision records

## 12. System Design Fundamentals

Start with small systems and gradually progress toward distributed systems.

- [ ] Functional and non-functional requirements
- [ ] Capacity estimation: requests per second, storage, and bandwidth
- [ ] Availability, reliability, and durability
- [ ] Scalability and performance
- [ ] Stateless vs stateful services
- [ ] Horizontal and vertical scaling
- [ ] Load balancers and service discovery
- [ ] Replication and database partitioning
- [ ] Sharding strategies
- [ ] Strong vs eventual consistency
- [ ] CAP theorem and its practical implications
- [ ] Synchronous vs asynchronous communication
- [ ] Fault tolerance, retries, timeouts, and circuit breakers
- [ ] Distributed transactions and Saga fundamentals
- [ ] Single points of failure
- [ ] Backpressure and graceful degradation
- [ ] Observability and failure analysis

### Practice designing these systems

- [ ] URL shortener
- [ ] Rate limiter
- [ ] Authentication service
- [ ] File upload and storage service
- [ ] Notification service
- [ ] Background job processing system
- [ ] Chat application
- [ ] E-commerce order management system
- [ ] News feed or activity feed
- [ ] Logging and metrics pipeline

## 13. Docker and Containerization

- [ ] What containers solve
- [ ] Containers vs virtual machines
- [ ] Images, containers, registries, and layers
- [ ] Dockerfile instructions and image builds
- [ ] Multi-stage builds
- [ ] Container networking and port mapping
- [ ] Volumes and persistent storage
- [ ] Environment variables and secrets
- [ ] Docker Compose and multi-container applications
- [ ] Container logs and debugging
- [ ] Health checks and graceful shutdown
- [ ] Container security and non-root execution
- [ ] Image size and build optimization
- [ ] Resource limits and container lifecycle

## 14. Linux, Deployment, and CI/CD

- [ ] Linux filesystem, permissions, and ownership
- [ ] Processes, signals, and process management
- [ ] SSH and remote server access
- [ ] Shell scripting and environment configuration
- [ ] Git, branches, merges, rebases, and pull requests
- [ ] GitHub Actions or another CI/CD platform
- [ ] Build, test, and deployment pipelines
- [ ] Automated tests and quality checks
- [ ] Secrets in CI/CD pipelines
- [ ] Development, staging, and production environments
- [ ] VPS deployment and cloud deployment fundamentals
- [ ] DNS, domains, and TLS certificate renewal
- [ ] Nginx reverse proxy deployment
- [ ] Database migrations during deployment
- [ ] Rollbacks and release strategies
- [ ] Blue-green and rolling deployments
- [ ] Zero-downtime deployment concepts
- [ ] Infrastructure as Code awareness

## 15. Cloud and Infrastructure Fundamentals

Learn the concepts first; use one cloud provider to gain hands-on experience.

- [ ] Compute instances and virtual machines
- [ ] Object storage, such as Amazon S3
- [ ] Managed relational databases
- [ ] Virtual networks, subnets, and firewalls
- [ ] Security groups and network access rules
- [ ] Identity and Access Management (IAM)
- [ ] Load balancers and autoscaling
- [ ] Managed caches and message queues
- [ ] Secrets and configuration services
- [ ] Logging and monitoring services
- [ ] Backups, recovery, and availability zones
- [ ] Cloud cost management
- [ ] Serverless functions and their trade-offs

Cloud platforms to explore: AWS, Google Cloud, Azure, or a VPS provider.

## 16. Testing and Code Quality

- [ ] Unit testing
- [ ] Integration testing
- [ ] End-to-end testing
- [ ] API testing
- [ ] Mocking, stubs, and test doubles
- [ ] Test fixtures and database setup
- [ ] Testing authentication and authorization
- [ ] Testing failure cases and edge cases
- [ ] Contract testing fundamentals
- [ ] Load and stress testing
- [ ] Static analysis, linting, and formatting
- [ ] Code reviews and readable pull requests
- [ ] Test coverage vs meaningful test quality

## 17. Observability and Production Engineering

- [ ] Structured logging
- [ ] Log levels and correlation/request IDs
- [ ] Metrics, logs, and distributed traces
- [ ] Monitoring and alerting
- [ ] Health and readiness checks
- [ ] Error rates, latency, throughput, and saturation
- [ ] Service Level Indicators (SLIs)
- [ ] Service Level Objectives (SLOs)
- [ ] Incident investigation and root cause analysis
- [ ] Graceful shutdown and resource cleanup
- [ ] Retry storms and cascading failures
- [ ] Database and application performance monitoring

## 18. Git and Collaborative Engineering

- [ ] Git fundamentals and commit history
- [ ] Branching and pull request workflows
- [ ] Merge conflicts and their resolution
- [ ] Code review practices
- [ ] Writing clear commit messages
- [ ] Issue tracking and technical documentation
- [ ] API specifications and architecture diagrams
- [ ] Agile development and incremental delivery
- [ ] Feature flags and controlled rollouts
- [ ] Semantic versioning and changelogs

## 19. Advanced and Optional Topics

These are valuable after the core foundations are in place.

- [ ] Kubernetes: pods, deployments, services, and ingress
- [ ] Infrastructure as Code: Terraform
- [ ] Service meshes
- [ ] gRPC and Protocol Buffers
- [ ] GraphQL
- [ ] Advanced Kafka and stream processing
- [ ] Elasticsearch or OpenSearch
- [ ] Vector databases and embeddings
- [ ] Distributed locks and leader election
- [ ] Multi-region architecture
- [ ] Advanced database internals
- [ ] Microfrontends and module federation
- [ ] Serverless architecture
- [ ] FinOps and cloud cost optimization

---

## 20. Practical Projects

Use projects to demonstrate that you can apply the concepts, not just explain them.

### Beginner

- [ ] CRUD REST API with validation and centralized error handling
- [ ] Authentication API with hashed passwords and refresh tokens
- [ ] PostgreSQL schema with foreign keys, indexes, and migrations
- [ ] API documentation and automated integration tests

### Intermediate

- [ ] E-commerce backend with users, products, carts, and orders
- [ ] Redis caching with cache invalidation
- [ ] Background jobs for emails or notifications
- [ ] Rate limiter and API key management
- [ ] File upload service with object storage
- [ ] Dockerized application with CI/CD deployment

### Advanced

- [ ] Order processing with asynchronous events and idempotency
- [ ] Real-time chat using WebSockets
- [ ] Observability dashboard with logs and metrics
- [ ] Scalable URL shortener with analytics
- [ ] Distributed notification service using a message broker

For every project, document the architecture, database schema, API contract, setup instructions, testing strategy, and key trade-offs.

---

## 21. Recommended Learning Order

| Phase | Focus |
|---|---|
| 1 | Programming language, Git, Linux, and CS fundamentals |
| 2 | HTTP, networking, REST APIs, and one backend framework |
| 3 | SQL, PostgreSQL, schema design, transactions, and indexes |
| 4 | Authentication, authorization, security, and testing |
| 5 | Redis, caching, background jobs, and messaging |
| 6 | React/browser fundamentals, API integration, and full-stack basics |
| 7 | Docker, Nginx, CI/CD, and deployment |
| 8 | System design, observability, scalability, and reliability |
| 9 | Advanced distributed systems and cloud infrastructure |

### Suggested primary stack

For a JavaScript/TypeScript-oriented developer:

- **Language:** TypeScript
- **Runtime:** Node.js
- **Framework:** Fastify or NestJS
- **Database:** PostgreSQL
- **Database access:** Prisma or Drizzle, alongside raw SQL
- **Cache:** Redis
- **Messaging:** RabbitMQ first, Kafka later
- **Frontend:** React and Next.js fundamentals
- **Web server:** Nginx
- **Infrastructure:** Linux, Docker, and Docker Compose
- **CI/CD:** GitHub Actions
- **Cloud:** AWS fundamentals

This is one coherent learning stack, not a mandatory industry standard.

## Final principle

A backend engineer should be able to explain **why a system behaves the way it does**, identify its bottlenecks, reason about failure modes, and implement a maintainable solution.

Knowing Docker, Kafka, Redis, Kubernetes, and microservices by name is not the goal. Understanding networking, data modeling, concurrency, reliability, security, and trade-offs is what makes those technologies useful.

**Priority:** Learn the fundamentals, build a working application, deploy it, test it, and improve it before moving to the next technology.
