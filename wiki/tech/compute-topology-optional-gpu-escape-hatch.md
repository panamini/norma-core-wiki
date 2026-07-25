---
title: "Compute topology and optional GPU escape hatch"
category: tech
status: proposed
created: 2026-07-24
updated: 2026-07-24
tags:
  - architecture
  - compute
  - gpu
  - railway
  - supabase
---

# Compute topology and optional GPU escape hatch

## Status and decision boundary

Proposed ADR. Railway in the United States is the target for the MCP server,
API, orchestration, and CPU workloads. Supabase PostgreSQL/RLS in the United
States remains the probable data target, with regions chosen as close as
available. Supabase Auth/OAuth is not selected.

The OAuth/MCP shortlist is `SHORTLISTED_PENDING_SANDBOX`: Scalekit is the first
sandbox candidate for the simplest ChatGPT → MCP path; Auth0 is the fallback and
must run the same exact contract if Scalekit fails a blocking criterion; WorkOS is
conditional on written confirmation of the custom scope, its presence in the MCP
JWT, and Supabase RLS compatibility. PR258 now documents Railway → Supabase/RLS
as the provider-neutral sandbox boundary. This page authorizes no production
resource creation, migration, deployment, or configuration change.

## Compute tiers

| Tier | Location | Allowed responsibility |
| --- | --- | --- |
| Tier 0 | Local/on-device | Core, deterministic geometry, ratio packs, guides/grids, Norma Construct on structured geometry, Norma Verify, JSON/SVG exports, and Camera real-time guidance/detection |
| Tier 1 | Railway CPU | MCP server, API, orchestration, and ordinary CPU workloads |
| Tier 2 | External GPU, optional | Only a demonstrated workload such as custom vision, self-hosted VLM, image generation, or heavy 3D rendering |

Core must remain executable locally without network access by Studio, Camera,
AutoCAD, Figma, and other adapters/plugins. Camera's mandatory per-frame loop
is local. A remote GPU may assist only deferred or ambiguous-scene analysis.

GPU observations are candidate evidence: they must become structured geometry
and be verified by Core before becoming canonical results.

## GPU escape hatch rule

Do not deploy or lock a GPU provider until a real workload benchmark demonstrates
that CPU/local execution is insufficient. The active benchmark budget is ten
executions total; this documentation update consumes zero executions.

Future GPU selection must compare latency, cold start, precision, cost per
analysis, region, confidentiality, scale-to-zero, and provider portability.
Railway remains the control plane and calls a provider-neutral GPU interface.
Modal and Cloud Run GPU are future candidates only; neither is selected or
implemented by this ADR.
