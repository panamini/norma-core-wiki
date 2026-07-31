---
title: "Post-PR299 local CV candidate truth sync"
category: output
status: current
created: 2026-07-31
updated: 2026-07-31
tags:
  - web-lab
  - local-cv
  - provenance
  - mcp
  - chatgpt
  - truth-sync
type: checkpoint
related:
  - "[[../strategy/mvp-pr-roadmap]]"
  - "[[../tech/core-interface-boundary]]"
---

# Post-PR299 local CV candidate truth sync

## Exact merged sequence

The active Norma Core `main` line now includes the measured private Web Lab
sequence below. The merge commit and PR links are the publication authority;
the descriptions summarize the merged titles and active changed surfaces.

| PR | Merged commit | Merged scope |
| --- | --- | --- |
| [#291](https://github.com/panamini/norma-core/pull/291) | `b70ba98256cf6799988b00c20c6556a9d9c7a1ae` | Measurable visual-review UX, review journal, MCP review smoke, and audit-oriented evidence. |
| [#292](https://github.com/panamini/norma-core/pull/292) | `f95fab3de2cd2e88be1eb4b7975939c6a8fa8507` | Private visual-measurement Web Lab shell, server boundary, browser model, styles, and contract tests. |
| [#293](https://github.com/panamini/norma-core/pull/293) | `3621d66a0149879fd672f728bb4cace83d6a71df` | Manual geometry authoring and its provider-neutral candidate flow. |
| [#294](https://github.com/panamini/norma-core/pull/294) | `af7d9e2c03caec78bfee760f72a8d1b61909ddb4` | Precise manual geometry editing and rendered browser coverage. |
| [#295](https://github.com/panamini/norma-core/pull/295) | `24b6ffe7f3e63c938a71ced5f623baf754c590ce` | Safe confirmed-result presentation and canonical receipt order. |
| [#296](https://github.com/panamini/norma-core/pull/296) | `b18a382a2bcae8a134a8cc1c3333486d609b9bcb` | Linked review-session recovery, stale-session handling, and launcher hardening. |
| [#297](https://github.com/panamini/norma-core/pull/297) | `8140f98d38c3c4305796d5b94ab78c07fbcd6cdc` | Declared spatial measurements between two explicitly confirmed rectangles. |
| [#298](https://github.com/panamini/norma-core/pull/298) | `a37380177e0f13cb6324f2aa3d4f90eb995d12c0` | Guided spatial picker UX and accessible candidate/order selection. |
| [#299](https://github.com/panamini/norma-core/pull/299) | `c0cc5183664648a11da8775abe8cd1a49ce91a51` | Browser-local deterministic CV candidate proposals, provenance, worker bounds, and fail-closed integration. |

PR #299's merged head was `bbc6c6201bbf890a1662bcb59baaf24534407472`.
Its merge added no new Core geometry authority, provider, MCP tool, package
dependency, SAM/VLM path, or frontend framework.

## Local CV boundary

Local CV is a browser-local candidate source. The image is decoded into bounded
browser raster/worker state; image bytes and crops are not sent to the server.
Each proposal remains an editable, deselectable candidate with explicit
`browser-local-cv` provenance. Proposals are unchecked by default and cannot
reach Core until the user includes them, prepares the linked review, and makes
the separate confirmation decision. Provenance binds the source image/session,
worker run and raster, proposal identity, original geometry, edits, selection,
receipt, and composite export identity. Stale, mismatched, tampered, timed-out,
or failed worker state abstains and leaves the manual path available.

The product answer is explicit: local CV complements the MCP/ChatGPT workflow;
it does not replace it and does not require disabling GPT, VLM, or SAM. MCP and
ChatGPT remain separate interaction/provider candidate sources, while Core
continues to receive only explicitly confirmed structured geometry.

Manual-only sessions remain free of local-CV fields. No provider, SAM, VLM,
OpenCV, or new frontend framework is part of this merged rail.

## Post-merge qualification evidence

- GitHub reports PR #299 merged at `2026-07-31T17:31:05Z`; `verify`, Semgrep
  CE, and Semgrep cloud checks passed on the PR.
- A rendered Chrome run against the merged PR #299 content reproduced one
  stale exact-string assertion in the existing recovery test. The runtime
  behavior was the intended `Incluez ou tracez…` wording; no CV or Core defect
  was reproduced. The one-line test-only alignment is isolated in corrective
  [PR #300](https://github.com/panamini/norma-core/pull/300), which is open and
  not part of merged `main` yet.
- After that isolated correction, the targeted scenario passed; the rendered
  Web Lab suite passed `22` with `1` intentional skip; and the full local check
  passed `2015` tests with `6` skips. These are qualification evidence for the
  merged runtime plus the pending test correction, not a claim that PR #300 is
  already merged.
- The browser benchmark recorded five warmups and thirty measured runs with
  no precision claim: p50/p95 were `2.2/2.9 ms` at `256x256`, `5.7/7.6 ms` at
  `512x512`, and `7.4/8.4 ms` at `640x640` on the observed headless Mac
  Chrome. These are machine-specific observations, not product SLOs.
- The repository contains one licit image fixture, `golden-split-poster.png`.
  A multi-image real-user matrix remains unverified until additional authorized
  fixtures are supplied; no broad accuracy claim is made.

## Next gates

1. Merge/reverify the focused PR #300 test correction if its checks stay green.
2. Run a separately recorded live matrix on multiple authorized real images,
   covering frames, lines, candidate selection/editing, two-frame measurement,
   confirmation, receipt, and export.
3. Only if that observation demonstrates a product gap, define a bounded PR10
   for two semantic candidate objects and their image-plane measurements. Keep
   it candidate-only, provenance-bound, explicitly confirmed, and outside Core,
   ratio, and scoring changes.
4. Consider a separate, optional PR11 only if the picker remains too technical;
   object-oriented presets must preserve the same candidate and confirmation
   boundaries.
5. Keep on-device SAM as a separate benchmark/privacy decision. Do not add a
   dependency or provider path merely because PR10 or PR11 is contemplated.

This checkpoint does not authorize production deployment, provider selection,
MCP contract changes, Core changes, or automatic geometric expansion.
