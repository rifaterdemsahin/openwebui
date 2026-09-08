# Problem Statement

> **Stage 1: Real Unknown** — The "Why" behind this project.

## Core Problem

Cloud AI chat assistants (ChatGPT, etc.) require an internet connection and send every
prompt to a third-party server. That's a privacy, cost, and availability problem for anyone
who wants a private, offline, or zero-marginal-cost AI assistant on hardware they already own.

## Target Audience

- Developers and power users with a capable local machine (Apple Silicon Mac, GPU-equipped PC)
  who already run [Ollama](https://ollama.com) and want a proper chat UI instead of the CLI.
- Anyone who wants ChatGPT-like UX without sending data to a third party.

## Goals

- Stand up [Open WebUI](https://docs.openwebui.com) locally, connected to a local Ollama instance.
- Document the setup so it's reproducible in minutes, not hours.
- Prove it works end-to-end with a real request/response and measured timings.
- Publish the guide as a public static site (GitHub Pages).

## Non-Goals

- Hosting a multi-user/cloud-deployed instance (this is a local-first, single-user setup).
- Building new LLM inference code — Ollama and Open WebUI are used as-is, not modified.

## Success Metrics

See [`okrs.md`](okrs.md).
