---
title: "MVP PR Roadmap"
category: strategy
status: current
created: 2026-06-11
updated: 2026-06-30
tags:
  - execution
  - roadmap
  - delivery
sources:
  - wiki/sources/2026-06-11-source-05.md
  - wiki/sources/2026-06-11-source-06.md
  - wiki/sources/2026-06-11-source-07.md
  - wiki/sources/2026-06-13-norma-core-business-readiness-roadmap.md
  - wiki/sources/2026-06-13-pr-agent.md
  - raw/Chapitre 15 — Plan PR, plan développeur de Norma Core.md
  - raw/PR 0.md
  - wiki/sources/2026-06-11-source-09.md
  - wiki/sources/2026-06-11-source-10.md
  - wiki/sources/2026-06-11-source-11.md
  - raw/Norma — Vision produit, UX cible et architecture d’intégration.md
  - wiki/sources/2026-06-19-norma-product-vision-ux-flows-and-integration-architecture-prompt.md
  - wiki/sources/2026-06-23-norma-core-pr-execution-map-v1.md
  - wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md
  - wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md
  - wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md
  - wiki/outputs/2026-06-30-post-r25-roadmap-compression-checkpoint.md
  - wiki/outputs/2026-06-30-post-r28-ratio-pack-family-catalog-checkpoint.md
---

# MVP PR Roadmap

Execution plan to keep implementation focused and avoid MVP drift.

## Current state

Norma Core is current through PR #150 / R28.

The recent Structured Analyze protection and inspection rail is complete:

- R10 protected deterministic pipeline behavior.
- R11 froze public API and package export contracts.
- R12 locked the MCP protocol contract and execution boundary.
- R13 locked ratio-pack authoring, registry, and strict pass-through behavior.
- R14 upgraded local `report.html` into a static read-only Structured Analyze inspection dashboard.
- R16, R18, R19, R20, R21, and R22 continued the local/private Structured Analyze inspection path.
- R22 added local-only, static, read-only inspection for existing Structured Analyze result JSON and completed `norma.analyzeStructuredCompositionV1` MCP responses.
- R23 added local inspection surface onboarding fixture and workflow polish.
- R24 added the Structured Analyze scenario regression harness.
- R25 added the local inspection surface static safety guard.
- R26 merged as docs/test-only roadmap truth sync and does not change runtime behavior.
- R27 is complete and added family ratio-pack meaning plus local report
  visibility smoke coverage.
- R28 is complete and added the ratio-pack family catalog boundary.

Current execution stays local, private, and manual. `result.json` remains
canonical Norma truth; report and viewer artifacts are derived inspection
surfaces only.

The current ratio-pack family catalog boundary is documentation-only. It is not
a runtime registry, not a package export, and not selection logic. The catalog
documents authored fixture examples that are supplied by explicit structured
input.

The active roadmap model is now gate-based and track-based, not a speculative
PR-number ladder.
Future PRs must be selected one at a time from real gaps. R labels may still be
used as local PR names, but old PR27-PR46 sequencing remains historical/gated
context, not the active queue. Next core work should be chosen from real current
gaps, not old numbering.

Do not start hosted MCP, public app submission, public package publishing,
remote API runtime, image/vision/CAD/camera/provider work, or recommendation /
optimization / beauty-scoring behavior before a later explicit checkpoint
approves that scope.

## Details

### Fundamental PR rules

- PR0 is docs-only and establishes non-negotiable guardrails.
- PRs are small and tightly scoped.
- No UI, camera, image/vision, plugin, CAD, or marketplace scope in MVP core PRs.
- No scoring before measurements exist.
- No artifacts before source objects and provenance exist.
- Replay concepts introduced explicitly; full replay-run execution may lag V1 if needed.
- PR is complete only when scope and acceptance checks pass.

### Roadmap phase rules

- Core is delivered before any interface/adaptor surface.
- Structured objects are authored before rendering artifacts.
- Minimal pack comes before any rich pack.
- Rule declarations drive construction.
- Constructions are measured before scoring.
- Evaluation and comparison happen only after measurements in the same context.
- Artifacts are always derived from source objects.
- Warnings/errors are emitted from the start.

### Sequence (normative)

1. PR0 — Spec freeze and project guardrails
2. PR1 — Core skeleton
3. PR2 — Operation contracts and canonical variables
4. PR3 — Geometry model V1
5. PR4 — Minimal ratio pack model
6. PR5 — Rule declarations and resolution
7. PR6 — Construction generation
8. PR7 — Measurements
9. PR8 — Evaluation profile and minimal scoring
10. PR9 — Comparison and decision
11. PR10 — Artifacts
12. PR11 — Run, PackLock, OperationContext
13. PR12 — MVP demo harness

