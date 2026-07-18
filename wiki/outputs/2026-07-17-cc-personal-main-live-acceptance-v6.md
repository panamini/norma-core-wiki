---
title: "CC-20260717 Personal Main Live Acceptance v6"
category: output
status: current
created: 2026-07-17
updated: 2026-07-18
type: runbook
---

# CC-20260717 Personal Main Live Acceptance v6

## Context

This checkpoint closes `CC-20260717-PERSONAL-MAIN-LIVE-ACCEPTANCE v6` after
the exact-head merge of `norma-core` PR #243 and the live PASS replay.

The source evidence is the local live acceptance report, section v6 around
line 460, plus the held-out matrix artifacts used to freeze the next gate.

## Result

- Status: `LIVE_ACCEPTANCE_PASS`
- Core PR: `#243`
- Reviewed exact head: `9148a8af9c7c529983299d2fcf3889cdd423def9`
- Merge commit and exact `origin/main`: `4cf8cd169a1c01fd64f654b1c6848061c590c7e0`
- Installed runtime: private exact-main install
- Build: PASS
- Suite: `1700/1700`
- `/healthz`: `live`
- `/readyz`: `ready`
- Installed runtime identity: byte-identical to the exact-main verification clone
- Conversation reused: `https://chatgpt.com/c/6a5a6f2d-8db8-83e9-95de-eb973d1b197d`
- New conversation: `0`
- Uploads: `0`
- Messages: `0`
- Replay confirmations: `1`
- Core successes: `1`
- Second retries: `0`

## Observed Final State

- Previous rejection `Triangle vertex point does not match its stable parent geometry.`
  disappeared.
- Final widget: `CORE + PLAN IMAGE VÉRIFIÉS`
- Visible state: rectangle Core, `0` harmonic reports, `3` visual relations,
  derived triangle, `3` medians, `1` centroid
- Authority preserved: `candidateEvidenceOnly=true`, `sourceTruth=false`,
  `coreAuthority=false`
- Medians and centroid remain separate from Core authority

## Evidence

Result hashes:

- `result.json`: `cedf6b20c36b99722b9d7f90f301d7289b938183a3ad201c8f8dd57aced88443`
- plan image: `8f6dcb645d2aca32a348faa3df88c7191376906dcea38e2dace81fd8430c6602`
- constructions: `6bf384e4b2029eb12587235b58132246b564b055ef2f75e625645c215827e936`

Acceptance report source:

- `/Users/pana/.codex/visualizations/2026/07/17/019f700d-eca4-72f1-b29e-052bb892370c/live-acceptance-report.md`
- section v6 around line 460

Held-out matrix artifacts:

- `/Users/pana/.codex/visualizations/2026/07/17/019f700d-eca4-72f1-b29e-052bb892370c/heldout-live-matrix/matrix-report.md`
- `/Users/pana/.codex/visualizations/2026/07/17/019f700d-eca4-72f1-b29e-052bb892370c/heldout-live-matrix/manifest.json`

Operational constraints preserved:

- no provider call
- no public deployment
- no secret, tunnel, app, profile, or permission change
- no second retry

## Postscript — 2026-07-18 personal MVP closure

- Core PR #244: reviewed head
  `303fd5145544596e153527db0869d7beeb27ad38`, merged as
  `0fec3e7d55eecbed41ec75f38660742c15ce19dc`.
- Private-widget UI PR #245: reviewed head
  `c7f0be117704248a2078d333e6f403ca16c9346e`, merged as current exact main
  `b93dbb824617b5624803a4a847ee164b7b1d3bf7`.
- Stable private runtime: byte-identical exact-main install, build PASS, suite
  `1707/1707`, `/healthz=live`, `/readyz=ready`, one bounded restart.
- Rollback snapshot:
  `/Users/pana/.local/share/norma-core-personal-runtime.rollback-20260718-pre-ui-b93dbb8`.
- Held-out matrix: `LIVE_MATRIX_PASS` for architecture/trapezoid,
  poster/refinement, and ambiguous negative; no Core bug reproduced.
- Live declared-ratio conversation:
  `https://chatgpt.com/c/6a5ac711-8864-83e9-a9e1-1a4aa797c10e`.
- Incomplete ratio selection disabled confirmation with an explicit recovery
  instruction; disabling the toggle immediately restored confirmation.
- After selecting `Trapèze principal · côté 3` and
  `Grande oblique · longueur du segment`, quadrilateral vertex 3 moved from
  SVG `cx=137.5` to `142.5`; both declared identities persisted and
  confirmation remained enabled.
- Exactly one confirmation/Core produced a separate `2/3` report:
  `406.787 px / 876.584 px`, dominant share `68.303%`, target `66.667%`,
  delta `1.637 pt`, with no Core authority.
- Hashes: result
  `dd9d78591397e65e0c146d4643ec3d0b1dbd90e27f72486dcedaf53aaa18d554`;
  plan image
  `c012b665025adf768a0b6da40065f30fec8b4da3886d3711fd5f0f5a98660e28`;
  declared ratio
  `6f28d751aaa7b2787bf86013da38bd80b367bab8178518c5b1dd4b9013344ca4`.

## Current Gate

The personal MVP is stable. The active gate is observation of real use:

- fix only a reproduced bug or demonstrated user need;
- keep geometric expansion stopped by default;
- require a new bounded contract and fresh evidence before any expansion;
- retain rhythms/repetitions, physical perspective/homography/rectification,
  circumcenter/incenter/orthocenter and other new centers, and new
  harmonic-report families as deferred nice-to-have work.

## Related

- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/tech/core-interface-boundary.md`
- `wiki/overview.md`
