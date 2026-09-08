# Cost Tracker

> **Stage 1: Real Unknown** — Environment, infrastructure, and LLM running costs.

## Summary

This project is **local-first and free to run**: no cloud LLM API calls, no hosted database,
no paid infrastructure. The only "cost" is electricity and the hardware already owned.

| Item | Cost | Notes |
|------|------|-------|
| Ollama (local inference) | $0 | Runs on-device; models already downloaded |
| Open WebUI | $0 | Open-source, self-hosted via `uvx` |
| GitHub Pages | $0 | Free for public repos |
| Azure Key Vault (`dp-kv-deliverypilot`) | ~$0.03 / 10,000 ops | Shared vault, pay-per-operation; no secrets needed yet for this project so $0 incurred |

## Monitoring

No token-metered LLM API is in use, so there is no per-request cost to monitor. If a cloud
LLM provider is added later (e.g. for a hosted fallback), add its pricing here and set a
spike-alert threshold.
