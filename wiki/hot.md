---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-06-30
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- Latest merged Norma Core state is PR #147 / R25 at `3889cf84d6df41391996d9d16cb76b5c48638a2d`.
- R22-R25 completed the local Structured Analyze inspection/protection rail: read-only viewer inspection, onboarding fixture, scenario regression harness, and static safety guard.
- PR #148 / R26 is open as the post-R25 roadmap truth-sync candidate at `67be4b4376a5f22272a3179b99c35e799aacb847`; it is not merged yet.
- Direct engine output and `result.json` remain canonical truth; report/viewer artifacts are derived inspection only.
- The active roadmap model is gate-based, not a PR27-PR46 execution queue. Pick one isolated PR from current gaps.
- Package publication, hosted MCP, remote API, public product/web surface, public ChatGPT submission, image/vision/CAD/provider input, recommendation, optimization, and beauty scoring remain blocked until explicit approval.

## Retrieval Map
- Project overview: `wiki/overview.md`
- Canonical page catalog: `wiki/index.md`
- Mutation history: `wiki/log.md`
- Orchestrator: `wiki/tech/norma-orchestrator.md`
- PR roadmap and gates: `wiki/strategy/mvp-pr-roadmap.md`
- Post-R25 roadmap checkpoint: `wiki/outputs/2026-06-30-post-r25-roadmap-compression-checkpoint.md`
- R22 checkpoint and R23 prompt: `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
- Post-PR6 checkpoint: `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- R6D checkpoint: `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest ingest
- Synced post-R25 roadmap compression state on 2026-06-30:
  - `wiki/outputs/2026-06-30-post-r25-roadmap-compression-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
  - updated `wiki/meta/pr0-governance-checklist.md`
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
