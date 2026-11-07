---
doc: ADR-002
title: Claude.ai Project for planning, Claude Code for the repo
status: Accepted
date: 2026-11-07
source: D-02
---

# ADR-002 · Claude.ai Project for planning, Claude Code for the repo

## Context

Thinking (discovery and planning) and execution (work in the repo) are different kinds of work. The brief gives the reason: keep them separate.

## Decision

A Claude.ai Project is used for discovery and planning. Claude Code in VS Code is used for everything in the repo.

## Consequences

- Each chat or session covers one sub-phase, and context moves between the two tools only through documents and handoff blocks (brief §6 and §7).
- None other stated in the docs.
