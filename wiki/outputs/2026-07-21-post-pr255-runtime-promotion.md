---
title: "Post-PR255 Runtime Promotion"
category: output
status: current
created: 2026-07-21
updated: 2026-07-23
tags:
  - personal-visual-harmony
  - runtime
  - live-evidence
  - ci
related:
  - wiki/outputs/2026-07-20-guided-entry-live-closure.md
  - wiki/strategy/mvp-pr-roadmap.md
  - wiki/howto/personal-visual-harmony-quick-start.md
---

# Post-PR255 Runtime Promotion

## Context

Norma Core PR #255 merged at
`077671ed49e6807066e6138bec0b3556065bd725` from reviewed head
`9de8814763e1ebe7ebc03aa0ce676da04ac34029`. Its changed behavior is limited
to CI push-baseline validation in `.github/workflows/ci.yml` and
`tests/changed-file-guard.mjs`; it does not change visual detection, geometry,
latency, the MCP product contract, or Core authority.

Since the previous wiki checkpoint, PR #252 separated dense overlay labels,
PR #253 stabilized the explicit two-length comparison before confirmation, and
PR #254 added correlated preparation-latency milestones. No new geometry or
harmonic pack was added.

## Result

Exact main was promoted to the existing private stable runtime through the
established bounded procedure.

- rollback snapshot:
  `/Users/pana/.local/share/norma-core-personal-runtime.rollback-20260721-post-PR255-pre-077671ed`;
- snapshot verification: recursive diff empty;
- source/runtime content verification: empty checksum rsync dry-run across the
  exact built tree, including 390 tracked source files;
- deployed MCP app SHA-256:
  `c9b4a9e64c97c7317d0567248da7186e490edf0bc5750f3bf7f4edbd2a8ba57c`;
- launchd after the one authorized restart: `running`, `runs=2`, `pid=81026`,
  `last exit code=0`;
- health: `live`;
- readiness: `ready`;
- direct MCP smoke: PASS with the three expected prepare, refine, and confirm
  tools; no provider API call and no automatic Core run.

These are live and offline deployment proofs. They prove exact-main runtime
integrity and deterministic MCP availability, not artistic usefulness or
exhaustive detection.

## ChatGPT acceptance boundary

After three failed automated Chrome chooser attempts across user-directed
resumptions, one permission correction, one browser reconnection, and a manual
file attachment, one fresh conversation completed the bounded acceptance for
distinct local image `DSC09546.jpeg`. No product operation had been accepted
before the manual attachment. The exact request was
`Analyse cette image avec Norma`, the reasoning level was `Moyenne`, and `Pro`
was not selected.

- conversation:
  `https://chatgpt.com/c/6a5f846f-5de0-83e9-ad71-1ba9334a3ec0`;
- fresh conversations with an accepted preparation: 1;
- candidate families/count: 1 rectangle and 6 segments, 7 total;
- missing candidates: several secondary or occluded batons remain unproposed,
  consistent with the non-exhaustive visual boundary;
- extra candidates: none clearly unsupported; the full-raster rectangle is the
  explicit Core reference frame;
- geometric precision: selected segment endpoints follow visible extents and
  stop at occlusions or the raster edge instead of inferring hidden geometry;
- editability: all six segment endpoints and the raster rectangle remained
  editable before confirmation, with one manual-segment path available;
- layout/comprehension: candidate labels were separated and readable, while
  the persistent ChatGPT composer obscured part of the lower overlay at this
  viewport; scrolling preserved access to the controls and candidate list;
- human geometry edits: 0;
- preparation visible at approximately 58.9 seconds; complete ChatGPT response
  at approximately 81.4 seconds; latency class: slow but bounded;
- confirmations/Core runs: 1/1 successful, approximately 7.1 seconds;
- provider API calls: 0;
- automatic retries: 0;
- ChatGPT/Chrome surface recoveries: 2, both before any accepted Norma
  operation;
- result SHA-256:
  `39991ea9bf980752addf485483472687c61c81ddd9d50d2259767052c5ee297f`;
- plan-image SHA-256:
  `85fdba7ba6de5da7b5c10cf74d016d00bc1bce0d6936d40cabd0eece22073c78`.

The result is `PRODUCT_OBSERVATION_PARTIAL`: the editable overlay and six
visible segment lengths are concretely useful for inspecting the dominant
baton structure, and Core completed deterministically. The final report has 0
declared ratio reports, 0 visual relations, 0 quadrilateral measurements, and
0 derived constructions because the two-length report remained disabled. It
therefore provides no new harmonic value. Surrounding ChatGPT prose continued
to say `À CONFIRMER` after the widget reached `CORE VÉRIFIÉ`; this is a surface
comprehension inconsistency, not a reproduced Core or Norma runtime defect.

Proof classes: conversation/widget/result are live; exact-tree and direct-smoke
checks are offline plus live runtime checks; artistic intent and exhaustive
detection remain explicitly unclaimed.

## Generated two-length gate

One fresh `Moyenne` conversation generated a square synthetic raster with
exactly two visible horizontal bars, then received the exact request
`Analyse cette image avec Norma`. The generation prompt asked for a `2:3`
length ratio; the visible raster did not preserve that requested ground truth.

- conversation:
  `https://chatgpt.com/c/6a6159dd-9a40-83e9-90d1-a3fc234f965a`;
- image identity: fresh ChatGPT-generated synthetic image, 1254 x 1254 px;
- generation latency: approximately 51.9 seconds;
- accepted preparations: 1;
- candidate families/count: 1 raster rectangle, 2 bar-envelope rectangles,
  and 2 segment axes, 5 total;
- missing candidates: none among the two intended visible bars;
- extra candidates: none unsupported; the frame and bar envelopes are distinct
  measurable references;
- measured axes: approximately 475 px and 667 px, observed ratio `0.712`
  (`1:1.404`), not the requested `2:3` (`0.667`);
- human geometry edits: 0; candidate editability could not be exercised because
  the widget never hydrated;
- preparation latency class: slow, with ChatGPT reporting 51 seconds of
  reasoning before the prepared result;
- confirmations/Core runs: 0; the blank widget remained loading for more than
  two additional minutes, so no two-length selection or confirmation was
  possible;
- provider API calls: 0; automatic product retries: 0;
- browser-control reconnections: 1 passive tab reclaim after the observer timed
  out; no page reload, resend, or ChatGPT recovery action;
- hashes/identities: no product result or plan-image hash was available because
  confirmation did not occur.

This case is live evidence with an inferred synthetic-design target. It is
`PRODUCT_OBSERVATION_PARTIAL`: the preparation text and measured primitive
inventory are useful and correctly expose that the generated raster missed its
requested ratio, but the opt-in harmonic report itself remains unproven. The
non-hydrating blank iframe is classified as a ChatGPT surface failure after an
accepted preparation, not as a reproduced Norma product-code or Core defect.

## Recommendation

Run one fresh manually attached, non-synthetic, non-spectacle image in
`Moyenne`, choose exactly two human-selected visible lengths before the single
confirmation/Core, and decide whether the opt-in harmonic report adds concrete
value. Do not add geometry or harmonic packs before that evidence.
