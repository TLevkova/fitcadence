---
doc: CHK-001
title: FitCadence – Private-data checklist
version: 0.3
status: Draft
updated: 2026-11-04
owner: Teodora
resolves: Q-18
---

# FitCadence – Private-data checklist

The repo is public (D-10, C-13). A public push cannot be taken back (R-2). This checklist defines what counts as private and is applied at every PR.

## Never committed (any file, comment, test data or commit message)

1. **Real training logs** and anything entered in the private instance.
2. **The actual program**: real exercises, loads, set counts, workout themes or weekly totals (C-15).
3. **Health, pain or symptom notes** of any kind.
4. **Secrets**: `.env` files, tokens, keys, OAuth credentials.

## Allowed in committed docs

- First name.
- Phone model (needed for the foldable layout, C-3).
- "Three sessions a week" and other product-level facts.
- Home equipment inventory (it explains the load constraints).

## Sample and test data

- Only the **demo program**: fictional, and different from the real one (D-15, proposed).
- No real data in tests, fixtures, screenshots or the demo instance (C-7).

## Private files live outside the repo

- Original `Training_System_Spec.md` and the workout files (Тренировка A, B, C) live in a separate repo, `fitcadence-private`, outside the public `fitcadence` repo folder (decided 2026-11-04).
- `fitcadence-private` is **local-only** (no GitHub remote) and sits on the same level as the public `fitcadence` folder, under one parent folder (Q-27, resolved 2026-11-04). It is never opened as Claude Code's working folder for this project and never added as an extra directory.
- The public repo holds only the redacted spec copy.
- `.gitignore` also lists `.env*` and local Claude Code settings from the first commit.

## Before every push and PR

- [ ] `git diff --staged` read in full
- [ ] Commit message checked for private details
- [ ] New or changed docs checked against items 1 to 4
- [ ] No new file outside the allowed paths
- [ ] CI private-data scan green (from P5.2)

## Open decisions

**Q-26 · Which automated safety nets do we use?** (Teodora wants to choose what is best for the project; not decided.) `.gitignore` alone cannot catch private content, so the options are:

1. **Pre-commit scanning** with gitleaks, detect-secrets or trufflehog, wired in through the `pre-commit` framework. Catches secrets by content, not by filename. Local hooks can be skipped with `--no-verify`.
2. **CI scanning** as a required check on pull requests. Cannot be skipped locally. Fits P5.2 and D-14.
3. **Server-side push protection**: GitHub secret scanning and push protection block pushes that contain known credential patterns.
4. **Branch protection and code review** so nothing reaches `main` unchecked (already planned in P5.2).
   To check when deciding: which of these are free for a public repo and what they detect. Secret scanners find credentials, not health notes or a real program, so private-content rules (checklist items 1 and 2) may need a custom pattern list **[ASSUMPTION]**.
   Decide: Q-26 in P1.1 for the local hook, and the CI part in P5.2.

**Q-27 · Layout of `fitcadence-private`**: resolved 2026-11-04. Side by side with the public repo, local-only.

## Change log

- 0.3 (2026-11-04): Q-27 resolved: `fitcadence-private` is local-only and on the same level as `fitcadence`.
- 0.2 (2026-11-04): Private files move to a separate repo, `fitcadence-private`. Added open decisions Q-26 (automated safety nets, her choice pending) and Q-27 (layout).
- 0.1 (2026-11-04): First draft from the P1.1 Q-18 interview.
