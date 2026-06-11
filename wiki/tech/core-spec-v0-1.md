---
title: "Norma Core Spec v0.1"
category: tech
status: current
created: 2026-06-11
updated: 2026-06-11
tags:
  - spec
  - mvp
  - replay-readiness
sources:
  - wiki/sources/2026-06-11-source-03.md
  - raw/Chapitre 12 Norma Core Global Spec v0.1.md
---

# Norma Core Spec v0.1

Canonical statement of what Norma Core V1 includes and excludes.

## Current state

Norma Core is a deterministic geometric engine over structured inputs, with explicit contracts for packs, rules, measurements, evaluation, decisions, and replay-ready provenance.

## Details

### Core definition

Core applies versioned proportional systems to structured geometric spaces to produce:

- constructions
- guides, zones, grids, diagonals, intersections
- measurements
- evaluations
- decisions
- explanations
- artifacts with provenance

The chain is:

`structured input → ratio pack → rule resolution → construction → measurement → evaluation → decision → explanation → artifacts → run/replay envelope`

### V1 scope (explicit)

- segment 1D + axis-aligned rectangular 2D spaces
- simple 2D compositions
- ratio packs / rule declarations / rule sets
- deterministic construction
- measurement and component-level evaluation
- comparison, decision, explanation
- structured artifacts (including simple visual artifact)
- `Run`, `PackLock`, `OperationContext` concepts
- explicit warnings/errors, idempotence, replay-readiness

### V1 exclusions

- camera / image / vision / tracking
- full UI, plugin ecosystems, API surface, SDK delivery
- CAD-native engine behavior
- cloud orchestration
- beauty or intent scoring

### Ownership contracts

- Core owns geometry, operations, measurements, evaluation semantics, and object contracts.
- Packs own ratio declarations and metadata only.
- Interfaces/adapters own calling format, presentation, transport, and environment integration.
- Artifacts are derived projections and cannot become the source of truth.

### Execution object summary

- Construction objects
- Measurement objects
- Evaluation objects
- Artifact objects
- Run metadata objects (`PackLock`, `OperationContext`, status/warnings)

### Guarded anti-patterns

- No hidden state in operation runtime.
- No silent defaults that modify rule outcomes.
- No implicit conversion from external visuals into core truth.
- No derived object without provenance chain to source input.

## Sources

- `raw/Chapitre 12 Norma Core Global Spec v0.1.md`
- `wiki/sources/2026-06-11-source-03.md`

## Related

- `wiki/tech/core-interface-boundary.md`
- `wiki/product/mvp-demo-brief.md`
- `wiki/strategy/mvp-pr-roadmap.md`
