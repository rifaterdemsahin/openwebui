# Risks

> **Stage 1: Real Unknown** — Risk register, updated every cycle.

## Active Risks

| ID | Risk | Severity | Mitigation |
|----|------|----------|------------|
| R-001 | Large local models (27B+) may be too slow on this hardware for interactive use | Medium | Document per-model timings; recommend smaller models (7-8B) as the default |
| R-002 | `.webui_secret_key` or local SQLite DB accidentally committed to git | Medium | `.gitignore` excludes `.webui_secret_key`, `*.db`; verified with `git status` before each commit |
| R-003 | Broken relative links after the template refactor (moved/renamed files) | Medium | `5_Symbols/toolbox/smoke_test.py` link-checks navigation config before every deploy |
| R-004 | Key Vault (`dp-kv-deliverypilot`) is a shared vault with many unrelated secrets — risk of touching the wrong one | Low | Only read/write secrets explicitly prefixed/scoped for this project; never list or dump the full vault in output |

## Solved Risks

| ID | Risk | Resolution |
|----|------|------------|
| R-S01 | No public documentation existed for the local setup | Published `index.html` via GitHub Pages |
| R-S02 | GitHub Pages was on the legacy branch-deploy path (no test gate) | Switched to Actions-based deploy gated on `smoke_test.py` |

## Risk Update Log

- 2026-09-08 — Initial risk register created during template refactor.
