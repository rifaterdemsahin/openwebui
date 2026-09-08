# Open Questions

> **Stage 1: Real Unknown** — Unresolved questions, revisited each cycle.

1. Should this project eventually support a remote/multi-user Open WebUI deployment (e.g. on
   Fly.io), which *would* require Azure Key Vault secrets (`OLLAMA_HOST` for a remote GPU box,
   auth tokens)? — Not yet decided; current scope is local-only.
2. Which additional models are worth documenting timings for (beyond `llama3:latest`)? Candidates
   already installed locally: `gemma3:12b`, `qwen3-coder:30b`, `deepseek-r1:latest`.
3. Is RAG / file upload (Open WebUI's built-in knowledge base) worth documenting as a follow-up
   guide?

Move fully resolved questions to `1_Real_Unknown/_obsolete/questions.md` if this log gets
too cluttered.
