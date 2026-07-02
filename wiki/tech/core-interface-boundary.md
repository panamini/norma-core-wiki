---
title: "Core / Interface / Adapter Boundary"
category: tech
status: current
created: 2026-06-11
updated: 2026-07-02
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
  - wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md
  - wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md
  - wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md
  - wiki/outputs/2026-06-30-post-r25-roadmap-compression-checkpoint.md
  - wiki/outputs/2026-07-01-post-pr82-accepted-geometry-structured-analyze-bridge-checkpoint.md
  - wiki/outputs/2026-07-01-pr86-normalization-metric-policy-checkpoint.md
  - wiki/outputs/2026-07-02-post-pr93-guided-inspection-package-api-checkpoint.md
  - wiki/outputs/2026-07-02-post-pr95-package-api-export-contract-checkpoint.md
---

# Core / Interface / Adapter Boundary

Defines strict ownership for what computes, what calls, and what displays.

## Current state

Core logic is authoritative and deterministic.
Interfaces and adapters can call, transform, or render outputs, but they must not define geometric rules.

Accepted geometry remains explicit structured input after acceptance. The
current accepted-geometry mapper and shared-unit-surface normalizer are
package-private and deterministic; they are not providers, perception layers,
public exports, package APIs, or source-truth shortcuts.

Guided inspection remains structural and truth-bounded. PR94 proved local
package-private consumption of the guided inspection demo envelope. PR95
approved only future package-root V1 API exports for that structural contract;
it did not implement exports or approve package publication, hosted runtime,
provider, adapter, or product scope. `result.json` remains canonical Norma truth
and derived files remain inspection artifacts only.

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
- PR #145 / R23, PR #146 / R24, and PR #147 / R25 continued this local
  inspection/protection rail through onboarding, scenario regression, and static
  safety guards.
- PR #148 / R26 merged as a docs/test-only roadmap truth sync. It does not
  authorize runtime changes.
- PR #153 through PR #159 extended local/private real-usecase demo, inspection,
  and CLI report boundary proof around explicit structured input and existing
  report surfaces.
- PR #160 / PR81 added the package-private accepted geometry to Core mapper.
  PR #162 / PR82 added synthetic test-only proof that mapped accepted geometry
  can reach Structured Analyze after explicit normalization, while unsupported
  primitives stop at the mapper.
- PR #165 / PR85 added the package-private shared-unit-surface normalizer.
  PR #166 / PR86 preserved metric policy through that normalizer so the
  synthetic shared surface and normalized output compositions remain coherent
  for downstream Structured Analyze operation contexts.
- PR #168 / PR88 through PR #175 / PR95 moved guided inspection package/API
  readiness from blocked future language into a local, package-private proof
  rail plus an approved future package-root V1 export contract: PR89 added the
  local guided inspection demo, PR90 defined the readiness gate, PR91 added the
  package-private artifact contract helper, PR92 wired the demo through it, PR93
  synced the roadmap, PR94 added the package-private consumer proof, and PR95
  approved only the future package-root V1 API export contract for PR96.
- R22-R26, PR81-PR86, and PR88-PR95 do not authorize adapter/viewer/source-truth
  execution, recomputation outside approved package-private test/demo paths,
  prompt/file/URL/media/CAD/provider input, hosted dashboard, public webapp,
  SDK, API runtime, package publication, public app submission, remote MCP,
  hosted MCP, ChatGPT connector runtime, OpenAI/provider calls, image/CAD/Figma
  adapters, correction, recommendation, optimization, scoring, automatic family
  selection, or inference.

## Sources

- `raw/Chapitre 11 — Interfaces, adapters et agent-readiness de Norma Core.md`
- `raw/Norma — Vision produit, UX cible et architecture d’intégration.md`
- `wiki/sources/2026-06-11-source-02.md`
- `wiki/sources/2026-06-19-norma-product-vision-ux-flows-and-integration-architecture-prompt.md`
- `wiki/sources/2026-06-23-norma-core-pr-execution-map-v1.md`
- `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`
- `wiki/outputs/2026-06-25-r6d-chatgpt-meta-connector-checkpoint.md`
- `wiki/outputs/2026-06-29-r22-local-structured-analyze-inspection-checkpoint.md`
- `wiki/outputs/2026-06-30-post-r25-roadmap-compression-checkpoint.md`
- `wiki/outputs/2026-07-01-post-pr82-accepted-geometry-structured-analyze-bridge-checkpoint.md`
- `wiki/outputs/2026-07-01-pr86-normalization-metric-policy-checkpoint.md`
- `wiki/outputs/2026-07-02-post-pr93-guided-inspection-package-api-checkpoint.md`
- `wiki/outputs/2026-07-02-post-pr95-package-api-export-contract-checkpoint.md`

## Related

- `wiki/tech/core-spec-v0-1.md`
- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/product/mvp-demo-brief.md`
- `wiki/product/norma-product-vision.md`
