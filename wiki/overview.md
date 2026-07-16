---
title: "Overview"
category: overview
status: current
created: 2026-06-11
updated: 2026-07-16
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
- PR #163 / PR83 synced the in-repo roadmap after PR82.
- PR #164 / PR84 hardened accepted-geometry integration determinism.
- PR #165 / PR85 added the package-private shared-unit-surface normalizer.
- PR #166 / PR86 preserved metric policy through the normalizer and closed the
  accepted-geometry bridge rail.
- PR #168 / PR88 approved gated integration unlock contracts.
- PR #169 / PR89 added the local guided inspection demo surface.
- PR #170 / PR90 defined the guided inspection package/API readiness gate.
- PR #171 / PR91 added the package-private guided inspection artifact contract
  helper.
- PR #172 / PR92 wired the guided inspection demo through that helper.
- PR #173 / PR93 synced the code roadmap after PR92 and named PR94 as the next
  local guided inspection consumer proof.
- PR #174 / PR94 added the package-private guided inspection consumer proof.
- PR #175 / PR95 approved only the future guided inspection package-root V1 API
  export contract.
- PR #176 / PR96 implemented the approved guided inspection package-root V1 API
  exports.
- PR #177 / PR97 proved local package-root consumer compatibility for the PR96
  guided inspection exports.
- PR #178 / PR98 defined the guided inspection package publication readiness
  gate without publishing, changing package metadata, widening exports, or
  implementing release mechanics.
- PR #179 / PR99 prepared the local `@norma/core` package tarball boundary and
  proved local packed-tarball install/import at merge commit
  `82b125d52e16760e58fb7db6928702269d03bb19`.
- PR #221 merged the private personal ChatGPT visual-harmony foundation at
  `6a061dbb43496b6147f8ad2e35c8c8ffd8375c67`; PR #222 hardened exact-file
  hydration and stale-payload behavior; PR #223 added a deterministic shadow
  pixel-refinement kernel that, at that checkpoint, had no widget caller.
- PR #224 merged the visual-harmony repository truth sync at
  `998bc2fcd8aa81e51bcd08af7d2bd0ec9cbfd2d2` without changing runtime
  behavior.
- PR #225 merged the bounded, disabled-by-default pixel-refinement proposal
  integration at `02c344246f51207fe15dcc96f4b6e0d09c017b30`; original and
  proposed geometry remain separate and require distinct adoption and
  confirmation actions.
- PR #226 merged support-line extensions and format diagonals at
  `f333c9a3ee6e7034b59b03401362a2aec6ffe5ad`; all are opt-in image-plane
  constructions with observed/derived provenance and no Core authority.
- PR #227 merged opt-in junction-angle measurements at
  `25810e39a01a65f9f2453f000d459633376c3419`; they require support-line
  extensions, preserve participant and observed-extent provenance, and remain
  outside Core authority.
- PR #228 merged the explicit opt-in triangle-construction layer at
  `22f4732fb4ce78347040285c956d283da8884eff`; exactly three stable parented
  vertices canonicalize to one derived identity and basic image-plane metrics,
  with invalid, stale, ambiguous, unsupported, or degenerate inputs rejected
  fail-closed and no Core authority.
- PR #229 merged explicit rotated-ellipse support at
  `26cba06d76d8a6eeb56c0dd0035b0be24e47a388`; equivalent rotations and axis
  swaps canonicalize deterministically, legacy axis-aligned meaning and
  identity remain stable, rotated overlays and line relations are supported,
  and the guides remain outside Core authority.
- PR #230 merged the bounded deterministic rotated-ellipse refinement kernel
  at `7eb6179972ea1f472c04256f6dcc90ee1ba6dcea`; it preserves the original,
  searches only a hard-bounded local parameter window, and abstains on weak,
  ambiguous, or orientation-degenerate evidence.
- PR #231 merged the disabled-by-default private-widget integration at
  `9d49d15286d9be854243dc7cb4ca350d10073695`; rotated proposals render
  separately and require explicit adoption before separate confirmation.
- PR #232 merged the controlled local A/B truth sync at
  `c3f04cdf4d7451b0c8818e2c1ddb9ebf46976b08` without runtime behavior change.
