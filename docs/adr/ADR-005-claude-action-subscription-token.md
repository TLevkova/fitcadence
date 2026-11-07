---
doc: ADR-005
title: "@claude GitHub Action with subscription token"
status: Accepted
date: 2026-11-07
source: D-05
---

# ADR-005 · `@claude` GitHub Action with subscription token

## Context

The project wants the `@claude` GitHub Action without API billing. The brief gives the reasons: no API billing, and it protects usage limits. Vision constraint C-11 notes that Claude Code usage is bounded by the Claude Pro usage limits, with no API budget (derived from D-05 and D-06). Learning objective L-3 includes running this Action.

## Decision

The `@claude` GitHub Action is authenticated with the subscription token (`CLAUDE_CODE_OAUTH_TOKEN`) and is triggered by comments only.

## Consequences

- No API billing.
- Usage limits are protected, because the Action runs only when a comment triggers it.
- Usage stays bounded by the Claude Pro limits (C-11), so sessions are kept small (vision R-3).
- The token is a secret and is never committed (private-data checklist, item 4).
