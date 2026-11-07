---
doc: ADR-014
title: E2E testing as a merge gate
status: Accepted
date: 2026-11-07
source: D-14
---

# ADR-014 · E2E testing as a merge gate

## Context

The brief gives the reason: make the E2E suite a real quality gate (vision L-5, D-07). The cost is stated too: every feature PR waits for her test, which touches R-1.

## Decision

E2E testing is a merge gate. A PR merges into `main` only when CI is green, including the full Playwright suite, which runs on every PR and is never skipped (required status check).

A PR that implements or changes a requirement includes its `@REQ-nnn` test, written by Teodora in the same PR.

## Consequences

- The E2E suite is a real quality gate.
- Every feature PR waits for her test (brief). This touches R-1: the MVP may be too big for about 8 hours a week. The vision's mitigation is thin slices that each work on their own.
- Builds on ADR-007: the suite is written by her, and Claude Code cannot write to `e2e/`.
