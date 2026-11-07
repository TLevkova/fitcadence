---
doc: ADR-003
title: GitHub for repo, Issues, Projects board and Actions
status: Accepted
date: 2026-11-07
source: D-03
---

# ADR-003 · GitHub for repo, Issues, Projects board and Actions

## Context

The project needs a home for code, work items, a board and automation. The brief gives the reasons: GitHub has the deepest Claude Code integration, and its free tier is sufficient. Vision constraint C-8 records this choice.

## Decision

GitHub hosts the repo, the Issues, the Projects board and the Actions.

## Consequences

- Work items are GitHub Issues, and each Issue title starts with its REQ ID (brief §5).
- Automation runs as GitHub Actions.
- Stays within the zero-cost decision (ADR-006), because the free tier is sufficient.
