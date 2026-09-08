# 📓 Lessons Learned & Active Reflection Journal

> This log captures retrospectives, insights, and lessons learned during development milestones.

---

## 📅 2026-09-08: Local Open WebUI + Ollama bring-up

### What went well
- `uvx open-webui serve` avoided any Docker dependency — fastest path to a working local UI.
- Verifying the "hello" round-trip directly against Ollama's `/api/chat` (bypassing the browser)
  gave reliable, reproducible timing data when the browser UI itself was flaky mid-session.

### Gaps & Challenges
- The Open WebUI chat UI occasionally failed to render a streamed response in the browser during
  testing, and unrelated text appeared in the input at one point — likely concurrent use of the
  same Chrome profile. Falling back to a direct API call was the pragmatic path to unblock.

## 📅 2026-09-08: Template refactor onto delivery-pilot-template

### What went well
- The template's own README documents the exact "Refactor" prompt as a first-class example —
  made intent unambiguous.
- `bootstrap-template` skill gave a clear placeholder table, reducing guesswork.

### Gaps & Challenges
- The template ships with the *template project's own* historical dev logs baked into
  `1_Real_Unknown/`, `4_Formula/llm_thinking_log.md`, and `6_Semblance/`. These had to be reset to
  project-specific content rather than literally kept, per the bootstrap skill's step 2.
- Several links used the template author's local absolute paths
  (`file:///Users/rifaterdemsahin/projects/delivery-pilot-template/...`) — broken for anyone else
  by construction. Converted to relative paths.
