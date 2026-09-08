# 🤖 openwebui

Open WebUI is an open-source, self-hosted web interface for chatting with LLMs. It works with
[Ollama](https://ollama.com) 🦙 or any OpenAI-compatible API, runs entirely on your own machine, and
gives you a ChatGPT-like experience 🔒 with no internet connection required after setup.

### 📖 Full guide (GitHub Pages)

👉 **https://rifaterdemsahin.github.io/openwebui/**

The published page has the full setup guide, a 📸 screenshot of it running, every command used, and
a verified ⏱️ "hello" round-trip timing test against a local Ollama model.

## 🚀 Quick start

```bash
# 1. Start Ollama
ollama serve &
ollama list

# 2. Launch Open WebUI (no Docker required)
uvx open-webui serve --port 8080

# 3. Open it
open -a "Google Chrome" http://localhost:8080
```

## 🗂️ Project structure

This repo follows the [`delivery-pilot-template`](https://github.com/rifaterdemsahin/delivery-pilot-template)
7-stage self-learning framework — click the ⚙️ debug button (bottom-right of the site) for the
full project log, or browse the numbered folders directly:

| Stage | Folder | Purpose |
|-------|--------|---------|
| 1 | [`1_Real_Unknown/`](1_Real_Unknown) | Problem statement, OKRs, risks, prompt log |
| 2 | [`2_Environment/`](2_Environment) | Setup guides — incl. [`setup_ai.md`](2_Environment/setup_ai.md) (Open WebUI + Ollama) |
| 3 | [`3_Simulation/`](3_Simulation) | Screenshot / visual evidence |
| 4 | [`4_Formula/`](4_Formula) | Specs, decisions, reasoning log |
| 5 | [`5_Symbols/`](5_Symbols) | Markdown renderer, toolbox scripts, coding rules |
| 6 | [`6_Semblance/`](6_Semblance) | Error/fix logs, lessons learned |
| 7 | [`7_Testing_Known/`](7_Testing_Known) | Smoke tests, validation report |

## 🔐 Secrets

Secrets (if any are ever needed) are read from the existing shared Azure Key Vault
**`dp-kv-deliverypilot`** — see [`2_Environment/setup_azure.md`](2_Environment/setup_azure.md).
No new vault is created for this project. Nothing in the current scope needs a secret: Ollama and
Open WebUI both run unauthenticated on `localhost`.

## 🔗 Links

- **GitHub:** [rifaterdemsahin/openwebui](https://github.com/rifaterdemsahin/openwebui)
- **LinkedIn:** [rifaterdemsahin](https://www.linkedin.com/in/rifaterdemsahin/)
- **YouTube:** [@RifatErdemSahin](https://www.youtube.com/@RifatErdemSahin)
