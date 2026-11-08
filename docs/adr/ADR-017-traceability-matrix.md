---
doc: ADR-017
title: Generated traceability matrix with CI checks
status: Proposed
date: 2026-11-08
source: D-17
---

# ADR-017 · Generated traceability matrix with CI checks

## Context

The chain is G → CAP → REQ → Issue → branch/PR → unit tests → @REQ E2E test → CI report (brief §5, learning objective L-4). A hand-kept matrix drifts and nothing enforces it. Q-29 asked how the chain is recorded and verified. The stack is still open (D-08), so the script language is not chosen here.

## Decision

- Each REQ block in `01-requirements.md` has a `Traces to: CAP-n, G-n` line. This is the source for the CAP and G links.
- A script generates `docs/traceability.md` from the REQ file, the GitHub Issues (title starts with the REQ ID) and the `@REQ-nnn` tags in `e2e/`.
- The generated file is committed. Teodora reviews its diff in every PR.
- CI (required check, set up in P5.2) fails when:
  1. a REQ has no CAP or no G (vision §10);
  2. an approved REQ has no GitHub Issue;
  3. an `@REQ-nnn` tag has no matching REQ;
  4. the committed `traceability.md` differs from a fresh regeneration.
- Not enforced: "REQ with no `@REQ` test". D-14 already requires the test in the same PR as the implementation.
- **[ASSUMPTION]** Each REQ block has a `Status:` line (Draft, Approved, Deprecated). Check 2 covers Approved REQs only; Deprecated REQs are excluded from all checks.

## Consequences

- One source of truth for CAP and G links; the matrix is only a view.
- The script and CI job are built in P5.2 and P6, in the language chosen in P3. Until then `traceability.md` does not exist.
- Check 2 needs read access to Issues in CI (the default `GITHUB_TOKEN` is enough **[ASSUMPTION]**).
- PR and unit-test links are not checked by CI. The PR links its REQ, Issue and tests (delivery roadmap P6, L-4).
- Closes Q-29.
- The number follows the brief rule (ADR number matches the decision). ADR-015 and ADR-016 stay reserved for D-15 and D-16 once those are confirmed.
