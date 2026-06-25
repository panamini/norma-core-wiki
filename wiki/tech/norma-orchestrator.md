---
title: "Norma Orchestrator"
category: tech
status: current
created: 2026-06-23
updated: 2026-06-24
tags:
  - orchestrator
  - codex
  - tooling
sources:
  - "[[2026-06-23-pr96-norma-orchestrator-v0]]"
  - wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md
related:
  - "[[Core Interface Boundary]]"
---

# Norma Orchestrator

Norma Orchestrator is the merged PR96 TypeScript/Node advisory tooling layer for building task-specific wiki context, planning validation, recording run evidence, and exposing a repo-local Codex workflow for Norma Core.

## Current state

- Maturity: `L1_ADVISORY`.
- Current use: context generation, doctor checks, path-aware validation planning, dry-run orchestration, and evidence capture.
- PR6 ChatGPT Secure MCP Tunnel smoke passed through `norma.runMvpDemoV1`, but the ChatGPT app remains private/dev and the tunnel was stopped after testing.
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

## PR6 checkpoint

PR6 proved the private ChatGPT Secure MCP Tunnel smoke path after merge commit `658ea2069d1c6a65b23df7f43ba4c4ba96fd8a31` on `main-after-codex-mcp-tool`.

Canonical observed smoke facts:

- `runRef`: `run:v1:5c6303f20c12537e`
- `measurementCounts`: `{ "a": 6, "b": 6 }`
- `decision.status`: `a_closer`
- `selectedComposition`: `composition:A`
- `replayReadiness.status`: `replay_ready`

This validates private/dev external invocation only. It does not make publishing, public app submission, automatic merge decisions, or autonomous implementation the next step.

## Sources

- `norma-core` PR96: Add local Norma orchestrator v0.
- `rawinput/2026-06-23-pr96-norma-orchestrator-v0.md` — staged raw summary requested by the user.
- `[[2026-06-23-pr96-norma-orchestrator-v0]]` — source summary.
- `wiki/outputs/2026-06-24-post-pr6-chatgpt-secure-mcp-tunnel-checkpoint.md`

## Related

- `[[Core Interface Boundary]]`
- `[[MVP PR Roadmap]]`
