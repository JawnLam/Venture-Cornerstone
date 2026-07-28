---
Item_ID: "<UUID>"
type: VCS_Stranger_Test_Log
title: "<Business> — Stranger Test Log"
vcs_Business_Slug: ""
vcs_Doc_Class: "stranger-test-log"
vcs_Band: V                            # V — Verification (the ship gate); verifies L0–L4, never L5
vcs_Stranger_Model: ""                 # model family/version of the fresh instance (ideally a different family than the drafter)
vcs_Primary_Audience: ""               # investor | lender | operating-partner — sets which role the fixed prompt casts the stranger as
vcs_Audience_Bar: ""                   # BI-4b — the audience threshold ST-2 is judged against (mirrors the selection record's vcs_Audience_Bar)
vcs_Freeze_Hashes_Ref: ""              # points at the Gate-1 `_freeze-hashes.md`; this run is executed against those exact audited bytes
vcs_Run_Date:
vcs_Rerun_Count: 0
vcs_Result: ""                         # pass | blocked — no `stack-should-answer` question remains (ST-3)
vcs_Ship_Verdict: ""                   # SHIP | SHIP-WITH-DECLARED-GAPS — SHIP-WITH-DECLARED-GAPS iff any open dependency is `blocking-for-stated-audience` (see Blocking gaps)
vcs_Document_Status: drafting          # drafting | internally-consistent | audited | stranger-passed | shipped
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — Stranger Test Log

> The Typed record of the per-business ship gate (`05-GATES.md` Gate 2). A fresh model instance receives ONLY the frozen `Artifacts/` folder and a **verbatim, never-augmented** fixed prompt, cast in the stack's primary audience role; the evaluator scores below. **Any `stack-should-answer` question blocks ship** — fix the stack, rerun with a fresh instance. Questions are classified *charitably* (the evaluator-stance calibration lesson). The drafting session never plays the stranger. Runs only after Gate 1 (the consistency audit) is clean, and **against the Gate-1 freeze bytes** — every `Artifacts/` file must match its SHA-256 in `_freeze-hashes.md` before the folder is handed over, so the stranger provably reads the *audited* bytes, not a silently-edited copy (`vcs_Freeze_Hashes_Ref`).
>
> The gate emits one of two verdicts (Decision 10 issue 3): **SHIP** (clean) or **SHIP-WITH-DECLARED-GAPS** (Gate 2 otherwise passed but at least one open dependency is `blocking-for-stated-audience`). Honest stamping cannot launder an unready stack — an `[ASSUMPTION]` TAM the market brief says "must be replaced before any investor sees it" is a blocking gap, so the verdict is SHIP-WITH-DECLARED-GAPS, not a clean SHIP. ST-2 (decision plausibility) is judged against the **BI-4b audience bar** (`vcs_Audience_Bar`), not a generic reader.

## Run

- **Stranger model / date:** `<model family; different family than drafter if possible>` / `<YYYY-MM-DD>`
- **Primary audience (role the stranger is cast as):** `<investor | lender | operating-partner>`
- **Fixed prompt (verbatim, never augmented):**
  > *"You have been handed the complete founding documents for a business. As the [investor / lender / operating partner] they are meant for: (a) restate what this business is and what it is asking of you; (b) state the decision you would make and why; (c) list every question you would need answered before committing."*
- **Stranger outputs (a)/(b)/(c):** *archived verbatim below or linked.*

## Criteria

| # | Criterion | Observed | Pass/Fail | Triage |
|---|-----------|----------|-----------|--------|
| ST-1 | Restatement fidelity — (a) matches the business's actual identity and ask; a misread is a stack defect | | | |
| ST-2 | Decision plausibility — (b) is a reasonable decision consistent with the stack, judged against the **BI-4b audience bar** (`vcs_Audience_Bar`) | | | |
| ST-3 | Question classification — no `stack-should-answer` question remains in (c) | | | |

## Question classification table (ST-3 — the pass rule)

Every question from output (c) is classified. `operator-only` = the founder's private data, taste, professional sign-offs, or genuinely-unavailable facts. `stack-should-answer` = something the founding stack itself should have answered. Classify charitably.

| Question from output (c) | `operator-only` or `stack-should-answer` | Disposition |
|--------------------------|--------------------------------------------|-------------|
|                          |                                            |             |

*Any `stack-should-answer` row = ship block: fix the stack, freeze, rerun with a fresh instance. Two consecutive reruns blocked by the same question class → candidate `_portfolio/failure-catalog.md` entry (moat REQ-M1).*

## Ship verdict

- **`vcs_Ship_Verdict`:** SHIP or SHIP-WITH-DECLARED-GAPS.
- **SHIP** — Gate 2 clean and no `blocking-for-stated-audience` open dependency remains.
- **SHIP-WITH-DECLARED-GAPS** — Gate 2 otherwise passed, but ≥1 open dependency is blocking for the stated audience (see Blocking gaps). The MANIFEST surfaces the verdict and every blocking gap; honest stamping never launders an unready stack into a clean SHIP.

## Blocking gaps (the `blocking-for-stated-audience` open dependencies)

Open dependencies carry a `severity`: `blocking-for-stated-audience` (must be closed before the stated audience acts) or `non-blocking`. Every blocking gap listed here forces the SHIP-WITH-DECLARED-GAPS verdict and must appear in the packaged MANIFEST and the operator-input register.

| Open dependency | Severity | Why it blocks for this audience | Where surfaced (doc / assumption-ID) |
|-----------------|----------|---------------------------------|--------------------------------------|
|                 |          |                                 |                                      |

## Rerun log

| Rerun # | Date | Stranger model | Result | What changed since last run |
|---------|------|----------------|--------|-----------------------------|
| 0 | | | | initial run |

## Naming

- **Filename:** `stranger-test-log.md` in the cartridge root, kept **outside** `Artifacts/` (the stranger must never see its own scoresheet).
- **Type value:** `type: VCS_Stranger_Test_Log`.

## Relationships

- `VCS_Selection_Record` — *verifies (Gate 1 side: every earned document maps to a BI-answer, every exclusion recorded, every sign-off flag present)*.
- `VCS_Narrative_Document`, `VCS_Model_Document`, `VCS_Market_Document`, `VCS_Financial_Document`, `VCS_Plan_Document`, `VCS_Pitch_Document` — *verifies (the L0–L4 decision-bearing stack the stranger must act on; L5 operations are out of scope for this gate)*.
