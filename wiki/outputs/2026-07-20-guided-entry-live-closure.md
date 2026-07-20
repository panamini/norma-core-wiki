---
title: "Guided Entry Live Closure"
category: output
status: current
created: 2026-07-20
updated: 2026-07-20
tags:
  - personal-visual-harmony
  - guided-entry
  - live-acceptance
  - runtime
related:
  - wiki/howto/personal-visual-harmony-quick-start.md
  - wiki/strategy/mvp-pr-roadmap.md
  - wiki/tech/core-interface-boundary.md
---

# Guided Entry Live Closure

## Verdict

`CC-20260720-PERSONAL-MVP-CLOSURE-v1` is complete for the guided-entry and
stable-runtime scope.

- Exact Norma Core main: `593b014052bc98e1065c2ce020f75f831f4a81d6`.
- Guided request: `Analyse cette image avec Norma`.
- Corrective replay: `REPLAY_PASS`.
- Stable private runtime: exact-main, `live`, `ready`, direct MCP smoke PASS.
- No geometric or harmonic-pack expansion.

## Application changes

- PR #249 added the short guided entry and six visible workflow goals.
- PR #250 restored the fixed-array schema representation accepted by ChatGPT.
- PR #251 canonicalized segment and axis envelopes from their authoritative
  endpoints.

PR #251 does not accept malformed geometry. Endpoints must still be finite,
normalized, distinct, and valid. The server only stops trusting a redundant
caller-supplied envelope and derives it from those endpoints, matching the
existing ellipse and quadrilateral canonicalization boundary.

## Six-case preparation matrix

The first exact-main run used six fresh conversations, one upload and the exact
short request per case, with no retries, confirmations, or Core runs.

- 2 cases produced usable prepared widgets.
- 2 cases failed closed because segment/axis envelopes disagreed with endpoints.
- 2 cases reached the 180-second ChatGPT surface boundary without a widget.

This was a product-path failure and correctly blocked stable-runtime promotion.
It did not justify more geometry.

## Corrective replay

The four prior non-PASS cells were replayed on exact main after PR #251:

| Case | Result | Prepared candidates |
| --- | --- | --- |
| Vertical-axis cluster | PASS | 1 rectangle, 6 axes |
| Low-contrast ambiguous | PASS | 2 rectangles, 1 ellipse, 1 segment |
| Cartier-Bresson amphitheatre | PASS | 1 rectangle, 1 ellipse, 5 segments |
| Leonardo Annunciation | PASS | 1 rectangle, 2 axes, 3 segments, 1 quadrilateral |

Aggregate: 4 fresh conversations, 4 uploads, 4 accepted preparation messages,
25 candidates, 0 retries, 0 confirmations, and 0 Core runs.

Every widget remained `À CONFIRMER`, with editable geometry and the manual
segment available. Six visible goals were present. Derived families remained
hidden or disabled; pixel proposals and the declared two-length report remained
disabled by default. No technical validation error occurred.

The low-contrast case proposed one more non-raster candidate than its frozen
qualitative expectation. That is not a validation or authority defect, but it
remains evidence that candidate discovery is not guaranteed to be minimal or
exhaustive.

## Stable runtime

The exact-main tree was promoted to the existing private runtime while
preserving `node_modules`, the Infisical-backed tunnel profile, and the verified
rollback snapshot:

`/Users/pana/.local/share/norma-core-personal-runtime.rollback-20260720-CC-PERSONAL-MVP-CLOSURE-v1-pre-0981331e`

One bounded launchd restart was used. Final evidence:

- source/runtime synchronization dry-run: empty;
- launchd: running, `runs=2`, `last exit=0`;
- `/healthz=live`;
- `/readyz=ready`;
- direct MCP smoke: tool-list schema PASS, three expected tools, no automatic
  Core, derived families fail closed without their explicit prerequisites, and
  centroid authority flags remain false.

## Current boundary and next gate

The personal MVP is stable for this scope. The next gate is observation-led
maintenance, not another geometric ladder.

- Fix a reproduced product-code bug with one surgical changeset.
- Implement a demonstrated user need only with a bounded acceptance case.
- Prefer documentation when code is unnecessary.
- Keep automatic harmonic-pack inference forbidden.
- Keep rhythms/repetitions, physical perspective/homography/rectification,
  circumcenter/incenter/orthocenter and other new centers, and new harmonic
  report families deferred nice-to-have work.
