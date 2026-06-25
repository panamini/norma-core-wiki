---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-06-25
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- Norma Core now has merged PR96 local orchestration tooling.
- Use `wiki/tech/norma-orchestrator.md` for the current trust contract.
- Treat the orchestrator as `L1_ADVISORY`: useful for context, doctor checks, validation planning, dry-run evidence, and PR support, but not yet a primary autonomous driver.
- PR6 ChatGPT Secure MCP Tunnel smoke passed and merged at `658ea2069d1c6a65b23df7f43ba4c4ba96fd8a31` on `main-after-codex-mcp-tool`; the app stayed private/dev and the tunnel was stopped after testing.
- PR113 / R6D merged at `bba597bca40facaf36fd7741712a0b0b9d8754e6`; current-main private ChatGPT connector smoke passed with the six-tool inventory, `_meta` compatibility, positive replay, and negative prompt guardrails.
- Next mandatory product/code PR: R1 duplicate geometry source identities. Do not start outputSchema, ChatGPT Analyze expansion, hosting, or publishing first.

## Retrieval Map
- Project overview: `wiki/overview.md`
- Canonical page catalog: `wiki/index.md`
- Mutation history: `wiki/log.md`
- Orchestrator: `wiki/tech/norma-orchestrator.md`
- PR roadmap and gates: `wiki/strategy/mvp-pr-roadmap.md`
- Post-PR6 checkpoint: `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- R6D checkpoint: `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest ingest
- Added R6D ChatGPT `_meta` connector checkpoint on 2026-06-25:
  - `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
- Updated durable pages from the post-PR6 ChatGPT Secure MCP Tunnel checkpoint on 2026-06-24:
  - `wiki/tech/norma-orchestrator.md`
  - `wiki/strategy/mvp-pr-roadmap.md`
  - `wiki/tech/core-interface-boundary.md`
- Ingested Norma Core PR execution map v1 on 2026-06-23:
  - `wiki/sources/2026-06-23-norma-core-pr-execution-map-v1.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
- Added PR96 orchestrator retrieval context on 2026-06-23:
  - `wiki/tech/norma-orchestrator.md`
  - `wiki/sources/2026-06-23-pr96-norma-orchestrator-v0.md`
- Ingested the product vision and integration draft from `rawinput/` into `raw/` on 2026-06-19.
- Ingested the attached Norma Core endgame prompt into raw on 2026-06-17.
- Ingested 2 files from rawinput into raw on 2026-06-13.
