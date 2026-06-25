---
title: "R6D ChatGPT Meta Connector Checkpoint"
category: output
status: current
created: 2026-06-25
updated: 2026-06-25
type: runbook
---

# R6D ChatGPT Meta Connector Checkpoint

## Context

PR113 closed the current-main ChatGPT connector compatibility blocker caused by
reserved MCP `_meta` fields.

This checkpoint records the private ChatGPT connector smoke state after PR113.
It is a handoff checkpoint, not a new product/code milestone.

## Result

- Status: `R6D_CHATGPT_META_COMPAT_PASSED`
- PR: `#113`
- Branch: `codex/r6d-chatgpt-meta-compat`
- Head commit: `fe7869cc7e26654f30f254cd3e2bf448ce5e71b0`
- Merge commit: `bba597bca40facaf36fd7741712a0b0b9d8754e6`
- Private ChatGPT connector smoke: passed
- Public app submission: not performed
- Hosted MCP endpoint: not implemented

## Observed Smoke Facts

- ChatGPT connector schema exposed exactly the current six tools:
  - `norma.getVersion`
  - `norma.serializeCanonicalJson`
  - `norma.verifyRun`
  - `norma.verifyArtifactFreshness`
  - `norma.replayMvpDemo`
  - `norma.analyzeStructuredCompositionV1`
- Positive `norma.getVersion` call succeeded.
- Positive `norma.replayMvpDemo` call succeeded.
- Replay verification status was verified / replay eligible.
- Replay readiness was ready.
- Selected evaluation refs included `evaluation:A:basic-grid-alignment`.
- The `_meta` blocker was fixed at the MCP envelope boundary.
- Root `_meta` on `tools/list.params` and `tools/call.params` is tolerated.
- Root `arguments._meta` is stripped before tool-specific validation.
- Nested structured `_meta` remains rejected.
- Unknown root or argument keys still fail with `-32602 Invalid params`.

## Negative Prompt Guardrails

No Norma analysis tool call was made for prompts that violated the structured
input boundary:

- image/layout alignment request without explicit structured geometry;
- beauty judgment or creative recommendation request;
- prose-only geometry inference request.

These remain outside the Norma Core guardrails.

## Non-Goals

This checkpoint does not authorize:

- public ChatGPT app submission;
- hosted or always-on MCP;
- outputSchema follow-up work;
- ChatGPT Analyze expansion;
- image, prose, or vision-based geometry inference;
- beauty scoring, recommendation, optimization, or intent inference;
- changes to core geometry, packs, ratios, rules, measurements, evaluation,
  comparison, artifacts, or deterministic outputs.

## Next Step

Immediate next step after this checkpoint:

```text
R1 - Reject duplicate geometry source identities
```

Do not start outputSchema, ChatGPT Analyze expansion, hosting, or publishing
before R1 unless a later explicit roadmap decision changes the sequence.
