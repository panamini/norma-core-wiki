# 

## 🎯 Objectif

Transformer les PRs en **système déterministe avec dépendances vérifiées**, pas en liste de tâches.

---

# 🧠 1. Vue globale (graph)

```
PR0  → Spec Freeze (LOCK)  ↓PR1  → Toolchain + CI baseline  ↓PR2  → Geometry identity correctness (P1 FIX)  ↓PR3  → Local MVP Proof Kit (manual execution)  ↓PR4  → MCP STDIO safety (transport hardening)  ↓PR5  → MCP tool exposure (Codex entry point)  ↓PR6  → ChatGPT MCP integration (optional external layer)
```

---

# 🔥 2. Dependency rules (IMPORTANT)

## Hard dependencies

```
PR2 depends on PR1 passing CIPR3 depends on PR2 correctness stablePR4 depends on PR3 working demo (baseline needed)PR5 depends on PR4 safe MCPPR6 depends on PR5 tool stability
```

---

# 🧱 3. Execution gates (CRITICAL)

## PR1 gate

```
BUILD_GREENCHECK_GREENNO_NPM_DEPENDENCYCI_REPRODUCIBLE
```

---

## PR2 gate

```
duplicate IDs rejectedvalid compositions unchangedmeasurement determinism preservedNO CORE BEHAVIOR DRIFT
```

---

## PR3 gate

```
pnpm demo:mvp worksresult.json existsreport.html generateddeterministic outputsno framework added
```

---

## PR4 gate

```
MCP cannot crash processdepth protection worksbyte limits enforcedidempotent error handlingtools/list blocked (or controlled)
```

---

## PR5 gate

```
norma.runMvpDemoV1 exposedMCP == CLI parityno duplication of core logicread-only tool
```

---

## PR6 gate

```
ChatGPT can call MCP tooloutputs identical to CLIsecure tunnel onlyno new compute logic
```

---

# 🧠 4. Architecture separation (VERY IMPORTANT)

## Core truth hierarchy

```
1. src/ (CORE LOGIC) → never touched by PR4–PR62. measurements/evaluation → PR2 boundary only3. MCP layer → PR4–PR5 only4. external integration → PR6 only
```

---

## Forbidden cross-layer actions

```
PR4/PR5/PR6 MUST NOT:- modify geometry logic- modify measurement logic- modify evaluation logic- change packs/ratios- alter deterministic output rules
```

---

# ⚠️ 5. Drift prevention rules

## If PR touches wrong layer → STOP

```
IF PR5 modifies geometry → BLOCKIF PR4 modifies core logic → BLOCKIF PR6 modifies MCP tool logic → BLOCK
```

---

# 🧭 6. Correct execution strategy

## The ONLY safe flow

```
PR4 must be merged first→ then PR5 can expose tool→ then PR6 can integrate external system
```

No parallel PR5/PR6 work.

---

# 🔒 7. System invariants (non-negotiable)

```
- determinism always preserved- same input → same output- no hidden defaults- no implicit packs- no runtime inference- no UI dependency anywhere in PR1–PR5
```

---

# 🧪 8. Testing hierarchy

## PR3 becomes baseline truth

```
pnpm demo:mvp = GOLDEN EXECUTION PATH
```

All PRs must preserve it.

---

## PR4 adds system-level safety tests

- crash resistance
- malformed input recovery
- process survival

---

## PR5 adds tool-level parity tests

- MCP == CLI identical output

---

## PR6 adds external parity tests

- ChatGPT == MCP == CLI

---

# 🧠 9. Critical insight (very important)

Tu construis en réalité 3 couches :

```
CORE (PR1–PR3)TRANSPORT (PR4–PR5)INTEGRATION (PR6)
```

---

# 🚀 10. Final execution rule

## Never mix layers

```
If a PR touches more than 1 layer → INVALID DESIGN
```

---

# 🧭 11. Recommended execution order (clean)

```
1. finish PR4 fully2. stabilize MCP3. validate PR3 again4. implement PR5 minimal tool exposure5. only then consider PR6
```

---

# 🟢 Final system state target

After PR6:

```
Norma Core =✔ deterministic engine✔ CLI execution✔ MCP tool exposure✔ ChatGPT integration✔ identical outputs across all layers
```