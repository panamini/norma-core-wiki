---
title: "Hot Cache"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-28
---

# Hot Cache

Active memory cache for agents. Keep this page under 500 words.

## Current focus

- Norma Core `origin/main` is
  `de1c11efc42bd409ecde19550061186d90ab5df6`. PR #281–#282 added the
  optional authenticated SAM 3 Modal sandbox boundary; PR #283–#287 repaired
  ChatGPT widget resource metadata, cache/MIME compatibility, stale aliases,
  and app-only remount behavior.
- SAM 3 is candidate perception only. In the implemented sandbox contract,
  Railway is the control plane and the Modal adapter is configured for one
  bounded L4 inference; deterministic code converts a returned mask to editable
  geometry, and explicit human confirmation remains mandatory before Core.
  Current Modal deployment and live inference remain unverified. The widget
  exposes interactive point/box prompts; the provider contract also supports
  bounded text prompts, but no semantic target field is exposed yet.
- Fresh 2026-07-28 ChatGPT evidence showed an editable widget with rectangles,
  ellipse, axis, and segments after the resource fixes. No SAM receipt, mask,
  provider timing, or cost was captured, so live SAM quality/latency remains
  unproven.
- P0 is the observed absence of an expected checked axis from the optional
  two-length selector. P1 is one bounded semantic SAM target field or target
  chips. P2 is clearer manual-segment and A/B comparison affordance. Manual
  rectangles, harmonic grids, surface highlights, and new ratio families stay
  deferred.
- Historical security sandbox qualification remains `9/9 PASS`; production
  readiness remains separate and closed. Changes limited to packs, performance,
  or UI use narrow affected tests unless auth/OAuth/JWT, PostgreSQL/RLS,
  Railway runtime, or provider registration changes.

## Retrieval map

- Overview: `wiki/overview.md`
- Index: `wiki/index.md`
- Log: `wiki/log.md`
- Roadmap: `wiki/strategy/mvp-pr-roadmap.md`
- Quick start: `wiki/howto/personal-visual-harmony-quick-start.md`
- SAM 3 pipeline: `wiki/tech/sam3-modal-perception-pipeline.md`
- Latest widget checkpoint:
  `wiki/outputs/2026-07-28-sam3-modal-widget-checkpoint.md`
- Authority boundary: `wiki/tech/core-interface-boundary.md`
- Security checkpoint:
  `wiki/outputs/2026-07-25-scalekit-supabase-sandbox-qualification-checkpoint.md`

## Guardrails

- This page is a cache, not canonical truth; trust current code/tests and
  durable pages first.
- SAM masks and automatic proposals never become source truth or Core authority.
- Never store provider tokens, signed URLs, raw prompts, images, or response
  bodies in Git, the wiki, tickets, or logs.
- Transport/integration PRs must not modify Core geometry, evaluation, ratios,
  packs, or deterministic output rules.