### Alternate phase reference (from chapter 14)

1. Spec freeze MVP
2. Operation contracts and canonical variables
3. Minimal geometry model
4. Minimal ratio pack
5. Rules and construction
6. Measurements
7. Evaluation/scoring minimal and comparison
8. Structured artifacts + visual artifact
9. Run / PackLock / OperationContext + replay-readiness
10. Minimal demo harness

### PR0 governance output (from prior plan)

- `SPEC_FREEZE.md` equivalent content
- `MVP_GUARDRAILS.md` equivalent content
- PR review checklist
- concise glossary of core objects

### Risk controls

- keep source-of-truth split: runtime code only in core PRs
- preserve provenance from PR1/PR2 onward
- delay feature surfaces (SDK/API/MCP, plugins, full visual products) until after core delivery

### Deterministic dependency map

- Treat PR execution as a dependency graph, not a parallel task list.
- Required order for the early execution map:
  1. PR0 — spec freeze lock
  2. PR1 — toolchain and CI baseline
  3. PR2 — geometry identity correctness
  4. PR3 — local MVP proof kit
  5. PR4 — MCP STDIO safety
  6. PR5 — MCP tool exposure
  7. PR6 — optional ChatGPT MCP integration
- PR2 depends on PR1 passing CI.
- PR3 depends on PR2 correctness stability.
- PR4 depends on a working PR3 demo baseline.
- PR5 depends on PR4 safe MCP transport.
- PR6 depends on PR5 tool stability.

### Layer gates

- PR1 gate: green build, green checks, no npm dependency, reproducible CI.
- PR2 gate: duplicate IDs rejected, valid compositions unchanged, measurement determinism preserved, no core behavior drift.
- PR3 gate: `pnpm demo:mvp` works, `result.json` exists, `report.html` is generated, outputs are deterministic, and no framework is added.
- PR4 gate: MCP malformed input cannot crash the process, depth protection works, byte limits are enforced, errors are idempotent, and `tools/list` is blocked or controlled.
- PR5 gate: `norma.runMvpDemoV1` is exposed, MCP output matches CLI output, core logic is not duplicated, and the tool is read-only.
- PR6 gate: ChatGPT can call the MCP tool through a secure tunnel and outputs remain identical to CLI/MCP, with no new compute logic.

### Post-PR6 checkpoint

- PR6 ChatGPT Secure MCP Tunnel smoke passed for `norma.runMvpDemoV1`.
- Merge commit: `658ea2069d1c6a65b23df7f43ba4c4ba96fd8a31`.
- Base branch: `main-after-codex-mcp-tool`.
- The app stayed private/dev, and the tunnel was stopped after testing.
- Observed output preserved deterministic proof facts: `measurementCounts` `{ "a": 6, "b": 6 }`, `decision.status` `a_closer`, selected composition `composition:A`, and `replayReadiness.status` `replay_ready`.
- Do not treat publishing or public submission as the default next step; use a small post-PR6 handoff/checkpoint or explicitly scoped internal follow-up.

### R6D current-main ChatGPT checkpoint

- PR113 / R6D merged at `bba597bca40facaf36fd7741712a0b0b9d8754e6`.
- Current-main private ChatGPT connector smoke passed after the `_meta`
  compatibility patch.
- The connector exposed exactly the six current tools and positive
  `norma.replayMvpDemo` returned replay-ready output with selected evaluation
  `evaluation:A:basic-grid-alignment`.
- Negative prompts for image/prose geometry inference, beauty/recommendation,
  and prose-only geometry inference were rejected without a Norma analysis tool
  call.
- This is private/developer checkpoint evidence only; it does not authorize
  public app submission, hosted MCP, ChatGPT Analyze expansion, outputSchema
  follow-up work, or any core geometry behavior change.
- Historical next step after this checkpoint was R1 duplicate geometry source
  identities. R1 and the later R7/R18/R19/R20/R21/R22 rail have since landed;
  do not treat this R6D note as the current next instruction.

### Post-R14 checkpoint

- PR #135 / R14 merged at
  `dcb113cb2abfcafbf1155b47a2a7c41d2fd50974`.
- Head merged: `b3e4349edabbb438c70087a80f662a8255762278`.
- Local Structured Analyze `report.html` is now a static read-only inspection
  dashboard.
- `result.json` remains canonical Norma truth.
- The current operating model remains local, private, and manual.
- No hosted MCP, public app submission, package publication, package export
  expansion, remote API runtime, image/vision/CAD/camera/provider runtime, or
  recommendation/optimization/beauty-scoring behavior is approved.
- Next implementation rail: R16 local demo/onboarding smoke for the Structured
  Analyze report workflow.

### R22 local Structured Analyze inspection checkpoint

