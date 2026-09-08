# 🤖 AI Stack Configuration Guide

> **Stage 2: Environment** — Configuration for Ollama, Qdrant, Kilo Code local indexing, and local embeddings.

---

## 💬 This Project: Open WebUI + Local Ollama (the product)

Open WebUI is an open-source, self-hosted chat interface for LLMs. It works with Ollama or any
OpenAI-compatible API, runs entirely on your own machine, and gives a ChatGPT-like experience
with **no internet connection required after setup**.

### Why local instead of cloud AI?

- **Privacy & data ownership** — prompts and chat history never leave your disk.
- **No internet dependency** — works fully offline once a model is downloaded.
- **Zero marginal cost** — no per-token billing; you already own the hardware.
- **Full model choice** — swap between Llama 3, Gemma 3, Qwen 3, DeepSeek-R1, etc. in one UI.

### Setup

```bash
# 1. Start Ollama
ollama serve &
ollama list                 # see which models you already have
ollama pull llama3.2:1b     # ~1.3GB, fast, good for testing (if you have no models yet)

# 2. Launch Open WebUI — no Docker required
uvx open-webui serve --port 8080

# 3. Open it
open -a "Google Chrome" http://localhost:8080
```

First run installs Open WebUI's Python dependencies and a small embedding model
(`sentence-transformers/all-MiniLM-L6-v2`) — this can take a couple of minutes. On first visit,
create a local admin account (name, email, password); it lives only in Open WebUI's local SQLite
database, not on any external server.

### Verified: "hello" round-trip timing

Confirmed end-to-end by calling Ollama's local API directly (the same path Open WebUI uses):

```bash
curl http://localhost:11434/api/chat -d '{
  "model": "llama3:latest",
  "messages": [{"role": "user", "content": "hello"}],
  "stream": false
}'
```

Response: *"Hello! It's nice to meet you. Is there something I can help you with, or would you
like to chat?"*

| Run | Total duration | Model load | Prompt eval | Response generation |
|-----|----------------|------------|--------------|----------------------|
| Cold start | 4.74s | 4.15s | 0.13s | 0.46s (26 tokens) |
| Warm | 3.24s | 0.33s | 0.16s | 2.52s (26 tokens) |

Measured on an Apple M1 Max, 64GB RAM, macOS 26.6.2, Ollama 0.32.15, Open WebUI v0.11.3.
Screenshot: [`3_Simulation/openwebui-chat.jpg`](../3_Simulation/openwebui-chat.jpg).

---

## 🏗 Framework Tooling: Semantic Search for This Codebase

The AI Stack supports two tiers of semantic search:

### Tier 1 — Kilo Code Local Nomic Text Indexing (Default for Small Projects)
Kilo Code has built-in nomic text indexing for semantic search. It runs locally without any external service and is the **recommended default** when using the delivery-pilot-template for smaller projects.

- **No setup required** — Kilo Code handles indexing internally
- **Zero infrastructure** — no Docker, no external services
- **Best for**: Small repos, template bootstrap, single-developer projects
- **Limitations**: Not designed for large codebases (>10k files) or multi-team repositories

### Tier 2 — Qdrant Vector Database (Big Repos Only)
Qdrant is a dedicated vector database for high-dimensional embedding storage and search. **Only deploy Qdrant when the project grows beyond what Kilo Code local indexing can handle.**

- **Requires Docker** — runs as a container on port 6333
- **Best for**: Large repos, multi-team projects, heavy semantic search workloads
- **Cost**: Docker runtime overhead + storage for embeddings
- **When to switch**: Consider Qdrant when local indexing becomes slow or when you need persistent, shared vector storage across a team

## 🗺 Decision Flow

```
Is this a small/mid-size project?
    ├── YES → Use Kilo Code local nomic text indexing (no setup needed)
    └── NO (big repo, multi-team) → Set up Qdrant below
```

---

## 📥 Installation & Launch

### 1. Qdrant Setup (Big Repos Only)
Qdrant is run inside a Docker container **only when the project outgrows Kilo Code local indexing**:
```bash
# Pull the latest Qdrant image
docker pull qdrant/qdrant

# Run Qdrant container with persistent storage
docker run -d -p 6333:6333 -p 6334:6334 \
    -v $(pwd)/qdrant_storage:/qdrant/storage \
    --name qdrant_local \
    qdrant/qdrant
```
- **REST Port:** `6333`
- **gRPC Port:** `6334`

### 2. Ollama Setup
Install Ollama from [ollama.com](https://ollama.com). Once installed, run the service and pull the embedding model:
```bash
# Pull the nomic-embed-text model (4096 dimensions)
ollama pull nomic-embed-text

# Pull LLM for logic tasks (e.g. llama3 or mistral)
ollama pull llama3
```

---

## 🔌 Connection & Integration Details
- **Kilo Code Local Indexing:** Built-in, no endpoint needed
- **Ollama Endpoint:** `http://localhost:11434`
- **Qdrant Endpoint:** `http://localhost:6333` (only when using big-repo Qdrant tier)
- **Dimensions:** `nomic-embed-text` produces vector embeddings of size `4096`.

---

## 🧪 Verification Checklist
- [ ] Kilo Code semantic search works on the project (built-in, no verification needed)
- [ ] Ollama service is active (`curl http://localhost:11434`) — if using Ollama fallback
- [ ] Qdrant Dashboard is accessible (`http://localhost:6333/dashboard`) — only if using Qdrant for big repos
- [ ] Embedding generation is tested successfully via CLI or script
