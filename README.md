# openwebui

Open WebUI is an open-source, self-hosted web interface for chatting with LLMs. It works with
[Ollama](https://ollama.com) or any OpenAI-compatible API, runs entirely on your own machine, and
gives you a ChatGPT-like experience with no internet connection required after setup.

See [`index.html`](index.html) (published via GitHub Pages) for the full setup guide, a screenshot
of it running, the commands used, and a verified "hello" round-trip timing test against a local
Ollama model.

## Quick start

```bash
# 1. Start Ollama
ollama serve &
ollama list

# 2. Launch Open WebUI (no Docker required)
uvx open-webui serve --port 8080

# 3. Open it
open -a "Google Chrome" http://localhost:8080
```
