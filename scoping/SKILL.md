---
name: scoping
description: >-
  Use when shaping a new project or feature before Musk filter / IRMPEW.
  Produces a scoped brief: named intent, in/out, unknowns. Mimics pstack
  playbook style. Not for code, Linear tickets, or verification.
---

# Scoping

Pstack-style entry playbook: turn a fuzzy ask into a **scoped brief** a later skill can filter and frame.

## When

- New project / feature / greenfield ask
- User says "scope this", "cadrer", "before IRMPEW"
- Orchestrator step 1

## Do not

- Delete requirements (that is `musk-filter`)
- Write FRAME.md / R+M+E (that is `irmpew-m-interrogate`)
- Touch the repo for proof (that is `w-real-code-verify`)

## Playbooks (pick one)

| Playbook | For |
|---|---|
| [greenfield](playbooks/greenfield.md) | New product or feature, no existing system in scope |
| [brownfield-delta](playbooks/brownfield-delta.md) | Change to an existing app / process |
| [clarify-only](playbooks/clarify-only.md) | Ask is too vague — questions first, brief after answers |

Copy the chosen playbook steps into the todo list **verbatim**, then execute.

## Prompt template (English)

```
You are running the SCOPING skill.

Goal: produce SCOPED-BRIEF.md only. No FRAME. No code. No Musk deletion yet.

Inputs:
- User ask (verbatim)
- Any linked docs / tickets (optional)
- Playbook: {greenfield | brownfield-delta | clarify-only}

Output must include:
1. Intent (I) — one paragraph, named requester if known
2. In scope — bullet list of what we are shaping
3. Out of scope — explicit exclusions
4. Stakeholders / named humans (or "unknown — flag")
5. Unknowns surfaced — questions we still cannot answer
6. Constraints observed (time, stack, legal) without inventing requirements

Done when: SCOPED-BRIEF.md exists and a human could hand it to musk-filter without guessing intent.
```

## Handoff contract → musk-filter

| Field | Required |
|---|---|
| `SCOPED-BRIEF.md` | yes |
| Intent named | yes |
| In / Out of scope | yes |
| Unknowns list | yes (may be empty with "none yet") |
| Requirements list (raw, unfiltered) | yes — even if messy |

## Done when

- [ ] Playbook selected and steps completed
- [ ] `SCOPED-BRIEF.md` written
- [ ] No FRAME.md, no code changes, no deletion log yet
