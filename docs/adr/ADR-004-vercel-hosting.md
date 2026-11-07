---
doc: ADR-004
title: Vercel hosting
status: Accepted
date: 2026-11-07
source: D-04
---

# ADR-004 · Vercel hosting

## Context

The app needs hosting. The brief gives the reasons: there is already a Vercel account, and Vercel is free for personal use. Vision constraint C-9 records this choice.

## Decision

The app is hosted on Vercel, using its Git integration: a preview for every PR and production on merge to `main`.

## Consequences

- Every PR gets a preview deployment, and merging to `main` deploys to production.
- Stays within the zero-cost decision (ADR-006), because Vercel is free for personal use.
