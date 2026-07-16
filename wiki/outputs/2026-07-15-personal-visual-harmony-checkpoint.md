---
title: "Personal visual harmony checkpoint"
category: output
status: current
created: 2026-07-15
updated: 2026-07-16
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
  - https://github.com/panamini/norma-core/pull/230
  - https://github.com/panamini/norma-core/pull/231
  - https://github.com/panamini/norma-core/pull/232
  - https://github.com/panamini/norma-core/pull/234
related:
  - wiki/strategy/mvp-pr-roadmap.md
  - wiki/tech/core-interface-boundary.md
---

# Personal visual harmony checkpoint

## Context

Norma Core `main` is current through PR #234 at merge commit
`d53357b7142dd83658a2ceffbf6b2cb50268d5eb`.

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
  and remain non-authoritative.
- PR #230 added the bounded deterministic rotated-ellipse refinement kernel.
  It searches center, axes, and orientation over immutable local luminance
  evidence, preserves the original ellipse separately, caps work at 214
  evaluations, and abstains fail-closed for weak, ambiguous, or
  orientation-degenerate evidence.
- PR #231 integrated that kernel into the private widget path. Refinement is
  disabled by default, the proposal has distinct rendering and identity, and
  adoption, confirmation, and Core execution remain separate explicit gates.
  Hydration now refreshes refinement controls immediately, while tolerant
  canonical-envelope validation preserves stale-payload rejection across the
  widget/server precision boundary.
- PR #232 synchronized the controlled same-image local A/B evidence and its
  exact changed-file guard. It does not change runtime behavior.

The PR #231 exact-head gate passed the build, focused rotated-refinement and
visual-harmony coverage (297/297), historical changed-file guards, and the
full repository suite (1672/1672). All three remote checks passed, review
threads were empty, and a fresh Codex review found no major issues on exact
final head `7fcbfa34e34a14d745bc961a573df1da7fb6044e`. Desktop and mobile local
widget smokes passed without console errors or horizontal overflow. The
exact-main desktop flow proved disabled-by-default refinement, a distinct
`REFINED` proposal, explicit adoption, no Core call before separate
confirmation, and a later verified Core result. The merge commit then passed
the build and five bounded integration regressions.

The controlled exact-main local A/B at
`9d49d15286d9be854243dc7cb4ca350d10073695` reused the same annotated
luminance rasters and starting candidates. The strong full-perimeter case
reduced mean annotated perimeter error from `1.657733384665 px` to `0 px` and
raised edge support from `0.486165660084` to `0.831046138518`. The nearby
tangent/crossing-line case reduced the same error to `0 px` and raised edge
support from `0.470385665047` to `0.783118773663`. Weak and competing-
orientation negatives abstained deterministically. Desktop/mobile local widget
smokes preserved original/proposal separation, explicit adoption, separate
confirmation, and zero Core calls before confirmation. This is
`LOCAL_UI_AB_PASS`.

The current private-app path can create and connect a temporary ChatGPT app to
the exact-main MCP server. The controlled same-image desktop run is now
`LIVE_CHATGPT_AB_PASS`; the local desktop/mobile widget run is
`LOCAL_UI_PASS`. Real mobile ChatGPT viewport proof remains unverified. No
provider or model API call was made. The temporary app, server, and tunnel were
removed. The Chrome file-URL permission was observed enabled for the live run
and is being restored to disabled. The two named temporary DNS aliases return no
authoritative records; no unrelated tunnel, parser.dasti.ai route, or Docker
service was changed.

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

Rotated-ellipse pixel refinement uses the same canonical major/minor-axis and
modulo-pi convention as confirmed ellipse geometry. Its bounded raster search
returns candidate evidence only with `sourceTruth=false` and no Core
authority. Near-circles preserve their admitted orientation or abstain; weak
or competing orientations fail closed. Proposal generation and adoption do
not confirm geometry or execute Core.

## Median completion

PR #234 is merged at `d53357b7142dd83658a2ceffbf6b2cb50268d5eb`. One explicit
canonical triangle derives exactly three opt-in vertex-to-opposite-side-midpoint
segments. Each carries stable triangle/vertex/side parent provenance and
`sourceTruth=false`; no centroid, bisector, center, automatic enumeration,
adoption, confirmation, or Core authority is introduced.

The median changeset passed build, 296/296 focused construction/MCP/HTTP/widget
and guard tests, 1678/1678 full tests, 3/3 remote checks, exact-head Codex
review, and 84/84 post-merge targeted regressions.

## Next gate

The live desktop same-image gate is complete. Keep `LOCAL_UI_PASS` and
`LIVE_CHATGPT_AB_PASS` separate; require future runs to preserve confirmation,
identity, cache, and Core output when a proposal is not adopted.

The next primitive remains a separate read-only assessment decision. Angle and
perpendicular bisectors, altitudes, triangle centers, rhythm, vanishing-point
inference, and harmonic interpretation remain deferred until that assessment.

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
- Application main after PR #230:
  `7eb6179972ea1f472c04256f6dcc90ee1ba6dcea`
- Application main after PR #231:
  `9d49d15286d9be854243dc7cb4ca350d10073695`
- Application main after PR #232:
  `c3f04cdf4d7451b0c8818e2c1ddb9ebf46976b08`
- Application main after PR #234:
  `d53357b7142dd83658a2ceffbf6b2cb50268d5eb`
- Provider/model calls: zero
- Public deployment or app submission: none
