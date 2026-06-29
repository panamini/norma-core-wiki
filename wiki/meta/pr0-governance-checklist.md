---
title: "PR0 Governance and Checklist"
category: meta
status: current
created: 2026-06-11
updated: 2026-06-30
tags:
  - governance
  - review
  - anti-drift
sources:
  - wiki/sources/2026-06-11-source-06.md
  - raw/PR 0.md
  - wiki/sources/2026-06-11-source-08.md
  - wiki/sources/2026-06-11-source-09.md
  - wiki/sources/2026-06-11-source-10.md
  - wiki/sources/2026-06-11-source-11.md
---

# PR0 Governance and Checklist

Minimum governing artifacts for every subsequent Norma Core implementation PR.

## Current state

PR0 defines the non-functional constraints for all future PRs and protects the MVP from scope expansion.

## Details

### Required outputs from the PR0 phase

- strict MVP definition (what core is / is not)
- explicit blocked capabilities list
- review checklist for PR1–PR12
- `PR complete` definition
- compact glossary for canonical objects
- locked decisions and no immediate product redesign

### PR0 acceptance gate

- documentation-only scope
- immutable raw/source separation preserved
- explicit references to anti-drift rules
- clear demo target: proportional composition + structured evaluation

### PR sequencing and execution discipline (post-PR25)

- Post-R25 execution no longer follows a speculative PR27-PR46 queue.
- Each PR must be one real isolated change selected from the current gap.
- PR labels may use R numbers for local continuity, but labels do not create a
  pre-approved roadmap chain.
- Package publication, hosted MCP, remote API runtime, public product surface,
  and business launch readiness remain blocked until explicit approval.
- PRs must state scope/non-scope and include validation commands for the actual
  change, not for an invented future phase.

### Review checklist used as default for later PRs

- Scope and non-scope defined
- Required artifacts defined
- Tests/validation strategy defined
- warnings/error behavior explicit
- success conditions and failure conditions explicit
- no cross-layer leakage from interfaces to core rules

## Sources

- `raw/PR 0.md`
- `wiki/sources/2026-06-11-source-06.md`

## Related

- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/tech/core-spec-v0-1.md`
- `wiki/product/mvp-demo-brief.md`
