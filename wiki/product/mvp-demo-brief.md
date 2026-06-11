---
title: "MVP Demo Brief"
category: product
status: current
created: 2026-06-11
updated: 2026-06-11
tags:
  - mvp
  - demo
  - evaluation
sources:
  - wiki/sources/2026-06-11-source-04.md
  - raw/Chapitre 13 — MVP demo brief de Norma Core.md
  - wiki/sources/2026-06-11-source-11.md
---

# MVP Demo Brief

Product-level objective for the first executable demonstration of Norma Core.

## Current state

The MVP demo must prove that Norma applies a versioned proportional system to structured geometry and can measure, evaluate, compare, and explain outcomes deterministically.

## Details

### Core claim

The demo demonstrates:

- structured input acceptance
- packed ratio resolution (`norma.basic-proportions@0.1.0` baseline)
- construction generation
- measurements for two candidate compositions
- evaluation A/B with explicit profile
- comparison and decision
- explanation traceability
- structured artifacts and simple visual artifact
- Run / PackLock / replay metadata visibility

### What the demo does not prove

- image parsing, camera flow, vision/tracking
- plugin or CAD integration
- complete UI/editor workflows
- beauty or intention inference
- auto selection of “creativity” outcomes

### Recommended inputs

- one structured rectangle-like surface
- one ratio pack + `PackLock`
- one rule set (`surface-basic-third-grid`)
- two structured compositions (A near target, B contrast case)
- explicit tolerance and comparison policy
- operation context and structured requested outputs

### Acceptance highlights

- deterministic outputs
- explicit `PackLock` failure modes
- structured warnings and errors
- replay-ready envelope available
- artifact generation does not alter computation

## Sources

- `raw/Chapitre 13 — MVP demo brief de Norma Core.md`
- `wiki/sources/2026-06-11-source-04.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/tech/core-interface-boundary.md`
