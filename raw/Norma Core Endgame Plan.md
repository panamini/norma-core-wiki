Here is the **copy-paste prompt** I would put into a fresh ChatGPT session (or your wiki) to continue efficiently from where we are:

---

# NORMA CORE — CURRENT ENDGAME PLAN (POST-PR64 / PR65)

## Context

Repo:

```txt
panamini/norma-core
```

Current state:

```txt
PR63 merged:
- onboarding docs
- examples docs

PR64 merged:
- beta pilot readiness approval

PR65 open/merged state must be verified:
- privacy security support approval boundary
```

Goal:

```txt
Finish a real usable local application as efficiently as possible.

Prefer:
- real code
- real files
- real tests
- real fixtures

Avoid:
- endless documentation-only PRs

Keep:
- source-truth guarantees
- visibility guarantees
- existing guardrails
```

---

# MUST READ FIRST

Read these documents before proposing anything:

## Product readiness

```txt
docs/decisions/2026-06-16-read-only-result-viewer-product-requirements.md
docs/plans/2026-06-16-read-only-result-viewer-plan.md
```

## Structured JSON viewer

```txt
docs/decisions/2026-06-16-structured-json-input-viewer-prototype-approval.md

src/structured-json-input-viewer.ts
tests/structured-json-input-viewer.test.mjs
```

## Verification/replay viewer

```txt
docs/decisions/2026-06-17-verification-replay-result-viewer-prototype-approval.md

src/verification-replay-result-viewer.ts
tests/verification-replay-result-viewer.test.mjs
```

## Onboarding/examples

```txt
docs/decisions/2026-06-17-onboarding-examples-approval.md

docs/onboarding/README.md

docs/examples/read-only-result-viewer-workflow.md
docs/examples/structured-json-input-viewer.md
docs/examples/verification-replay-result-viewer.md
```

## Beta readiness

```txt
docs/decisions/2026-06-17-beta-pilot-readiness-approval.md
```

## Privacy/security/support

```txt
docs/decisions/2026-06-17-privacy-security-support-approval.md
```

## Roadmap

```txt
docs/BUSINESS_READINESS_ROADMAP.md
```

---

# IMPORTANT STRATEGIC DECISION

Do NOT continue a long sequence of policy-only PRs.

The objective is now:

```txt
Move from approvals -> real implementation.
```

We already have enough approvals.

---

# TARGET ENDGAME

## PR66 — Local Viewer UI Approval

Approval-only.

Purpose:

Approve exact implementation locations for the local app.

Expected future paths:

```txt
src/local-viewer/read-only-viewer-model.ts
tests/read-only-viewer-model.test.mjs

viewer/read-only-result-viewer.html
viewer/read-only-result-viewer.js
viewer/read-only-result-viewer.css

tests/read-only-viewer-static.test.mjs
```

No implementation yet.

Just approve paths and boundaries.

Constraints:

```txt
local only
no deployment
no server
no API
no remote MCP
no package exports
no dependencies
no public npm
no real user data
no file reads
no URL fetch
no shell/env
paste-only JSON
displayability != validation
```

---

## PR67 — Read-Only Viewer Model

Real code.

Files:

```txt
src/local-viewer/read-only-viewer-model.ts
tests/read-only-viewer-model.test.mjs
```

Consumes:

```txt
StructuredJsonInputDisplayModel
VerificationReplayResultViewerDisplayModel
```

Outputs:

```txt
UI-friendly state
```

Must expose:

```txt
status
diagnostics
warnings
errors
mismatches
provenance
source refs
output refs
artifact freshness
operation context
pack locks
tolerance policy
serialization version
operation version
result identity
unknown fields
```

No execution.

No source-truth inference.

---

## PR68 — Local Static Viewer

Real UI.

Files:

```txt
viewer/read-only-result-viewer.html
viewer/read-only-result-viewer.js
viewer/read-only-result-viewer.css

tests/read-only-viewer-static.test.mjs
```

Capabilities:

```txt
paste JSON
inspect
render sections
show warnings
show errors
show mismatches
show provenance
show unknown fields
```

No backend.

No deployment.

No network.

No server.

---

## PR69 — Real Fixtures

Files:

```txt
tests/fixtures/viewer/run-verification.json
tests/fixtures/viewer/run-replay-mismatch.json
tests/fixtures/viewer/artifact-freshness-stale.json
tests/fixtures/viewer/unsupported-prompt-input.json

tests/read-only-viewer-fixtures.test.mjs
```

Purpose:

Real examples.

Real validation.

Real regression protection.

---

## PR70 — Final Local Demo Readiness

Checkpoint only.

Verify:

```txt
viewer works
fixtures pass
onboarding exists
examples exist
no deployment
no real user data
no remote MCP
no public API
```

---

# RULES

Always:

```txt
Read real files before proposing changes.

No general audit.

No refactor.

One PR at a time.

Use actual repo state as source of truth.

If unverified:
write Unknown.
```

Never introduce:

```txt
camera/image/vision
CAD
plugin
marketplace
beauty score
creative recommendation
intent inference
prompt-as-source
artifact-as-source
source-truth inference
arbitrary replay
norma.replayRun
/replay-run
```

---

# NEXT TASK

Prepare:

```txt
PR66 — local read-only viewer UI approval
```

Deliver:

```txt
READY_TO_IMPLEMENT or BLOCKED

Exact scope
Branch
Files
Anchors
Tests
Validation
Acceptance criteria
Risks
Rollback
PR body
```

Do not edit files until explicitly told:

```txt
execute
```

---

That is the plan I would use to finish the app efficiently while preserving the benefits of the existing architecture and documentation.
