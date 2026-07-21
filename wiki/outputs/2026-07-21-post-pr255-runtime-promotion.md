---
title: "Post-PR255 Runtime Promotion"
category: output
status: current
created: 2026-07-21
updated: 2026-07-21
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

One fresh ChatGPT conversation was opened for a distinct local image,
`DSC09546.jpeg`, and the reasoning level was changed from `Très élevée` to
`Moyenne`; `Pro` was not selected. The Chrome extension did not open the file
chooser. Therefore the evidence count is:

- fresh conversations opened: 1;
- images accepted by ChatGPT: 0;
- Norma preparations accepted: 0;
- confirmations/Core runs: 0;
- provider API calls: 0;
- automatic retries: 0;
- documented surface recoveries consumed: 1.

This is a Chrome/ChatGPT upload-surface block, not a reproduced Norma product
defect. No candidate, latency, editability, usefulness, result hash, or report
claim is available for this unaccepted case.

## Recommendation

Enable Chrome file-URL access for the ChatGPT extension, then execute exactly
one fresh `Moyenne` conversation with `DSC09546.jpeg` and the exact request
`Analyse cette image avec Norma`. Record one preparation and at most one
confirmation/Core; do not add geometry or harmonic packs before that evidence.

