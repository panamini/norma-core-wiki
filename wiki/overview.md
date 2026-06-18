---
title: "Overview"
category: overview
status: current
created: 2026-06-11
updated: 2026-06-17
---

# Overview

Norma Core vault is now at the durable layer.
Raw inputs have been ingested into `raw/`, source summaries live in `wiki/sources/`, and canonical durable pages were promoted under `product`, `tech`, `strategy`, `meta`, and `concepts` after PR0 ingest waves.

## Current State
- Norma Core is treated as a deterministic proportional engine with immutable structured inputs.
- Interfaces/adapters are clients of the engine; they must not change geometric rule semantics.
- MVP is gated to V1 deterministic composition evaluation.
- PR roadmap remains sequence-based: spec freeze → core skeleton → contracts → geometry → pack/rules → construction → measurements → evaluation/comparison → artifacts → replay envelope → demo harness.
- A later continuation prompt now exists for the PR66–PR70 local viewer path, but it is still only a planning artifact.
- Raw staging in `rawinput/` has been processed and cleaned twice; additional PR0 controls were promoted in the latest wave.
