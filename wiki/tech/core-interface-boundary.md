---
title: "Core / Interface / Adapter Boundary"
category: tech
status: current
created: 2026-06-11
updated: 2026-07-11
tags:
  - architecture
  - adapters
  - mvp-boundaries
sources:
  - wiki/sources/2026-06-11-source-02.md
  - raw/Chapitre 11 — Interfaces, adapters et agent-readiness de Norma Core.md
  - raw/Norma — Vision produit, UX cible et architecture d’intégration.md
  - wiki/sources/2026-06-19-norma-product-vision-ux-flows-and-integration-architecture-prompt.md
  - wiki/sources/2026-06-23-norma-core-pr-execution-map-v1.md
  - wiki/outputs/2026-07-11-pr214-validation-hardening-checkpoint.md
  - wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md
  - wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md
  - wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md
---

# Core / Interface / Adapter Boundary

Defines strict ownership for what computes, what calls, and what displays.

## Current state

Core logic is authoritative and deterministic.
Interfaces and adapters can call, transform, or render outputs, but they must not define geometric rules.

PR131 selected a separate local visual candidate review surface. PR132 implemented the local static PNG/candidate review, non-authoritative selection intent, package-private finalizer, and the existing no-network resume path to AcceptedGeometry, Core / Structured Analyze, and canonical `result.json`. PR133 selected private/dev ChatGPT + MCP visual pilot as the next external track, but it did not approve connector/runtime/hosting/auth/provider/public surface. PR214 hardened bounded reads, exact false persistence fields, receipt/candidate provenance linkage, and durable validation evidence. Selection intent is non-authoritative; the existing PR129 `--resume` path remains the only route to AcceptedGeometry, Core / Structured Analyze, and canonical `result.json`. logical PR134 remains blocked until an exact HIGH-risk local-only MCP orchestration contract is separately approved.

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

### Perception provider split

- Normalize every visual or exact-geometry input into a structured observation before it reaches core.
- OpenAI Vision is the fastest first provider for image perception.
- Norma Vision is the later precision path for camera and repeatability.
- CAD adapters can supply exact geometry without perception loss.
- Core must never depend on which provider was used.

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

### PR layer separation

- `CORE` work covers PR1-PR3 and owns deterministic engine behavior.
- `TRANSPORT` work covers PR4-PR5 and owns MCP safety and read-only tool exposure.
- `INTEGRATION` work starts at PR6 and owns external system access.
- PR4, PR5, and PR6 must not modify geometry logic, measurement logic, evaluation logic, packs, ratios, or deterministic output rules.
- If transport or integration work touches core computation, stop and split the PR.
- PR6 has passed a private/dev ChatGPT Secure MCP Tunnel smoke, but that validates external invocation only; it does not relax the boundary or authorize public app submission as the default next step.
- PR113 / R6D has passed current-main private ChatGPT connector smoke for the
  six-tool inventory after the `_meta` compatibility patch. This remains an
  interface checkpoint only and does not authorize hosted MCP, public
  submission, ChatGPT Analyze expansion, or core behavior changes.
- PR #144 / R22 has merged the local-only, static, read-only Structured Analyze
  inspection surface for existing result JSON and completed
  `norma.analyzeStructuredCompositionV1` MCP responses. This is an inspection
  surface only: direct engine output and `result.json` remain canonical truth,
  and viewer output remains derived display data.
- PR131-PR134 remain selection and validation checkpoints only. They do not
  relax the core boundary, and they do not replace the existing PR129
  `--resume` path to AcceptedGeometry, Core / Structured Analyze, and canonical
  `result.json`.
- R22 does not authorize execution, recomputation, source-truth creation,
  prompt/file/URL/media/CAD/provider input, hosted dashboard, public webapp,
  SDK, API runtime, public package readiness, public app submission, remote MCP,
  correction, recommendation, optimization, scoring, or inference.

## Sources

- `raw/Chapitre 11 — Interfaces, adapters et agent-readiness de Norma Core.md`
- `raw/Norma — Vision produit, UX cible et architecture d’intégration.md`
- `wiki/sources/2026-06-11-source-02.md`
- `wiki/sources/2026-06-19-norma-product-vision-ux-flows-and-integration-architecture-prompt.md`
- `wiki/sources/2026-06-23-norma-core-pr-execution-map-v1.md`
- `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`
- `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/product/mvp-demo-brief.md`
- `wiki/product/norma-product-vision.md`
