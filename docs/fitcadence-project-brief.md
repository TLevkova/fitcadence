---
doc: BRIEF-001
title: FitCadence – Project brief
version: 0.11
status: Draft
updated: 2026-11-08
owner: Teodora
---
 
# FitCadence – Project brief
 
## 1. Purpose
FitCadence is a personal app built from scratch with AI. It has two goals:
1. **Product:** an app I really need for my own fitness and nutrition routine.
2. **Learning:** hands-on practice with Claude Code and agentic, AI-assisted SDLC, to use in future work.
Former working names: Stackfit, MacroLoop.
 
## 2. Seed scope (unvalidated input for the P0.1 Vision interview)
These are my initial ideas, not approved requirements:
- Workout tracking
- Supplement tracking
- Food and recipes with macros
- Meal suggestions based on calorie/nutrient limits and activity
- Recipes with ingredients that feed into a shopping list
## 3. Roles
- **AI (Claude Code):** writes application code, unit tests, docs drafts, CI config.
- **Me:** product owner, approver of every plan and PR, and sole author of the Playwright E2E suite (with AI guidance only).
## 4. Decisions so far (pre-ADR log)
Each one becomes a formal ADR in `docs/adr/` during P1.
 
| ID | Decision | Reason |
|----|----------|--------|
| D-01 | Docs-as-code: all SDLC artifacts live as Markdown in the repo `/docs`; diagrams in Mermaid | Single source of truth; readable by Claude Code; versioned in git |
| D-02 | Claude.ai Project for discovery/planning; Claude Code in VS Code for everything in the repo | Thinking vs. execution separation |
| D-03 | GitHub for repo, Issues, Projects board and Actions | Deepest Claude Code integration; free tier sufficient |
| D-04 | Vercel for hosting (Git integration: preview per PR, production on merge to `main`) | Already have a Vercel account; free for personal use |
| D-05 | `@claude` GitHub Action authenticated with subscription token (`CLAUDE_CODE_OAUTH_TOKEN`), comment-triggered only | No API billing; protects usage limits |
| D-06 | Zero cost beyond the Claude Pro subscription | Personal and training use |
| D-07 | Playwright E2E suite written by me; Claude Code is denied write access to `e2e/` via permissions | Learning goal; deterministic enforcement |
| D-08 | Tech stack: **not decided**; decided in P3 | Requirements first |
| D-09 | Vocabulary, used in every doc, the UI and the tests: **Workout** (1, 2, 3) → **Block** (A, B, C) → **Round** (one pass through a block) → **Set** (one exercise performed once, in one round). Done or skipped is marked explicitly at set, round and block level; nothing is pre-selected | One consistent language across vision, requirements, UI and tests (P0.1 stage 3) |
| D-10 | The GitHub repo is public. No private data is ever committed. Private means real training logs, health notes and secrets (checklist CHK-001 v0.4); the program and exercises are not private. Checked in every iteration (`.gitignore` for private paths from the first commit, gitleaks pre-commit and CI, GitHub push protection, manual checklist at every PR) | Showcase for interviews while handling private information iteratively; a public push cannot be taken back (vision R-2, C-13) |
| D-11 | Two deployments: a private instance with her real data, and a demo instance with sample data only. No real training logs, health notes or secrets are hardcoded; she enters her logs through the UI | Keeps the repo and the demo free of private data while the app stays useful to her (vision C-7, C-15) |
| D-12 | The product is a PWA (installable web app) with no native app. Stack still open (D-08) | Same features on mobile and web (vision C-1, NG-3) |
| D-13 | When learning and delivery speed conflict, the slower, more instructive route wins | Learning goal (vision C-6, L-1 to L-6) |
| D-14 | E2E testing is a merge gate. A PR merges into `main` only when CI is green, including the full Playwright suite, which runs on every PR and is never skipped (required status check). A PR that implements or changes a requirement includes its `@REQ-nnn` test, written by me in the same PR | Makes the E2E suite a real quality gate (vision L-5, D-07). Cost: every feature PR waits for my test, which touches R-1 (see delivery roadmap, merge gate) |
| D-15 [proposed] | The demo instance ships with one prefilled demo program that differs from my real program (see Q-30, open) | Keeps sample data fictional (checklist, vision C-7, C-15) |
| D-16 [proposed] | Safety nets for private data (Q-26): gitleaks as a local pre-commit hook (via the `pre-commit` framework) and as a required CI check, GitHub push protection, and the manual checklist. No custom word list | Scanners catch secrets, not health notes, so the manual checklist stays; proportionate to the risk (checklist CHK-001 v0.4, vision R-2) |
 
