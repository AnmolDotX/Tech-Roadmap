AI Engineer (1 month roadmap)
---

## 1. Prerequisites: Sequential Learning Syllabus

To build this architecture smoothly without getting stuck in dependency loops, learn these concepts in the exact sequence outlined across four dedicated weeks.

```
Week 1: Async Python & Multi-Provider Abstraction
Week 2: Vector Embeddings & Agentic Memory (Mem0 + pgvector)
Week 3: Stateful Agent Workflows with LangGraph
Week 4: Full-Stack Integration, Containerization & KinD

```

---

### Phase 1: Python, Async APIs & Multi-Provider Abstraction

Before orchestrating complex agents, you need to understand how to stream responses asynchronously and decouple your application from a single model provider.

* **Asynchronous Python (`asyncio`):**
* Learn how event loops, `async def`, `await`, and `asyncio.gather` work.
* Understand the difference between blocking I/O (e.g., standard `requests`) and non-blocking I/O (e.g., `httpx`, `aiohttp`).


* **FastAPI Core Patterns:**
* **Pydantic v2:** Build rigid schemas for request validation, structured output models, and response serialization.
* **Dependency Injection (`Depends`):** Use dependencies to inject database sessions, configuration instances, and authentication context into route handlers cleanly.
* **Streaming with Server-Sent Events (SSE):** Master `StreamingResponse` with an async generator (`async for chunk in stream: yield ...`) to stream token-by-token output back to the client.


* **LLM Abstraction via Factory Pattern & LiteLLM:**
* Why avoid direct SDK hardcoding: Hardcoding `from openai import OpenAI` ties your business logic to a single vendor's request/response schema.
* Using `litellm`: Study how `litellm.acompletion()` normalizes API calls across OpenAI, Anthropic, Gemini, Groq, and Mistral into a unified OpenAI-compatible output schema.
* Implement the **Factory Pattern**: Write an `LLMFactory` class that receives a provider name (e.g., `anthropic`), a model string (`claude-3-5-sonnet`), and a raw API key, then returns a configured client dynamically.



---

### Phase 2: Vector Embeddings & Long-Term Semantic Memory

Agentic memory requires moving past transient chat histories and building persistent, queryable knowledge graphs and vector indices.

* **Embeddings & Vector Spaces:**
* Understand how high-dimensional vectors represent semantic meaning (distance metrics: Cosine Similarity, Dot Product, Euclidean Distance).
* Learn the trade-offs of lightweight local embedding models (e.g., `sentence-transformers/all-MiniLM-L6-v2` running via ONNX or Hugging Face) versus hosted embedding endpoints (e.g., OpenAI `text-embedding-3-small`).


* **PostgreSQL with `pgvector`:**
* Install and activate the `pgvector` extension in PostgreSQL (`CREATE EXTENSION vector;`).
* Index types: Compare **HNSW** (Hierarchical Navigable Small World) for fast approximate nearest-neighbor search with **IVFFlat** for memory-constrained setups.
* Write raw SQL similarity queries using the `<=>` (cosine distance) operator.


* **Agentic Memory Mechanics with Mem0:**
* **Short-Term vs. Long-Term Memory:** Short-term memory lives in working context during an active thread. Long-term memory persists across days, sessions, and platforms.
* **Fact Extraction Pipelines:** When a user says, *"We are migrating from MySQL to PostgreSQL and using Prisma,"* an extraction prompt must parse out atomic facts:
* `User is migrating database: MySQL -> PostgreSQL`
* `User prefers ORM: Prisma`


* **Update/Invalidation Logic:** If the user later says, *"We dropped Prisma for Drizzle,"* the memory manager must locate the conflicting fact via semantic similarity and supersede or update it, rather than accumulating contradictory data.



---

### Phase 3: Stateful Agent Workflows with LangGraph

Standard chains (like basic LangChain `LLMChain`) are linear pipelines: Prompt $\rightarrow$ Model $\rightarrow$ Output. Real engineering research requires cyclical workflows, self-correction, tool execution, and state manipulation.

