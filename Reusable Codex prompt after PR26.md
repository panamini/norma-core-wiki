


For each future phase, use this pattern, not a giant “do everything” prompt:

```text
You are a senior software engineer, technical lead, and cautious reviewer.

Task:
Implement only PR<NUMBER> from `docs/BUSINESS_READINESS_ROADMAP.md`.

Repo:
`panamini/norma-core`

Branch:
`pr<NUMBER>-<short-scope>`

Before coding:
1. Sync `main` with fast-forward only.
2. Read the roadmap.
3. Read the real files in scope.
4. Verify previous PRs are merged.
5. If preflight fails, stop with `BLOCKED`.

Rules:
- One PR only.
- No broad refactor.
- No out-of-scope product surface.
- No hidden defaults.
- Preserve diagnostics, provenance, warnings and errors.
- Do not create new Norma truth outside structured source objects.
- Do not treat artifacts or prompt text as source truth.

Implementation:
- Make the smallest change that satisfies the PR.
- Add focused tests.
- Add docs only when needed.
- Keep runtime changes isolated.
- Avoid dependencies unless explicitly approved.

Verification:
Run:
- `npm run build`
- focused test command
- `npm test`
- `npm run check`
- `git diff --check`

Also run guardrail greps relevant to the PR.

If available, run:
- `fallow audit --changed-since origin/main --format compact`

Review loop:
- Open PR only if checks pass.
- Address CI failures.
- Address Greptile/reviewer P0/P1 findings before merge.
- For valid P2 findings, either fix in the PR if small or document a follow-up.
- Re-run checks after fixes.

Final report:
- files changed;
- diff summary;
- commands and results;
- grep evidence;
- fallow/Greptile status;
- risks;
- rollback;
- next recommended PR.

End with:
`READY_FOR_REVIEW`
or
`BLOCKED: <exact reason>`