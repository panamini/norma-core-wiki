---
title: "SAM 3 Modal perception pipeline"
category: tech
status: current
created: 2026-07-28
updated: 2026-07-28
tags:
  - sam3
  - modal
  - perception
  - chatgpt
  - railway
sources:
  - https://github.com/panamini/norma-core/pull/281
  - https://github.com/panamini/norma-core/pull/282
  - https://github.com/panamini/norma-core/blob/main/docs/howto/modal-sam3-perception-sandbox.md
  - https://github.com/facebookresearch/sam3/tree/46957e47805eaa273f4aa7bbbd25a88bca9108ce
related:
  - wiki/tech/core-interface-boundary.md
  - wiki/tech/compute-topology-optional-gpu-escape-hatch.md
  - wiki/howto/personal-visual-harmony-quick-start.md
  - wiki/strategy/mvp-pr-roadmap.md
  - wiki/outputs/2026-07-28-sam3-modal-widget-checkpoint.md
---

# SAM 3 Modal perception pipeline

SAM 3 is an optional, replaceable perception provider for candidate discovery.
It does not define Norma geometry, confirm a candidate, select a ratio, or run
Norma Core. The current implementation is a sandbox/private-app path, not a
production provider lock.

## Current state

- Norma Core PR #281 merged the authenticated SAM 3 perception boundary at
  `83b0dc3c919f763e89f5250d95048b0fa8621752`.
- PR #282 merged the Modal runtime dependency packaging fix at
  `328f09d3689dcdef88448b54458d7da61a3f094e`.
- The current repository main after the widget compatibility sequence and the
  PR #288 two-length selector fix is
  `ea12c967bbd7c3acfd8401e5d75dd6f59e8d07e4`.
- The provider implementation supports interactive point/box prompts and
  bounded text prompts. The current widget exposes only the interactive path:
  it derives a point or box from an existing selected candidate.
- A free-text target such as `personne`, `arche`, or `fenêtre` is not yet
  exposed in the widget.
- A fresh ChatGPT widget has loaded and remained editable after the PR
  #283–#287 resource/remount corrections. A successful SAM inference receipt
  was not captured in the same observation, so live mask quality, latency, and
  subject recall remain unproven.

## End-to-end path

```text
ChatGPT image
  -> typed automatic candidates
  -> exact-file widget hydration
  -> optional local pixel proposals
  -> optional SAM 3 start action
  -> authenticated Railway MCP boundary
  -> ephemeral Railway perception job
  -> authenticated Modal Server
  -> pinned Meta SAM 3 model and checkpoint
  -> bounded mask response
  -> deterministic mask-to-primitive extraction
  -> editable candidate evidence and receipt
  -> explicit human confirmation
  -> structured geometry only
  -> deterministic Norma Core
```

The image can be observed by the optional perception provider only after the
user starts the SAM action. The resulting mask and primitive remain candidate
evidence until the user verifies and confirms them.

## Modal boundary

- Workspace/environment: `panamini` / `main`
- App: `norma-sam3-perception`
- Secret name: `norma-sam3-hf`
- Secret key contract: `HF_TOKEN`
- Model: `facebook/sam3`, checkpoint file `sam3.pt`
- Meta code revision:
  `46957e47805eaa273f4aa7bbbd25a88bca9108ce`
- Checkpoint revision:
  `3c879f39826c281e95690f02c7821c4de09afae7`
- Runtime: Python 3.12, pinned PyTorch/CUDA dependencies, one L4 sandbox GPU
- Storage: no Modal Volume, Dict, or durable image/job store

The Modal Server is authenticated. Its proxy-token secret belongs only in the
Railway sandbox secret manager. The Hugging Face token remains only in the
Modal Secret. Neither value belongs in Git, the wiki, tickets, chat, logs, or
local fixtures.

## Railway configuration contract

The provider is enabled only when all four sandbox variables are present:

- `NORMA_PERSONAL_VISUAL_HARMONY_SEGMENTATION_URL`
- `NORMA_PERSONAL_VISUAL_HARMONY_MODAL_KEY`
- `NORMA_PERSONAL_VISUAL_HARMONY_MODAL_SECRET`
- `NORMA_PERSONAL_VISUAL_HARMONY_SOURCE_IMAGE_ALLOWED_ORIGINS`

All four absent means disabled. Partial configuration fails startup. The origin
allowlist contains credential-free HTTPS origins only, never complete signed
download URLs.

## Safety and determinism

- The source image is identity-bound, size-bounded, downloaded into memory,
  normalized to at most 512 x 512, and not persisted.
- Readiness may use at most three bounded probes during cold start.
- The inference POST is sent exactly once and is never replayed after timeout,
  connection loss, 503, or preemption.
- Jobs are subject/session/source-bound, process-memory-only, capacity-bounded,
  and TTL-bound.
- Provider responses and mask payloads are bounded and schema-validated.
- Receipts preserve provider/model/prompt provenance without granting source
  truth or Core authority.
- Raw images, prompts, signed URLs, provider bodies, credentials, and database
  contents must not enter application logs.

## Prompt paths

The provider contract already accepts:

- an interactive prompt containing include/exclude points and an optional box;
- a bounded text prompt.

The widget currently selects one existing candidate and sends an interactive
point/box prompt. This can refine or segment around known geometry but does not
provide a semantic target for an omitted subject such as a person.

The next semantic-discovery slice should expose one short, explicit target
field or a few target chips. It must remain one user action, one inference,
candidate-only, redacted, and separately confirmed. Prompt text must never
become geometric source truth.

## Rollback

1. Remove all four Railway sandbox variables together.
2. Restart only the Railway sandbox.
3. Roll back or stop `norma-sam3-perception` in Modal if needed.
4. Revoke the dedicated Modal proxy token.
5. Keep `norma-sam3-hf` intact unless credential rotation is separately
   authorized.

The ChatGPT automatic-candidate path and deterministic Core remain available
when SAM 3 is disabled.

## Evidence boundary

Repository contracts, tests, and merged implementation prove the provider
boundary and failure behavior offline. The fresh widget observation proves
that the current ChatGPT review UI can hydrate and remain editable. It does not
yet prove a successful live SAM receipt, person detection, model quality,
Railway-to-Modal latency, GPU cold-start distribution, or production
readiness.
