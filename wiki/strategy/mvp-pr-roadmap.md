---
title: "MVP PR Roadmap"
category: strategy
status: current
created: 2026-06-11
updated: 2026-06-11
tags:
  - execution
  - roadmap
  - delivery
sources:
  - wiki/sources/2026-06-11-source-05.md
  - wiki/sources/2026-06-11-source-06.md
  - wiki/sources/2026-06-11-source-07.md
  - raw/Chapitre 15 — Plan PR, plan développeur de Norma Core.md
  - raw/PR 0.md
---

# MVP PR Roadmap

Execution plan to keep implementation in sequence and avoid MVP drift.

## Current state

The roadmap is now split into strict phases that separate architecture lock, core build, and ecosystem growth.

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

## Sources

- `raw/Chapitre 15 — Plan PR, plan développeur de Norma Core.md`
- `raw/PR 0.md`
- `wiki/sources/2026-06-11-source-05.md`
- `wiki/sources/2026-06-11-source-06.md`
- `wiki/sources/2026-06-11-source-07.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/product/mvp-demo-brief.md`
- `wiki/meta/pr0-governance-checklist.md`
