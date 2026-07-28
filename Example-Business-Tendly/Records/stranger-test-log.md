---
type: VCS_Stranger_Test_Log
Item_ID: "6F3B0D27-8C41-49E2-A5B7-1D0E9C2F4A83"
title: "Tendly — Stranger Test Log"
vcs_Business_Slug: "TND"
vcs_Doc_Class: stranger-test-log
vcs_Band: V
vcs_Stranger_Model: "Fresh model instance (isolated, no drafting context), acting as the angel investor"
vcs_Run_Date: 2026-07-27
vcs_Rerun_Count: 0
vcs_Ship_Verdict: "SHIP-WITH-DECLARED-GAPS"
vcs_Audience_Bar: "$25K-$100K pre-seed angel; wants durable retention + a believable market (BI-4b; recorded in _selection-record.md)"
vcs_Freeze_Hashes_Ref: "_freeze-hashes.md (Gate-1 SHA-256s; run executed against the audited bytes)"
vcs_Result: "run-1 SHIP-WITH-DECLARED-GAPS (verbatim prompt, zero stack-should-answer, ST-1/2/3 pass) — one open dependency is severity: blocking-for-stated-audience: the unsourced TAM (TND-A7), which the market brief itself says must be replaced before any investor sees it. Not a clean SHIP: the blocking gap is surfaced below and must travel into the package manifest as a pre-use hard stop."
vcs_Document_Status: shipped
vcs_Precedence_Rank: 0
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Stranger Test Log (Gate 2)

> Gate 2 (`05-GATES.md` → THE TWO GATES). A fresh, context-isolated model instance received **only** the frozen `Artifacts/` folder — the six founding documents **plus `_assumptions-register.md`, which now travels inside the stack** (Decision 10 issue 2: anyone judging the financial model needs the assumptions, owners, statuses, and severities) — plus the verbatim, audience-targeted fixed prompt. **The run was executed against the Gate-1 freeze hashes** (`_freeze-hashes.md`): every `Artifacts/` file was confirmed byte-for-byte identical to its audited SHA-256 before hand-over, so the stranger read the audited bytes, not a silently-edited copy. The drafting session never plays the stranger. This log lives outside `Artifacts/` — a gate record, not a founding document.

## Fixed prompt (verbatim, never augmented)

> *"You have been handed the complete founding documents for a business. As the **angel investor** they are meant for: (a) restate what this business is and what it is asking of you; (b) state the decision you would make and why; (c) list every question you would need answered before committing."*

*No "be adversarial / count gaps / classify" instruction was appended — the prompt is the canonical one, and questions are classified charitably by the evaluator afterward (Gate 2, **Baseplate PF-6** evaluator-stance calibration; locally PF-6 = cross-document number-drift, so the Baseplate prefix is load-bearing).*

## Run 1 — 2026-07-27 — SHIP-WITH-DECLARED-GAPS

The three criteria all pass and **zero `stack-should-answer` questions** remain — but one open dependency is tagged `severity: blocking-for-stated-audience` (the unsourced TAM). Under the Decision-10 verdict rule (`05-GATES.md` → *The ship verdict*), a clean ST-1/2/3 is **necessary but not sufficient**: an honest `[ASSUMPTION]` stamp converts every hard question about the TAM to `operator-only`, which would let a self-admitted disqualifier ride into a clean SHIP. The severity tag stops exactly that. Verdict: **SHIP-WITH-DECLARED-GAPS** — packageable, but the blocking gap must be surfaced in `Stack/MANIFEST.md` and the `AI-BOOTSTRAP.md` operator-input register as a pre-use hard stop (see **Blocking gaps** below).

### Criteria

