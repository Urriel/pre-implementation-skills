---
name: irmpew-m-interrogate
description: >-
  Use after human-approved lean R from musk-filter. Build IRMPEW FRAME.md with
  R locked from lean R, M interrogated for tacit assumptions (hypothesis /
  Unknown), E as checkable Done when. Paper arXiv 2609.12039. No code, no
  milestones.
---

# IRMPEW + M interrogation

Letter map (Krentsel et al., arXiv 2609.12039): I intent · R requirements · M world model · E evaluator · P program · W world.

This skill writes **FRAME.md** only. **R is pre-leaned** (do not re-inflate). **M is transformed**: every M line must answer "what am I assuming without saying it?"

## When

- Human approved `MUSK-LOG.md` / `LEAN-R.md`
- Orchestrator step 3
- User says "frame IRMPEW", "M interrogate"

## Do not

- Re-open Musk deletion (unless human sends back to musk-filter)
- Implement P
- Run live W verification (next skill)

## Prompt template (English)

```
You are running IRMPEW-M-INTERROGATE.

Inputs (required):
- LEAN-R.md (LOCKED — copy into ## R; may tighten wording but not add scope)
- SCOPED-BRIEF.md (Intent / Out of scope)
- MUSK-LOG.md (context only)

Build FRAME.md with sections:

## I — Intent
One short paragraph from scoped brief.

## R — Requirements
Paste lean R. Add Done when (checkable) and Out of R.
Do not smuggle deleted items back.

## M — World model (INTERROGATED)
For EACH assumption about users, data, systems, time, locale, auth, volume:
1. Write the assumption as a statement.
2. Ask: "What am I assuming without saying it?"
3. Tag: Hypothesis | Unknown | Observed
4. If Unknown: what would falsify it in W.

Refuse vague M like "users will understand". Force concrete claims.

## E — Evaluator
How we prove R under M. Numbered steps a stranger can run.
Include V1 proof (~minutes) and Done proof if they differ.
No "demo vibes" — checkable outcomes only.

## Guardrails
- Fail closed if R has no Done when.
- Fail closed if M has zero Unknowns tagged (force at least the honest unknowns).
- Do not invent analytics, mobile apps, or extra surfaces not in lean R.

Done when: FRAME.md exists with R+M+E complete and M lines all interrogated.
```

## Handoff contract → w-real-code-verify

| Field | Required |
|---|---|
| `FRAME.md` | yes |
| `## R` + Done when + Out of R | yes |
| `## M` with Hypothesis/Unknown tags | yes |
| `## E` numbered proof steps | yes |
| Code / PR | no |

## Done when

- [ ] FRAME.md written
- [ ] R matches lean R (no scope creep)
- [ ] Every M line interrogated
- [ ] E is executable as a checklist
