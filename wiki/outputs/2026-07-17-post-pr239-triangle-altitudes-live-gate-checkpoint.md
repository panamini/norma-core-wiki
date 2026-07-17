---
title: "Post PR240 Triangle Truth Checkpoint"
category: output
status: current
created: 2026-07-17
updated: 2026-07-17
type: runbook
---

# Post PR240 Triangle Truth Checkpoint

## Context
Live triangle altitude evidence was recorded in ChatGPT after PR #239 merged
and after the dedicated triangle construction gate. PR #240 then merged the
bounded preparation diagnostic and this checkpoint records the deterministic
post-merge truth. It does not claim a post-PR240 live smoke or change core
geometry; it does not claim centroid, circumcenter, incenter, orthocenter,
rhythm, perspective, physical rectification, or harmonic interpretation.

## Result
- Status: `LIVE_TRIANGLE_ALTITUDES_PASS`
- ChatGPT URL: `https://chatgpt.com/c/6a596b18-c084-83e9-a179-e1cab9d1b094`
- Explicit canonical triangle: `1`
- Derived altitudes: `3`
- Parentage: all three altitudes share the same triangle parent
- Provenance: `derived-construction`
- sourceTruth: `false`
- Core authority: `none`
- UI dependency order: `Prolongements -> Triangles -> Hauteurs -> one explicit confirmation`
- Core/result layer: `HAUTEURS DÉRIVÉES / 3 droites`
- Result sha256: `4864a51fd21c1c63f025dcb425ce10f7198c70abfddd59cf916d39fc010d4240`
- Plan-image sha256: `bc1dd792b717287a0050f2617dad5419655da1143524fc81ff16414c1c8e9096`
- Constructions sha256: not directly recoverable from the supplied source facts
- Exclusions: no centroid, circumcenter, incenter, orthocenter, rhythm,
  perspective, physical rectification, or harmonic interpretation
- Real mobile ChatGPT and multiple live triangle-shape cases remain unverified
- Repo/task mutation: none during the test task

## Non-Goals
- This run does not modify code, wiki runtime, connectors, tunnels, app
  settings, secrets, or config.
- This run does not broaden into center selection, rhythm, perspective, or
  harmonic interpretation.

## Recommendations
- PR #240 is complete; the next application leaf is the read-only triangle-center
  assessment in core PR #241.
- The centroid is the first safe candidate only after assessment, with a separate
  overlay, `candidateEvidenceOnly=true`, `sourceTruth=false`,
  `coreAuthority=false`, and fail-closed validation. No center is implemented.
- Circumcenter, incenter, and orthocenter remain separate future decisions.
- Keep rhythm, perspective, physical rectification, and harmonic interpretation
  deferred.
- Real mobile ChatGPT and multiple live triangle-shape cases remain unverified
  but do not invalidate the passed gate.

## Post-PR240 diagnostic and smoke status
- Core merge: PR #240 at `1ecf1e4bc46c2292a688e5f0d06b7692e9a710fb`; reviewed head `e097e5434902bf883f88720ab12c2a3b2102ae8e`.
- Deterministic preparation proof: 0 requests report unavailable; 1 request with format-diagonal/junction reports the full conditional order; 2 requests report derived families unavailable; every pre-confirmation result has `coreRun=false`.
- Private smoke: `LIVE_NOT_RUN / VERIFICATION_BLOCKED / BLOCKED`. The existing runtime is detached at `b6352bd6d751cc25c6036c28b208f47b7dd0e0d8`, does not expose `triangleRequestCount`, and no safe target SHA is available. No provider, retry, tunnel, key, app, or public deployment was used.

## Verification
- The live run used the linked ChatGPT conversation with one explicit
  confirmation.
- The widget observed exactly one canonical triangle and exactly three
  altitudes.
- The widget reported the dependency order `Prolongements -> Triangles ->
  Hauteurs -> confirmation`, and the result layer reported `HAUTEURS DÉRIVÉES /
  3 droites`.
- The result and plan-image hashes above were captured from the live run.
- The full constructions hash was not directly recoverable from the supplied
  source facts and is intentionally omitted.

## Related
- `wiki/strategy/mvp-pr-roadmap.md`
- `wiki/overview.md`
- `wiki/hot.md`
- `wiki/tech/core-interface-boundary.md`
- `wiki/outputs/2026-07-16-triangle-constructions-live-gate-checkpoint.md`
- `wiki/outputs/2026-07-16-personal-visual-harmony-checkpoint.md`
