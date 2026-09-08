# Tasks & Phases

> **Stage 1: Real Unknown** — Phase breakdown feeding the Kanban board.

## Phase 1 — Local Stack Bring-up ✅

1. Start Ollama, confirm models installed
2. Launch Open WebUI (`uvx open-webui serve --port 8080`)
3. Create local admin account
4. Select a chat model and verify a real response

## Phase 2 — Evidence & Documentation ✅

1. Screenshot the running app
2. Time a "hello" round-trip (cold + warm) directly against the Ollama API
3. Write the setup guide and rationale (`index.html`)
4. Enable GitHub Pages

## Phase 3 — Framework Refactor ✅

1. Pull in `delivery-pilot-template` 7-stage scaffold
2. Replace placeholders, migrate existing content into the right stage folders
3. Fix broken/absolute links inherited from the template
4. Wire Azure Key Vault (`dp-kv-deliverypilot`) reference pattern — no secrets needed yet
5. Switch GitHub Pages deploy to the Actions-based, smoke-test-gated workflow
6. Commit and push

## Phase 4 — Follow-ups (Backlog)

1. Document more installed models with timings
2. Decide on remote/hosted deployment scope
