---
title: "Harmonic Ratio Bible"
category: concept
status: current
created: 2026-06-11
updated: 2026-06-11
tags:
  - ratio governance
  - harmonic rules
  - core-principles
sources:
  - wiki/sources/2026-06-11-source-01.md
  - raw/# Bible des ratios et règles harmoniques — Norma.md
  - wiki/sources/2026-06-11-source-08.md
---

# Harmonic Ratio Bible

Source-first catalog of how Norma must classify ratios, constants, and geometric rules.

## Current state

The ratio set is organized as discovery knowledge first, then candidate engineering knowledge.
This page summarizes the strict boundaries and tagging model used by the team today.

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

## Sources

- `raw/# Bible des ratios et règles harmoniques — Norma.md` (immutable copy)
- `wiki/sources/2026-06-11-source-01.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/tech/core-interface-boundary.md`
- `wiki/strategy/mvp-pr-roadmap.md`
