---
title: "Harmonic Ratio Bible"
category: concept
status: current
created: 2026-06-11
updated: 2026-06-30
tags:
  - ratio governance
  - harmonic rules
  - core-principles
sources:
  - wiki/sources/2026-06-11-source-01.md
  - raw/# Bible des ratios et règles harmoniques — Norma.md
  - wiki/sources/2026-06-11-source-08.md
  - wiki/outputs/2026-06-30-post-r28-ratio-pack-family-catalog-checkpoint.md
---

# Harmonic Ratio Bible

Source-first catalog of how Norma must classify ratios, constants, and geometric rules.

## Current state

The ratio set is organized as discovery knowledge first, then candidate engineering knowledge.
This page summarizes the strict boundaries and tagging model used by the team today.

Current authored fixture families in Norma Core are harmonic triads and root-two
harmonics. They are authored fixture examples only, not runtime registry entries.

## Details

### 1) Scope of this knowledge

The document defines three dimensions that must remain separate:

- format scope (ex: largeur/hauteur)
- surface scope (ex: ratios A:B:C)
- positional/symbolic scope (points, intersections, angles, snapping, scoring, observed constants)

A ratio can appear in several dimensions, but a value is never assumed to mean the same thing across dimensions.

### 2) Governance taxonomy

Each ratio or rule must be tagged with:

- `coded_currently` (already in the current app)
- `observed_external` (found in captures/analysis)
- `candidate_to_add` (future candidate)
- `derived_known` (derivable from a known formula)
- `ambiguous` (multiple plausible readings)
- `speculative` (weak/uncertain match)
- `do_not_use_yet` (must not enter runtime)

Confidence levels must remain explicit:

- exact / strong / approximate / speculative / unknown

Decision rule: when uncertain, mark as `ambiguous` or `speculative` only.

### 3) Core rule set categories

The bible separates at least:

- formats
- surface families
- positions
- angles
- intersection logic
- construction families
- snapping
- scoring logic
- externally observed constants
- numerical collisions

### 4) Hard constraints

- Do not mix format ratios with surface ratios.
- Do not convert observations into engine truth.
- Preserve `_r` / `_d` suffix meaning.
- Keep numeric collisions explicit (e.g., near-equal constants).
- Do not force speculative matches into engine constraints.
- Do not apply ratios directly to product behavior without validation flow.
- Do not treat authored fixture families as runtime registry entries.
- Do not choose, infer, rank, recommend, optimize, score, correct, or
  auto-select ratio families in Norma Core.

### 5) Current authored fixture examples

As of PR #150 / R28, Norma Core documents these authored fixture examples:

- `norma.harmonic-triads@0.1.0` in
  `tests/fixtures/ratio-packs/norma-harmonic-triads-0.1.0.json`, representing
  harmonic triads with rule set `surface-harmonic-triads`.
- `norma.root-two-harmonics@0.1.0` in
  `tests/fixtures/ratio-packs/norma-root-two-harmonics-0.1.0.json`,
  representing root-two harmonics with rule set `surface-root-two-section`.

These examples are supplied by explicit structured input. They do not authorize
runtime discovery, registry lookup, scoring, correction, recommendation,
optimization, inference, beauty scoring, or automatic family selection.

## Sources

- `raw/# Bible des ratios et règles harmoniques — Norma.md` (immutable copy)
- `wiki/sources/2026-06-11-source-01.md`
- `wiki/outputs/2026-06-30-post-r28-ratio-pack-family-catalog-checkpoint.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/tech/core-interface-boundary.md`
- `wiki/strategy/mvp-pr-roadmap.md`
