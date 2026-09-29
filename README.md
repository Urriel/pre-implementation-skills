# Pre-implementation skill chain

A small chain of agent skills that **close the gaps before implementation**.

They sit **upstream of coding** and are an **excellent complement to Pstack**-style verification: Pstack is strong at proving that what shipped actually works; this chain is strong at making sure you are building the **right, lean thing** before you write code.

```
scoping → musk-filter → [HUMAN OK] → irmpew-m-interrogate → w-real-code-verify
         \________________ orchestrator ________________/
```

## Why this exists

Common failure modes before (and during) implementation:

- Fuzzy intent and unbounded scope
- Requirements that were never questioned or deleted
- Thin or missing world model (assumptions treated as facts)
- “Done” claimed without an observable proof path
- Verification that never touches the real app / repo

This chain addresses those **before** a large implementation pass. Use Pstack (or similar) **during / after** implementation to close proxy-done, user-path, and side-effect gaps.

| Phase | This repo | Pstack-style verify |
|---|---|---|
| Before coding | Scope → delete → frame (R + M + E) | — |
| After / while coding | Optional `w-real-code-verify` proof of E | Full prove-it-works stack |

They reinforce each other; they do not replace each other.

## Skills

| Folder | Role | Primary output |
|---|---|---|
| [`scoping/`](scoping/) | Named intent, in/out, unknowns | `SCOPED-BRIEF.md` |
| [`musk-filter/`](musk-filter/) | Musk steps **1–3 only** (question / delete / simplify). Steps 4–5 are **out of scope** here | `LEAN-R.md` + `MUSK-LOG.md` |
| [`irmpew-m-interrogate/`](irmpew-m-interrogate/) | Lock lean **R**, interrogate **M**, define **E** (IRMPEW letter map) | `FRAME.md` |
| [`w-real-code-verify/`](w-real-code-verify/) | Prove **E** on the real repo/app (not a slide) | `VERIFY-REPORT.md` |
| [`orchestrator/`](orchestrator/) | Runs 1→2→**human gate**→3→4 | Stops after deletion log until a human OKs |

## Human gate (required)

After `musk-filter`, the orchestrator **stops**. A human must review `MUSK-LOG.md` (what was deleted / kept and why) before framing continues. Do not skip this gate.

## How to use

1. Drop the folders into your agent skill library (Cursor / Grok Bot / similar), or point the agent at this repo.
2. Prefer running via [`orchestrator/`](orchestrator/) so the human gate is enforced.
3. Keep prompts in skills in **English**. Operator chat can stay in any language.
4. After a solid `FRAME.md`, implement. Then verify with Pstack (or `w-real-code-verify` for a lighter E proof).

## Design notes

- **Musk 1–3 before IRMPEW framing** — delete first; do not polish requirements you should not have.
- **IRMPEW** — Intent / Requirements / Model / Plan / Evaluation / Workflow (see letter map under `irmpew-m-interrogate/references/`). Frames for coding should carry **R + M + E**.
- **W here means real-code verify** — not “write a plan”; prove the evaluation criteria on the actual system.

## License

MIT (see [`LICENSE`](LICENSE)).