## 5. ID conventions (traceability)
| Prefix | Meaning | Lives in |
|--------|---------|----------|
| G-n | Product goal | 00-vision.md |
| L-n | Learning objective | 00-vision.md |
| CAP-n | Capability area (e.g. CAP-1 Workout tracking) | 00-vision.md |
| NG-n | Non-goal | 00-vision.md |
| C-n / A-n / R-n | Constraint / Assumption / Risk | 00-vision.md |
| Q-n | Open question | any doc |
| REQ-nnn | Requirement (traces to CAP and G) | 01-requirements.md |
| ADR-nnn | Architecture decision record. Number matches the decision: ADR-001 is D-01 and so on. ADR-008 is reserved for D-08 (decided in P3). New ADRs after that take the next free number [ASSUMPTION] | docs/adr/ |
| #n | GitHub Issue (title starts with REQ ID) | GitHub |
| @REQ-nnn | Playwright tag on E2E tests | e2e/ |
 
Chain: **G → CAP → REQ → Issue → branch/PR → unit tests → @REQ E2E test → CI report**
 
Rules: IDs are never renumbered or reused. Removed items are marked *Deprecated*.
 
## 6. Phase map and where each phase happens
Chat naming: `P0.1 · Vision interview`. One sub-phase per chat or session.
 
| Phase | Sub-phase | Where | Output |
|-------|-----------|-------|--------|
| **P0 Discovery** | P0.1 Vision interview | Claude.ai (this Project) | `00-vision.md` v0.x |
| | P0.2 Vision review & challenge | Claude.ai, new chat | `00-vision.md` v1.0 Approved |
| **P1 Setup** | P1.1 Repo + tooling + `/init` + docs structure; D-01…D-07 → ADRs | Claude Code | Repo skeleton, ADRs |
| | P1.2 Traceability approach [ASSUMPTION] | Claude.ai (this Project) | ADR, brief update |
| **P2 Requirements** | P2.1 Requirements interview (requirements-interview skill, AskUserQuestion) | Claude Code | `01-requirements.md` |
| | P2.2 Requirements review | Claude.ai or Claude Code subagent | Approved REQs |
| | P2.3 Backlog | Claude Code (`gh` CLI) | Issues, milestones, board |
| **P3 Architecture** | P3.1 Stack & options exploration | Claude.ai | Option comparison |
| | P3.2 Architecture doc, C4 + data model diagrams, ADRs | Claude Code | `02-architecture.md`, ADRs |
| **P4 Agent scaffolding** | CLAUDE.md, permissions, hooks, skills, subagents | Claude Code | `.claude/` |
| **P5 Walking skeleton + CI/CD** | Skeleton app, GitHub Actions, Vercel, `@claude` | Claude Code | Green pipeline, live URL |
| **P6 Feature delivery** | One session per Issue/REQ: plan → implement → review → PR | Claude Code | Merged PRs |
| **P7 Playwright track** (parallel from P5) | My E2E suite; test-coach guidance | VS Code + Claude Code (read-only coach) | `e2e/`, @REQ tags |
| **P8 Maintenance** | Dependabot, changelog, CLAUDE.md pruning, retros | Both | Healthy repo |
 
Delivery (P1 to P8) is detailed in `fitcadence-delivery-roadmap.md`; discovery (P0) in `fitcadence-discovery-roadmap.md`.
 
## 7. Handoff block (end of every chat or session)
```
Phase: P0.1 · Status: Done / In progress
Artifacts: 00-vision.md v0.3
Decisions: D-09 …
Open questions: Q-4, Q-7
Next step: P0.2 – review & challenge
```
 
