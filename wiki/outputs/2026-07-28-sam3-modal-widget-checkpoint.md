---
title: "SAM 3 Modal and widget checkpoint"
category: output
status: current
created: 2026-07-28
updated: 2026-07-28
type: analysis
tags:
  - sam3
  - modal
  - chatgpt
  - widget
  - live-observation
sources:
  - https://github.com/panamini/norma-core/pull/281
  - https://github.com/panamini/norma-core/pull/282
  - https://github.com/panamini/norma-core/pull/287
related:
  - wiki/tech/sam3-modal-perception-pipeline.md
  - wiki/strategy/mvp-pr-roadmap.md
---

# SAM 3 Modal and widget checkpoint

## Context

PR #281 added the authenticated SAM 3 Modal perception boundary. PR #282 fixed
its packaged runtime dependencies. PR #283–#287 then repaired the ChatGPT MCP
resource metadata, cache/MIME compatibility, stale resource aliases, and
app-only remount behavior.

## Result

The initial observation was made with repository main
`de1c11efc42bd409ecde19550061186d90ab5df6`. PR #288 later merged the
two-length selector correction at
`ea12c967bbd7c3acfd8401e5d75dd6f59e8d07e4`.

Fresh operator-visible ChatGPT evidence on 2026-07-28 showed:

- the `norma sandbox scalekit` connector preparing a new image;
- one fully hydrated editable widget without the earlier template-fetch error;
- eight visible candidates across rectangles, ellipse, axis, and segments;
- manual guide correction remaining available before confirmation;
- the explicit confirmation boundary remaining separate from preparation.

The operator reported performing the confirmation. This checkpoint does not
claim an independently captured final result for that exact latest turn.

## Open observations

- The initial operator flow did not visibly offer the expected confirmed axis
  in the two-length dropdown. PR #288 corrected the merge path and completed a
  live recheck for selected axes, segments, and quadrilateral lengths.
- The person visible in the image was not proposed. The current widget SAM
  action uses an interactive point/box derived from an existing candidate and
  exposes no semantic text target.
- No `perceptionReceiptIdentity`, SAM mask, or live provider timing was captured
  in this observation. The button being present is not proof that a SAM
  inference completed.

## Decisions

1. Freeze the PR #281–#287 implementation and widget recovery rail.
2. Treat the missing axis/dropdown behavior as closed by PR #288.
3. Consider one bounded semantic SAM target field using
   the already-supported text-prompt provider contract.
4. Keep manual rectangles, harmonic grids, surface highlights, and additional
   ratio visualizations as later product slices.

## Verification boundary

- **Merged/offline:** provider contract, Modal server, fail-closed client,
  source/session binding, deterministic extraction, and widget compatibility.
- **Live widget:** fresh hydration and editable candidate review.
- **User-reported:** confirmation on the latest fresh image.
- **Not yet proven:** successful live SAM receipt, semantic person detection,
  SAM quality/latency/cost, and production readiness.
