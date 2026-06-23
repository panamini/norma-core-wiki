# PR96 Norma Orchestrator v0 Raw Input

This staged note preserves the raw operational summary for the merged PR96 orchestrator work.

## Facts

- Repository: `panamini/norma-core`.
- PR: `#96 Add local Norma orchestrator v0`.
- Status: merged.
- Merge commit: `562959461566e6903b6cd2551667bd61bf1536de`.
- Head before merge: `712940e7b514a35e99bb9a76650f393fc6bcf457`.
- Changed files: 23.
- Diff size: +2255 / -2.
- CI status before merge: green.

## Added by PR96

- TypeScript/Node orchestrator under `tools/orchestrator/`.
- Repo-local Skill under `.agents/skills/norma-orchestrator/`.
- Example config `.orchestrator.example.json`.
- Orchestrator README.
- Orchestrator regression test file.
- Package scripts for doctor, context, validate, run, and test.

## Trust level

Current level: `L1_ADVISORY`.

Trusted for:

- context generation
- doctor checks
- validation planning
- dry-run evidence
- PR support

Not trusted for:

- autonomous implementation
- automatic wiki mutation
- automatic PR creation
- merge decisions
- source-of-truth decisions

## Note

This file was intentionally staged in `rawinput/` because the user asked for the orchestrator source material to be available as raw input too. A later ingest pass may move it to `raw/` if the vault owner wants rawinput cleaned.
