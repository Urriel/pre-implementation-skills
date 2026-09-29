---
name: musk-filter
description: >-
  Use after scoping, before IRMPEW. Musk algorithm steps 1–3 only: question
  requirements (named human, make less dumb), delete hard (~10% add-back),
  simplify/optimize survivors. Steps 4–5 (accelerate, automate) are OUT until
  the system is operated. Output: lean R + deletion/simplify log.
---

# Musk filter (steps 1–3 only)

Strict order. Source: Musk 5-step algorithm (Starbase / Tim Dodd; skill `musk-algorithm`). **Steps 4 and 5 are forbidden in this skill.**

## When

- `SCOPED-BRIEF.md` exists (from `scoping`)
- Orchestrator step 2
- User says "Musk this brief", "lean R", "filter requirements"

## Explicitly OUT

| Musk step | Status here |
|---|---|
| 1 Question requirements | IN |
| 2 Delete parts/process | IN |
| 3 Simplify / optimize | IN (only after 1–2) |
| 4 Accelerate cycle time | **OUT** — apply once system is operated |
| 5 Automate | **OUT** — Fremont rule; after manual operation |

## Prompt template (English)

```
You are running MUSK-FILTER (steps 1–3 only).

Input: SCOPED-BRIEF.md
Do NOT write FRAME.md. Do NOT code. Do NOT propose acceleration or automation.

Step 1 — Question every requirement:
For each raw requirement:
  Requirement: [verbatim]
  Named human: [person or UNKNOWN]
  Steelman: [...]
  Challenge: what breaks if removed?
  Survivors reformulation (less dumb): [...]
  Verdict: KEEP | CUT | REWRITE

Step 2 — Delete:
List everything CUT. Cut hard. If you would not add back ~10% later, you did not cut enough — note that calibration.

Step 3 — Simplify (survivors only):
For each KEEP/REWRITE, narrow scope. No new features.

Outputs:
1. LEAN-R.md — numbered lean requirements (checkable language)
2. MUSK-LOG.md — deleted list + simplified list + named humans + note that steps 4–5 are deferred

Done when: LEAN-R.md has zero anonymous requirements and MUSK-LOG.md lists cuts.
```

## Handoff contract → orchestrator (human gate) → irmpew-m-interrogate

| Field | Required |
|---|---|
| `LEAN-R.md` | yes |
| `MUSK-LOG.md` | yes |
| Human approval of deletion log | **yes — orchestrator stops here** |
| Accelerate / automate proposals | must be absent |

## Done when

- [ ] Steps 1→2→3 visible in order
- [ ] `LEAN-R.md` + `MUSK-LOG.md` written
- [ ] No step-4/5 content
- [ ] Ready for human OK on the deletion log
