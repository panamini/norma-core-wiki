---
title: "R22 Local Structured Analyze Inspection Checkpoint"
category: output
status: current
created: 2026-06-29
updated: 2026-06-29
type: runbook
---

# R22 Local Structured Analyze Inspection Checkpoint

## Context

PR #144 landed the R22 local Structured Analyze inspection surface.

This checkpoint records the merged state and the next scoped PR prompt. It is a
handoff checkpoint, not a new product approval.

## Result

- Status: `R22_LOCAL_STRUCTURED_ANALYZE_INSPECTION_MERGED`
- PR: `#144`
- PR title: `R22: local Structured Analyze inspection surface`
- Head commit: `1a3eb9a937a588ef302e67912c9f5d1a95fac260`
- Merge commit: `b80a53d3d13863abd4dca4f944dcdc74aab6eaa3`
- Merged at: `2026-06-29T17:47:21Z`
- Local verification before merge: `pnpm run check`, `git diff --check`, and
  Fallow audit new-only gate passed.
- Remote note: GitHub `verify` and `semgrep-ce/scan` were zero-step infra
  failures; `semgrep-cloud-platform/scan` completed successfully.

## Current Behavior

The local read-only viewer can inspect existing Structured Analyze result JSON
and completed `norma.analyzeStructuredCompositionV1` MCP responses when they
already contain deterministic result output.

The viewer preserves result payload visibility for `measurements` and
`evaluations`, keeps unknown fields inert, and keeps diagnostics, warnings,
errors, refs, provenance, replay readiness, comparison, decision, and
serialization details inspectable.

The pasted JSON path keeps the old body-size guard for unrelated JSON and only
uses the large-payload Structured Analyze fallback for marker-bearing result or
MCP payloads. It rejects execution-shaped wrappers, source-truth-shaped fields,
unsupported replay inputs, and structural limit violations before rendering.

## Non-Goals

R22 does not authorize:

- analysis execution or recomputation from the viewer;
- source-truth creation;
- prompt, file path, URL, media, CAD, camera, design-tool, or provider input;
- correction, recommendation, optimization, scoring, beauty judgment, or intent
  inference;
- SDK behavior, API runtime, hosted or remote MCP, public package readiness,
  hosted dashboard, public webapp, or public ChatGPT app submission;
- engine correctness, package exports, schemas, package metadata, lockfile, CLI,
  MCP runtime, or report-kit behavior changes beyond the scoped local viewer.

## Next PR Prompt

```text
You are working on panamini/norma-core.

Start from latest origin/main after PR #144 merged.

Goal: implement R23, a narrow local inspection surface onboarding fixture and
workflow polish PR.

Context:
- PR #144 / R22 merged the local-only, static, read-only Structured Analyze
  inspection surface.
- The viewer can inspect existing Structured Analyze result JSON and completed
  norma.analyzeStructuredCompositionV1 MCP responses.
- Direct engine output and result.json remain canonical truth.
- Viewer output is derived inspection only.
- Existing local verification for R22 passed with pnpm run check, git diff
  --check, and Fallow audit new-only gate.

Scope:
- Add or update a small onboarding fixture/workflow path that helps a local user
  inspect an existing Structured Analyze result with the static viewer.
- Keep the work local-only, static, read-only, and documentation/test backed.
- Prefer docs, fixtures, and focused viewer/static tests over runtime changes.
- Preserve the current package-private viewer boundary.
- Keep all changes inside the existing local viewer/onboarding/test scope unless
  a current test proves one extra file is required.

Required checks:
- Existing Structured Analyze result JSON remains inspectable.
- Existing completed analyzeStructuredCompositionV1 MCP response remains
  inspectable.
- Large unrelated pasted JSON still fails through the body-size guard before
  parsing.
- Execution-shaped wrappers with method or params remain rejected.
- /replay-mvp-demo replay input shapes remain rejected.
- HTML/script-like strings remain inert text.
- The workflow docs do not imply analysis execution, recomputation, source-truth
  creation, hosted behavior, public package readiness, SDK/API behavior, remote
  MCP, image/vision/CAD/provider input, correction, recommendation,
  optimization, scoring, or prompt inference.

Non-goals:
- No engine behavior changes.
- No package export or package metadata changes.
- No lockfile churn.
- No CLI or MCP runtime changes.
- No report-kit runtime changes.
- No hosted dashboard, public webapp, SDK, API runtime, remote MCP, public npm,
  or public ChatGPT app work.
- No image, vision, camera, CAD, plugin, file-path, URL, media, or provider
  input.
- No recommendation, optimization, correction, beauty scoring, or intent
  inference.

Validation:
- Run the narrow viewer/onboarding tests first.
- Run pnpm run build.
- Run pnpm run check before publishing.
- Run git diff --check.
- If Fallow is available, run fallow audit in read-only advisory mode and treat
  findings as advisory unless they identify a concrete new regression.

Deliverable:
- A small PR titled:
  R23: local inspection surface onboarding fixture and workflow polish
- Include a concise PR body with scope, non-goals, and validation evidence.
```

## Related

- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/tech/core-interface-boundary.md`
- `docs/BUSINESS_READINESS_ROADMAP.md`
- `docs/examples/read-only-result-viewer-workflow.md`
- `docs/onboarding/README.md`
