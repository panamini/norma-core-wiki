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
related:
  - wiki/strategy/mvp-pr-roadmap.md
  - wiki/tech/core-interface-boundary.md
---

# Personal visual harmony checkpoint

## Context

Norma Core `main` is current through PR #227 at merge commit
`25810e39a01a65f9f2453f000d459633376c3419`.

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

The PR #227 exact-head gate passed the build, focused visual-harmony and
changed-file tests (269/269), historical exact-guard regressions (347/347),
the full repository suite (1642/1642), the static widget harness, and a local
Streamable HTTP MCP smoke. All three remote checks passed and a fresh Codex
review found no major issues on exact head
`721b2d5716f3707d84e0fd85d1517ce62c165b8d`. The post-merge bounded rail
passed the build and 65/65 personal visual-harmony/MCP tests. A temporary
private ChatGPT app and tunnel reached the current app
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
invisible extension observed, infer intent, or authorize Core input.

## Next gate

Add one opt-in triangle-construction slice from three explicit confirmed or
deterministically derived image-plane vertices after validating distinct
vertices, non-zero area, stable ordering, and parent provenance. Keep triangle
construction outside Core authority and leave medians, bisectors, centers,
rhythm, vanishing-point inference, and harmonic interpretation deferred.
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
- Provider/model calls: zero
- Public deployment or app submission: none
