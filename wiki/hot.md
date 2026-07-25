---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-25
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- Latest merged Norma Core state is PR #268 at `678134b59db146b1ad8a2c8f3344df52f16ce642`; PR #259-#268 established provider-neutral OAuth/Scalekit remote MCP auth, remote visual sandbox hardening, provider-neutral authorization-data boundaries, the PostgreSQL transaction adapter, and safe authorization transaction closeout.
- Current strongest status is a proven local PostgreSQL contract with live Supabase RLS still deferred. Railway remains the control-plane target, Supabase PostgreSQL/RLS is the probable data target, Scalekit is the first sandbox, Auth0 remains the fallback, Core stays local/offline, and GPU/package/geometry expansion stays deferred.
- The private stable runtime was promoted byte-identically from merged content with a rollback snapshot and exactly one authorized launchd restart; direct MCP initialize/tools-list smoke passed.
- Three fresh ChatGPT preparations/confirmations passed after reload with zero provider API calls and zero retry. The declared comparisons were 50.175% vs 50% (delta 0.175 pt), 63.258% vs 61.803% (delta 1.454 pt), and 67.846% vs 66.667% (delta 1.18 pt); the phi-minor/50% discrepancy was a separate Core card, not a gate failure.
- `CC-20260719-PERSONAL-POST-PR248-LIVE-ACCEPTANCE v1` is PASS: one omitted vertical guide was drawn manually, refined as separate pixel evidence, adopted and reverted, deleted without stale references, restored cleanly after reload, confirmed once through Core, and absent from a fresh same-file repréparation.
- Personal Visual Acceptance Pack v1 produced semantically acceptable preparations for `6/6` cases and `5/6` bounded confirmation/Core successes with zero human geometry corrections and zero accepted-operation retries in the same case/conversation. Case 2 used one case-level fresh isolated execution after a non-terminal surface attempt; no accepted call or recovery action was repeated in that conversation. The remaining case was blocked by a non-terminal ChatGPT surface response.
- Guided entry is live-accepted: `Analyse cette image avec Norma` produced usable editable `À CONFIRMER` widgets for all six frozen cases after the one corrective PR, with no automatic confirmation or Core run.
- Verdict remains `observation-partial`: declared geometric comparisons are useful in the private flow, but artistic usefulness, latency p50/p95, mobile proof, sustained use, and commercial/public readiness remain unproven. The next dependency is explicit Auth0/Render private-beta authorization; no benchmark, new geometry, harmonic-pack expansion, public deployment, or provider work first.
- Use `wiki/strategy/mvp-pr-roadmap.md`, `wiki/outputs/2026-07-17-cc-personal-main-live-acceptance-v6.md`, `wiki/tech/core-interface-boundary.md`, and `wiki/overview.md` for current truth.

## Retrieval Map
- Overview/index/log: `wiki/{overview,index,log}.md`
- Roadmap: `wiki/strategy/mvp-pr-roadmap.md`
- Quick start: `wiki/howto/personal-visual-harmony-quick-start.md`
- Final visual acceptance pack: `wiki/outputs/2026-07-19-personal-visual-acceptance-pack-v1.md`
- Live acceptance checkpoint: `wiki/outputs/2026-07-17-cc-personal-main-live-acceptance-v6.md`
- Guided-entry closure: `wiki/outputs/2026-07-20-guided-entry-live-closure.md`
- Two-length gate: `wiki/outputs/2026-07-23-post-pr256-two-length-observation-gate.md`
- Authority boundary: `wiki/tech/core-interface-boundary.md`

## Guardrails
- This page is a cache, not canonical truth.
- Update durable pages first; update this page only to keep near-term retrieval cheap.
- For orchestrator usage, trust code, tests, CI, durable wiki pages, and explicit user direction over generated run evidence.
- Transport/integration PRs must not modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Latest update
- Recorded PR #268 and the PR #259-#268 auth/sandbox chain, plus the current
  local PostgreSQL contract with live Supabase RLS still deferred.
- Routed the current control-plane and data-target split to Railway and
  Supabase, with Scalekit first and Auth0 fallback.
