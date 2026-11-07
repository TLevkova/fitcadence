---
doc: ADR-006
title: Zero cost beyond the Claude Pro subscription
status: Accepted
date: 2026-11-07
source: D-06
---

# ADR-006 · Zero cost beyond the Claude Pro subscription

## Context

The project is for personal and training use (brief reason). Vision constraint C-10 records this choice.

## Decision

The project costs nothing beyond the Claude Pro subscription.

## Consequences

- Claude Code usage is bounded by the Claude Pro usage limits, with no API budget (C-11).
- Open questions must fit inside this limit: the two-instance setup and where the private instance keeps her data (Q-16), and how the private instance is protected by login (Q-20).
- GitHub (ADR-003) and Vercel (ADR-004) were chosen partly because they are free for this use.
