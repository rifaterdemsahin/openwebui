# Kanban Board

> **Stage 1: Real Unknown** — Task tracking across the 7 stages.

## Done

- Install Ollama + confirm local models available — [`2_Environment/setup_ai.md`](../2_Environment/setup_ai.md)
- Run Open WebUI via `uvx` (no Docker) on port 8080
- Create local admin account, select `llama3:latest`, verify chat round-trip
- Capture screenshot of running app — [`3_Simulation/`](../3_Simulation/)
- Measure cold-start vs warm timing via direct Ollama API call
- Publish `index.html` guide + enable GitHub Pages
- Refactor repo onto `delivery-pilot-template` 7-stage structure
  - Stage Reference: [`README.md`](../README.md)

## In Progress

- Wire CI smoke-test gate into GitHub Pages deploy
  - Stage Reference: [`6_Semblance/`](../6_Semblance/)

## Backlog

- Document additional installed models (gemma3, qwen3-coder, deepseek-r1) with timings
  - Stage Reference: [`2_Environment/setup_ai.md`](../2_Environment/setup_ai.md)
- Evaluate whether a remote/hosted Open WebUI deployment is worth documenting (Fly.io + Key Vault)
  - Stage Reference: [`2_Environment/setup_azure.md`](../2_Environment/setup_azure.md)

## Maintenance

- Review commits regularly, keep this board and `tasks.md` in sync with actual repo state
