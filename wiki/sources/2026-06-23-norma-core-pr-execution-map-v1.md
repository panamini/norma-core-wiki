---
title: "Norma Core PR Execution Map v1"
category: source
status: current
created: 2026-06-23
updated: 2026-06-23
type: runbook
related:
  - "[[MVP PR Roadmap]]"
  - "[[Core / Interface / Adapter Boundary]]"
---

# Norma Core PR Execution Map v1

## Summary

This source reframes the near-term Norma Core PR plan as a deterministic dependency system with explicit gates, layer boundaries, and drift-prevention rules.

## Key points

- PR execution should follow verified dependencies, not a flat task list.
- PR1 establishes a green, reproducible baseline before correctness fixes.
- PR2 protects geometry identity correctness without core behavior drift.
- PR3 becomes the golden manual MVP proof path.
- PR4 and PR5 harden MCP transport and tool exposure without touching core geometry, measurement, or evaluation logic.
- PR6 is external ChatGPT integration only after MCP tool stability.
- The execution layers are `CORE`, `TRANSPORT`, and `INTEGRATION`.
- A PR touching more than one layer is an invalid design signal.

## Implications

The existing roadmap should treat PR4, PR5, and PR6 as strictly sequential transport/integration work. PR5 and PR6 should not run in parallel, and none of PR4-PR6 should modify core geometry, measurement, evaluation, packs, ratios, or deterministic output rules.

## Touched pages

- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/tech/core-interface-boundary.md`
- `wiki/index.md`
- `wiki/log.md`
- `wiki/hot.md`
