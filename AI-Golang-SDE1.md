# 🎯 Frontend Engineer → AI / LLM Application Engineer (Go-first)

> **Your goal:** land a first AI Engineer / LLM Application Engineer / AI Platform (backend) role, with an offer in the **$80k–$100k** range
> **Your starting point:** frontend/UI engineer
> **Not in scope:** research, model training, deep ML math
> **Language plan:** Go as the core, with working fluency in Python and TypeScript for market reality
> **Time:** ~28 weeks of focused learning (12–15 hrs/week alongside a job), then an active job hunt

---

## 📋 Table of Contents

1. [TL;DR](#1--tldr)
2. [Reality Check: Level, Salary & Geography](#2--reality-check-level-salary--geography)
3. [What Employers Actually Hire For](#3--what-employers-actually-hire-for)
4. [Your Edge as a Frontend Engineer](#4--your-edge-as-a-frontend-engineer)
5. [Language Strategy: Go vs Python vs TypeScript](#5--language-strategy-go-vs-python-vs-typescript)
6. [Timeline at a Glance](#6--timeline-at-a-glance)
7. [Learning Modules (with market overview per topic)](#7--learning-modules)
8. [Portfolio Projects](#8--portfolio-projects)
9. [Job Search Playbook](#9--job-search-playbook)
10. [Interview Prep Bank](#10--interview-prep-bank)
11. [Master Checklist](#11--master-checklist)
12. [Sources](#12--sources)

---

## 1. ⚡ TL;DR

1. **Target role:** *AI Application Engineer* (full-stack, frontend-leaning) first, *AI Platform / Backend* second. You are not aiming at ML Engineer or research.
2. **Target level:** SDE-1 to SDE-2 (mid) with a "software engineer who ships LLM features" profile. Your frontend years count for a lot. You are *not* a fresher.
3. **Hiring is portfolio-heavy.** Employers want shipped, deployed, evaluated projects far more than certificates.
4. **Biggest honesty point:** most AI job postings ask for **Python** (and/or TypeScript). Go is a strong **differentiator** for platform/gateway/infra roles but is rarely the only language required. So learn Go deeply, and also build the same core ideas in Python.
5. **$80–100k is realistic only on certain paths** (Section 2). Plan for a first offer in a lower band if you are India-based and applying locally, and plan how to reach the higher band (remote/global roles, or after 1–2 years of production AI experience).
6. **Most valuable differentiators:** evals, observability, RAG quality, agent reliability, streaming UX, and cost/latency control. Almost no tutorial-level candidates have these.

---

## 2. 🧪 Reality Check: Level, Salary & Geography

> Salary sites disagree a lot and many are marketing pages. Treat every number below as **indicative**, not guaranteed.

### What the data suggests

| Market | Indicative data (2026) | What it means for you |
|---|---|---|
| **US, "entry-level"** | Sources range from about **$69k** (ZipRecruiter-type average) to **$88k** to **$100k–$135k** base. One recruiter guide stresses that "entry-level" AI offers often go to people with a CS degree/master's and real project work. | $80–100k lies inside the US range. Getting a US-company offer without a degree edge means you need strong evidence of shipped work. |
| **US, mid-level** | About **$120k–$220k** depending on the source. | Your SDE-2-equivalent target eventually. |
| **India, freshers / IT services** | Roughly **₹6–9 LPA** for AI-titled roles. | Not your target. |
| **India, mid-level applied AI (2–5 yrs)** | One guide reports ~₹20 LPA average, top 25% ~₹32 LPA, top 10% ~₹40 LPA. Another reports **₹30–55 LPA** at global tech offices for mid-level. | A realistic landing zone for a strong frontend engineer who builds real LLM projects. |
| **India, senior/remote** | One guide cites **₹60–80 LPA equivalent** for senior AI engineers working remotely from India. | This is the band where $80–100k lives if you're India-based. |

> 💱 **Conversion:** $80–100k is roughly **₹70–90 LPA** at recent exchange rates. Check today's rate.

### Honest conclusions

- **If you're in India and apply locally:** a first AI role at roughly **₹15–45 LPA** is the achievable range depending on your current experience, company type (startup vs GCC vs product) and portfolio. Reaching $80–100k-equivalent usually takes **either** a remote/global employer **or** 1–2 years of production AI experience on your CV.
- **If you're targeting US/EU remote roles:** doable but very competitive. Expect strict screening, timezone expectations, and often contractor terms. Your open-source work, demos and writing matter more than anywhere else.
- **If you already have 3+ years of frontend experience,** the transition can come with a strong salary step. One guide reports a 60–100% jump when engineers move from AI integration work at services firms to production LLM work at product companies. Treat that as an upper-end example, not a promise.
- **Time reality:** employed engineers often need **6–12 months** of consistent work to get a portfolio strong enough. Your 6-month learning plan plus 2–4 months of focused applying is a sensible budget.

### Which level to apply for

| If you have... | Apply for | Notes |
|---|---|---|
| 0–2 yrs frontend | AI Engineer (junior) / SDE-1 / full-stack with AI | Portfolio must carry you. Consider startups. |
| 2–5 yrs frontend | AI Engineer / SDE-2 / "Applied AI Engineer" | Sweet spot. Frame yourself as a product engineer who ships AI features. |
| 5+ yrs frontend | AI Engineer (mid/senior) / "AI Product Engineer" | Lean on UX, architecture and ownership. |

> ❓ **Fill this in for yourself:** years of experience: ___ · country/city: ___ · current salary: ___ · target date: ___

---

## 3. 🏢 What Employers Actually Hire For

Reports from 2026 hiring data and skills guides agree on a common core:

| Skill area | What "good" looks like |
|---|---|
| **LLM application development** | Prompt design, structured outputs, tool/function calling, predictable failure handling |
| **RAG engineering** | Chunking, embeddings, retrieval quality, reranking, citations |
| **Agent building** | Loops with tools, state, limits, human-in-the-loop |
| **Evaluation** | Datasets, regression tests, LLM-as-judge, RAG metrics |
| **Production deployment** | Docker, cloud, latency/cost, observability |
| **Software engineering basics** | Clean APIs, testing, version control, system design |

Other consistent signals:
- The role is mainly a **software engineering discipline** applied to LLM systems: you engineer the system around a probabilistic API.
- Typical postings list **Python** (sometimes Java) plus LLM APIs, agents and a cloud platform. Common named skills in lists include LangChain and RAG.
- Hiring is **portfolio-heavy**. Most hires at competitive companies come with shipped projects, not AI-specific degrees.
- Teams do not expect mastery of every layer, but they expect you to explain how the layers connect, starting at the LLM application layer.

---

## 4. 💪 Your Edge as a Frontend Engineer

Most AI engineer candidates are weak at UX. You are not. Lean into it:

- **Streaming UIs:** token-by-token rendering, stop/regenerate, optimistic UI, error recovery, markdown/code rendering
- **Generative UI:** model-driven components, tool results rendered as widgets
- **Voice and multimodal:** microphone input, realtime audio, image upload and vision
- **Product sense:** you know what makes an AI feature feel fast and trustworthy (latency perception, loading states, citations, feedback buttons)
- **TypeScript:** your existing strength. Many AI product teams use TS end to end.

**Positioning statement:**
> "I'm a product engineer who ships AI features end to end: streaming frontend, a typed backend (Go/Python), retrieval and agent logic, evals and observability."

**Your gaps to close** (backend-side, since you're coming from frontend): HTTP/REST depth, auth, databases (Postgres), caching, queues, Docker, cloud basics, testing and system design. These are built into the modules below.

---

## 5. 🗣️ Language Strategy: Go vs Python vs TypeScript

### Honest market picture

| Language | Role in AI jobs | Strengths | Weaknesses |
|---|---|---|---|
| **Python** | The default for AI app code, evals, data work, notebooks, most tutorials and most SDK/example coverage | Largest ecosystem (LangChain, LangGraph, LlamaIndex, Pydantic, FastAPI, Ragas), fastest prototyping, document parsing, ML libraries | Slower runtime, concurrency/GIL nuances, packaging/typing hygiene needs discipline |
| **TypeScript/JS** | Common for AI product teams and full-stack AI apps | Same language front to back, Vercel AI SDK, strong typing with Zod, great streaming UI ecosystem | Fewer data/eval libraries than Python, CPU-heavy work is awkward |
| **Go** | Gateways, proxies, orchestration services, infra tooling, high-concurrency backends | Goroutines/channels, tiny memory footprint, single static binary, fast startup, simple deployment, great for streaming proxies | Smaller AI ecosystem, fewer framework options, fewer jobs that list Go as the *only* requirement, no Pydantic-equivalent runtime validation magic |

### Recommended plan for you

| Layer | Use |
|---|---|
| UI | TypeScript/React (you already have this) |
| Core AI backend learning + gateway/infra projects | **Go** |
| RAG experiments, evals, notebooks, framework literacy | **Python** (read and write comfortably) |
| Interview answers | Be able to explain *why* you'd pick each language for a given job |

**Rule of thumb for interviews:**
- "Python for model-adjacent, data and eval work and rapid iteration."
- "TypeScript for product surface and full-stack velocity."
- "Go when I need high concurrency, low memory, predictable latency, or a simple deployable service, like a gateway."

---

## 6. 🗓️ Timeline at a Glance

```
Weeks 1-3     M0-M1   LLM fundamentals + Python bridge
Weeks 4-8     M2-M3   Go core + backend skills + streaming API + provider abstraction
Weeks 9-10    M4      AI frontend/UX showcase (your edge)
Weeks 11-14   M5      RAG (Go + Python comparison)
Weeks 15-18   M6-M7   Agents, tools, MCP, concurrency & agent runtime
Weeks 19-21   M8      Memory, caching, queues, durable workflows
Weeks 22-24   M9-M10  Evals + observability
Weeks 25-26   M11-M12 Security + deployment
Weeks 27-28   M13-M14 Inference overview + system design/interview prep
Weeks 20+     Start applying (portfolio is already strong by then)
```

---

## 7. 📚 Learning Modules

Each module has: **Learn → Market overview → Go vs Python vs JS → Deliverable**.

---

### M0 · Weeks 1–2 · LLM Fundamentals & Prompting

**Learn**
- [ ] Tokens, context windows, temperature/top-p, system/user/assistant roles, stop sequences
- [ ] Prompting: few-shot, step-by-step reasoning, role/format control, **structured outputs / JSON schema mode**
- [ ] Hallucination, grounding, citations
- [ ] Cost, latency and TTFT, prompt caching, batch APIs, rate limits
- [ ] Embeddings (what they are, how similarity works)
- [ ] Call provider APIs directly (`curl`/Postman), then via SDKs. Try OpenAI, Anthropic, Gemini and a local model via **Ollama**.

**Market overview**

| Area | Popular |
|---|---|
| Frontier providers | OpenAI, Anthropic (Claude), Google (Gemini), Mistral, Cohere, xAI |
| Hosted open models | Together, Fireworks, Groq, OpenRouter |
| Local | Ollama, LM Studio, llama.cpp |
| Learning | Provider docs and cookbooks, prompt-engineering guides |

**Deliverable:** a TypeScript CLI or small web page that streams responses from two providers and shows token usage and latency.

---

### M1 · Weeks 2–3 · Python Bridge (read + write, not mastery)

**Learn**
- [ ] `uv`/venv, functions, classes, dataclasses, type hints
- [ ] `async/await`, `asyncio.gather`, `httpx`
- [ ] **Pydantic v2** (structured outputs and validation)
- [ ] **FastAPI** basics with streaming responses
- [ ] Read LangChain/LangGraph/LlamaIndex example code without fear

**Market overview**

| Area | Python | JS/TS | Go |
|---|---|---|---|
| Web framework | FastAPI, Flask, Django | Express, Fastify, Hono, Next.js | `net/http`, chi, Gin, Echo |
| Validation | Pydantic | Zod | struct tags + `validator` |
| Async model | asyncio | event loop + promises | goroutines + channels |

**Deliverable:** a FastAPI endpoint that streams a model response and returns a Pydantic-validated JSON object.

---

### M2 · Weeks 4–6 · Go Core + Backend Skills

**Learn (Go)**
- [ ] Types, structs, **struct tags**, methods, pointer vs value receivers
- [ ] Interfaces (implicit), embedding, generics basics
- [ ] **Errors as values:** `%w`, `errors.Is`, `errors.As`
- [ ] Packages, modules, simple project layout
- [ ] Testing: table-driven tests, `httptest`, `-race`
- [ ] Tooling: `go vet`, `golangci-lint`, `pprof` basics

**Learn (backend skills for a frontend dev)**
- [ ] HTTP in depth (methods, status codes, headers, CORS, timeouts)
- [ ] Auth basics (API keys, JWT, sessions)
- [ ] **Postgres** + SQL + migrations, `pgx`
- [ ] Docker basics, environment config, `log/slog`

**Market overview**

| Topic | Go | Python | JS/TS |
|---|---|---|---|
| Error handling | explicit `err` values | exceptions | exceptions / promise rejection |
| Typing | static, compiled | gradual (type hints) | static via TS (erased at runtime) |
| DB access | pgx, sqlc, GORM | SQLAlchemy, SQLModel, asyncpg | Prisma, Drizzle, Knex |
| Deployment unit | single static binary | virtualenv + deps | node_modules + runtime |

**Deliverable:** a small Go REST service (auth + Postgres + tests + Dockerfile).

> 💡 **Mindset map from frontend:** `fetch` → `http.Client` · React props types → structs · `Promise.all` → `errgroup` · `try/catch` → `if err != nil` · `useEffect` cleanup → `context.Context` cancellation

---

### M3 · Weeks 6–8 · Streaming APIs, Provider Abstraction & Structured Output

**Learn**
- [ ] **SSE** with `http.Flusher`, client-disconnect handling
- [ ] `LLMClient` interface + **factory pattern** for multiple providers
- [ ] OpenAI-compatible API shape (many providers copy it)
- [ ] **Structured output:** JSON schema, validation, **retry on invalid output**
- [ ] Rate-limit handling: retries with jittered backoff, 429 handling, fallback provider

**Market overview**

| Need | Python | JS/TS | Go |
|---|---|---|---|
| Unified provider access | **LiteLLM**, LangChain wrappers | **Vercel AI SDK**, LangChain.js | official SDKs, langchaingo, Eino, Genkit, Bifrost |
| Hosted gateway | OpenRouter, Portkey, Helicone, Cloudflare AI Gateway | same | same |
| Structured output | Pydantic, Instructor, Pydantic AI | Zod + AI SDK `generateObject` | structs + `invopop/jsonschema` + validator |

**Go vs Python trade-off:** Go gives you typed structs and cheap concurrency for streaming many connections. Python gives you Pydantic + Instructor ergonomics and faster iteration. In Go you write more code for validation and retry logic, but you get predictable runtime behavior.

**Deliverable:** a Go streaming chat server with two providers behind one interface, tested, containerized, with a TS React client that consumes the SSE stream.

---

### M4 · Weeks 9–10 · AI Frontend UX (your differentiator)

**Learn**
- [ ] Streaming chat UI: partial markdown, code blocks, auto-scroll, stop/retry, error states
- [ ] Rendering **tool calls** and citations; feedback (👍/👎) capture
- [ ] **Generative UI** patterns, voice input, file upload
- [ ] State management for conversations (React 19 patterns, optimistic updates)

**Market overview**

| Tool | Notes |
|---|---|
| **Vercel AI SDK** (`useChat`, streaming helpers) | The most common JS/TS option |
| assistant-ui, CopilotKit | Chat/copilot UI frameworks |
| Open WebUI, LibreChat | Open-source chat apps worth studying |
| Gradio, Streamlit | Python-side rapid UIs (demos, internal tools) |

**Deliverable:** a polished chat UI (React + TS) that talks to your Go backend, with citations, tool-call cards, feedback buttons and good error handling. **This becomes the visual front of your portfolio.**

---

### M5 · Weeks 11–14 · RAG (Retrieval-Augmented Generation)

**Learn**
- [ ] **Ingestion:** parsing PDF/HTML/Markdown, chunking strategies (fixed, recursive, structure-aware, semantic), metadata
- [ ] Embeddings: batching, caching, re-embedding when the model changes
- [ ] **pgvector** first (HNSW/IVFFlat), then **Qdrant**
- [ ] **Hybrid search** (BM25 + vector), metadata filters, **reranking**, query rewriting
- [ ] Answer generation with **citations**
- [ ] Concurrent ingestion with `errgroup`, backpressure, idempotent re-runs
- [ ] Basic RAG metrics: recall@k, MRR, faithfulness (more in M9)

**Market overview**

| Layer | Python | JS/TS | Go |
|---|---|---|---|
| Frameworks | LlamaIndex, LangChain, Haystack | LlamaIndex.TS, LangChain.js | hand-built, langchaingo, Genkit |
| Parsing | Unstructured, Docling, PyMuPDF | pdf.js, LlamaParse (API) | call a Python parsing service or API |
| Vector DB | pgvector, Qdrant, Milvus, Weaviate, Pinecone, Chroma, LanceDB | same (client libs) | pgx + pgvector, Qdrant gRPC client, others |
| Rerank | Cohere Rerank, bge-reranker, cross-encoders | Cohere/API | API-based or sidecar |

**Go vs Python trade-off:** Python wins on document parsing and experimentation speed. Go wins on high-throughput ingestion pipelines and low-memory serving. A very common real architecture is **Go for serving + Python for parsing/evals**, and you can say so in interviews.

**Deliverable:** a RAG service: upload docs → chunk → embed concurrently → store in pgvector → answer with citations over SSE. **Also implement the retrieval part in Python (LlamaIndex or plain code) and compare quality and latency.**

---

### M6 · Weeks 15–16 · Agents, Tool Calling & MCP

**Learn**
- [ ] **Tool/function calling:** JSON Schema from Go structs, argument validation, safe execution, timeouts, error feedback to the model
- [ ] **Agent patterns:** ReAct, plan-and-execute, supervisor/worker, reflection/critic, human-in-the-loop
- [ ] Max-step limits, loop detection, token/cost budgets
- [ ] **MCP (Model Context Protocol):** build an MCP server with 2–3 tools and connect it to an MCP-capable client
- [ ] Parallel tool calls; sandboxing for code execution (overview)

**Market overview**

| Layer | Python | JS/TS | Go |
|---|---|---|---|
| Agent frameworks | **LangGraph**, CrewAI, AutoGen/AG2, OpenAI Agents SDK, Pydantic AI, Google ADK, smolagents | LangGraph.js, Mastra, Vercel AI SDK, OpenAI Agents SDK (JS) | custom loops, Eino, langchaingo, Genkit, ADK for Go |
| MCP SDKs | FastMCP, official Python SDK | official TS SDK | official Go SDK, `mcp-go` |

**Go vs Python trade-off:** frameworks in Python give you checkpoints, graph visualization and tracing out of the box. In Go you assemble these yourself, so you understand exactly what's happening, but ship slower. Many production teams use thin custom loops anyway.

**Deliverable:** an agent with 3 real tools (DB lookup, web fetch, calculator) plus an MCP server wrapping them.

---

### M7 · Weeks 17–18 · Concurrency & Custom Agent Runtime (Go's superpower)

**Learn**
- [ ] Goroutines, `WaitGroup`, `Mutex`, `atomic`
- [ ] Channels (buffered/unbuffered), `select`, fan-in/fan-out, worker pools
- [ ] **`context.Context`:** deadlines, timeouts, **cancel LLM calls when the user leaves**
- [ ] `errgroup`, semaphores, `x/time/rate`
- [ ] Race detector, goroutine leaks, deadlock debugging
- [ ] State ownership rule: pass values or transfer ownership. Avoid sharing mutable pointers across goroutines.

**Deliverable → Project 2** (Section 8): a multi-agent engine with Supervisor, Research, Code and Review nodes, checkpointing and cost budgets. **Also build the same graph in LangGraph (Python) and write a comparison.**

---

### M8 · Weeks 19–21 · Memory, Caching, Queues & Durable Workflows

**Learn**
- [ ] Short-term memory (windowing, summarization) vs long-term memory (facts, vectors)
- [ ] Redis (`go-redis`): exact-match caching, rate limits, session state
- [ ] **Semantic cache** (vector similarity + threshold, tenant isolation, TTL, staleness risks)
- [ ] Provider **prompt caching** concepts
- [ ] Queues and durable execution: **Temporal**, NATS JetStream, Redis Streams, Kafka (overview), idempotency and retries

**Market overview**

| Need | Python | JS/TS | Go |
|---|---|---|---|
| Memory layers | Mem0, Zep, Letta, LangMem | Mem0 SDK, custom | custom with Redis/Postgres |
| Queues/workflows | Celery, Temporal, Prefect, Airflow | BullMQ, Inngest, Trigger.dev, Temporal | Temporal, Asynq, River, NATS |
| Caching | Redis, GPTCache-style | Redis, Upstash | Redis, in-memory (ristretto) |

**Deliverable:** add memory + two-tier cache + resumable runs to your agent project.

---

### M9 · Weeks 22–23 · Evals (a top differentiator)

**Learn**
- [ ] Build a **golden dataset** (50–200 cases) for your RAG and agent projects
- [ ] LLM-as-judge (and its biases), pairwise comparison, human review loop
- [ ] RAG metrics: context recall, faithfulness, answer relevance
- [ ] **Regression evals in CI** (fail the build if quality drops)
- [ ] Prompt/version management and A/B comparison

**Market overview**

| Category | Popular |
|---|---|
| Frameworks | promptfoo, Ragas, DeepEval, OpenAI Evals, Inspect, Braintrust |
| Platforms | LangSmith, Langfuse, Arize Phoenix |
| Language note | Mostly Python/TS. Call these from Go CI via CLI or HTTP. |

**Deliverable:** an eval suite with ≥50 cases and a CI job that runs it on every PR, plus a short report of before/after improvements. **Employers love seeing this.**

---

### M10 · Weeks 23–24 · Observability & Cost Control

**Learn**
- [ ] **OpenTelemetry** traces (request → retrieval → LLM → tool) and metrics (TTFT, tokens in/out, cost, cache hit rate, errors)
- [ ] OTel GenAI semantic conventions
- [ ] Prometheus + Grafana dashboards, alerting
- [ ] Structured logging and request IDs
- [ ] Budgeting per user/tenant, model routing (cheap vs strong model)

**Market overview**

| Category | Popular |
|---|---|
| LLM-specific | Langfuse (open-source), LangSmith, Arize Phoenix, Helicone, Braintrust, W&B Weave |
| Standards/infra | OpenTelemetry, OpenLLMetry/OpenInference, Prometheus, Grafana, Tempo/Jaeger, Datadog |

**Deliverable:** a Grafana dashboard JSON committed to your gateway repo plus a README screenshot.

---

### M11 · Week 25 · Security & Guardrails

**Learn**
- [ ] Prompt injection (direct and **indirect via retrieved docs or tool results**)
- [ ] Least-privilege tools, allow-lists, confirmation steps for risky actions
- [ ] PII redaction, secrets handling, per-tenant data isolation, audit logs
- [ ] Output validation and moderation
- [ ] **OWASP Top 10 for LLM Applications** (read it end to end)

**Market overview:** Guardrails AI, NeMo Guardrails, LLM Guard, provider moderation endpoints, Lakera, Azure Prompt Shields.

**Deliverable:** a short threat model document for your capstone plus 5 attack test cases in your eval suite.

---

### M12 · Week 26 · Deployment & Cloud

**Learn**
- [ ] Multi-stage Dockerfile (distroless/scratch for Go), health/readiness probes
- [ ] **KinD** + manifests/Helm, ConfigMaps/Secrets, HPA basics
- [ ] CI/CD with GitHub Actions (lint, test, race, build, image scan, deploy)
- [ ] One real cloud deploy (Cloud Run, Fly.io, AWS ECS/Lambda, or similar)
- [ ] Load testing (k6, vegeta) and `pprof` profiling

**Market overview**

| Area | Popular |
|---|---|
| Platforms | AWS (Bedrock, ECS, Lambda), GCP (Vertex AI, Cloud Run), Azure (OpenAI), Fly.io, Modal (Python-heavy) |
| IaC | Terraform/OpenTofu, Pulumi |
| K8s local | KinD, minikube, k3d |

**Deliverable:** your gateway live on a public URL, with CI/CD and a load-test report.

---

### M13 · Week 27 · Inference & Fine-Tuning (overview only)

You are **not** training models. Just know the landscape.

- [ ] Serving engines: vLLM, SGLang, TGI, TensorRT-LLM, llama.cpp, Ollama
- [ ] Managed inference: Together, Fireworks, Groq, Replicate, AWS Bedrock, Vertex AI
- [ ] Fine-tuning overview: LoRA/QLoRA, Hugging Face PEFT, Unsloth. **Know when *not* to fine-tune** (prompting, RAG and evals come first).
- [ ] Multimodal and voice APIs (vision, speech-to-text, realtime audio)

---

### M14 · Week 28 · System Design, DSA & Interview Readiness

- [ ] **DSA:** keep sharpening (arrays, hash maps, trees, graphs, two pointers). Many companies still run a standard coding round. 3–5 problems/week throughout the plan.
- [ ] **System design for AI:** gateway, RAG at scale, multi-tenant chatbot, agent platform, semantic cache
- [ ] **Behavioral:** prepare 5 stories (ownership, failure, conflict, impact, learning)

---

## 8. 🛠️ Portfolio Projects

Build **3 flagship projects + 1 small extra**. Quality beats quantity: each needs a README, architecture diagram, demo video, deployed link, eval results and a "trade-offs" section.

### Project 1 · "StreamChat": Full-Stack Streaming AI App (Weeks 8–10)
- React 19 + TS frontend (streaming, citations, feedback), Go backend, 2+ providers, auth, Postgres chat history
- **Shows:** full-stack ability, streaming UX, provider abstraction

### Project 2 · "DocMind": Production RAG with Evals (Weeks 11–14, finish by 23)
- Ingestion pipeline, pgvector/Qdrant, hybrid search + reranking, citations
- Eval suite with golden dataset and CI gating; before/after metrics
- Python comparison of retrieval quality
- **Shows:** RAG depth and eval discipline, the strongest hiring signals

### Project 3 · Agent Engine + MCP Server (Weeks 15–18)
- Framework-free Go agent runtime with Supervisor + workers, tool calling, checkpointing, budgets
- Same workflow in LangGraph (Python), with a written comparison
- MCP server exposing your tools
- **Shows:** agent reliability, concurrency, framework literacy

### Capstone · AI Gateway Proxy (Weeks 19–26)

```
┌────────────────────────┐
│   React + TS Chat UI   │
└───────────┬────────────┘
            │ HTTPS + SSE
            ▼
┌──────────────────────────────────────────────────┐
│                 Go AI Gateway                    │
│ Auth → Rate limit → Cache → Router → Providers   │
│ OTel · slog · circuit breaker · cost budgets     │
└──┬──────────────┬─────────────┬─────────────┬────┘
   │              │             │             │
 Redis        Postgres        Qdrant       LLM providers
(exact cache,  (keys, usage)  (semantic    (OpenAI, Anthropic,
 rate limits)                  cache/RAG)   Gemini, Ollama)
```

- Unified OpenAI-compatible endpoint, SSE streaming, fallback chains, per-key rate limits and budgets
- Two-tier cache (exact → semantic), OTel metrics + Grafana dashboard
- Deployed with CI/CD, load-test numbers in README, threat model
- **Shows:** platform engineering, reliability, cost awareness

### Optional small extras (a weekend each)
- A published **MCP server** for something genuinely useful
- A voice-enabled assistant demo
- A **blog post** per flagship project ("What I learned building evals for a RAG app")

### Open-source contribution (target 1–3 merged PRs)

| Repo | Why |
|---|---|
| ollama/ollama | Very popular Go project, real server design |
| tmc/langchaingo | Interface-heavy Go AI library, approachable issues |
| firebase/genkit (Go) | Typed flows, tools and tracing |
| cloudwego/eino | Go LLM framework with graph-style orchestration |
| modelcontextprotocol/go-sdk, mark3labs/mcp-go | Small, active MCP libraries |
| maximhq/bifrost | A Go-based LLM gateway to compare with yours |
| vercel/ai, assistant-ui | TS-side streaming UI ecosystem (leverages your frontend skills) |

Ladder: read → docs/typo fix → tests → "good first issue" → small feature.

---

## 9. 🧭 Job Search Playbook

### Start applying around week 18–20
Your portfolio (Projects 1–3) will already be strong. Don't wait for "perfect."

### Titles to search
*AI Engineer · LLM Engineer · Applied AI Engineer · AI Application Engineer · GenAI Engineer · AI Product Engineer · Full-Stack Engineer (AI) · Backend Engineer (AI Platform) · Go Backend Engineer*

### Where to look
- Startup job boards (Wellfound, Y Combinator's Work at a Startup), LinkedIn, company career pages
- Global tech companies' local offices and GCCs (global capability centers) for stable pay
- Remote-first companies (for the higher USD band)
- Referrals: they beat cold applications by a wide margin. Reach out to engineers at target companies after you've shipped something relevant.

### Resume and profile
- Lead with a **one-line positioning** and 3 projects with metrics (latency, cost saved, eval score, throughput)
- Keep your frontend experience prominently: it signals product ownership
- GitHub: pinned repos, clean READMEs, demo videos, architecture diagrams
- Write 2–4 technical posts; share them on LinkedIn/X

### Targeting strategy
| Band | Where | How |
|---|---|---|
| **First realistic offer** | Startups, product teams adding AI, GCCs | Portfolio + strong interviews |
| **Higher USD band ($80–100k)** | Remote-first global companies, or after 1–2 yrs of production AI experience | Open-source presence, writing, referrals, proof of shipped systems |

### Interview process to expect
1. Recruiter screen → 2. Coding round (DSA + practical) → 3. Take-home or live build (RAG/agent/API) → 4. System design (AI-flavored) → 5. Behavioral/product round

### Negotiation
- Know the market range for your location and level (use multiple sources, since they disagree)
- Compare total compensation (base, bonus, equity, benefits), not just base
- Having a second offer or active process is the strongest lever

### Parallel safety net
While learning, try to **introduce AI features at your current job** (support bot, search, summarization, internal tools). A real work project can be your fastest credential.

---

## 10. 🎤 Interview Prep Bank

**LLM fundamentals**
1. What are tokens, and how do they affect cost and latency?
2. How do you reduce hallucinations in an LLM application?
3. When would you use RAG vs fine-tuning vs better prompting?

**RAG**
4. How do you choose chunk size and overlap?
5. Why add reranking and hybrid search?
6. How would you evaluate a RAG system before launch?

**Agents & tools**
7. How do you stop an agent from looping forever?
8. How do you defend against prompt injection through tool outputs or retrieved documents?
9. When is a single LLM call better than an agent?

**Systems (Go/backend)**
10. How do you cancel an in-flight LLM call when the client disconnects?
11. Design a semantic cache. What can go wrong?
12. Design an AI gateway with provider fallback and per-tenant rate limits.
13. Where would you use Temporal or a queue instead of goroutines?

**Languages**
14. Why Go for a gateway but Python for evals and document parsing?
15. What does TypeScript's type system *not* protect you from at runtime, and how do you validate LLM output in each language?

**Frontend edge**
16. How do you design a streaming chat UI that stays responsive and handles errors?
17. How do you show citations and tool calls in a way users trust?

---

## 11. ✅ Master Checklist

**Foundations**
- [ ] LLM basics & prompting · [ ] Python bridge · [ ] Go core · [ ] Backend basics (HTTP, auth, Postgres, Docker)

**Build**
- [ ] Streaming API + provider abstraction · [ ] Structured output + retries · [ ] AI frontend UX

**AI Systems**
- [ ] RAG (chunking, hybrid, rerank, citations) · [ ] Agents + tools + MCP · [ ] Go concurrency + custom agent runtime · [ ] Memory + caching + durable workflows

**Production**
- [ ] Evals in CI · [ ] OTel + Prometheus/Grafana · [ ] Security/guardrails · [ ] Docker + KinD + cloud deploy · [ ] Load tests

**Career**
- [ ] 3 flagship projects + capstone · [ ] 1–3 OSS PRs · [ ] 2–4 blog posts · [ ] Resume + GitHub polished · [ ] DSA practice ongoing · [ ] System design mocks · [ ] Applications started by week ~20

**Monthly review:** every 4 weeks, check progress against this list, adjust the plan and update your portfolio. Tools change quickly; the fundamentals (software engineering, evals, reliability, UX) do not.

---

## 12. 🔗 Sources

Salary and hiring figures come from public aggregator and guide pages from 2026. They disagree with each other, so use them for ranges and not exact numbers.

- [The AI Engineer in 2026: What the Role Actually Requires](https://www.tribuneindia.com/news/business/the-ai-engineer-in-2026-what-the-role-actually-requires/)
- [AI Engineer Skills in 2026: The Real Checklist Hiring Teams Want (Scaler)](https://www.scaler.com/topics/ai-engineer-skills-2026-checklist-hiring-teams-want/)
- [How to Become an AI Engineer: A Developer's Roadmap for 2026 (Scrimba)](https://scrimba.com/articles/how-to-become-an-ai-engineer-a-developers-roadmap-for-2026)
- [AI Engineer Roadmap 2026 (Let's Data Science)](https://letsdatascience.com/blog/ai-engineer-roadmap-2026-skills-tools-and-career-path)
- [AI Engineer Salary Guide 2026: Entry Level to Senior (Millersville)](https://techprogram.millersville.edu/blog/ai-engineer-salary-guide-2026/)
- [AI Engineer Salary Guide (KORE1)](https://kore1.com/ai-engineer-salary-guide/)
- [AI Engineer Salaries in 2026: US vs Europe vs Latin America](https://www.remotelytalents.com/blog/ai-engineer-salaries-2026-us-vs-europe-vs-latin-america)
- [Entry Level AI Engineer Salary (ZipRecruiter)](https://www.ziprecruiter.com/Salaries/Entry-Level-Ai-Engineer-Salary)
- [AI Engineer Salary in India 2026 (Taggd)](https://taggd.in/blogs/ai-engineer-salary/)
- [AI Engineer Salary in India (Instahyre)](https://resources.instahyre.com/blog/ai-engineer-salary-in-india/)
- [Applied AI Engineer in India (Recrew)](https://www.recrew.ai/salary-guides/applied-ai-engineer-in-india)
- [AI Engineer Salary in India 2026 (Weekday)](https://www.weekday.works/post/ai-engineer-salary-in-india-2026)