* **The ReAct Pattern (Reason + Act):**
* The core execution cycle: Thought $\rightarrow$ Action (Tool Call) $\rightarrow$ Observation (Tool Result) $\rightarrow$ Reflection $\rightarrow$ Final Answer.


* **LangGraph Fundamentals:**
* **The State Schema:** Define a typed dictionary or Pydantic model (`AgentState`) containing conversation history, active retrieved memories, research scratchpads, and execution flags.
* **Nodes:** Pure Python functions that accept the current `State`, perform an operation (call LLM, query vector database, scrape a doc), and return partial state updates.
* **Edges & Conditional Routing:** Write conditional router functions that inspect the state (e.g., *“Did the LLM request an external web search or can it finalize the response?”*) and route execution to the search node or the synthesis node.
* **State Reducers (`Annotated[list, add_messages]`):** Understand how LangGraph appends messages rather than overwriting the entire history array on state transitions.



---

### Phase 4: Frontend & Infrastructure Orchestration

To turn a Python script into a portfolio-grade system, containerize every layer and deliver a real-time reactive UI.

* **Frontend (React 19 & TypeScript):**
* **Readable Stream Consumption:** Use the native `fetch` API and `ReadableStreamDefaultReader` with `TextDecoder` to handle streaming SSE chunks from FastAPI without third-party bloat.
* **Client-Side Key Vault:** Store user API keys securely in browser `localStorage` and inject them into custom request headers (`X-Provider`, `X-API-Key`, `X-Model`).


* **Containerization (Docker & Multi-Stage Builds):**
* Write a multi-stage `Dockerfile` for React: compile TypeScript with Node.js in stage 1, then copy static assets to an alpine Nginx server in stage 2 to minimize image size.
* Write a slim `Dockerfile` for FastAPI using non-root user execution, explicit dependency caching, and poetry/uv/pip-tools.


* **Local Kubernetes Orchestration (KinD):**
* Why KinD over plain Docker Compose: It proves you understand production cloud-native primitives—Pods, Deployments, ClusterIP Services, ConfigMaps, and Persistent Volume Claims (PVCs).
* Build and load images locally without pushing to Docker Hub using `kind load docker-image`.
* Expose services locally using `kubectl port-forward` or ingress controllers.



---

## 2. Project Deep-Dive: The Multi-Provider Stateful Research Agent

### The Problem It Solves

| Common Chatbot Flaw | How This Project Solves It |
| --- | --- |
| **Session Amnesia** | Uses Mem0 + `pgvector` to persist technical preferences across distinct chat threads. |
| **Vendor Lock-in** | Decoupled router accepts user-supplied API keys for OpenAI, Anthropic, Gemini, or Groq on the fly. |
| **Hallucinated Answers** | Employs a LangGraph ReAct loop with web search tools to fetch, cite, and synthesize live documentation. |
| **Opaque Black Box** | Includes a real-time "Memory Inspector" UI showing extracted user facts and active system context. |

---

### The System Architecture

```
                     +---------------------------------------+
                     |      React 19 + TypeScript UI         |
                     |  (BYOK Settings + Live Memory Panel)  |
                     +-------------------+-------------------+
                                         |
                       HTTP / SSE Stream | Headers: X-Provider, X-API-Key
                                         v
                     +---------------------------------------+
                     |            FastAPI Gateway            |
                     |   (Auth Validation & Stream Router)   |
                     +-------------------+-------------------+
                                         |
                                         v
                     +---------------------------------------+
                     |            LangGraph Engine           |
                     |             (StateGraph)              |
                     +---+-------------------------------+---+
                         |                               |
        1. Query Memory  |                               | 2. Run ReAct
                         v                               v
           +---------------------------+   +---------------------------+
           |       Mem0 Service        |   |       LiteLLM Router      |
           |  (Fact Extraction/Search) |   |  (OpenAI/Anthropic/Groq)  |
           +-------------+-------------+   +-------------+-------------+
                         |                               |
                         v                               v
           +---------------------------+   +---------------------------+
           |     PostgreSQL Pod        |   |    Tavily / DuckDuckGo    |
           |   (pgvector Extension)    |   |     (Web Search Tool)     |
           +---------------------------+   +---------------------------+

```

