# Sanity Check Report

> **Stage 1: Real Unknown** — Delivery-correctness report, consumes `7_Testing_Known/` data.

## Latest Run: 2026-09-08

| # | Check | Result |
|---|-------|--------|
| 1 | `index.html` exists at repo root | ✅ |
| 2 | `navigation_config.json` present and valid JSON | ✅ |
| 3 | All 7 stage folders present with README | ✅ |
| 4 | README contains GitHub Pages URL | ✅ `https://rifaterdemsahin.github.io/openwebui/` |
| 5 | `.github/workflows/static.yml` present (Actions-based Pages deploy, smoke-gated) | ✅ |
| 6 | No secrets committed to git (`.webui_secret_key`, `.env` excluded) | ✅ |
| 7 | Key Vault reference uses existing `dp-kv-deliverypilot` (no new vault created) | ✅ |
| 8 | Broken absolute `file:///Users/...` links from template inheritance | ✅ Fixed (converted to relative paths) |

Full smoke test output: [`6_Semblance/smoke_test_report.md`](../6_Semblance/smoke_test_report.md).
