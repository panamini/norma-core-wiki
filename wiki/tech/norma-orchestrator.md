---
title: "Norma Orchestrator"
category: tech
status: current
created: 2026-06-23
updated: 2026-06-23
tags:
  - orchestrator
  - codex
  - tooling
sources:
  - "[[2026-06-23-pr96-norma-orchestrator-v0]]"
related:
  - "[[Core Interface Boundary]]"
---

# Norma Orchestrator

Norma Orchestrator is the merged PR96 TypeScript/Node advisory tooling layer for building task-specific wiki context, planning validation, recording run evidence, and exposing a repo-local Codex workflow for Norma Core.

## Current state

- Maturity: `L1_ADVISORY`.
- Current use: context generation, doctor checks, path-aware validation planning, dry-run orchestration, and evidence capture.
- Not yet trusted as primary autonomous driver, auto-repair authority, auto-PR opener, merge gate, or source of truth.
- Source of truth remains current code, tests, CI, durable wiki pages, and explicit user direction.
- Orchestrator output is derived evidence only.

## Details

PR96 added the orchestrator to `norma-core` with:

- `tools/orchestrator/` TypeScript implementation
- `.agents/skills/norma-orchestrator/` repo-local Skill
- `.orchestrator.example.json` configuration
- package scripts for doctor, context, validate, run, and test
- ignored `.orchestrator/` run evidence paths

Agents should discover it through the root `AGENTS.md`, then the repo-local Skill, then `tools/orchestrator/README.md`.

The safe usage rule is:

```text
Use PR96 orchestrator as advisory tooling.
Do not let it replace the strict PR prompt pipeline until it survives repeated real PRs and failure-pressure tests.
```

## Trust contract

Trusted for:

- building deterministic Markdown context packs from `norma-core-wiki`
- reporting environment and repository readiness through doctor checks
- planning and dispatching configured validation commands
- recording run evidence under ignored `.orchestrator/` paths
- making dry-run orchestration explicit with planned/skipped validation state

Not trusted for:

- autonomous implementation decisions
- automatic wiki mutation
- automatic PR creation or merge decisions
- resolving multi-agent conflicts
- overriding test, CI, or human review results

Promotion to `L2_GATED_VALIDATION` requires multiple successful dogfood PRs, failure-pressure tests, and a machine-readable capability/trust manifest.

## Sources

- `norma-core` PR96: Add local Norma orchestrator v0.
- `rawinput/2026-06-23-pr96-norma-orchestrator-v0.md` — staged raw summary requested by the user.
- `[[2026-06-23-pr96-norma-orchestrator-v0]]` — source summary.

## Related

- `[[Core Interface Boundary]]`
- `[[MVP PR Roadmap]]`