---

## 3. Step-by-Step Implementation Guide

Follow these sequential build phases to construct, test, and containerize the system.

### Phase 1: Database Setup & Infrastructure Bootstrapping

Start by configuring local persistent storage for vectors and relation data.

#### Step 1.1: Local Vector Database Manifest

Create a local database container running PostgreSQL with `pgvector` enabled. In your `docker-compose.yml`:

```yaml
services:
  vectordb:
    image: pgvector/pgvector:pg16
    container_name: agent_postgres
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgrespassword
      POSTGRES_DB: agent_memory
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:

```

#### Step 1.2: Mem0 Initialization

Initialize Mem0 with PostgreSQL as the vector store backend and configure an embedding provider.

```python
# backend/app/core/memory.py
import os
from mem0 import Memory

def get_memory_client() -> Memory:
    config = {
        "vector_store": {
            "provider": "pgvector",
            "config": {
                "connection_string": "postgresql://postgres:postgrespassword@localhost:5432/agent_memory",
                "table_name": "user_memories",
                "embedding_model_dims": 1536
            }
        },
        "llm": {
            "provider": "litellm",
            "config": {
                "model": "gpt-4o-mini"
            }
        }
    }
    return Memory.from_config(config)

```

---

### Phase 2: Multi-Provider LLM Abstraction Layer

Build the factory pattern to accept dynamic user credentials per HTTP request.

#### Step 2.1: Request Context & Provider Registry

Create an execution context that captures the incoming user's chosen provider and key:

```python
# backend/app/core/llm.py
from dataclasses import dataclass
from typing import Optional
import litellm

@dataclass
class LLMContext:
    provider: str
    api_key: str
    model: str

class LLMRegistry:
    @staticmethod
    def get_completion_params(context: LLMContext, messages: list, stream: bool = True):
        # LiteLLM format: 'provider/model' or standard model names
        model_name = context.model
        if context.provider == "anthropic" and not model_name.startswith("anthropic/"):
            model_name = f"anthropic/{model_name}"
        elif context.provider == "gemini" and not model_name.startswith("gemini/"):
            model_name = f"gemini/{model_name}"
            
        return {
            "model": model_name,
            "api_key": context.api_key,
            "messages": messages,
            "stream": stream
        }

```

---

### Phase 3: LangGraph Agent & Memory Pipeline

This is the core engine where memory retrieval, reasoning, tool execution, and memory extraction happen.

#### Step 3.1: Define Agent State

```python
# backend/app/agent/state.py
from typing import TypedDict, Annotated, List, Dict, Any
from langgraph.graph.message import add_messages

class AgentState(TypedDict):
    messages: Annotated[list, add_messages]
    user_id: str
    memories: List[str]
    research_data: List[str]
    llm_context: Dict[str, Any]

```

#### Step 3.2: Implement Graph Nodes

