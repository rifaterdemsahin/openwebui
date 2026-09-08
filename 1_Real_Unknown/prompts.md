# Prompts

Every prompt used in this project is recorded here as an audit trail.

---

| Date | Agent | Purpose | Prompt (summary) | Outcome |
|------|-------|---------|-------------------|---------|
| 2026-09-08 | Claude | Stand up Open WebUI + local Ollama | "implement openwebui and access the local ollama on this macbook. take a screenshot when it runs and explain how to use it in index.html, commit and push, enable github pages" | Ran Ollama + `uvx open-webui serve`, created admin account, verified `llama3:latest` chat via direct API call, wrote `index.html` guide with rationale, screenshot, and timing table; enabled GitHub Pages; committed and pushed |
| 2026-09-08 | Claude | Add GitHub Pages link to README | "add the github pages links to the readme.md use emojis where it makes sense" | Added Pages URL + emojis to `README.md`; committed and pushed |
| 2026-09-08 | Claude | Refactor onto delivery-pilot-template | "Refactor the existing project. use the template from delivery-pilot-template. Replace the codes the necessary folders and fix the broken links, commit push, use key vault /vaults/dp-kv-deliverypilot/secrets (no new vault), get the necessary skills from popular github repos" | Pulled the 7-stage scaffold + agent persona files, replaced placeholders, migrated existing guide content into stage folders, fixed inherited absolute-path links, wired Key Vault reference pattern (no new vault, no secrets needed yet), switched Pages to Actions-based smoke-gated deploy; committed and pushed |
