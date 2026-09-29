---
name: w-real-code-verify
description: >-
  Use after FRAME.md exists and code (or a candidate P) exists. Prove Done
  against real repo + running app (pstack prove-it-works + show-me-your-work),
  not against the spec alone. Output: verification report with evidence.
---

# W — real-code verify

Reality is the final verifier. Read **actual current repo state**, drive user-facing paths as a user, check side effects, score FRAME `## E` against evidence.

## When

- `FRAME.md` exists
- A repo / worktree / running app is available
- Orchestrator step 4
- User says "prove it", "verify W", "reality check"

## Do not

- Trust agent self-report, "it compiles", or README alone
- Edit product code to make the report green (report gaps; optional separate fix pass)
- Invent evidence

## Prompt template (English)

```
You are running W-REAL-CODE-VERIFY (pstack-style prove-it-works + show-me-your-work).

Inputs:
- FRAME.md (R / M / E are the contract)
- Repo path or running base URL
- Optional: prior decision log

Protocol:
1. Read the real tree (routes, tests, configs) — not the brief.
2. Doctor: can we launch? Note exact command and readiness signal.
3. For each E step: drive the real user path; capture evidence (command output, HTTP body, screenshot path, DB/file side effect, test name+result).
4. For each M Unknown/Hypothesis touched: mark Supported | Falsified | Untested with evidence pointer.
5. Write VERIFY-REPORT.md:
   - Summary: PASS | PARTIAL | FAIL against Done when
   - E checklist with evidence links (no bare assertions)
   - M interrogation results
   - Gaps / next outer-loop revise suggestions (R/M/E), if any
6. Append rows to DECISION-LOG.tsv (ts, phase, decision, why, evidence, result).

Done when: VERIFY-REPORT.md cites observable evidence for every claimed E step, or explicitly marks Untested/Fail.
```

## Handoff contract (end of chain)

| Field | Required |
|---|---|
| `VERIFY-REPORT.md` | yes |
| Evidence paths / commands | yes |
| `DECISION-LOG.tsv` (or append) | yes |
| PASS/PARTIAL/FAIL vs Done when | yes |

## Done when

- [ ] Real app/repo exercised (or blocked with concrete doctor failure)
- [ ] Report is evidence-backed
- [ ] No "looks good" without artifact