```python
# backend/app/agent/graph.py
from langgraph.graph import StateGraph, END
from app.agent.state import AgentState
from app.core.memory import get_memory_client
from app.core.llm import LLMRegistry, LLMContext
import litellm

memory_client = get_memory_client()

async def memory_retrieval_node(state: AgentState):
    """Retrieve long-term facts relevant to the latest user message."""
    user_id = state["user_id"]
    latest_message = state["messages"][-1].content
    
    # Semantic search over historical user facts
    past_memories = memory_client.search(query=latest_message, user_id=user_id)
    memory_strings = [m["memory"] for m in past_memories.get("results", [])]
    
    return {"memories": memory_strings}

async def reasoning_node(state: AgentState):
    """Call LLM with system prompt enriched by long-term memories."""
    context = LLMContext(**state["llm_context"])
    
    # Inject persistent memory into system prompt
    memory_context = "\n- ".join(state["memories"])
    system_prompt = (
        "You are an expert research engineer. Tailor your answer to the user's constraints.\n"
        f"Known User Constraints & Stack Preferences:\n- {memory_context}\n"
    )
    
    prompt_messages = [{"role": "system", "content": system_prompt}] + state["messages"]
    params = LLMRegistry.get_completion_params(context, prompt_messages, stream=False)
    
    response = await litellm.acompletion(**params)
    return {"messages": [response.choices[0].message]}

async def memory_extraction_node(state: AgentState):
    """Extract new facts from the conversation turn and store in pgvector."""
    user_id = state["user_id"]
    # Pass user and assistant messages to Mem0 for atomic fact extraction
    interaction = [
        {"role": "user", "content": state["messages"][-2].content},
        {"role": "assistant", "content": state["messages"][-1].content}
    ]
    memory_client.add(interaction, user_id=user_id)
    return {}

# Build the Graph
workflow = StateGraph(AgentState)
workflow.add_node("retrieve_memory", memory_retrieval_node)
workflow.add_node("reason", reasoning_node)
workflow.add_node("extract_memory", memory_extraction_node)

workflow.set_entry_point("retrieve_memory")
workflow.add_edge("retrieve_memory", "reason")
workflow.add_edge("reason", "extract_memory")
workflow.add_edge("extract_memory", END)

agent_runner = workflow.compile()

```

---

### Phase 4: Streaming FastAPI Gateway

Create an API endpoint that extracts user credentials from headers and streams agent tokens via SSE.

```python
# backend/app/main.py
from fastapi import FastAPI, Header, HTTPException
from fastapi.responses import StreamingResponse
from fastapi.middleware.cors import CORSMiddleware
from pydantic import BaseModel
from app.agent.graph import agent_runner
from app.core.memory import get_memory_client
import json

app = FastAPI(title="Stateful Agent Gateway")

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_methods=["*"],
    allow_headers=["*"],
)

class ChatRequest(BaseModel):
    user_id: str
    message: str

@app.post("/api/chat")
async def chat_endpoint(
    req: ChatRequest,
    x_provider: str = Header(..., alias="X-Provider"),
    x_api_key: str = Header(..., alias="X-API-Key"),
    x_model: str = Header(..., alias="X-Model")
):
    llm_context = {
        "provider": x_provider,
        "api_key": x_api_key,
        "model": x_model
    }

    async def event_generator():
        initial_state = {
            "messages": [{"role": "user", "content": req.message}],
            "user_id": req.user_id,
            "memories": [],
            "research_data": [],
            "llm_context": llm_context
        }
        
        # Stream events from the graph
        async for output in agent_runner.astream(initial_state):
            for node_name, state_update in output.items():
                chunk = {
                    "node": node_name,
                    "data": state_update.get("messages", [{}])[-1].content if "messages" in state_update else None,
                    "memories": state_update.get("memories", None)
                }
                yield f"data: {json.dumps(chunk)}\n\n"

    return StreamingResponse(event_generator(), media_type="text/event-stream")

@app.get("/api/memories/{user_id}")
async def get_memories(user_id: str):
    """Allows the UI to inspect stored vector facts."""
    mem_client = get_memory_client()
    return mem_client.get_all(user_id=user_id)

```

---

### Phase 5: React UI with Memory Inspector

Build the interface with a settings modal for API keys, an active streaming chat window, and a live Memory Inspector panel.

