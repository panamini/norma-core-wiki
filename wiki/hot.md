---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-11
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- GitHub PR #214 merged the PR132 validation hardening checkpoint at `643fc88af508efe271741c23249807b62bc577ed`.
- Current local visual candidate review and selection surface is PR131/PR132; selection intent is non-authoritative.
- Existing PR129 `--resume` remains the only path to AcceptedGeometry, Core / Structured Analyze, and canonical `result.json`.
- logical PR134 is the next implementation contract, but it remains blocked until the exact loopback/local-only MCP orchestration contract is separately approved.
- Private/dev ChatGPT + MCP visual pilot is selected as the next external track, but connector/runtime/hosting/auth/provider/public surfaces remain unapproved.
- Use `wiki/outputs/2026-07-11-pr214-validation-hardening-checkpoint.md` for the current durable checkpoint.

## Retrieval Map
- Project overview: `wiki/overview.md`
- Canonical page catalog: `wiki/index.md`
- Mutation history: `wiki/log.md`
- Orchestrator: `wiki/tech/norma-orchestrator.md`
- PR roadmap and gates: `wiki/strategy/mvp-pr-roadmap.md`
- PR214 checkpoint: `wiki/outputs/2026-07-11-pr214-validation-hardening-checkpoint.md`
- Post-PR6 checkpoint: `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- R6D checkpoint: `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest ingest
- Added PR214 validation hardening checkpoint on 2026-07-11:
  - `wiki/outputs/2026-07-11-pr214-validation-hardening-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
  - updated `wiki/product/norma-product-vision.md`
  - updated `wiki/overview.md`
- Added R22 local Structured Analyze inspection checkpoint on 2026-06-29:
  - `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
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
