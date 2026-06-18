---
title: "Norma Product Vision"
category: product
status: planned
created: 2026-06-19
updated: 2026-06-19
tags:
  - vision
  - adapters
  - ux
sources:
  - raw/Norma — Vision produit, UX cible et architecture d’intégration.md
  - wiki/sources/2026-06-19-norma-product-vision-ux-flows-and-integration-architecture-prompt.md
---

# Norma Product Vision

Norma is a family of adapters around a deterministic proportional core: the first slice lives in ChatGPT, while Camera, CAD, and renderer surfaces reuse the same structured contracts.

## Vision

- Core receives structured geometry only.
- Adapters transform external inputs into normalized observations or intents.
- Perception is pluggable: OpenAI Vision first, Norma Vision later, CAD when geometry is exact.
- Outputs stay explicit about source, system, confidence, tolerance, and provenance.

## Use cases

- ChatGPT image analysis with overlays, correction, and explicit pack selection.
- ChatGPT composition creation from confirmed `DesignIntent` data.
- Norma Camera live overlays on mobile.
- AutoCAD read-only evaluation of selected geometry or viewports.
- Future web, Figma, Illustrator, and batch QA adapters.

## Non-goals

- No silent core mutation from interfaces or overlays.
- No treating raster, SVG, or prompt inference as source of truth.
- No automatic design edits without explicit user action.

## Related

- `wiki/tech/core-interface-boundary.md`
- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/product/mvp-demo-brief.md`
