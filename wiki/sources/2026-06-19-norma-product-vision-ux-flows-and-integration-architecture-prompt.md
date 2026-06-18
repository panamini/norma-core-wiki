---
title: "Norma Product Vision, UX Flows, and Integration Architecture Prompt"
category: source
status: current
created: 2026-06-19
updated: 2026-06-19
source_file: raw/Norma — Vision produit, UX cible et architecture d’intégration.md
---

# Source: Norma Product Vision, UX Flows, and Integration Architecture Prompt

## Summary
Ingested a broad vision draft that frames Norma as a deterministic proportional engine exposed through multiple adapters, with ChatGPT as the first vertical slice and Camera, CAD, and rendering as later adapters.

## Key points
- Separates Norma Core from perception, UI, and environment adapters.
- Defines a product family: Norma Core, Norma Codex, Norma Vision, Norma ChatGPT App, Norma Camera, Norma CAD, and Norma Renderer.
- Recommends a hybrid perception path with OpenAI Vision first, Norma Vision later, and CAD as an exact-geometry provider.
- Reiterates that Core must not parse images, open cameras, or alter drawings silently.
- Stages PR71 as a documentation-only vision and roadmap freeze rather than an implementation PR.

## Implications
- Add the adapter-family and perception-provider split to the core/interface boundary page.
- Record the PR71 documentation-only vision freeze in the roadmap.
- Capture the product vision itself on a planned product page so retrieval can find the future-state narrative without overloading the demo brief.

## Touched pages
- wiki/product/norma-product-vision.md
- wiki/tech/core-interface-boundary.md
- wiki/strategy/mvp-pr-roadmap.md
- wiki/overview.md
