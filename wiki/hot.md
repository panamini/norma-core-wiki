---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-06-29
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- PR #144 / R22 merged at `b80a53d3d13863abd4dca4f944dcdc74aab6eaa3`.
- Current local static read-only viewer can inspect existing Structured Analyze result JSON and completed `norma.analyzeStructuredCompositionV1` MCP responses.
- Direct engine output and `result.json` remain canonical truth; viewer output is derived inspection only.
- Current recommended next PR: `R23: local inspection surface onboarding fixture and workflow polish`.
- R23 must stay local-only, static, read-only, docs/tests backed, and must not change engine behavior, package exports, package metadata, lockfiles, CLI runtime, MCP runtime, report-kit runtime, hosted/remote behavior, SDK/API behavior, public package readiness, public app submission, or source-truth rules.
- R14/R16/R18/R19/R20/R21 are historical context now, not current next-step instructions.

## Retrieval Map
- Project overview: `wiki/overview.md`
- Canonical page catalog: `wiki/index.md`
- Mutation history: `wiki/log.md`
- Orchestrator: `wiki/tech/norma-orchestrator.md`
- PR roadmap and gates: `wiki/strategy/mvp-pr-roadmap.md`
- R22 checkpoint and R23 prompt: `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
- Post-PR6 checkpoint: `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- R6D checkpoint: `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest ingest
- Added R22 local Structured Analyze inspection checkpoint on 2026-06-29:
  - `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
- Synced post-R14 roadmap state on 2026-06-27:
  - `wiki/strategy/mvp-pr-roadmap.md`
  - `wiki/overview.md`
  - removed stale R1-as-next guidance from active retrieval
- Added R6D ChatGPT `_meta` connector checkpoint on 2026-06-25.
- Updated durable pages from the post-PR6 ChatGPT Secure MCP Tunnel checkpoint on 2026-06-24.
