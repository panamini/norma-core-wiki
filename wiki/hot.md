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
- Latest merged Norma Core state is PR #239 at `652574fb435c20233658c0c681a8f06f56ef80d1` from reviewed head `b6352bd6d751cc25c6036c28b208f47b7dd0e0d8`.
- The latest personal visual-harmony checkpoint is `wiki/outputs/2026-07-16-personal-visual-harmony-checkpoint.md`.
- The dedicated triangle construction gate later passed in a separate live run
  with 13 derived constructions total.
- PR #239 completed the altitude gate: one explicit canonical triangle now
  yields exactly three derived altitudes, and the next immediate application
  leaf is a small diagnostic/runbook PR exposing triangle request presence/
  count and missing prerequisites. After that comes read-only triangle-center
  assessment, with centroid as the first candidate only after assessment.
  Circumcenter, incenter, orthocenter, rhythm, perspective, physical
  rectification, and harmonic interpretation remain deferred.
- The local static read-only viewer still inspects existing Structured Analyze result JSON and completed `norma.analyzeStructuredCompositionV1` MCP responses.
- Direct engine output and `result.json` remain canonical truth; viewer output is derived inspection only.
- Use `wiki/strategy/mvp-pr-roadmap.md` and `wiki/outputs/2026-07-17-post-pr239-triangle-altitudes-live-gate-checkpoint.md` for current truth.

## Retrieval Map
- Overview/index/log: `wiki/{overview,index,log}.md`
- Roadmap: `wiki/strategy/mvp-pr-roadmap.md`
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
- Updated `wiki/outputs/2026-07-16-triangle-constructions-live-gate-checkpoint.md`
  with the separate triangle gate pass and next dependency.
- Added `wiki/outputs/2026-07-17-post-pr239-triangle-altitudes-live-gate-checkpoint.md`
  for the PR #239 altitude gate pass and next-step ordering.
- Updated `wiki/outputs/2026-07-16-personal-visual-harmony-checkpoint.md` through PR #238.
- Updated roadmap, overview, index, log, and boundary through the merged PR #239
  altitude gate; the dedicated triangle construction gate later passed in a
  separate live run, and the next immediate application leaf is the diagnostic/
  runbook PR exposing triangle request presence/count and missing prerequisites.
