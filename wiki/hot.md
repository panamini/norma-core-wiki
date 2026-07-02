---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-03
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- Latest merged Norma Core state is PR #179 / PR99 at `82b125d52e16760e58fb7db6928702269d03bb19`.
- PR99 prepared the local `@norma/core` package tarball boundary and proved local packed-tarball install/import.
- Package state remains pre-publication: `private: true`, version `0.1.0`, package-root export only, and minimal `files` allowlist: `dist/src/**/*.d.ts`, `dist/src/**/*.js`, `README.md`.
- Direct engine output and `result.json` remain canonical truth; `guide.html`, `report.html`, `visual.svg`, `summary.json`, and `summary.md` are derived local inspection artifacts only.
- PR99 did not publish, tag, release, configure npm auth, set provenance, add a release workflow, change dependencies or lockfiles, add package-level `bin`, or unlock hosted MCP, ChatGPT connector runtime, providers, adapters, or runtime behavior.
- Current recommended next Norma Core PR: PR100 finalize the package publication candidate without publishing.
- Actual npm publication still requires explicit maintainer approval and a separate operation.

## Retrieval Map
- Project overview: `wiki/overview.md`
- Canonical page catalog: `wiki/index.md`
- Mutation history: `wiki/log.md`
- PR roadmap and gates: `wiki/strategy/mvp-pr-roadmap.md`
- Post-PR99 package tarball checkpoint: `wiki/outputs/2026-07-03-post-pr99-package-tarball-local-install-checkpoint.md`
- Post-PR98 publication gate checkpoint: `wiki/outputs/2026-07-03-post-pr98-guided-inspection-publication-gate-checkpoint.md`
- Post-PR95 package API export checkpoint: `wiki/outputs/2026-07-02-post-pr95-package-api-export-contract-checkpoint.md`
- Post-PR93 guided inspection checkpoint: `wiki/outputs/2026-07-02-post-pr93-guided-inspection-package-api-checkpoint.md`
- PR86 metric-policy checkpoint: `wiki/outputs/2026-07-01-pr86-normalization-metric-policy-checkpoint.md`
- Archived PR85 endgame snapshot: `wiki/outputs/2026-07-01-pr85-endgame-roadmap-status.md`
- Post-PR82 accepted geometry bridge checkpoint: `wiki/outputs/2026-07-01-post-pr82-accepted-geometry-structured-analyze-bridge-checkpoint.md`
- R22 checkpoint and R23 prompt: `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
- Post-PR6 checkpoint: `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- R6D checkpoint: `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest ingest
- Added post-PR99 package tarball local install checkpoint on 2026-07-03:
  - `wiki/outputs/2026-07-03-post-pr99-package-tarball-local-install-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
  - updated `wiki/overview.md`
- Added post-PR98 guided inspection package publication gate checkpoint on 2026-07-03:
  - `wiki/outputs/2026-07-03-post-pr98-guided-inspection-publication-gate-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
  - updated `wiki/overview.md`
- Added post-PR95 guided inspection package API export checkpoint on 2026-07-02:
  - `wiki/outputs/2026-07-02-post-pr95-package-api-export-contract-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
  - updated `wiki/overview.md`
- Added post-PR93 guided inspection package/API checkpoint on 2026-07-02:
  - `wiki/outputs/2026-07-02-post-pr93-guided-inspection-package-api-checkpoint.md`
  - updated `wiki/strategy/mvp-pr-roadmap.md`
  - updated `wiki/tech/core-interface-boundary.md`
  - updated `wiki/overview.md`
