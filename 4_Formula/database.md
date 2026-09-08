# 🗄️ Database

This project currently has **no external database**. Open WebUI persists chat history, users,
and settings in its own local SQLite database (created automatically on first run, inside Open
WebUI's data directory) — nothing else to configure.

## If a hosted database is ever needed

The template's default choice is **Supabase** (hosted Postgres, Auth, Realtime). If this project
grows to need one (e.g. syncing chat history across machines), follow the same pattern used
project-wide for secrets:

- Config scaffold: `2_Environment/supabase/config.toml` (`project_id = "openwebui"`)
- Secrets: stored in the existing Azure Key Vault **`dp-kv-deliverypilot`** — do **not** create a
  new vault. See [`2_Environment/setup_azure.md`](../2_Environment/setup_azure.md) for the
  read/write command pattern.

| Environment Variable | Key Vault Secret Name | Purpose |
| :--- | :--- | :--- |
| `SUPABASE_URL` | `SUPABASE-URL` | Project endpoint |
| `SUPABASE_ANON_KEY` | `SUPABASE-ANON-KEY` | Client-safe API key (RLS-scoped) |
| `SUPABASE_SERVICE_ROLE_KEY` | `SUPABASE-SERVICE-ROLE-KEY` | Admin key — backend only, never expose to frontend |

## Best Practices (if adopted)

1. **Row Level Security (RLS):** enable on every table.
2. **Access Control:** anon key for client queries, service-role key for backend/migrations only.
3. **No Secrets in Code:** `.env.example` holds placeholder names only; real values come from
   `dp-kv-deliverypilot` at runtime.
