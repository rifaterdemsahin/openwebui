# OKRs

> **Stage 1: Real Unknown** — Objectives and Key Results.

## Objective 1: Run a private, local ChatGPT-equivalent

- **KR1:** Open WebUI reachable at `http://localhost:8080`, backed by a local Ollama instance — ✅ Done
- **KR2:** At least one chat model responds correctly to a real prompt, with timing evidence captured — ✅ Done (`llama3:latest`, see [`2_Environment/setup_ai.md`](../2_Environment/setup_ai.md))
- **KR3:** Setup is reproducible from a documented command list in under 10 minutes — ✅ Done

## Objective 2: Publish reproducible documentation

- **KR1:** Public GitHub Pages site describing rationale + setup — ✅ Done — https://rifaterdemsahin.github.io/openwebui/
- **KR2:** Repo follows the delivery-pilot-template 7-stage structure so it's self-learning and auditable — ✅ Done (this refactor)
- **KR3:** CI smoke-tests gate every deploy — ✅ Done (`.github/workflows/static.yml`)

## Related

- Final validation checklist: [`7_Testing_Known/README.md`](../7_Testing_Known/README.md)
