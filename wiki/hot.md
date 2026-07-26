---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-26
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current Focus
- Latest merged Norma Core state is PR #274 at `f84a71cb9e1d592eeadbc749cdb1f48e796d556b`; PR #274 closed the immediate-revocation review gaps, while PR #258 remains the provider-neutral RLS boundary and Scalekit-first MCP sandbox contract.
- The private stable runtime, guided entry, manual-primitive workflow, and Personal Visual Acceptance Pack remain live-accepted. The pack produced acceptable preparations for `6/6` cases and bounded confirmation/Core success for `5/6`; the remaining failure was a ChatGPT surface block, not a reproduced Core defect.
- Verdict remains `observation-partial`: declared geometric comparisons are useful in the private flow, but artistic usefulness, latency p50/p95, mobile proof, sustained use, and commercial/public readiness remain unproven. The Railway/Supabase gate is `SHORTLISTED_PENDING_SANDBOX`: Scalekit first sandbox, Auth0 fallback, WorkOS conditional, and provider-neutral Railway → Supabase/RLS boundary; no production provider, migration, or resource creation.
- Sandbox checkpoint 2026-07-26: Railway deployment `8fa03f94` serves exact merged `main@f84a71c`; Railway/Supabase TLS and RLS isolation, native OAuth/PKCE MCP transport, and immediate same-token revocation are PASS. The exact merged path reproduced `200 → 401 → 200` around a durable HMAC cutoff with verified database cleanup and no persisted token material. One preliminary Inspector DCR client still needs admin-session cleanup verification. Production readiness remains `CLOSED` until that cleanup, the remaining consent/refresh evidence, and complete matrix review.
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
- Recorded PR #256, the three fresh two-length gates, the exact-main stable-runtime
  promotion, and the bounded observation-partial verdict.
- PR258 merged the RLS boundary and Scalekit-first MCP sandbox qualification
  contract; the next dependency is the isolated Scalekit sandbox, with Auth0 as
  fallback. Automatic benchmark, provider production lock, GPU, and geometric
  expansion remain deferred.
- Immediate revocation is merged and live-proven; finish consent/refresh
  evidence and the complete matrix before any production-readiness decision.
