---
title: "Overview"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-01
---

# Overview

Norma Core vault is now at the durable layer.
Raw inputs have been ingested into `raw/`, source summaries live in `wiki/sources/`, and canonical durable pages were promoted under `product`, `tech`, `strategy`, `meta`, and `concepts` after PR0 ingest waves.

## Current State
- Norma Core is treated as a deterministic proportional engine with immutable structured inputs.
- Interfaces/adapters are clients of the engine; they must not change geometric rule semantics.
- MVP is gated to V1 deterministic composition evaluation.
- The historical MVP sequence remains reference context only; current roadmap
  execution is gate-based and track-based, with one isolated PR selected from
  real current gaps.
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
- PR #149 / R27 completed family ratio-pack meaning and local report visibility
  smoke coverage.
- PR #150 / R28 completed the documentation-only ratio-pack family catalog
  boundary.
- PR #151 / R29 added runnable local Structured Analyze examples and
  deterministic report smoke coverage for the authored ratio-pack families.
- PR #152 / R30 added the local Structured Analyze demo workflow smoke.
- PR #153 / R31 added the real-usecase Structured Analyze layout demo.
- PR #154 / R32 synced the in-repo roadmap after R31.
- PR #155 / R32 added the real-usecase local inspection demo smoke.
- PR #156 / R33 consolidated local truth projection smoke coverage.
- PR #157 / R34 added the local real-usecase demo command.
- PR #158 / R35 hardened the local real-usecase demo command.
- PR #159 / R36 froze the local CLI report boundary.
- PR #160 / PR81 added the package-private accepted geometry to Core mapper.
- PR #161 fixed PR81 mapper review findings.
- PR #162 / PR82 proved the synthetic accepted geometry to Structured Analyze
  bridge.
- The current authored fixture examples are `norma.harmonic-triads@0.1.0` and
  `norma.root-two-harmonics@0.1.0`.
- Runnable local examples now exist under
  `examples/structured-analyze/families/` for both authored families.
- The local demo workflow stitches an existing family example input, the
  existing local report entrypoint, an output directory, `result.json` as
  canonical truth, and optional derived inspection artifacts.
- The accepted-geometry mapper is package-private. PR82 proves deterministic
  synthetic bridge reachability only; unsupported primitives stop at the mapper,
  and no provider, image, OpenAI, ChatGPT, CLI, MCP, UI, package, dependency, or
  public export scope is approved.
- The family catalog is not a runtime registry, not a package export, and not
  selection logic; authored fixtures enter execution only through explicit
  structured input.
- Current roadmap model is gate-based: no speculative PR27-PR46 execution queue, one isolated PR per real gap, with package/public/exposure/product layers blocked until explicit approval.
