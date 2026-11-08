---
doc: CHK-001
title: FitCadence – Private-data checklist
version: 0.4
status: Draft
updated: 2026-11-08
owner: Teodora
resolves: Q-18, Q-26, Q-27
---

# FitCadence – Private-data checklist

The repo is public (D-10, C-13). A public push cannot be taken back (R-2). This checklist defines what counts as private and is applied at every PR. Rule of thumb: private means something that could hurt if it leaked. Ordinary fitness content is not private.

## Never committed (any file, comment, test data or commit message)
1. **Real training logs**: dated entries, loads and reps actually performed, and anything entered in the private instance.
2. **Health, pain or symptom notes** of any kind.
3. **Secrets**: `.env` files, tokens, keys, OAuth credentials.

## Allowed in committed docs and code
- First name.
- Phone model (needed for the foldable layout, C-3).
- "Three sessions a week" and other product-level facts.
- Home equipment inventory (it explains the load constraints).
- Exercise names, workout structure (Workout, Block, Round, Set), set and rep schemes and progression rules. These are ordinary fitness content, not personal data.

## Sample and test data
- The demo instance and all tests use sample data only. The demo program may be based on the real structure, as long as it contains no logs and no health notes (C-7).
- No real logs or health notes in tests, fixtures, screenshots or the demo instance.

## Private files live outside the repo
- The original `Training_System_Spec.md` and the workout files (Тренировка A, B, C) can contain health notes, so they live in a separate repo, `fitcadence-private`, outside the public `fitcadence` repo folder (decided 2026-11-04).
- `fitcadence-private` is **local-only** (no GitHub remote) and sits on the same level as the public `fitcadence` folder, under one parent folder (Q-27). It is never opened as Claude Code's working folder for this project and never added as an extra directory.
- The public repo holds only the redacted spec copy.
- `.gitignore` also lists `.env*` and local Claude Code settings from the first commit.

## Before every push and PR
- [ ] `git diff --staged` read in full
- [ ] Commit message checked for private details
- [ ] New or changed docs and code checked against items 1 to 3 (in particular: no health or pain wording)
- [ ] No new file outside the allowed paths
- [ ] gitleaks green (local pre-commit hook; CI scan from P5.2)

## Safety nets (Q-26, resolved 2026-11-08)
Decision: keep it simple and proportionate.
1. **gitleaks** as a local pre-commit hook (via the `pre-commit` framework), set up in P1.1. Catches secrets by content. Can be skipped with `--no-verify`, so it is backed by item 2.
2. **gitleaks in CI** as a required check on pull requests, from P5.2. Cannot be skipped locally. Fits D-14.
3. **GitHub push protection**: on by default for users on public repos. Free backstop for known credential patterns.
4. **Manual checklist** above, for health notes and logs. Scanners find credentials, not health notes, so this part stays a human check.

Dropped: a custom private word list and a local hook that reads it (over-engineered for the actual risk; exercise names are not private).

## Open decisions
- **Q-27 · Layout of `fitcadence-private`**: resolved 2026-11-04. Side by side with the public repo, local-only.

## Change log
- 0.4 (2026-11-08): Scope narrowed. Private is now only real training logs, health/pain/symptom notes and secrets. The actual program (exercise names, set counts, themes) moved to "Allowed". Q-26 resolved: gitleaks (pre-commit and CI) plus push protection plus this manual checklist; custom word-list hook dropped.
- 0.3 (2026-11-04): Q-27 resolved: `fitcadence-private` is local-only and on the same level as `fitcadence`.
- 0.2 (2026-11-04): Private files move to a separate repo, `fitcadence-private`. Added open decisions Q-26 (automated safety nets, her choice pending) and Q-27 (layout).
- 0.1 (2026-11-04): First draft from the P1.1 Q-18 interview.
