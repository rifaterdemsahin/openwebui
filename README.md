# 🤖 openwebui

Open WebUI is an open-source, self-hosted web interface for chatting with LLMs. It works with
[Ollama](https://ollama.com) 🦙 or any OpenAI-compatible API, runs entirely on your own machine, and
gives you a ChatGPT-like experience 🔒 with no internet connection required after setup.

### 📖 Full guide (GitHub Pages)

👉 **https://rifaterdemsahin.github.io/openwebui/**

The published page has the full setup guide, a 📸 screenshot of it running, every command used, and
a verified ⏱️ "hello" round-trip timing test against a local Ollama model. Source: [`index.html`](index.html).

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
