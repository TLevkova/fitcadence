---
doc: ADR-001
title: Docs-as-code
status: Accepted
date: 2026-11-07
source: D-01
---

# ADR-001 · Docs-as-code

## Context

The project needs one place for all its SDLC artifacts (vision, requirements, architecture, decisions). The brief gives the reason: a single source of truth that Claude Code can read and that is versioned in git.

## Decision

All SDLC artifacts live as Markdown in the repo under `/docs`. Diagrams are written in Mermaid.

## Consequences

- One source of truth for project documents.
- Claude Code can read the documents directly.
- Every change to a document is versioned in git.
- The repo is public (ADR-010), so every document in `/docs` is subject to the private-data checklist (D-10).
