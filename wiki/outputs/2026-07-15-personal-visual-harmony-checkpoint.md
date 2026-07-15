---
title: "Personal visual harmony checkpoint"
category: output
status: current
created: 2026-07-15
updated: 2026-07-15
type: analysis
sources:
  - https://github.com/panamini/norma-core/pull/221
  - https://github.com/panamini/norma-core/pull/222
  - https://github.com/panamini/norma-core/pull/223
  - https://github.com/panamini/norma-core/pull/224
  - https://github.com/panamini/norma-core/pull/225
  - https://github.com/panamini/norma-core/pull/226
  - https://github.com/panamini/norma-core/pull/227
  - https://github.com/panamini/norma-core/pull/228
  - https://github.com/panamini/norma-core/pull/229
related:
  - wiki/strategy/mvp-pr-roadmap.md
  - wiki/tech/core-interface-boundary.md
---

# Personal visual harmony checkpoint

## Context

Norma Core `main` is current through PR #229 at merge commit
`26cba06d76d8a6eeb56c0dd0035b0be24e47a388`.

## Result

- PR #221 merged the personal ChatGPT visual-harmony widget/MCP foundation,
  rectangle Core mapping, segment/axis/axis-aligned ellipse/quadrilateral
  guides, and deterministic image-plane measurements.
- PR #222 hardened exact-file hydration, retry/refresh, same-file changed
  payload, different-file reuse, and stale-payload protection.
- PR #223 added a deterministic shadow pixel-refinement kernel and a small
  synthetic corpus. At that checkpoint the kernel had no widget or
  candidate-preparation caller.
- PR #224 synchronized repository documentation and changed-file guards. It
  did not change runtime behavior.
- PR #225 integrated bounded, disabled-by-default pixel-refinement proposals
  into the private widget path. Original and proposed geometry stay separate,
  adoption requires its own explicit action, and confirmation/Core execution
  remain separate later gates. This is locally proved, not a live ChatGPT A/B.
- PR #226 added separately controlled support-line extensions and format
  diagonals. A user-confirmed observed segment remains finite observed
  geometry; its frame-clipped infinite support line and both corner-to-corner
  frame diagonals are deterministic derived constructions with no Core
  authority.
- PR #227 added a disabled-by-default junction-angle layer over confirmed
  support lines, enabled format diagonals, and confirmed frame edges. It
  reports deterministic pixel-scaled smaller and supplementary image-plane
  angles, participant provenance, and whether a support-line crossing lies
  within the originally observed segment. The layer requires support-line
  extensions and never becomes Core-authoritative geometry.
- PR #228 added a disabled-by-default triangle-construction layer for an
  explicit request containing exactly three stable, parented image-plane
  vertices. It canonicalizes winding and starting vertex, returns stable
  identity plus basic area/side/angle measurements, and fails closed on
  missing or stale parents, ambiguous or unsupported junctions, duplicates,
  bounds violations, and normalized or pixel-space degeneracy. Triangles are
  derived constructions only and never become source truth or Core input.
- PR #229 added explicit rotated ellipses with deterministic modulo-pi
  canonicalization, stable major/minor-axis and near-circle rules, accurate
  rotated overlay rendering, and rotation-aware image-plane line relations.
  Legacy axis-aligned inputs keep their established meaning and identity.
  Rotated ellipses remain confirmed image-plane guides outside Core authority,
  and rotated-ellipse pixel refinement remains disabled and deferred.

The PR #229 exact-head gate passed the build, focused visual-harmony/MCP tests
(75/75), changed-file guard (206/206), historical guard regressions, and the
full repository suite (1656/1656). All three remote checks passed, both review
findings were fixed and resolved, and a fresh Codex review found no major
issues on exact final head
`cf73965aad200616d80fac666a5196db5d75570b`. Desktop and mobile local widget
smokes passed without console errors or horizontal overflow. The merge commit
then passed the build and 75/75 bounded personal visual-harmony/MCP tests. A
temporary private ChatGPT app and tunnel reached the current app
management flow, but the image prompt produced no request at the exact-main
server and never reached the widget, confirmation, or Core result. Full live
ChatGPT hydration/write proof is therefore `UNVERIFIED`, not a live pass.

## Authority boundary

ChatGPT supplies typed image-plane candidates. The widget owns the hydrated
image and the server does not download image bytes. Core receives only
explicitly selected and confirmed structured geometry. Non-rectangle guides
remain image-plane evidence, and image-plane claims are not physical-plane,
harmonic, aesthetic, or artistic-intent claims.

Pixel-refined geometry is a separate proposal/evidence object, disabled by
default and adopted by a distinct explicit user action. It never replaces
original ChatGPT geometry, confirms a candidate, or runs Core automatically.
Observed line segments, derived support-line extensions, and derived format
diagonals also retain distinct provenance and authority. Junction angles are
derived measurements over those bounded constructions; they do not make an
invisible extension observed, infer intent, or authorize Core input. An
explicit triangle preserves the stable provenance of each of its three
vertices, remains derived/non-authoritative, and does not enumerate other
triangles or introduce harmonic classification. Explicit ellipse orientation
changes only deterministic image-plane geometry; it does not make an ellipse
source truth, physical-world evidence, or Core-authoritative input.

## Next gate

Add one bounded, disabled-by-default rotated-ellipse pixel-refinement shadow
slice. It must keep original and proposed ellipses separate, abstain on weak or
orientation-degenerate evidence, require an explicit adoption action, and
remain unable to confirm geometry or run Core. Keep medians, bisectors,
triangle centers, rhythm, vanishing-point inference, and harmonic
interpretation deferred.
Repeat the same-image disabled/enabled refinement A/B when the available
ChatGPT entitlement supports the full write path.

## Verification

- Application base before the documentation merge:
  `6a061dbb43496b6147f8ad2e35c8c8ffd8375c67`
- Application main after PR #224:
  `998bc2fcd8aa81e51bcd08af7d2bd0ec9cbfd2d2`
- Application main after PR #225:
  `02c344246f51207fe15dcc96f4b6e0d09c017b30`
- Application main after PR #226:
  `f333c9a3ee6e7034b59b03401362a2aec6ffe5ad`
- Application main after PR #227:
  `25810e39a01a65f9f2453f000d459633376c3419`
- Application main after PR #228:
  `22f4732fb4ce78347040285c956d283da8884eff`
- Application main after PR #229:
  `26cba06d76d8a6eeb56c0dd0035b0be24e47a388`
- Provider/model calls: zero
- Public deployment or app submission: none
