---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-17
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- Latest merged Norma Core state is PR #243 at `4cf8cd169a1c01fd64f654b1c6848061c590c7e0` from reviewed head `9148a8af9c7c529983299d2fcf3889cdd423def9`; the live replay is `LIVE_ACCEPTANCE_PASS` with build PASS, suite `1700/1700`, `/healthz=live`, `/readyz=ready`, and byte-identical install.
- The live acceptance checkpoint is `wiki/outputs/2026-07-17-cc-personal-main-live-acceptance-v6.md`.
- The canonical next gate is `PERSONAL-HELDOUT-LIVE-ACCEPTANCE-MATRIX-v1`; do not jump to another immediate triangle-center changeset.
- The dedicated triangle construction gate later passed in a separate live run with 13 derived constructions total; keep that checkpoint as historical context only.
- The local static read-only viewer still inspects existing Structured Analyze result JSON and completed `norma.analyzeStructuredCompositionV1` MCP responses.
- Direct engine output and `result.json` remain canonical truth; viewer output is derived inspection only.
- Use `wiki/strategy/mvp-pr-roadmap.md`, `wiki/outputs/2026-07-17-cc-personal-main-live-acceptance-v6.md`, `wiki/tech/core-interface-boundary.md`, and `wiki/overview.md` for current truth.

## Retrieval Map
- Overview/index/log: `wiki/{overview,index,log}.md`
- Roadmap: `wiki/strategy/mvp-pr-roadmap.md`
- Live acceptance checkpoint: `wiki/outputs/2026-07-17-cc-personal-main-live-acceptance-v6.md`
- Triangle altitude checkpoint: `wiki/outputs/2026-07-17-post-pr239-triangle-altitudes-live-gate-checkpoint.md`
- Triangle gate checkpoint: `wiki/outputs/2026-07-16-triangle-constructions-live-gate-checkpoint.md`
- Visual-harmony checkpoint: `wiki/outputs/2026-07-16-personal-visual-harmony-checkpoint.md`
- Authority boundary: `wiki/tech/core-interface-boundary.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest update
- Updated `wiki/outputs/2026-07-17-cc-personal-main-live-acceptance-v6.md` with
  the exact-main live acceptance PASS, final triangle/medians/centroid state,
  and held-out gate handoff.
- Updated roadmap, overview, index, log, and boundary to reflect PR #243 and
  the canonical held-out next gate.
- Kept `wiki/outputs/2026-07-17-post-pr239-triangle-altitudes-live-gate-checkpoint.md`
  and `wiki/outputs/2026-07-16-triangle-constructions-live-gate-checkpoint.md`
  as historical retrieval anchors.
