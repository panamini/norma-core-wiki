---
title: "Post-PR6 ChatGPT Secure MCP Tunnel Checkpoint"
category: output
status: current
created: 2026-06-24
updated: 2026-06-24
type: runbook
---

# Post-PR6 ChatGPT Secure MCP Tunnel Checkpoint

## Context

PR6 completed the private ChatGPT Secure MCP Tunnel smoke for the Norma Core MCP
tool.

## Result

- Status: `PR6_SMOKE_PASSED_CHATGPT_SECURE_MCP_TUNNEL`
- Base branch: `main-after-codex-mcp-tool`
- Merge commit: `658ea2069d1c6a65b23df7f43ba4c4ba96fd8a31`
- Tool: `norma.runMvpDemoV1`
- ChatGPT tunnel smoke: passed
- App state: private/dev only
- Tunnel state after test: stopped

## Secure tunnel setup path

Use this setup only for private Developer Mode testing. Keep tunnel IDs, runtime
keys, workspace IDs, tokens, cookies, and auth headers redacted in logs and
reports.

Known PR6 local inputs:

- Worktree: `/Volumes/video/git/norma-core-worktrees/codex-mcp-smoke`
- Base branch: `main-after-codex-mcp-tool`
- Merge commit: `658ea2069d1c6a65b23df7f43ba4c4ba96fd8a31`
- Tunnel profile: `norma-core-chatgpt-pr6`
- Tunnel client:
  `/Users/pana/Downloads/tunnel-client-v0.0.9--context-conduit-topaz/extracted/tunnel-client`
- Local MCP command:
  `/Applications/Codex.app/Contents/Resources/cua_node/bin/node /Volumes/video/git/norma-core-worktrees/codex-mcp-smoke/bin/norma-core-mcp-stdio.mjs`
- Local tunnel admin surface: `http://127.0.0.1:8080/ui`
- Health endpoints:
  - `http://127.0.0.1:8080/healthz`
  - `http://127.0.0.1:8080/readyz`

Repeatable tunnel preflight:

```sh
/Users/pana/Downloads/tunnel-client-v0.0.9--context-conduit-topaz/extracted/tunnel-client doctor \
  --profile norma-core-chatgpt-pr6 \
  --explain
```

Repeatable private tunnel run:

```sh
/Users/pana/Downloads/tunnel-client-v0.0.9--context-conduit-topaz/extracted/tunnel-client run \
  --profile norma-core-chatgpt-pr6
```

Expected local admin checks while the tunnel is running:

```sh
curl -fsS http://127.0.0.1:8080/healthz
curl -fsS http://127.0.0.1:8080/readyz
```

Expected ChatGPT Developer Mode connector state:

- Connection type: Tunnel
- Authentication: No Authentication
- Permission mode: Always ask
- App state: private/dev only
- Expected tool inventory: exactly `["norma.runMvpDemoV1"]`
- Public app submission: not part of PR6

## Secure tunnel teardown path

After testing, stop the screen-backed tunnel process if present:

```sh
screen -ls
screen -S <screen-id>.norma-pr6-tunnel -X quit
```

If the screen is gone but the local tunnel client is still listening, stop the
remaining local process:

```sh
ps aux | grep -F 'tunnel-client' | grep -v grep
kill <pid>
```

Teardown verification:

```sh
screen -ls
ps aux | grep -F 'tunnel-client' | grep -v grep || true
curl -fsS http://127.0.0.1:8080/healthz || true
```

Expected teardown state:

- No `norma-pr6-tunnel` screen remains.
- No `tunnel-client run --profile norma-core-chatgpt-pr6` process remains.
- `http://127.0.0.1:8080/healthz` does not respond.

## Local smoke checklist

Use this checklist before depending on ChatGPT Developer Mode behavior:

1. Confirm the worktree is on or contains merge commit
   `658ea2069d1c6a65b23df7f43ba4c4ba96fd8a31`.
2. Run `pnpm run build`.
3. Run `node --test tests/mcp-stdio-hardening.test.mjs`.
4. Run `node --test tests/mvp-demo-v1.test.mjs`.
5. Run `pnpm run check`.
6. Run `git diff --check`.
7. Run direct MCP stdio initialize smoke for `2025-03-26`.
8. Run direct MCP stdio initialize smoke for `2025-06-18`.
9. Confirm `tools/list` returns exactly `["norma.runMvpDemoV1"]`.
10. Confirm `norma.replayRun` is absent.
11. Confirm `tools/call` for `norma.runMvpDemoV1` returns the deterministic
    proof facts below.

No new compute logic is required for this checklist. It only verifies the
existing MCP transport/tool behavior and deterministic MVP demo output.

## Recommendations

- Do not publish the ChatGPT app as the next step.
- Do not submit the app publicly as the next step.
- Treat the next step as a small post-PR6 handoff/checkpoint or another
  explicitly scoped internal follow-up.
- Do not broaden into external integration, autonomous orchestrator promotion,
  or core geometry, measurement, evaluation, comparison, pack, ratio, artifact,
  or output behavior changes.

## Verification

Observed canonical smoke facts:

- `runRef`: `run:v1:5c6303f20c12537e`
- `measurementCounts`: `{ "a": 6, "b": 6 }`
- `decision.status`: `a_closer`
- `selectedComposition`: `composition:A`
- `replayReadiness.status`: `replay_ready`
