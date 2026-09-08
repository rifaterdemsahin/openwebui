# Hypotheses

> **Stage 1: Real Unknown** — What we believe but haven't fully proven yet.

## H1: Open WebUI + Ollama is "good enough" to replace cloud chat for local/offline use

- **Belief:** Response quality and latency on consumer Apple Silicon hardware (M1 Max, 64GB)
  is acceptable for everyday chat use.
- **Evidence so far:** `llama3:latest` warm response in ~3.2s for a short prompt (26 tokens).
  See timing table in [`2_Environment/setup_ai.md`](../2_Environment/setup_ai.md).
- **Status:** Supported for short prompts on 7-8B models; larger models (27B+) will be slower —
  not yet benchmarked.
- **Linked Test:** [`7_Testing_Known/validation_report.md`](../7_Testing_Known/validation_report.md)

## H2: `uvx open-webui serve` is a viable Docker-free path for quick local setup

- **Belief:** Avoiding Docker Desktop reduces setup friction on macOS.
- **Evidence so far:** Confirmed working — first run installs ~260 Python packages and an
  embedding model, subsequent runs start in seconds.
- **Status:** Confirmed.

## H3: No secrets are required for a fully local setup

- **Belief:** Since Ollama and Open WebUI both run unauthenticated on localhost, no Azure Key
  Vault secret is needed for this project's current scope.
- **Status:** Confirmed — see [`2_Environment/setup_azure.md`](../2_Environment/setup_azure.md).
  Revisit if this project later adds a hosted/multi-user deployment.
