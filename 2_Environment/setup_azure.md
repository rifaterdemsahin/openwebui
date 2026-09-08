# ☁️ Azure Key Vault & Credentials Setup Guide

> **Stage 2: Environment** — Configuration and onboarding instructions for secrets management.

---

## 🔒 Azure Key Vault — Existing Vault Only

This project uses the **existing, shared** Azure Key Vault **`dp-kv-deliverypilot`**
(resource group `deliverypilot-rg`, region `uksouth`). **Do not create a new Key Vault** for this
project — it's a shared vault across multiple delivery-pilot projects.

### Current status: no secrets needed

Open WebUI and Ollama both run **unauthenticated on localhost** — nothing in this project's
current scope calls an external API or needs a credential. Nothing has been written to the vault
for this project. This section documents the pattern to follow **if/when** that changes (e.g. a
remote Ollama host, a hosted Open WebUI deployment, or a cloud LLM fallback).

### 1. Azure Authentication
```bash
az login
az account set --subscription "Azure subscription 1"
```

### 2. Read a secret (never dump the whole vault)
```bash
az keyvault secret show --vault-name dp-kv-deliverypilot --name "<SECRET-NAME>" --query value -o tsv
```

### 3. Write a secret — only for a value this project actually owns
```bash
az keyvault secret set --vault-name dp-kv-deliverypilot --name "<SECRET-NAME>" --value "<value>"
```

Naming convention: prefix project-specific secrets with `openwebui-` (e.g.
`openwebui-remote-ollama-token`) so they're identifiable inside the shared vault without
colliding with unrelated projects' secrets.

> ⚠️ `dp-kv-deliverypilot` is a large shared vault containing many unrelated personal and
> project credentials. Never run a bare `az keyvault secret list` and paste the output somewhere
> public — always target a specific, known secret name.

---

## 🔑 GitHub Actions Integration (for when secrets are needed)

1. Create/reuse a Service Principal scoped to `dp-kv-deliverypilot` only.
2. Store its JSON credentials as a GitHub repository secret named `AZURE_CREDENTIALS`.
3. In workflows:
   ```yaml
   - name: Azure Login
     uses: azure/login@v1
     with:
       creds: ${{ secrets.AZURE_CREDENTIALS }}
   - name: Get secrets
     uses: Azure/get-keyvault-secrets@v1
     with:
       keyvault: "dp-kv-deliverypilot"
       secrets: "openwebui-example-secret"
   ```

---

## 🧪 Verification Checklist
- [ ] Azure CLI authenticated (`az account show`)
- [ ] Vault reference is `dp-kv-deliverypilot` — no new vault created
- [ ] Zero secret values committed to source files
- [ ] Any project secret is named with the `openwebui-` prefix