```tsx
// frontend/src/App.tsx
import React, { useState, useEffect } from 'react';

interface MemoryItem {
  id: string;
  memory: string;
}

export default function App() {
  const [provider, setProvider] = useState(() => localStorage.getItem('provider') || 'openai');
  const [apiKey, setApiKey] = useState(() => localStorage.getItem('apiKey') || '');
  const [model, setModel] = useState(() => localStorage.getItem('model') || 'gpt-4o');
  const [input, setInput] = useState('');
  const [messages, setMessages] = useState<Array<{ role: string; content: string }>>([]);
  const [memories, setMemories] = useState<MemoryItem[]>([]);
  const userId = "dev-user-01";

  useEffect(() => {
    localStorage.setItem('provider', provider);
    localStorage.setItem('apiKey', apiKey);
    localStorage.setItem('model', model);
    fetchMemories();
  }, [provider, apiKey, model]);

  const fetchMemories = async () => {
    try {
      const res = await fetch(`http://localhost:8000/api/memories/${userId}`);
      const data = await res.json();
      setMemories(data.results || []);
    } catch (err) {
      console.error("Failed to load memories", err);
    }
  };

  const sendMessage = async () => {
    if (!input || !apiKey) return;
    
    const userMsg = { role: 'user', content: input };
    setMessages(prev => [...prev, userMsg, { role: 'assistant', content: '' }]);
    setInput('');

    const response = await fetch('http://localhost:8000/api/chat', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'X-Provider': provider,
        'X-API-Key': apiKey,
        'X-Model': model,
      },
      body: JSON.stringify({ user_id: userId, message: input })
    });

    const reader = response.body?.getReader();
    const decoder = new TextDecoder();

    while (reader) {
      const { done, value } = await reader.read();
      if (done) break;
      
      const chunk = decoder.decode(value);
      const lines = chunk.split('\n\n');
      for (const line of lines) {
        if (line.startsWith('data: ')) {
          const payload = JSON.parse(line.replace('data: ', ''));
          if (payload.node === 'reason' && payload.data) {
            setMessages(prev => {
              const updated = [...prev];
              updated[updated.length - 1].content = payload.data;
              return updated;
            });
          }
        }
      }
    }
    fetchMemories(); // Refresh inspector after interaction
  };

  return (
    <div style={{ display: 'flex', height: '100vh', fontFamily: 'monospace' }}>
      {/* Sidebar / Configuration */}
      <div style={{ width: '320px', padding: '16px', borderRight: '1px solid #ddd' }}>
        <h3>BYOK Credentials</h3>
        <label>Provider</label>
        <select value={provider} onChange={e => setProvider(e.target.value)} style={{ width: '100%', marginBottom: '8px' }}>
          <option value="openai">OpenAI</option>
          <option value="anthropic">Anthropic</option>
          <option value="groq">Groq</option>
        </select>

        <label>Model</label>
        <input value={model} onChange={e => setModel(e.target.value)} style={{ width: '100%', marginBottom: '8px' }} />

        <label>API Key</label>
        <input type="password" value={apiKey} onChange={e => setApiKey(e.target.value)} style={{ width: '100%', marginBottom: '16px' }} />

        <hr />
        <h3>🧠 Memory Inspector</h3>
        <p style={{ fontSize: '12px', color: '#666' }}>Facts stored in pgvector for this user:</p>
        <ul>
          {memories.map(m => (
            <li key={m.id} style={{ fontSize: '12px', marginBottom: '4px' }}>{m.memory}</li>
          ))}
        </ul>
      </div>

      {/* Main Chat Interface */}
      <div style={{ flex: 1, display: 'flex', flexDirection: 'column', padding: '16px' }}>
        <div style={{ flex: 1, overflowY: 'auto' }}>
          {messages.map((m, idx) => (
            <div key={idx} style={{ marginBottom: '12px' }}>
              <strong>{m.role === 'user' ? 'You: ' : 'Agent: '}</strong>
              <span>{m.content}</span>
            </div>
          ))}
        </div>
        <div style={{ display: 'flex', gap: '8px' }}>
          <input 
            style={{ flex: 1, padding: '8px' }} 
            value={input} 
            onChange={e => setInput(e.target.value)} 
            placeholder="Ask research questions or state your architectural constraints..."
          />
          <button onClick={sendMessage} style={{ padding: '8px 16px' }}>Send</button>
        </div>
      </div>
    </div>
  );
}

