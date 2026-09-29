---
name: orchestrator
description: >-
  Thin setup skill that chains scoping → musk-filter → (human OK) →
  irmpew-m-interrogate → w-real-code-verify. Stop after musk-filter deletion
  log and ask the human before M interrogation. No extra steps.
---

# Orchestrator (lean ship chain)

Thin pstack-style conductor. **No extra steps** beyond 1→2→gate→3→4.

## Chain

```
scoping → musk-filter → [HUMAN OK on MUSK-LOG] → irmpew-m-interrogate → w-real-code-verify
```

## When

- User says "run the chain", "setup lean ship", "/orchestrator"
- New scoped product work that needs Musk + IRMPEW + reality proof

## Prompt template (English)

```
You are the ORCHESTRATOR.

Run exactly:
1. Load skill `scoping` — produce SCOPED-BRIEF.md
2. Load skill `musk-filter` — produce LEAN-R.md + MUSK-LOG.md
3. STOP. Show MUSK-LOG.md (deleted + simplified) to the human.
   Ask: "OK to lock this lean R and start M interrogation? (yes / edit / abort)"
   Do not continue on silence. Wait for explicit yes.
4. On yes: load `irmpew-m-interrogate` — produce FRAME.md
5. When code/repo is available (or user says verify now): load `w-real-code-verify` — produce VERIFY-REPORT.md

Never insert extra phases (no Linear milestones, no accelerate/automate, no optional polish).
If a skill's Done when fails, stop and report which skill blocked.
```

## Handoff contracts (summary)

| From | To | Artifact |
|---|---|---|
| scoping | musk-filter | `SCOPED-BRIEF.md` |
| musk-filter | **human** | `LEAN-R.md` + `MUSK-LOG.md` |
| human yes | irmpew-m-interrogate | approved lean R |
| irmpew-m-interrogate | w-real-code-verify | `FRAME.md` |
| w-real-code-verify | end | `VERIFY-REPORT.md` + evidence |

## Done when

- [ ] All four skills completed **or** stopped at documented gate/failure
- [ ] Human gate after step 2 was respected
