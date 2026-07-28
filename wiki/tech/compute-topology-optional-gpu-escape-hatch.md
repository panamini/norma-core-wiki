---
title: "Compute topology and optional GPU escape hatch"
category: tech
status: current
created: 2026-07-24
updated: 2026-07-28
tags:
  - architecture
  - compute
  - gpu
  - railway
  - supabase
---

# Compute topology and optional GPU escape hatch

## Status and decision boundary

Railway remains the MCP/API control plane and ordinary CPU runtime. Supabase
PostgreSQL/RLS remains the provider-neutral authorization data boundary;
Supabase Auth/OAuth is not selected.

The OAuth/MCP shortlist is `SHORTLISTED_PENDING_SANDBOX`: Scalekit is the first
sandbox candidate for the simplest ChatGPT → MCP path; Auth0 is the fallback and
must run the same exact contract if Scalekit fails a blocking criterion; WorkOS is
conditional on written confirmation of the custom scope, its presence in the MCP
JWT, and Supabase RLS compatibility. PR258 now documents Railway → Supabase/RLS
as the provider-neutral sandbox boundary. PR #281 and PR #282 added a separate,
optional SAM 3 adapter implemented and configured to target Modal for private
sandbox perception. This page authorizes no production resource creation,
migration, deployment, or configuration change.

## Compute tiers

| Tier | Location | Allowed responsibility |
| --- | --- | --- |
| Tier 0 | Local/on-device | Core, deterministic geometry, ratio packs, guides/grids, Norma Construct on structured geometry, Norma Verify, JSON/SVG exports, and Camera real-time guidance/detection |
| Tier 1 | Railway CPU | MCP server, API, orchestration, and ordinary CPU workloads |
| Tier 2 | Modal L4 sandbox adapter, implemented but live-unverified | One explicitly requested SAM 3 candidate-mask inference; never Core, confirmation, ratio selection, or canonical geometry |

Core must remain executable locally without network access by Studio, Camera,
AutoCAD, Figma, and other adapters/plugins. Camera's mandatory per-frame loop
is local. A remote GPU may assist only deferred or ambiguous-scene analysis.

GPU observations are candidate evidence: they must become structured geometry
and be verified by Core before becoming canonical results.

## GPU escape hatch rule

Modal is selected only as the implemented target for the current private SAM 3
sandbox adapter. Its current deployment and live inference are not verified by
this page, and it is not a production provider commitment. Do not promote,
reserve, or lock GPU capacity until a live workload benchmark records useful
mask quality, latency including cold start, and cost. The current observation
captured no SAM receipt or timing.

Any later GPU decision must compare latency, cold start, precision, cost per
analysis, region, confidentiality, scale-to-zero, and provider portability.
Railway remains the control plane and calls a provider-neutral segmentation
interface. Modal is the implemented sandbox adapter; another server or an
on-device model may replace it without changing widget confirmation or Core.
