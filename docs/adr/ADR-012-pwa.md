---
doc: ADR-012
title: PWA with no native app
status: Accepted
date: 2026-11-07
source: D-12
---

# ADR-012 · PWA with no native app

## Context

The same features are wanted on mobile and web (brief reason). Vision constraint C-1 requires an installable web app (PWA) for Android and web, with the same features on mobile and desktop. Non-goal NG-3 rules out a native mobile app.

## Decision

The product is a PWA (installable web app) with no native app. The tech stack is still open (D-08).

## Consequences

- The PWA is the only app (NG-3).
- The tech stack is decided in P3 (D-08).
- PWA limits may affect later features: offline use, the half-folded layout and Samsung Health steps (vision R-4). Feasibility is checked before each is scheduled (Q-9, Q-12).