- PR #144 / R22 merged at `b80a53d3d13863abd4dca4f944dcdc74aab6eaa3`.
- Checkpoint: `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`.
- The local static read-only viewer can inspect existing Structured Analyze
  result JSON and completed `norma.analyzeStructuredCompositionV1` MCP
  responses.
- Direct engine output and `result.json` remain canonical truth; viewer output
  is derived inspection only.
- The viewer preserves measurements, evaluations, diagnostics, warnings,
  errors, refs, provenance, replay readiness, comparison, decision,
  serialization details, and inert unknown fields.
- Pasted unrelated large JSON still uses the existing body-size rejection before
  parsing. Structured Analyze fallback remains marker-gated and bounded by
  structural depth, array, and string limits.
- R22 does not authorize hosted dashboard, public webapp, SDK, API runtime,
  public npm publication, hosted or remote MCP, image/vision/CAD/provider input,
  correction, recommendation, optimization, scoring, prompt inference, or source
  truth creation.

### Post-R25 compressed execution gates

The PR27-PR46 readiness ladder is historical/gated context, not the current
execution queue.

Current gate:

- The roadmap truth-sync gate is complete through PR #150 / R28. Choose the next
  PR as one isolated change from a current gap, not from a speculative numbered
  queue.

Allowed ongoing tracks after R26:

- regression and safety work for real invariant gaps or bug fixes;
- one evolving deterministic scenario suite;
- light local inspection UX polish that remains static, read-only, and derived.

Blocked by default:

- package publication;
- hosted or remote MCP;
- remote API runtime;
- public web/product surface;
- public ChatGPT app submission;
- image, vision, CAD, camera, plugin, provider, file-path, URL, or media input;
- recommendation, optimization, correction, beauty scoring, prompt inference,
  or source-truth creation.

### Post-R28 ratio-pack family catalog checkpoint

- PR #149 / R27 merged at `2228c0b2756464f02abb9a8c92b95011f63cc23b`.
- PR #150 / R28 merged at `3236fc5733a670689639d1cea8b92cc37643ae76`.
- R27 is complete.
- R28 is complete.
- Current authored fixture families:
  - `norma.harmonic-triads@0.1.0` in
    `tests/fixtures/ratio-packs/norma-harmonic-triads-0.1.0.json`, with rule
    set `surface-harmonic-triads`.
  - `norma.root-two-harmonics@0.1.0` in
    `tests/fixtures/ratio-packs/norma-root-two-harmonics-0.1.0.json`, with
    rule set `surface-root-two-section`.
- The catalog is documentation-only: not a runtime registry, not a package
  export, not runtime selection, and not engine/MCP/CLI/viewer behavior change.
- The executable boundary remains explicit structured input plus engine
  validation of that input.
- The current gate can select explicit runnable family examples or a demo
  workflow in Norma Core, but only as a separate PR selected from the current
  gap set.

### No-parallelism rule for transport work

- Transport and integration work must not run in parallel with core or
  source-truth changes.
- Hosted/remote MCP must wait for explicit threat-model and deployment approval.
- If a PR touches more than one of `CORE`, `TRANSPORT`, or `INTEGRATION`, treat
  it as invalid design until split.

### Local viewer endgame prompt

- A later continuation prompt adds a PR66–PR70 local viewer path focused on implementation after the approval stages.
- The sequence covers local viewer UI approval, a read-only viewer model, a static viewer, real fixtures, and final demo readiness.
- Treat that prompt as a planning artifact for retrieval and scoping, not as a replacement for the canonical roadmap.

### PR71 vision and UX freeze

- The new product vision prompt is a documentation-only planning artifact for PR71.
- PR71 should capture product vision, UX flows, integration architecture, and the post-MVP adapter family without broadening MVP core scope.
- Keep it separate from implementation sequencing so the roadmap stays anchored
  on the current gate-based execution model.

## Sources

- `raw/Chapitre 15 — Plan PR, plan développeur de Norma Core.md`
- `raw/PR 0.md`
- `wiki/sources/2026-06-11-source-05.md`
- `wiki/sources/2026-06-11-source-06.md`
- `wiki/sources/2026-06-11-source-07.md`
- `wiki/sources/2026-06-17-norma-core-endgame-plan.md`
- `raw/Norma — Vision produit, UX cible et architecture d’intégration.md`
- `wiki/sources/2026-06-19-norma-product-vision-ux-flows-and-integration-architecture-prompt.md`
- `wiki/sources/2026-06-23-norma-core-pr-execution-map-v1.md`
- `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`
- `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
- `wiki/outputs/2026-06-30-post-r28-ratio-pack-family-catalog-checkpoint.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/product/mvp-demo-brief.md`
- `wiki/meta/pr0-governance-checklist.md`
- `wiki/product/norma-product-vision.md`
