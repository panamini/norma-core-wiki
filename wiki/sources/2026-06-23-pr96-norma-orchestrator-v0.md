---
title: "PR96 Norma Orchestrator v0"
category: source
status: current
created: 2026-06-23
updated: 2026-06-23
type: runbook
related:
  - "[[Norma Orchestrator]]"
---

# PR96 Norma Orchestrator v0

## Summary

PR96 added the first local Norma Orchestrator to `norma-core`.

It is a TypeScript/Node advisory tooling layer. It should support context building, validation planning, doctor checks, dry-run orchestration, and evidence capture. It should not yet replace the strict PR prompt pipeline.

## Key points

- Maturity level: `L1_ADVISORY`.
- Primary value: deterministic project context and validation evidence.
- Not trusted for autonomous implementation, automatic wiki mutation, automatic PR creation, or merge decisions.
- The wiki was not modified by PR96 itself.
- CI passed before merge after a pnpm lockfile repair.

## Implications

Agents should discover the orchestrator through `AGENTS.md`, then `.agents/skills/norma-orchestrator/SKILL.md`, then `tools/orchestrator/README.md` inside `norma-core`.

The next hardening work should add a machine-readable trust/capability manifest, canonical pnpm handling, and failure-pressure tests.

## Touched pages

- `wiki/tech/norma-orchestrator.md`
- `wiki/index.md`
- `wiki/log.md`
- `wiki/hot.md`