- PR #234 merged the opt-in triangle-median construction layer at
  `d53357b7142dd83658a2ceffbf6b2cb50268d5eb`: one explicit canonical triangle
  yields exactly three vertex-to-opposite-side-midpoint segments. Medians retain
  triangle/vertex/side provenance, `sourceTruth=false`, and no Core authority;
  no centroid, bisector, or center is surfaced.
- PR #235 merged the opt-in perpendicular-bisector layer at
  `2f22b7a6363d397acca0d1faadf0b0c2429b08ce`: exactly three deterministic
  side-midpoint perpendicular constructions for that explicit canonical triangle.
  Infinite support lines remain distinct from frame-clipped render segments;
  provenance, `sourceTruth=false`, no Core authority, and off-by-default controls
  are preserved.
- Exact-head evidence passes build, focused rotated-refinement and
  visual-harmony tests (297/297), historical changed-file guards, full suite
  (1672/1672), desktop and mobile local widget smoke, three remote checks,
  empty review threads, and fresh Codex review on exact final head
  `7fcbfa34e34a14d745bc961a573df1da7fb6044e`. The bounded post-merge rail
  passes build and five integration regressions. The controlled same-image
  local A/B is `LOCAL_UI_AB_PASS`: both supported rotated cases reduce mean
  annotated perimeter error from `1.657733384665 px` to `0 px`, while weak and
  competing-orientation cases abstain. PR #232 passes full suite 1673/1673,
  three remote checks, empty threads, and exact-head Codex review. The private
  app can now connect to exact-main and the controlled same-image desktop run is
  `LIVE_CHATGPT_AB_PASS`; the local desktop/mobile widget run is
  `LOCAL_UI_PASS`. Real mobile ChatGPT viewport proof remains unverified. The
  Chrome file-URL permission was observed enabled during the live run and is
  being restored to disabled; the two named temporary DNS aliases currently
  return no authoritative records.
- The current authored fixture examples are `norma.harmonic-triads@0.1.0` and
  `norma.root-two-harmonics@0.1.0`.
- Runnable local examples now exist under
  `examples/structured-analyze/families/` for both authored families.
- The local demo workflow stitches an existing family example input, the
  existing local report entrypoint, an output directory, `result.json` as
  canonical truth, and optional derived inspection artifacts.
- The guided inspection package/API rail is current through PR99. `result.json`
  is still canonical truth; `guide.html`, `report.html`, `visual.svg`,
  `summary.json`, and `summary.md` are derived local inspection artifacts only.
  PR94 proved local/package-private guided inspection consumption. PR95
  approved only the future package-root V1 API export contract. PR96
  implemented the approved package-root V1 exports. PR97 proved local
  package-root consumer compatibility. PR98 defined the publication readiness
  gate. PR99 prepared the local package tarball boundary while keeping
  `private: true`, version `0.1.0`, and the package metadata implementation
  limited to `dist/src/**/*.d.ts`, `dist/src/**/*.js`, and `README.md`.
  PR99 still did not approve package publication, tags, releases, npm auth,
  provenance, release workflows, dependency or lockfile changes, package-level
  `bin`, hosted MCP, ChatGPT connector runtime, provider calls, adapters, or
  runtime behavior.
- The accepted-geometry mapper and PR85/PR86 normalizer path are
  package-private. PR82 proves deterministic synthetic bridge reachability only;
  PR84 hardens determinism coverage; PR85 adds the package-private normalizer;
  PR86 preserves metric policy through that normalizer. No provider, image,
  OpenAI, ChatGPT, CLI, MCP, UI, package, dependency, or public export scope is
  approved.
- The family catalog is not a runtime registry, not a package export, and not
  selection logic; authored fixtures enter execution only through explicit
  structured input.
- Current roadmap model is gate-based. Rotated-ellipse shadow refinement is
  complete locally through PR #231 with separate original/proposed geometry,
  fail-closed abstention, explicit adoption, and no Core authority. The
  controlled local A/B is non-regressive; the active validation gate is the
  same-image live ChatGPT A/B is now non-regressive, and PR #234 provides the
  derived median-construction slice. Angle/perpendicular bisectors, altitudes,
  centers, rhythm, and harmonic interpretation remain later gates. Package
  publication remains a separate gate.
