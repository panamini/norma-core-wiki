---
title: "Core / Interface / Adapter Boundary"
category: tech
status: current
created: 2026-06-11
updated: 2026-06-11
tags:
  - architecture
  - adapters
  - mvp-boundaries
sources:
  - wiki/sources/2026-06-11-source-02.md
  - raw/Chapitre 11 — Interfaces, adapters et agent-readiness de Norma Core.md
---

# Core / Interface / Adapter Boundary

Defines strict ownership for what computes, what calls, and what displays.

## Current state

Core logic is authoritative and deterministic.
Interfaces and adapters can call, transform, or render outputs, but they must not define geometric rules.

## Details

### Core ownership

- geometric models (segments, surfaces, guides, zones, intersections)
- rule execution
- construction and measurement
- evaluation and scoring inputs
- decisions, explanations, provenance, and replay metadata

Core output is truth. Interfaces must not alter output semantics.

### Interface/adapter ownership

- transport and invocation (CLI, API, SDK, MCP tool surface)
- rendering/UX (UI, overlays, colors, gestures)
- environment integration (camera, plugin, CAD/design app bridges)
- import/export adaptation around structured objects

Adapters should map external shapes to structured inputs and report conversion losses.

### Interface taxonomy

- CLI / SDK / API / MCP / plugin / camera / CAD adapter / design adapter / agent skill
- each interface type can change *how* Norma is called, never *what* Norma computes

### Adapter contract

1. Convert external representations to structured inputs.
2. Preserve provenance.
3. Emit explicit warnings for lossy conversion.
4. Never rewrite core rules, ratios, or scoring meaning.

### Agent-readiness constraints

- Core-first response contracts only.
- No hidden mutable state in interface layers.
- No prompt-based hidden logic as a substitute for core rule declarations.
- No interface-generated defaults that materially change deterministic core outcomes.

### Interface leakage risks to block

- UI claiming ratio authority.
- SVG or external visual artifacts becoming the source of truth.
- Plugin structures overriding core primitives.
- MCP/tooling inventing rules not declared by core contracts.

## Sources

- `raw/Chapitre 11 — Interfaces, adapters et agent-readiness de Norma Core.md`
- `wiki/sources/2026-06-11-source-02.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/product/mvp-demo-brief.md`
