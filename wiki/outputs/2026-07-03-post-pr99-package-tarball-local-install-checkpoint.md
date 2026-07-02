---
title: "Post-PR99 package tarball local install checkpoint"
category: output
status: current
created: 2026-07-03
updated: 2026-07-03
type: analysis
---

# Post-PR99 Package Tarball Local Install Checkpoint

## Context

Norma Core PR #179 / PR99, "PR99: prepare package tarball and local install
proof", merged on 2026-07-02 at
`82b125d52e16760e58fb7db6928702269d03bb19`.

Verified identity:

- PR URL: `https://github.com/panamini/norma-core/pull/179`
- PR head: `97d1d255ab1fcc7b039524ac8ca819a31b11543a`
- Merge commit / current Norma Core `main`:
  `82b125d52e16760e58fb7db6928702269d03bb19`

## Result

PR99 prepared the local `@norma/core` package tarball boundary and proved local
packed-tarball install/import.

The current package state at the PR99 merge commit remains private and
pre-publication:

- package name: `@norma/core`
- `private: true`
- version: `0.1.0`
- package-root export remains bounded to the built root entrypoint
- package metadata implementation is limited to the `files` allowlist:
  - `dist/src/**/*.d.ts`
  - `dist/src/**/*.js`
  - `README.md`

`result.json` remains canonical Norma truth. `guide.html`, `report.html`,
`visual.svg`, `summary.json`, and `summary.md` remain derived local inspection
artifacts only.

## Non-changes

PR99 did not:

- publish the package;
- tag or release a version;
- configure npm authentication;
- set provenance;
- add a release workflow;
- change dependencies or lockfiles;
- add a package-level `bin`;
- unlock hosted MCP, ChatGPT connector runtime, provider calls, API runtime, or
  adapters;
- approve public npm publication.

## Remaining blocked surfaces

Still blocked until a later explicit maintainer-approved operation:

- actual npm publication;
- registry authentication and provenance;
- release tagging and release workflow;
- hosted or remote MCP;
- ChatGPT connector runtime;
- provider, image, CAD, Figma, file, URL, or media adapters;
- inference, recommendation, optimization, correction, scoring, automatic
  family selection, or artifact-derived source truth.

## Recommendations

The next compressed Norma Core code PR is PR100: finalize the package
publication candidate without publishing.

PR100 should verify that the package candidate is publication-ready while still
preserving `private: true` unless explicit maintainer approval authorizes an
actual publication operation. Public npm publication remains a separate
maintainer-approved action, not an implied follow-up from PR99.

## Verification

Wiki sync evidence for this checkpoint:

- live PR state checked through GitHub: PR #179 is merged;
- live Norma Core `main` checked at
  `82b125d52e16760e58fb7db6928702269d03bb19`;
- live `package.json` at the merge commit checked for `private: true`, version
  `0.1.0`, root export, and minimal `files` allowlist;
- wiki update kept to durable/control pages and this output checkpoint.