| # | Criterion | Observed | Verdict |
|---|---|---|---|
| **ST-1** | Restatement fidelity | Accurate and complete: compliance OS for independent childcare centers; `$299`/center/mo; **12 centers / `$43,200` ARR** today; raising **`$750,000` on a `$6.0M`-cap SAFE (~12.5%)** for ~18 months' runway to ~200 centers (`$720,000` ARR); Sequoia-arc deck; and — critically — the stranger **noticed and correctly characterized** that all market sizing is stamped `[ASSUMPTION]` and that the cap table/SAFE are flagged for counsel. A misread would have been a stack defect; there was none. | **pass** |
| **ST-2** | Decision plausibility *(judged against the BI-4b bar)* | Reasonable and stack-consistent **for the audience Tendly is actually raising from** — a **`$25K`–`$100K` pre-seed angel who wants to see real retention and a believable market** (BI-4b, recorded in the selection record's `vcs_Audience_Bar`; the bar itself never travels inside the stack), not a generic reader and not a `$750K` lead. Against that bar: *"a plausible **take-the-meeting / diligence** decision"* on the strength of real early traction (`$43,200` ARR, 11/12 retained — the retention the bar asks for), sticky compliance data, and a domain founder — while explicitly conditioning any **term-sheet** on (i) a sourced TAM and (ii) verification of the churn assumption that the LTV:CAC hinges on. The "believable market" half of the bar is precisely what the unsourced TAM does **not** yet clear — which is why the verdict is SHIP-WITH-DECLARED-GAPS, not clean SHIP. That the stack itself flags both as assumptions is what let the stranger reach a coherent take-the-meeting decision rather than stall. | **pass** |
| **ST-3** | Question classification (the pass rule) | **Zero `stack-should-answer`.** 11 questions, all `operator-only` or already-answered by the frozen stack — see below. | **pass** |

### Question classification (all 11 → operator-only or already-answered)

**Operator-only** (an investor takes these to diligence / the founder / a professional — the stack cannot and should not answer them):
1. The founder's actual signed customer agreements and the billing-system export behind the 12 centers / `$43,200` ARR (`TND-S1` — the stack states it; diligence verifies it).
2. Real churn and cohort-retention data beyond the n=12 pilot directional figure (`TND-A4`/`TND-S2`) — the number the whole LTV rests on; only the founder's data can settle it.
3. A **sourced** TAM/SAM to replace `TND-A7/A8` — the stack itself names this as the open dependency (`TND-S5`) and routes it to the founder; asking for it confirms the flag worked.
4. The **securities attorney's** review of the SAFE terms and the **CPA's** review of the cap table and model (`requires-signoff-by`, `04-financial-summary` §5) — professional sign-offs, definitionally not the stack's to give.
5. **Privacy counsel's** view on children's/staff PII handling and the ToS (BI-9 flag).
6. Reference calls with several of the 12 current centers.
7. Founder backgrounds / references and the equity split in the (counsel-owned) founder agreement.
8. CAC attribution behind the `$2,400` blended assumption (`TND-A3`) as the motion scales.
9. Competitive-response risk from the billing-first incumbents.
10. Regulatory variation across the 6 launch states and its effect on per-state build cost.

**Already answered by the frozen stack** (the stranger asked, the documents are determinate):
11. "What exactly is the ask and the runway?" — `04-financial-summary` §3 and the one-pager state it precisely (`$750,000`, `$6.0M` cap, ~18 months, ~200 centers); the deck `TND-D10` cites the same figures. Nothing to add.

**None** of the 11 would make two competent investors reach *observably different* decisions from the stack as written; every one is either their diligence to run, a professional's to sign, or already on the page. Under the charitable, reproducible evaluator stance that is a clean pass on ST-1/2/3 — which is why the verdict is a *passing* one. It is not clean, because of the blocking gap below.

## Blocking gaps (why SHIP-WITH-DECLARED-GAPS, not SHIP)

A `stack-should-answer` question blocks outright (fix and rerun); there were none. A `blocking-for-stated-audience` open dependency does **not** block packaging, but it downgrades the verdict and must be declared, in the package, as a pre-use hard stop:

| Gap | Assumption / source ID | Severity | What it blocks | Resolution (when to close) |
|---|---|---|---|---|
| **Unsourced TAM/SAM** | `TND-A7` (TAM), `TND-A8` (SAM, inherits); logged `TND-S5` | **blocking-for-stated-audience** | The market brief cannot be shown to an investor as-is — the brief and the `TND-D5` market-size slide both carry `[ASSUMPTION / UNVERIFIED]`, and the brief states the figure "must be replaced before any investor sees it." Clears ST-2's "believable market" half of the BI-4b bar only once sourced. | **Replace with a sourced, dated figure** (Child Care Aware of America / IBISWorld / state licensing registries) and rebuild SAM bottom-up **before the market brief goes in front of any angel** — a REVISE-STACK trigger, past `TND-A7`'s `valid-until` 2026-09-30. |

Everything else the investor flagged (churn cohorts, CAC attribution, the SAFE/cap-table sign-offs, PII counsel) is `operator-only` — founder's private data or a professional's signature — and is `severity: non-blocking` for the take-the-meeting decision. Only the TAM is a self-admitted disqualifier the stack itself routes for replacement, so only the TAM is declared here. This single blocking gap travels into `Stack/MANIFEST.md` and the `AI-BOOTSTRAP.md` operator-input register at packaging.

## Finding — the front-run worked (the demonstration)

This stack passed Gate 2 on **run 1** because the risky material was **frozen up front** rather than discovered by the stranger:

- **The assumptions were pre-registered.** Every figure the investor would probe — ARPA, CAC, churn, TAM, burn, dilution — was already stamped `[ASSUMPTION]` in `_assumptions-register.md` with an owner and a status, so the stranger's "where does this number come from?" was pre-answered on the page. The investor's questions became *"verify the founder's data,"* never *"the stack failed to say."*
- **The single most dangerous number was neutralized by honesty.** An unsourced TAM is the classic stack-poisoner (`01-THE-CANON.md` §5.1). Because the market brief and deck **both carry the `[ASSUMPTION / UNVERIFIED]` stamp** and the source log names it as the open dependency (`TND-S5`), the stranger treated "get a sourced TAM" as an operator-only next step — exactly the intended outcome — instead of catching a fabricated statistic and discounting the whole stack. *(Two axes, not one: "get a sourced TAM" is `operator-only` as a **question** — it does not block ST-3 — and simultaneously `blocking-for-stated-audience` as a **dependency**, which is what downgrades the verdict to SHIP-WITH-DECLARED-GAPS. The front-run neutralized the question; the severity tag keeps the gap honest anyway.)*
- **The authority boundary pre-empted the legal questions.** Cap table, SAFE, entity, founder agreement, and PII/ToS were all flagged `requires-signoff-by` before the stranger asked, so every legal question landed as `operator-only` by construction.
- **Reconciliation held.** The ARR series (`$43,200` → `$180K` → `$720K` → `$2.16M`), the `$750,000` raise, the `$6.0M` cap, and the `$299`/`$3,600` pricing are identical across the canvas, financial summary, deck, and one-pager — the deck cites, never restates — so the stranger found no contradicting twin to flag (Gate 1 clean, confirmed here).

**Equivalence-class framing:** the questions an angel can ask this stack fall into three classes — *verify the founder's private data*, *obtain a professional sign-off*, and *is-it-already-answered*. The front-run collapsed the third class to near-zero and made the first two `operator-only` by design. That is the business-domain analog of Baseplate's PF-6 behavioral-completeness lesson: freeze every equivalence class before the stranger sees the stack, and Gate 2 passes on the first run.

## Rerun log

| Rerun # | Date | Stranger model | Result | What changed since last run |
|---------|------|----------------|--------|-----------------------------|
| 0 | 2026-07-27 | fresh isolated instance (angel-investor role) | SHIP-WITH-DECLARED-GAPS | initial run |

*Re-freeze note (2026-07-27, Decision 11 follow-through): after this run, non-decisional edits were applied to the stack — self-containment rewording of document headers, the canvas burn figure qualified pre/post-raise, the BI-4b bar (former TND-A13) relocated out of the traveling register, and a stated cash convention added to the post-raise runway line. No figure, ask, or claim the decision rests on changed, so per the REVISE-STACK cosmetic rule Gate 1 was re-run (reconciliation + arithmetic identities recomputed clean — see `_meta/ARITHMETIC-CHECK.md` reference run), `_freeze-hashes.md` was regenerated over the edited bytes, and this verdict carries. Any future decision-touching change re-runs Gate 2 with a fresh instance.*

**Result: SHIP-WITH-DECLARED-GAPS on run 1** — ST-1/ST-2/ST-3 all pass with zero `stack-should-answer` questions, run against the Gate-1 freeze hashes; one open dependency (`TND-A7` TAM) is `severity: blocking-for-stated-audience` and is declared above and carried into the package as a pre-use hard stop. The stack is cleared for close-out with its gap on the record, not buried in a stamp — which is the whole point of the two-verdict design.
