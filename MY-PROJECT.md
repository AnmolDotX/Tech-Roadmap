## 1). Product Requirements Document: AI-Powered Local Knowledge Base (Code Name: Memex)

**Product Vision**
Memex is a privacy-first, blazingly fast Markdown knowledge base packaged as a native macOS desktop application. It bridges the gap between secure, local-only filesystem storage and powerful, opt-in AI capabilities. By leveraging a Bring-Your-Own-Key (BYOK) model, users get automated semantic tagging, bidirectional link generation, and document summarization without paying subscription fees or exposing their data to cloud telemetry.

**Technical Stack**

* **Application Framework:** Wails v2 (Go + Webview2/WebKit).
* **Backend:** Go 1.22+, `database/sql` with SQLite (CGO), `fsnotify` for filesystem events.
* **Frontend:** React 18, Vite (SWC compiler), Yarn, Tailwind CSS, Motion.dev, Zustand for client-side state.
* **Target Architecture:** Apple Silicon (M-series) native `.app` binary.

## 1. Core Feature Specifications

**1.1 Local Filesystem Sync & Markdown Parsing**

* The application operates directly on a standard local directory of `.md` files. No proprietary data lock-in.
* A Go background worker uses `fsnotify` to listen for file additions, modifications, or deletions in real-time.
* File events are debounced using Go channels to prevent UI freezing or excessive database writes during rapid typing or Git pulls.
* Parsed Markdown is passed to the React frontend via Wails IPC (Inter-Process Communication).

**1.2 LLM Provider Gateway (BYOK Layer)**

* A dedicated configuration screen allows users to input API keys for Groq, Google AI Studio (Gemini), or GitHub Models.
* The Go backend implements a standard `LLMProvider` interface, allowing dynamic dependency injection based on the user's active key.
* Implement a robust fallback router: if a rate limit (HTTP 429) is hit on Groq, the Go backend automatically retries the request using the GitHub Models endpoint.

**1.3 Background AI Processing Engine (The SDE-2 Showpiece)**

* When a note is modified, a job is pushed to a Go worker pool (managed via Goroutines and WaitGroups) for AI processing.
* **Semantic Tagging:** The LLM analyzes the note content and generates 3-5 highly relevant tags.
* **Daily Summarization:** A cron-like Go scheduler generates a daily digest of all notes modified that day.
* **Bidirectional Linking:** The LLM identifies potential relationships with existing notes and suggests links.
* All AI processing is strictly non-blocking. The React frontend continues to render at 60 FPS while the Go backend handles network requests.

**1.4 Local Relational Graph Database**

* SQLite acts as the local indexing engine.
* **Schema Design:** Tables for `Notes` (ID, Path, Checksum, Last_Modified), `Tags` (ID, Name), `Note_Tags` (Many-to-Many), and `Links` (Source_ID, Target_ID, Context).
* Go's `database/sql` manages connection pooling. Prepare statements are used to prevent SQL injection and optimize read/write speeds.
* The graph structure powers a "Backlinks" panel in the UI, showing users every note that references the current one.

## 2. Frontend User Interface Architecture

**2.1 Editor & Workspace**

* **Vite + SWC:** Fast hot-module replacement during development and optimized bundling for production.
* **Zustand Store:** Manages the active workspace state, current open file, and AI processing status (e.g., a non-intrusive loading spinner in the corner while Go processes tags).
* **Markdown Rendering:** React component that renders markdown in real-time, supporting GitHub Flavored Markdown and code syntax highlighting.

**2.2 Motion & Feedback**

* **Motion.dev:** Implement fluid layout transitions when opening the sidebar, expanding the AI suggestion panel, or switching between note and graph views.
* Ensure animations are hardware-accelerated and do not drop frames when Wails passes large text payloads over the IPC bridge.

## 3. SDE-2 Competency Mapping (Resume & Interview Impact)

Building this specific architecture directly demonstrates the exact skills required for SDE-2 and Senior backend engineering roles:

