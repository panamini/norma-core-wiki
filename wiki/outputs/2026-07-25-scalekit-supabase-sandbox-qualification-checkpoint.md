---
title: "Scalekit and Supabase Sandbox Qualification Checkpoint"
category: output
status: current
created: 2026-07-25
updated: 2026-07-26
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
- A separate MCP SDK client completed OAuth authorization with PKCE using
  ephemeral in-memory credentials, then passed `initialize`, `tools/list`,
  `resources/list`, and `resources/read`. The live server exposed four tools
  and one `ui://widget/norma-personal-visual-harmony-v1.html` resource; the
  resource read returned `text/html;profile=mcp-app`.
- PR #273 candidate code `7a27cb1` added a provider-neutral durable revocation
  cutoff registry. The final PR head also includes the token-free operator
  runbook.
- Scalekit public-DCR tokens passed local RS256/JWKS, exact issuer, exact MCP
  audience, scope, subject, `iat`, expiry, and `oid` tenant checks. The
  provider-specific confidential-client introspection path was disabled
  explicitly because it did not accept this public-DCR token and is not the
  documented Scalekit MCP validation path.
- The Railway database role was confirmed least-privileged. Its exact schema
  `USAGE`, table `SELECT`, and RLS policy were corrected without exposing the
  role name or connection material.
- The exact same in-memory token passed the sequence `200 → 401 → 200`: accepted
  before the wildcard cutoff, denied immediately after it, and accepted after
  the proof row was deleted. Cleanup was independently verified.

## Gate status

Native MCP transport and immediate same-token revocation are PASS.
`productionReadiness: CLOSED` remains intentional until PR #273 is merged and
the remaining consent/refresh evidence and full nine-criterion matrix are
reviewed. This checkpoint is not a production authorization.

## Operator reference

These identifiers and URLs are non-secret routing information for the
disposable sandbox:

- Railway project: `2666fa64-e58d-4599-8bda-8e30eee7b504`
- Railway service: `294010ef-0f2b-4189-897e-9bdf716175f8`
- Railway environment: `be59114e-b0fb-4e57-a60a-11277df94cc0`
- Active deployment: `e0da5150-44cf-4226-9ab7-edfef2f0d186`
- Public service: `https://norma-core-remote-mcp-beta-production.up.railway.app`
- MCP endpoint: `https://norma-core-remote-mcp-beta-production.up.railway.app/mcp`
- Protected-resource metadata:
  `https://norma-core-remote-mcp-beta-production.up.railway.app/.well-known/oauth-protected-resource/mcp`
- Scalekit authorization-server metadata:
  `https://twoweeks.scalekit.dev/resources/res_135600270506722306/.well-known/oauth-authorization-server`
- Scalekit JWKS: `https://twoweeks.scalekit.dev/keys`
- Supabase sandbox project: `bxjfhqtbosdbnpjihfwe`

To rerun the safe repository check, from `norma-core` run:

```bash
node bin/norma-core-sandbox-qualification.mjs
```

This is dry-run/provider-free. A live qualification operator must then use
the already-authorized Scalekit client, verify the metadata endpoints, run the
same nine-criterion matrix, capture only sanitized evidence references, and
clean up the disposable fixture. The Railway secrets
`NORMA_MCP_AUTHZ_DATABASE_URL` and `NORMA_MCP_POSTGRES_CA` stay only in the
Railway secret store. No account email, account name, token, claim, prompt,
database row, or credential belongs in this page.

For the token-free immediate-revocation procedure, use
`docs/runbooks/oauth-immediate-revocation-sandbox.md` in `norma-core`.

## Next decision

Merge PR #273 only after its exact-head CI and review gates pass. Then complete
or revalidate the remaining consent/refresh evidence and review the complete
nine-criterion matrix before any production-readiness decision. Auth0 remains
fallback-only after a blocking Scalekit failure.

## Sources

- `norma-core` PR #272 and merged `main`.
- `docs/runbooks/sandbox-qualification-launch-gates.md`.
- `docs/runbooks/oauth-immediate-revocation-sandbox.md`.
- `docs/decisions/2026-07-24-railway-supabase-oauth-provider-qualification.md`.
