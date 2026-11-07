---
doc: ADR-007
title: Playwright E2E suite written by me, e2e/ write-denied to Claude Code
status: Accepted
date: 2026-11-07
source: D-07
---

# ADR-007 · Playwright E2E suite written by me, `e2e/` write-denied to Claude Code

## Context

Writing the E2E suite herself is the priority learning objective (L-5), with AI as coach only. The brief gives the reasons: the learning goal, and deterministic enforcement.

## Decision

The Playwright E2E suite is written by Teodora. Claude Code is denied write access to `e2e/` through permissions.

## Consequences

- The rule is enforced by permissions, not by prompts.
- Evidence for L-2 is the `.claude/` folder in the repo, including this write block on `e2e/`.
- `e2e/` is authored by Teodora, with Claude Code guiding only (brief §3).
- ADR-014 builds on this decision and makes the suite a merge gate.