* **Concurrency & Resource Management:** Using Goroutines, Channels, and WaitGroups to handle background API polling and file system watching without creating race conditions or memory leaks.
* **System Design & Interfaces:** Designing the LLM Gateway using Go interfaces demonstrates an understanding of the Strategy pattern and decoupled architecture.
* **Database Optimization:** Designing an efficient normalized SQLite schema for a local graph network, implementing proper indexing, and handling concurrent SQLite locks.
* **Production Readiness:** Writing custom `Makefile` or shell aliases in `zsh` to handle the Wails build process, managing the cross-compilation to Apple Silicon, and ensuring the final binary is stripped and optimized.

----

## 2). Product Requirements Document: Trace (Context-Aware Research Engine)

**1. Product Overview**
Trace is a self-hosted, privacy-first RAG (Retrieval-Augmented Generation) search engine. It captures technical documentation and articles a user reads, indexes them in a local vector database, and retains this memory for exactly 7 days. Users can query their recent reading history using natural language to retrieve specific code snippets or concepts without relying on generic web search.

**2. System Architecture & Tech Stack**

* **Browser Extension:** React-based Chrome extension for capturing whitelist URLs.
* **Web Dashboard:** React, Vite, Tailwind CSS, deployed on Vercel.
* **Backend API:** Go 1.22+, `go-chi/chi` router.
* **Datastore & Vector Engine:** PostgreSQL with `pgvector` extension.
* **Message Queue:** Redis for asynchronous web scraping and LLM processing.
* **AI/LLM Gateway:** LiteLLM proxy to handle fallback routing between free providers (Groq, GitHub Models, Google AI Studio).
* **Orchestration:** Docker Compose for local development; K3s for VPS deployment.

**3. Core Workflows**
**3.1. Asynchronous Ingestion & Scraping**

* The Chrome extension sends a URL payload to the Go API (`POST /api/ingest`).
* The API validates the domain against the user's whitelist, pushes the URL to a Redis queue, and immediately returns a `202 Accepted` to prevent browser blocking.
* Go background workers (`Goroutines`) consume the Redis queue, download the HTML, strip out navigation/footer noise, and chunk the core text.

**3.2. Vectorization & Storage**

* Using `tmc/langchaingo`, the Go worker sends the text chunks to the LiteLLM proxy.
* LiteLLM routes the embedding request to the configured free-tier provider.
* The Go worker stores the raw chunk, the vector embedding, the source URL, and a `created_at` timestamp in PostgreSQL.

**3.3. RAG Search Pipeline**

* The user submits a query via the React frontend (`GET /api/search?q=...`).
* The Go backend converts the query into a vector embedding.
* A Cosine Similarity SQL query runs against `pgvector` to fetch the top 3 most relevant text chunks saved within the last 7 days.
* The chunks and the user's question are sent to LiteLLM to generate a synthesized, context-aware answer. The response is streamed back to the frontend using Server-Sent Events (SSE).

**3.4. Data Lifecycle Management (7-Day TTL)**

* A background Go scheduler (`robfig/cron`) executes daily at 00:00 UTC.
* It runs a `DELETE` SQL transaction on the PostgreSQL database for any records where `created_at < NOW() - INTERVAL '7 days'`, ensuring compliance with the short-term memory promise.

**4. Open Source & Local Development Setup**

* **BYOK (Bring Your Own Key):** The application relies on a `.env` file where users inject their own `GROQ_API_KEY` or `GITHUB_MODELS_KEY`.
* **Dockerized Environment:** The repository includes a `docker-compose.yml` that spins up the Go API, PostgreSQL (with pgvector pre-installed), Redis, and the LiteLLM proxy container in a single `docker compose up -d` command.
* **LiteLLM Configuration:** A provided `litellm_config.yaml` handles load balancing and rate-limit fallbacks automatically without requiring changes to the Go backend code.

Will the Chrome extension automatically scrape URLs based on a predefined domain whitelist, or will it require a deliberate manual click from the user to save a specific page? : **It should be saved first to save the memory**
