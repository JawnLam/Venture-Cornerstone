---
type: Fleeting
Item_ID: "F7C30B92-5A14-4D68-B2E9-8D1C6A0F4E23"
title: "Tendly — Business Bootstrap (Read Me First)"
vcs_Business_Slug: "TND"
vcs_Doc_Class: business-bootstrap
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Read Me First

## 1. What this folder is

**Tendly is the compliance operating system for independent childcare centers** — certification-expiry tracking, live staff-to-child ratio monitoring, a records vault, and one-click inspection-ready reports, sold at `$299` per center per month. This folder is Tendly's **complete founding-document stack**: consistency-audited, decision-tested by a fresh reader, and packaged. **The decision it enables:** as the **angel investor** it is written for — decide whether to take the meeting / fund the **`$750,000` post-money SAFE** ask, from these documents alone. The founder also **executes** from it (the plan and milestones live in the stack; execution tracking lives in `Workspace/`). *(A worked example: every figure in here is fictional and stamped founder-supplied or `[ASSUMPTION]` — no number is a real-world statistic.)*

## 2. Verify first

Before reading further, verify `Stack/MANIFEST.md` against this folder: every listed file present, every SHA-256 matching. On any mismatch, **stop and report to the founder** — do not act on an unverified stack.

## 3. Contents + precedence

Three subfolders: **`Stack/`** — the founding documents (act on these); **`Records/`** — history (why the stack is shaped this way; not needed to act); **`Workspace/`** — the founder's execution state.

| Stack document | One line | Band | Precedence |
|---|---|---|---|
| `04-financial-summary.md` | Do the numbers work — unit economics, 3-yr top line, raise/burn/runway, sensitivity, cap-table math | L3 | **1 (numeric law)** |
| `03-market-brief.md` | Who the customer is, market sizing (all `[ASSUMPTION]`), competition, go-to-market | L2 | 2 |
| `02-lean-canvas.md` | The business model, nine blocks | L1 | 3 |
| `01-vision-brief.md` | Why this deserves to exist | L0 | 4 |
| `05-pitch-deck.md` | Sequoia-arc investor re-cut — cites, owns no figure | projection | 5 |
| `06-one-pager.md` | Fast top-of-funnel read — cites, owns no figure | projection | 6 |
| `_assumptions-register.md` | The single authored home of every assumption: value, owner, status, **severity**, valid-until | V | numeric authority's spine |

Reading order: `01 → 02 → 03 → 04 → _assumptions-register → 05 → 06`. On any conflict, **the precedence declaration is law**: lower rank wins; a projection conforms to its source document, never the reverse.

## 4. Operator-input register — everything you could ever need from the founder that is NOT in this stack

If an actor needs something from the founder that is not in this table, that is a package defect — report it.

| Item | Category | Why needed | When to ask / resolve |
|---|---|---|---|
| **Sourced TAM/SAM to replace `TND-A7`/`TND-A8`** | **BLOCKING DECLARED GAP** | The market case runs on an unsourced founder recollection; the stack itself says it must be replaced before investor use — this is why the verdict is SHIP-WITH-DECLARED-GAPS, not SHIP | **Before any investor sees the market brief or deck**; also a REVISE-STACK time trigger past 2026-09-30 |
| CPA review of the financial model | Professional sign-off | Investor-facing financials are drafted, not blessed (`vcs_Requires_Signoff_By`) | Before showing the model in diligence |
| Securities attorney review of the SAFE + cap table | Professional sign-off | The SAFE is a security; dilution math and instrument are counsel's | Before the round closes |
| Privacy counsel review of PII handling + ToS | Professional sign-off | Tendly stores children's/staff records (background checks, immunizations, incidents) | Before scaled onboarding / before diligence asks |
| Billing export behind 12 centers / `$43,200` ARR (`TND-S1`) | Private data | The stack states traction; diligence verifies it | In diligence |
| Cohort/churn data beyond the n=12 directional figure (`TND-A4`) | Private data | The LTV rests on the 18% churn assumption | In diligence; re-verify by 2026-12-31 (staleness trigger) |
| CAC attribution as the motion scales (`TND-A3`) | Private data | Blended `$2,400` CAC is an assumption with no cohort attribution yet | In diligence; re-verify by 2026-12-31 (staleness trigger) |
| Cash balance + burn refresh (`TND-A11`/`A12`, `TND-S9`) | Staleness trigger | A cash position decays fast (~6.7-month clock) | Re-verify past 2026-10-31, or at any material spend change |
| Round terms confirmation (`TND-A10`) | Staleness trigger / taste call | `$6.0M` cap is founder-proposed, not agreed | At term-sheet time; past 2026-10-31 |
| Founder references, agreement terms, equity split detail | Private data / counsel-owned | Named in the interview; the agreement is attorney-drafted | In diligence |

## 5. Definition of done

For the **investor**: you can reach a take-the-meeting / fund / pass decision from `Stack/` alone — every question left should be your diligence, a professional's signature, or the one declared blocking gap above. For the **founder executing**: the growth path and use of funds in `04` §2–4 are the plan; **no `requires-signoff-by` document is used until the named professional clears it**, and the blocking gap closes before any investor meeting. "It reads well" is not done; the verification chain and the sign-off boundary are.

## 6. Workspace rules

All execution tracking lives in `Workspace/`. Update `Workspace/execution-state.md` every working session (state lives in files). **Never edit `Stack/` or `Records/` during execution** — a needed change to the stack is a REVISE-STACK event (change spec → edit affected documents, IDs stable → re-run affected gates → regenerate manifest + freeze hashes), not an in-place edit.

## 7. Deviations rule

When reality contradicts a stack document — the raise closes at a different cap, a market figure is disproven, a competitor moves, a cost lands higher — do **not** silently edit the stack to match. Record the finding in `Workspace/deviations.md` and surface it; those entries are the feedstock for REVISE-STACK.

## 8. Records notice

`Records/` is history: the founder interview, selection record (including the audience bar the decision test was judged against), source log, stranger-test log, and freeze hashes. Useful for *why* this stack is shaped as it is — **not needed to act on or execute it, and never to be modified.** (The assumptions register is deliberately *not* here — it is a Stack decision document.)

## 9. Provenance

Produced by **Venture Cornerstone v0.1.0** (`vcs_` namespace) on **2026-07-27**. Gate 1: clean (reconciliation + arithmetic identities; re-run at re-freeze). Gate 2: **SHIP-WITH-DECLARED-GAPS**, run 1, rerun count 0 — fresh isolated instance, angel-investor role, verbatim fixed prompt, executed against the freeze hashes; one blocking gap (unsourced TAM) declared on the manifest cover. Drafting note: documents drafted by an AI engine under a verify-or-flag data discipline; **no regulated document in this folder is blessed as compliant** — the operator-input register's sign-off rows are load-bearing.
