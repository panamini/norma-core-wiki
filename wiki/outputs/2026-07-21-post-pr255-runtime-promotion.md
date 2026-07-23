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
  the widget had not hydrated during the initial observation window;
- preparation latency class: slow, with ChatGPT reporting 51 seconds of
  reasoning before the prepared result;
- the blank widget remained loading for more than two additional minutes, but
  later hydrated without a resend or product retry;
- confirmations/Core runs: 1/1 successful after that delayed hydration; the
  two-length report was not selected before confirmation and remained disabled
  afterward;
- provider API calls: 0; automatic product retries: 0;
- browser-control reconnections: 1 passive tab reclaim after the observer timed
  out; no page reload, resend, or ChatGPT recovery action;
- result SHA-256:
  `79b6af8a09070c34a7882d7f31a4db874857042e104bf73f04bf1b8311c4bb3c`;
- plan-image SHA-256:
  `4f0d2c759ba72e1ce0854223a32c2e6c9cf689bbb92a30093059ed6ec3127eda`;
- final widget: `CORE VÉRIFIÉ`, 7 geometric reports and 0 visual relations.

This case is live evidence with an inferred synthetic-design target. It is
`PRODUCT_OBSERVATION_PARTIAL`: the preparation text and measured primitive
inventory are useful and correctly expose that the generated raster missed its
requested ratio, but no human-declared two-length report was produced. The
initial blank iframe is a delayed ChatGPT-surface hydration event, not a terminal
Norma product-code or Core failure. Surrounding prose remained stale at
`À CONFIRMER` after the widget reached `CORE VÉRIFIÉ`.

## Manually attached non-synthetic gate

One fresh `Moyenne` conversation used the user-provided image
`composition_en_rouge_bleu_et_137350.webp` and the exact request
`Analyse cette image avec Norma`.

- conversation:
  `https://chatgpt.com/c/6a618039-7a30-83e9-a839-965ed5e10ad9`;
- image identity: fresh manually attached geometric composition, raster
  860 x 854 px;
- accepted preparations: 1;
- candidate families/count: 6 rectangles and 2 axes, 8 total;
- missing candidates: the small yellow lower-left field and the small white
  lower field;
- extra candidates: none clearly unsupported;
- geometric precision: the proposed major fields and the horizontal and
  vertical separator axes followed visible boundaries; slight pictorial
  irregularity remained explicit;
- editability: all eight candidates were exposed before confirmation;
- layout/comprehension: candidates, goals, and controls were readable, although
  the persistent ChatGPT composer obscured part of the lower widget at the
  observed viewport;
- human geometry edits: 0, because the two major axes were defensible and the
  omitted small fields could not be repaired honestly with the single
  manual-segment correction path;
- preparation: ChatGPT reported 57 seconds of reasoning; candidates were
  observed at approximately 71.0 seconds wall time; latency class: slow but
  bounded;
- the `Comparer 2 longueurs` goal exposed no selectable length and the report
  control remained disabled despite two confirmed visible axes;
- confirmations/Core runs: 1/1 successful, observed within approximately
  12.6 seconds;
- final widget: `CORE VÉRIFIÉ`, 3 geometric reports and 0 visual relations;
- detected reports: `2/3` for the left vertical white field height
  (66.5 %, 0.167 pt from target), `φ minor` for the central upper white field
  width (37.8 %, 0.397 pt), and `2/3` for that field's right-edge position
  (66.2 %, 0.467 pt);
- result SHA-256:
  `8650eacf2e0021db6681118024a8de078f7fa48974519394cc55f8c1a17bc40d`;
- plan-image SHA-256:
  `4b763efe1ad8a452dbe8a20be73d093be8c5bf5dc84cd3402758485e1abe2d89`;
- provider API calls: 0; automatic product retries: 0; human corrections: 0.

This live case is `PRODUCT_OBSERVATION_PARTIAL`. The three deterministic
rectangle reports give concrete compositional measurements, so the result is
partially useful. It does not prove the opt-in two-length value because the
selection surface was unavailable. Surrounding ChatGPT prose again remained
stale at `À CONFIRMER` after the widget reached `CORE VÉRIFIÉ`; this is a
reproduced surface-comprehension inconsistency, not a Core failure.

## Recommendation

Stop the observation gate at `PRODUCT_OBSERVATION_PARTIAL`. Two independent
real-image cases exposed enough segment or axis guides for a human comparison
but left the two-length report disabled, while the synthetic case proves the
control can receive selectable axes. A code change is justified only as one
narrow candidate changeset: make already-confirmed visible segment and axis
guides available to the opt-in two-length selectors, preserving explicit human
choice, exactly two lengths, no automatic confirmation, and no new geometry or
harmonic pack. Freeze that contract in focused tests before implementation.