## 8. Target repository structure
The shape the repo grows into. Folders appear in the phase noted in the comment; nothing is created ahead of its phase. Items marked **[ASSUMPTION]** are not decisions yet and are confirmed in the phase named. Private files live outside this repo (see the note under the tree).
 
```
fitcadence/                          # public repo (D-10)
├── CLAUDE.md                        # short, always-loaded project rules (first draft from /init in P1.1, pruned in P4.1)
├── .gitignore                       # from the first commit (D-10)
├── .pre-commit-config.yaml          # gitleaks hook (P1.1, Q-26)
├── docs/
│   ├── 00-vision.md                 # problem, goals (G-n), non-goals (NG-n)
│   ├── fitcadence-project-brief.md  # decisions D-nn, ID conventions, phase map
│   ├── fitcadence-discovery-roadmap.md   # P0, frozen
│   ├── fitcadence-delivery-roadmap.md    # P1 to P8 tracker
│   ├── private-data-checklist.md    # CHK-001, applied at every PR
│   ├── Training_System_Spec.redacted.md  # public copy; the original is private
│   ├── 01-requirements.md           # REQ-nnn with acceptance criteria (P2.1)
│   ├── 02-architecture.md           # C4 context/container + data model, Mermaid (P3.2)
│   ├── adr/                         # ADR-nnn-title.md, from D-01..D-07 in P1.1
│   ├── specs/                       # [ASSUMPTION] one spec per feature, written before coding (P2 or P6)
│   └── traceability.md              # [ASSUMPTION] generated matrix G → CAP → REQ → Issue → PR → test (P6)
├── .claude/
│   ├── settings.json                # permissions + hooks, checked in; denies writes to e2e/ (D-07)
│   ├── skills/                      # repeatable workflows (P4.2)
│   └── agents/                      # subagents, incl. read-only test coach (P4.2)
├── src/                             # AI-written, approved by me; stack decided in P3 (D-08)
├── e2e/                             # MY Playwright suite (D-07, D-14); `@REQ-nnn` tags
└── .github/workflows/               # CI (P5.2) and the `@claude` Action (P5.3)
```
 
Outside the repo, never committed (checklist CHK-001, Q-27): `../fitcadence-private/` on the same level as `fitcadence/`, local-only. It holds the original training spec and the workout files.
 
## Change log
- 0.11 (2026-11-08): Section 8: added `.pre-commit-config.yaml` (gitleaks hook, P1.1, Q-26) to the target repo tree.
- 0.10 (2026-11-08): "Private" narrowed to real training logs, health notes and secrets (checklist v0.4). D-10 and D-11 reworded. D-15 now points to Q-30 (open: does the demo program still need to differ from the real one?). Added D-16 (proposed): gitleaks pre-commit and CI, push protection, manual checklist; no custom word list.
- 0.9 (2026-11-07): Phase map, P2.1 row: replaced `/spec` (not a built-in Claude Code command) with a requirements-interview skill, per Teodora's decision.
- 0.8 (2026-11-07): Added D-15 (proposed): one prefilled demo program, different from the real one. Added P1.2 Traceability approach [ASSUMPTION] to the phase map. Added the ADR numbering rule to the ID conventions.
- 0.7 (2026-11-07): Reworded one line in section 1 for the public repo.
- 0.6 (2026-11-07): Added section 8, Target repository structure (tree adapted to FitCadence, with the phase in which each folder appears). `docs/specs/` and `docs/traceability.md` marked [ASSUMPTION].
- 0.5 (2026-11-03): D-14 confirmed (no longer proposed).
- 0.4 (2026-11-03): Added D-14 (proposed): E2E testing as a merge gate. Added a pointer to the two roadmaps under the phase map.
- 0.3 (2026-11-01): Added D-10 to D-13 from the P0.1 vision interview.
- 0.2 (2026-11-01): Added D-09 (vocabulary and done/skipped marking model).
- 0.1 (2026-10-31): Initial brief.
 
