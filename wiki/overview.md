---
title: "Overview"
category: overview
status: current
created: 2026-06-11
updated: 2026-06-30
---

# Overview

Norma Core vault is now at the durable layer.
Raw inputs have been ingested into `raw/`, source summaries live in `wiki/sources/`, and canonical durable pages were promoted under `product`, `tech`, `strategy`, `meta`, and `concepts` after PR0 ingest waves.

## Current State
- Norma Core is treated as a deterministic proportional engine with immutable structured inputs.
- Interfaces/adapters are clients of the engine; they must not change geometric rule semantics.
- MVP is gated to V1 deterministic composition evaluation.
- PR roadmap remains sequence-based: spec freeze → core skeleton → contracts → geometry → pack/rules → construction → measurements → evaluation/comparison → artifacts → replay envelope → demo harness.
- A later continuation prompt now exists for the PR66–PR70 local viewer path, but it is still only a planning artifact.
- A new planned product-vision page captures the ChatGPT, Camera, CAD, and renderer adapter family plus the hybrid perception split.
- PR6 proved private/dev ChatGPT Secure MCP Tunnel invocation through `norma.runMvpDemoV1`; the app was not published, the tunnel was stopped after testing, and deterministic output facts were preserved in a checkpoint output.
- PR113 / R6D proved current-main private ChatGPT connector compatibility for the six-tool MCP inventory after the `_meta` patch; that R6D-to-R1 sequencing is now historical.
- PR #135 / R14 completed the local static report dashboard checkpoint for Structured Analyze report inspection.
- PR #144 / R22 merged the local-only, static, read-only Structured Analyze inspection surface for existing result JSON and completed `norma.analyzeStructuredCompositionV1` MCP responses.
- PR #145 / R23 added local inspection surface onboarding fixture and workflow polish.
- PR #146 / R24 added the Structured Analyze scenario regression harness.
- PR #147 / R25 added the local inspection surface static safety guard.
- PR #148 / R26 merged the post-R25 roadmap truth sync.
- Current roadmap model is gate-based: no speculative PR27-PR46 execution queue, one isolated PR per real gap, with package/public/exposure/product layers blocked until explicit approval.
