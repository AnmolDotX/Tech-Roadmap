# LIst of AI topics for AI interview app
-----

## 1. Real-Time Audio & Mobile Engineering (React Native)
Before touching AI APIs, you must master handling raw media streams on a mobile device.

* Audio Recording & Buffer Streaming
* Raw PCM audio capture vs. compressed formats (e.g., AAC, MP3)
   * Buffer chunking (emitting audio data arrays every 20–50ms)
   * Using native bridge libraries like react-native-live-audio-stream
* Audio Playback Processing
* Streaming incoming raw binary audio chunks into a playback buffer
   * Handling audio session interruptions (e.g., incoming phone calls)
* Network Transport for Media
* WebSockets protocols (ws:// and wss://) for binary data transmission
   * Managing network reconnect states and packet loss on mobile networks

## 2. Backend Orchestration & Streaming Architecture
Your backend acts as the traffic controller, piping data between the app and NVIDIA NIMs.

* Event-Driven Servers
* Handling WebSocket connections via Node.js (ws or Socket.io) or Python (FastAPI WebSockets)
   * Managing asynchronous streaming tasks without blocking the main event loop
* Voice Activity Detection (VAD)
* Understanding VAD algorithms (e.g., WebRTC VAD, Silero VAD)
   * Detecting speech thresholds (identifying when a candidate starts and stops talking)
   * Implementing silence timeouts (e.g., waiting 800ms of silence before triggering the LLM)
* API Interoperability (gRPC vs. REST)
* Streaming tokens out of LLM APIs using server-sent events (SSE)
   * Connecting to NVIDIA Riva STT/TTS using high-throughput gRPC connections

## 3. Core AI/ML Engineering & LLM Context Management
This is where you build the "brain" of the interviewer, ensuring it remains fast, accurate, and relevant.

* Inference Optimization
* Time-to-First-Token (TTFT): Strategies to minimize the initial delay before the LLM starts speaking
   * Streaming Generation (stream=True): Reading chunks from the LLM model token-by-token
   * Context/Prompt Caching: How NVIDIA NIMs reuse previously processed chat history to save compute time and reduce latency
* Tokenomics & Context Windows
* How text is broken into tokens by tokenizers (e.g., TikToken, Llama tokenizer)
   * Managing context window limits during a long conversation
   * Chat history trimming and summarisation strategies to prevent memory overflow

## 4. RAG (Retrieval-Augmented Generation) & Candidate Data Parsing
This gives the AI the ability to cross-reference the candidate's resume and job requirements on the fly.

* Document Processing
* Extracting clean text from unstructured Resume PDFs and Job Descriptions
* Text Embedding Models
* How embedding models convert text chunks into high-dimensional numerical vectors
* Vector Database Operations
* Setting up lightweight vector databases (e.g., ChromaDB, Faiss, or Pinecone)
   * Semantic Search: Querying the vector database to pull up contextually relevant resume details based on the user's spoken answer

## 5. Agentic AI Development & Flow Control
This prevents the conversation from breaking down into chaotic text loops.

* Finite State Machine (FSM) Design
* Structuring strict conversation phases (e.g., Intro ➔ Resume Deep Dive ➔ Coding Round ➔ Q&A)
   * Using libraries like LangGraph or writing custom code to handle state transitions
* Structured Outputs & Tool Calling
* Forcing the LLM to return JSON objects (Function Calling)
   * Triggering background actions (e.g., scoring the candidate's answer) before generating the next voice question
* System Prompt Crafting
* Defining strict persona constraints (e.g., preventing the AI from repeating itself, controlling output length to ensure short, conversational voice lines)

