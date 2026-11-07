---
doc: ADR-010
title: Public repo with no private data
status: Accepted
date: 2026-11-07
source: D-10
---

# ADR-010 · Public repo with no private data

## Context

The repo is a showcase for interviews while private information is handled iteratively (brief reason). A public push cannot be taken back (vision R-2, C-13). Vision risk R-2 and constraint C-15 (no personal data hardcoded in the app or the repo) apply.

## Decision

The GitHub repo is public. No personal or private data is ever committed. This is checked in every iteration:

- `.gitignore` for private paths from the first commit
- an automated scan in CI
- a manual checklist at every PR

## Consequences

- What counts as private is defined in `docs/private-data-checklist.md` (vision Q-18, resolved in P1.1).
- The checklist is applied at every PR.
- Her program, equipment and logs are entered only through the UI, never hardcoded (C-15).
- R-2 is a top risk (Teodora); its mitigations include the three checks above and C-15.
