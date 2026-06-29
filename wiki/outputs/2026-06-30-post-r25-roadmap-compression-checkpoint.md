---
title: "Post-R25 Roadmap Compression Checkpoint"
category: output
status: current
created: 2026-06-30
updated: 2026-06-30
type: runbook
---

# Post-R25 Roadmap Compression Checkpoint

## Context

This checkpoint syncs the wiki to the post-R25 Norma Core state and the R26
roadmap truth-sync PR.

It is a wiki state checkpoint, not a product approval and not a runtime change.

## Result

- Latest merged Norma Core checkpoint: PR #147 / R25.
- PR #147 title: `R25: local inspection surface static safety guard`.
- PR #147 merge commit: `3889cf84d6df41391996d9d16cb76b5c48638a2d`.
- R26 core PR: PR #148, `R26: post-R25 roadmap truth sync`.
- PR #148 head at sync time: `67be4b4376a5f22272a3179b99c35e799aacb847`.
- PR #148 state at sync time: open, not merged.

The wiki should treat PR #148 as the current roadmap-compression candidate until
it merges. After PR #148 merges, the wiki can update this checkpoint with the
merge commit or supersede it with a merged-state checkpoint.

## Current Roadmap Model

Norma Core no longer needs a speculative PR27-PR46 execution ladder as the
active queue.

The current operating model is:

1. Local Structured Analyze protection rail is complete through R25.
2. R26 aligns roadmap/docs truth and demotes old PR ladders to historical or
   gated context.
3. Future work must be selected as one isolated PR from a current gap.
4. Ongoing allowed tracks are regression/safety, scenario-suite coverage, and
   light local inspection UX polish.
5. Package publication, hosted MCP, remote API, public web/product surface,
   ChatGPT public submission, image/vision/CAD/provider input, optimization,
   recommendation, and beauty scoring remain blocked until explicit approval.

## Production Gate Shape

Use gates instead of numbered PR chains:

- `local-structured-analyze`: complete through R25, with R26 docs truth sync in
  review.
- `regression-and-safety`: ongoing only for real invariant gaps or bug fixes.
- `scenario-system`: one evolving deterministic suite, not separate artificial
  roadmap layers.
- `inspection-ux`: local-only, static/read-only polish only.
- `exposure-layer`: blocked by default.
- `business-launch`: blocked until package/product/exposure gates are approved.

## Non-Goals

This checkpoint does not authorize:

- Norma Core engine, schema, package, lockfile, CLI, MCP, report-kit, viewer, or
  runtime changes;
- hosted or remote behavior;
- public npm publication;
- SDK/API/product expansion;
- image, vision, CAD, camera, plugin, provider, or file/URL input;
- recommendation, optimization, correction, beauty scoring, prompt inference,
  or source-truth creation.

## Related

- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/tech/core-interface-boundary.md`
- `wiki/meta/pr0-governance-checklist.md`
- `wiki/overview.md`
- `docs/BUSINESS_READINESS_ROADMAP.md`
- `docs/decisions/2026-06-30-post-r25-roadmap-truth-sync.md`
