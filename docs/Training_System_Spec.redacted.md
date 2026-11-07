---
title: Training system — domain summary for product discovery (public redacted copy)
version: 0.6.1-redacted
status: Input (not requirements)
updated: 2026-11-07
owner: Teodora
source: Training_System_Spec.md v0.6 (full original kept privately, outside this repo)
---

# Training system — domain summary for product discovery

> **Redacted copy for the public repo.** Private program and personal content has been removed. The full original is kept privately outside this repo.

Input document for a vision/discovery interview. It describes an existing, in-use training system. It deliberately contains no app design, feature or data-model recommendations; those are decided during discovery and later phases. The actual programs are kept privately (called Workouts 1, 2 and 3 in the product vocabulary, brief D-09).

---

## 1. Who it is for

A single user training at home, no gym, no coach. Intermediate-beginner. Three sessions per week, hard ceiling of 70 minutes per session including warm-up, realistic target 45–55 minutes.

Primary goal is **consistency over speed**: balanced muscle development, nothing specialised. Secondary constraint: keep the number of exercises low, because exercise count is what pushes sessions over the time budget.

---

## 2. Program architecture

**Three full-body workouts (1, 2, 3), rotated in order.** The goal is three sessions a week, on no fixed days. The rotation is positional, not calendar-bound: a missed day resumes from where the rotation stopped.

Rationale for full-body over a split, at three sessions per week:

- each muscle group gets trained 2–3× per week instead of once
- a missed session still leaves every group trained at least twice
  **Each workout is a sequence of blocks.** Blocks are labelled A, B, C. A block is a group of exercises performed as a circuit (A1 → A2 → A3 → rest → repeat), sharing one equipment setup. Each pass through the block is a round, and an exercise performed once in a round is a set. Rest is 60–90 s per round.

---

## 3. The equipment constraint

Home equipment: an adjustable 40 kg set — **8 × 3 kg, 4 × 2.5 kg, 4 × 1.25 kg plates, two 50 cm dumbbell handles, one connector that joins the handles into a 1.20 m barbell** — plus fixed dumbbells 1/2/3 kg, ankle weights 1 and 2 kg, three tensions each of long/flat/loop bands, a stool and a 3-step ladder. No bench, no pull-up bar.

Three hard consequences of this equipment:

1. **Barbell and dumbbells are mutually exclusive.** The barbell _is_ the two dumbbell handles. No block may require both at once.
2. **Changeovers cost real time.** Screw collars on concrete plates take 40–90 s. Budget: **max one plate change and one implement conversion per session**, both scheduled to fall inside a rest period, and ideally covered by a bodyweight or band exercise performed during the change.
3. **Achievable loads are a function of plate inventory, not a continuous range.** For a symmetric pair of dumbbells the reachable loads are 2.5 / 5 / 6 / 8.5 / 11 / 12 / 14.5 / 17 / 19.5 kg of plate per hand. Barbell: 2.5–39 kg in 2.5 kg steps. Smallest possible increment anywhere is **+2.5 kg total** (1.25 kg per side).

---

## 4. Progression rules

**Double progression** is the core rule:

> Pick a load where the last 2 reps are hard with clean form. Stay on that load until you hit the **top of the rep range in every set**. Only then increase, and drop back to the bottom of the range.

Progression is typed per exercise, not universal:

| Type         | Applies to                 | Next step                               |
| ------------ | -------------------------- | --------------------------------------- |
| Load         | barbell and dumbbell lifts | next achievable load, +2.5 kg           |
| Band tension | band exercises             | next band                               |
| Leverage     | bodyweight exercises       | lower the hand support, never more reps |
| Tempo        | small muscles, core        | 3 s eccentric, then load                |

**Small muscles have a separate rule.** Their working loads are low, and the smallest plate increment is +2.5 kg, i.e. up to +100%. Order of progression there is **reps → tempo → load**, and the intermediate load is a bare handle plus one 1.25 kg plate per side rather than jumping to the 5 kg dumbbell (handle plus plates).

**Set ramping**: the set count per exercise ramps up after the first weeks, and differs between main and accessory exercises.

---

## 5. Session-level rules

- **No fixed rule for skipping when time runs short**: the user decides on the day what to skip. The workout files list suggested exercises to drop; this is guidance only.
- **2 sets beat 3 unfinished**: if 3 sets are chronically not completed, stay at 2 and raise the load.
- **Warm-up is short and fixed.** Long static stretching comes after the session.

---

## 6. Withheld

Withheld from the public copy (private; see the checklist in `docs/private-data-checklist.md`). Section number kept so references to later sections stay stable.

---

## 7. Logging

The workout files include a "record today" table: per-exercise load and reps **per set**, plus a free-text note. Band exercises record tension level instead of kg; bodyweight exercises record support height.

The user does not use a spreadsheet for logging and prefers a lighter way: mark an exercise as complete with the planned reps pre-filled, and change them only if different.

Progression depends on reps per set (top of the range in every set), so a single total or an average is not enough to apply the rule.

---

## 8. Stance of the training system

The training system deliberately takes a position that differs from common fitness-app behaviour:

- **No spot reduction.** Training a body part does not reduce fat there. Fat distribution is systemic.
  The system is a training log and programming approach, not medical advice.

---

## Change log

- 0.6.1-redacted (2026-11-07): Public copy of the private original; private content removed. Earlier history is kept in the private original.
