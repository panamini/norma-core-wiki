---
title: "Overview"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-11
---

# Overview

Norma Core vault is now at the durable layer.
Raw inputs have been ingested into `raw/`, source summaries live in `wiki/sources/`, and canonical durable pages were promoted under `product`, `tech`, `strategy`, `meta`, and `concepts` after PR0 ingest waves.

## Current State
- Norma Core is treated as a deterministic proportional engine with immutable structured inputs.
- Interfaces/adapters are clients of the engine; they must not change geometric rule semantics.
- GitHub PR #212 merged logical PR132, GitHub PR #213 merged logical PR133, and GitHub PR #214 merged PR132 validation hardening.
- PR131 selected the local visual candidate review surface.
- PR132 implemented the local static PNG/candidate review, non-authoritative selection intent, package-private finalizer, and the existing no-network resume path.
- PR132 operator validation proves a deterministic synthetic path through AcceptedGeometry, Core / Structured Analyze, and canonical `result.json`, but not authenticated human review, live provider proof, production data proof, or public readiness.
- PR133 selected private/dev ChatGPT + MCP visual pilot as the single next external track, but runtime, hosting, auth, provider, and public surfaces remain unapproved.
- PR134 is the next implementation contract, but it remains blocked pending exact HIGH-risk contract approval.
- PR6, PR113 / R6D, and PR144 / R22 remain historical checkpoints only.
- The current durable checkpoint is `wiki/outputs/2026-07-11-pr214-validation-hardening-checkpoint.md`.
