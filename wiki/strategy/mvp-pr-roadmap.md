---
title: "MVP PR Roadmap"
category: strategy
status: current
created: 2026-06-11
updated: 2026-07-17
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
---

# MVP PR Roadmap

Execution plan to keep implementation in sequence and avoid MVP drift.

## Current state

The roadmap is now split into strict phases that separate architecture lock, core build, and ecosystem growth.
It is extended from post-PR25 planning with an explicit PR27–PR46 sequence and explicit gating before broadening scope.

## Différé / nice-to-have après stabilisation de Norma

Ces éléments restent différés et ne bloquent pas le MVP stable.
Ils ne doivent être repris qu'après réussite de la matrice d'acceptation live.

- Les rythmes et répétitions restent d'abord des mesures, puis une interprétation humaine.
- La perspective physique, la rectification et l'homographie relèvent d'un contrat séparé, avec hypothèses et provenance explicites.
- Les nouveaux centres triangulaires `circoncentre`, `incentre` et `orthocentre` ne passent que via des contrats bornés et des preuves; aucune inférence automatique.
- Les triangles automatiques non explicitement défendables restent différés.
- Les nouveaux rapports harmoniques restent après le gate live tenu à l'écart.
- La prochaine lecture doit conserver le vocabulaire et le schéma existants, sans diluer la séparation entre preuve offline, preuve runtime et preuve live.

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
- Historical next step after R6D: R1 duplicate geometry source identities.
  R1 and the later R7/R18/R19/R20/R21/R22 rail have since landed; do not treat
  this R6D note as the current next instruction.

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

### Current recommended next PR after R22

```text
R23: local inspection surface onboarding fixture and workflow polish
```

R23 should remain local-only, static, read-only, documentation/test backed, and
focused on helping a local user inspect existing Structured Analyze result JSON
or completed MCP output with the static viewer.

R23 should not change engine behavior, package exports, package metadata,
lockfiles, CLI runtime, MCP runtime, report-kit runtime, SDK behavior, API
runtime, hosted/remote behavior, public package readiness, public app
submission, source-truth creation, prompt inference, image/vision/CAD/provider
input, correction, recommendation, optimization, scoring, or beauty judgment.

### No-parallelism rule for transport work

- PR4 must merge before PR5 exposes the tool.
- PR5 must stabilize before PR6 integrates an external system.
- Do not run PR5 and PR6 in parallel.
- If a PR touches more than one of `CORE`, `TRANSPORT`, or `INTEGRATION`, treat it as invalid design until split.

### Readiness extension (post-PR25)

- Current execution plan is now post-PR25 and proceeds through PR27–PR46 with explicit gates:
  - PR27–PR29: local CLI and release checkpoint
  - PR30–PR32: package readiness and publish governance
  - PR33–PR35: MCP contract and local MCP implementation
  - PR36–PR39: threat model and API contract
  - PR40–PR43: user-facing product requirements and read-only viewer
- PR44–PR46: onboarding, beta readiness, and launch checks
- PR0 governance and core sequencing remain the hard baseline for all expansion.

### Local viewer endgame prompt

- A later continuation prompt adds a PR66–PR70 local viewer path focused on implementation after the approval stages.
- The sequence covers local viewer UI approval, a read-only viewer model, a static viewer, real fixtures, and final demo readiness.
- Treat that prompt as a planning artifact for retrieval and scoping, not as a replacement for the canonical roadmap.

### PR71 vision and UX freeze

- The new product vision prompt is a documentation-only planning artifact for PR71.
- PR71 should capture product vision, UX flows, integration architecture, and the post-MVP adapter family without broadening MVP core scope.
- Keep it separate from implementation sequencing so the roadmap stays anchored on the current PR27–PR46 execution plan.

### Next canonical live gate

`PERSONAL-HELDOUT-LIVE-ACCEPTANCE-MATRIX-v1`

- Small held-out corpus: 3-4 images that were not used to design the last fixes.
- Coverage: ellipse + large oblique + trapezoid/quadrilateral; poster/chevron refinement; architecture/design quadrilaterals; one ambiguous negative that must abstain.
- Measure: missing/superfluous candidates, pixel error before and after refinement, human correction/adoption, abstention, hydration/confirmation/Core reliability, and relation accuracy.
- Limit: one preparation and one confirmation/Core maximum per image.
- Default: no code changes unless a bug is reproduced.
- This gate replaces any other immediate triangle-center changeset.
- After PASS, the next assessment may consider a bounded family of user-declared measurements on confirmed geometries.

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

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/product/mvp-demo-brief.md`
- `wiki/meta/pr0-governance-checklist.md`
- `wiki/product/norma-product-vision.md`