```

---

### Phase 6: Local Kubernetes Deployment with KinD

To make the repository reproducible and showcase cloud-native engineering, automate deployment using KinD.

#### Step 6.1: Cluster Config (`kind-config.yaml`)

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
  extraPortMappings:
  - containerPort: 30080
    hostPort: 8000
    protocol: TCP
  - containerPort: 30000
    hostPort: 3000
    protocol: TCP

```

#### Step 6.2: Kubernetes Manifests (`k8s/deployment.yaml`)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: agent-backend
spec:
  replicas: 1
  selector:
    matchLabels:
      app: agent-backend
  template:
    metadata:
      labels:
        app: agent-backend
    spec:
      containers:
      - name: backend
        image: agent-backend:local
        imagePullPolicy: Never
        ports:
        - containerPort: 8000
        env:
        - name: DATABASE_URL
          value: "postgresql://postgres:postgrespassword@vectordb:5432/agent_memory"
---
apiVersion: v1
kind: Service
metadata:
  name: agent-backend-service
spec:
  type: NodePort
  selector:
    app: agent-backend
  ports:
  - port: 8000
    targetPort: 8000
    nodePort: 30080

```

#### Step 6.3: Automation Makefile (`Makefile`)

Provide a single command for reviewers to run your entire stack:

```makefile
.PHONY: deploy clean

deploy:
	@echo "Creating KinD cluster..."
	kind create cluster --config kind-config.yaml --name agent-cluster || true
	@echo "Building Docker images..."
	docker build -t agent-backend:local ./backend
	docker build -t agent-frontend:local ./frontend
	@echo "Loading images into KinD..."
	kind load docker-image agent-backend:local --name agent-cluster
	kind load docker-image agent-frontend:local --name agent-cluster
	@echo "Applying Kubernetes manifests..."
	kubectl apply -f k8s/
	@echo "Ready! App accessible at http://localhost:3000 (UI) and http://localhost:8000 (API)"

clean:
	kind delete cluster --name agent-cluster

```

---

## 4. GitHub Repository Structure

Your project directory should reflect production standards:

```
├── .github/
│   └── workflows/
│       └── ci.yaml              # Linting (ruff, eslint) and unit tests
├── backend/
│   ├── app/
│   │   ├── agent/               # LangGraph StateGraph, nodes, and routers
│   │   ├── core/                # LiteLLM router, Mem0 client, DB session
│   │   ├── schemas/             # Pydantic request/response models
│   │   └── main.py              # FastAPI app & SSE endpoints
│   ├── tests/                   # Pytest mocks for tools and nodes
│   ├── Dockerfile
│   └── pyproject.toml
├── frontend/
│   ├── src/
│   │   ├── components/          # MemoryInspector, ConfigSidebar, ChatStream
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── Dockerfile
│   ├── nginx.conf
│   └── package.json
├── k8s/
│   ├── vectordb.yaml            # PostgreSQL + pgvector Deployment & PVC
│   ├── backend.yaml             # FastAPI Deployment & NodePort Service
│   └── frontend.yaml            # React Nginx Deployment & NodePort Service
├── kind-config.yaml             # Port mappings for host access
├── docker-compose.yml           # Alternative local setup without K8s
├── Makefile                     # One-click build and deploy scripts
└── README.md                    # Architecture diagram, setup guide & design memo

```

---

## 5. What Interviewers Look For

When presenting this project in an interview for a 12–20 LPA SDE-1 / AI Engineer role, lead with the engineering trade-offs:

1. **Stateful vs. Stateless AI:** Explain how you use a vector database to solve context fragmentation without inflating prompt token costs on every call.
2. **Resilience & Security (BYOK):** Emphasize that API keys are strictly ephemeral and client-managed via headers, ensuring the backend stores zero sensitive user credentials.
3. **Decoupled Architecture:** Highlight how `LLMRegistry` lets the application adapt to new models or providers in minutes without altering business logic.
4. **Cloud-Native Competency:** Walk through your KinD manifests, explaining how the application scales, handles persistent database volumes, and isolates network communication across services.
