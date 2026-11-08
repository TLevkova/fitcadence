# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

FitCadence is a personal fitness and nutrition app. The repo holds docs only. The tech stack is undecided (D-08), so there are no build, lint or test commands. Do not create `src/`, `e2e/`, `.claude/` or `.github/` before their phase. Current status: top of `docs/fitcadence-delivery-roadmap.md`.

## Privacy (this repo is public)

- Follow `docs/private-data-checklist.md` as a hard rule.
- Never put my real training logs, health notes or secrets into any file or commit message.
- Never read, list or reference `../fitcadence-private`.
- Do not push.

## Source of truth

- `docs/` is the source of truth. IDs and conventions are in `docs/fitcadence-project-brief.md`.
- Never renumber or reuse an ID.

## Docs hygiene

- When work changes a doc, bump its version, add a change-log entry, and update the roadmap tracker in the same session.
- At the end of a session, print a handoff block: Phase · Status · Artifacts (with versions) · Decisions · Open questions · Next step.

## Boundaries

- The Playwright suite in `e2e/` is mine (D-07). Never write or edit files there.
- Never bypass the pre-commit hook: no `--no-verify`, no `SKIP=...`. The hook is added later in P1.1.
- I approve every plan and PR.
- Mark anything unconfirmed as [ASSUMPTION] or Q-n.
