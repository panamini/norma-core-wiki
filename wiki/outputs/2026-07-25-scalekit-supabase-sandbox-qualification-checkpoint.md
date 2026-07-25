---
title: "Scalekit and Supabase Sandbox Qualification Checkpoint"
category: output
status: current
created: 2026-07-25
updated: 2026-07-25
tags:
  - sandbox
  - scalekit
  - railway
  - supabase
  - mcp
type: checkpoint
---

# Scalekit and Supabase Sandbox Qualification Checkpoint

## Context

The Norma Core repository-side Railway → PostgreSQL/Supabase sandbox rail is
merged. This checkpoint records the exact live evidence observed on the
disposable sandbox without storing tokens, claims, secrets, prompts, emails,
or database contents.

## Result

- PR #272 is merged into `main` at `f95d829a8141379e7ba936d2f86fdda14733525c`;
  its branch head was `632753333bcad61df303f2ef5f5a954fbda25473`.
- Railway deployment `e0da5150-44cf-4226-9ab7-edfef2f0d186` became active and
  served `/readyz` with HTTP 200.
- The deployed application pool factory connected to Supabase with verified
  TLS using the configured private CA; no raw connection material was emitted.
- The live application-path RLS proof passed: same-tenant allow,
  cross-tenant deny, missing-context deny, rollback isolation, and pooled
  authorization-setting reset.
- The disposable Supabase fixture was deleted after proof; cleanup completed.
- The already-authorized Scalekit connector executed a protected
  `norma.analyzeStructuredCompositionV1` call and returned a valid result with
  no blocking errors.

## Gate status

`productionReadiness: CLOSED` remains intentional. The ChatGPT connector
surface does not expose raw `initialize`, `resources/list`, or `resources/read`
transport evidence, and the complete consent/refresh/revocation and exact
resource-audience records are not independently captured in the repository.
The MCP business call is live and functional, but missing qualification
records must not be represented as a production pass.

## Next decision

No further code PR is justified for this checkpoint. Either pause here, or
collect the remaining sanitized native OAuth/MCP transport evidence with an
authorized operator/client, then review the nine-criterion matrix before any
production-readiness decision. Auth0 remains fallback-only after a blocking
Scalekit failure.

## Sources

- `norma-core` PR #272 and merged `main`.
- `docs/runbooks/sandbox-qualification-launch-gates.md`.
- `docs/decisions/2026-07-24-railway-supabase-oauth-provider-qualification.md`.
