---
doc: ADR-009
title: Workout, Block, Round, Set vocabulary
status: Accepted
date: 2026-11-07
source: D-09
---

# ADR-009 · Workout, Block, Round, Set vocabulary

## Context

The vision, requirements, UI and tests need one consistent language. The brief gives the reason and the origin: one consistent language across vision, requirements, UI and tests (P0.1 stage 3).

## Decision

One vocabulary is used in every doc, the UI and the tests:

**Workout** (1, 2, 3) → **Block** (A, B, C) → **Round** (one pass through a block) → **Set** (one exercise performed once, in one round).

Done or skipped is marked explicitly at set, round and block level. Nothing is pre-selected.

## Consequences

- Every document, the UI and the tests use these four terms.
- Marking is explicit at three levels (set, round, block), and nothing is pre-selected (vision CAP-1 describes how round, block and workout status follow from the marks).
