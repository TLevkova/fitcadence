---
doc: ADR-011
title: Private and demo instances
status: Accepted
date: 2026-11-07
source: D-11
---

# ADR-011 · Private and demo instances

## Context

The repo and the demo must stay free of personal data while the app stays useful to her (brief reason). Vision constraints C-7 (two deployments, sensitive information stays out of the demo) and C-15 (no personal data hardcoded) apply.

## Decision

Two deployments:

- a private instance with her real data
- a demo instance with sample data only

No personal data is hardcoded. She enters her program, equipment and logs through the UI.

## Consequences

- The demo instance is available by URL and holds sample data only (C-7).
- The private instance requires login (C-16). Its public URL is a risk (R-7), and the mechanism is decided in P3 (Q-20).
- Her program and equipment enter the app through the UI, so the plan editor is in the first release (vision CAP-1).
- Where the private instance keeps her data is open (Q-16).

## Amended 2026-11-08

The scope of "private" was narrowed to real training logs, health notes and secrets (`docs/private-data-checklist.md` v0.4; brief D-11 reworded). Her program and equipment are no longer treated as personal data, so the statement that they enter the app only through the UI no longer rests on privacy. Whether the plan editor stays in the first release is open (Q-31). The safety nets are in D-16 [proposed]. The original text above is kept as written.
