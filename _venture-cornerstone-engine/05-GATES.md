---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-05-gates"
title: "Venture Cornerstone Engine — 05 Gates"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: gates
scope: subject-agnostic
---

# 05 — GATES (consistency audit, stranger decision test, revision)

> **A stack ships only after it passes the consistency audit and then the stranger decision test. The audit checks the stack's form — do the numbers reconcile, is every figure sourced or assumed, is every sign-off flagged. The stranger test executes its function — a fresh instance actually tries to make the fund / lend / run decision the stack exists to enable. Both are manually runnable with no tooling. Any failure: fix, or founder-waive with a written reason, and assess as a candidate `_portfolio/failure-catalog.md` entry (the REQ-M1 flywheel). The generation standards these gates enforce are in `04-GENERATION-STANDARDS.md`; the canon that decides which documents exist is `01-THE-CANON.md`.**

## Gate 1 — Consistency audit (run first)

Mechanical checklist over the frozen `Artifacts/` folder. Every document must already be at `vcs_Document_Status: internally-consistent` before the audit begins. Every item is a hard check:

- [ ] **Every figure reconciles across documents.** Each quantity that appears in more than one document — ARR, raise amount, valuation, unit price, gross margin, CAC, LTV, headcount, runway, TAM/SAM/SOM — agrees everywhere. The deck's ARR = the financial model's ARR = the plan's ARR = the executive summary's ARR. A figure that disagrees with its twin is a block (PF-6 cross-document number drift). Confirm each shared quantity is authored once in its home document and cited elsewhere by the same claim ID.
- [ ] **Every derived figure recomputes from its drivers (arithmetic identities).** Agreement across documents is necessary but *not sufficient* — a figure can match everywhere and still be arithmetically wrong. Every computed quantity must recompute from its stated driver values using the standard identity, or the audit blocks even though no twin disagrees. Check at least: **LTV = ARPA × gross-margin% ÷ churn-rate**; **CAC payback (months) = CAC ÷ (monthly revenue per customer × gross-margin%)**; **ARR = paying units × ARPA** (annualized); **LTV:CAC = LTV ÷ CAC**; **net burn = gross burn − revenue**; **runway (months) = current cash ÷ net monthly burn**; **ownership % from the cap table sums to 100%**; **each year's revenue = prior × (1 + stated growth)**. **Unit discipline:** an identity's inputs enter on the same period — ARPA and churn both annual or both monthly ("annualized" = ×12 on a monthly figure), and the runway identity states its cash convention as a named register line (current cash at t₀, or raise-only as a conservative post-raise floor — either is legal; silently mixing them is not). Recompute each from the assumptions-register drivers; a derived figure that does not reconcile with its own inputs is a hard block. This is the audit's headline check for a numbers-first OV — mechanical, reproducible, and the one Gate-1 item the reconciliation check cannot cover. The manual walkthrough and an optional runnable checker live in `_meta/ARITHMETIC-CHECK.md`.
- [ ] **Every figure is sourced-or-assumed.** Each market or financial number has exactly one provenance — founder-supplied, sourced-and-dated, or `[ASSUMPTION]`/`[UNVERIFIED]` — visible at the point of use, with a matching `_source-log.md` row (`claim-ID | quantity | source | date | method | verified? | provenance`). No un-sourced, un-assumed numbers anywhere in the stack. No `_source-log.md` row with `provenance = sourced` and `verified? = no` left standing.
- [ ] **The assumptions register is single-owned and travels in-folder.** The cartridge `_assumptions-register.md` is the single authored home for every named assumption (`assumption-ID | quantity | value | basis | owner | status | severity | valid-until | drives`), and it lives **inside** the frozen stack (`Artifacts/`, then `Stack/` at packaging) — for anyone judging the financial model, the register with owners and statuses is a decision document, not history. In-document assumptions sections **cite** the register by assumption-ID; they never re-author the values. Two authored copies of the same assumption is the OV's own PF-6/PF-8 defect and is a block. Every computed result traces to named assumption-IDs; no assumption is buried in prose.
- [ ] **Every open dependency carries a severity.** Each `[ASSUMPTION]`/`[UNVERIFIED]` figure and each register line at `status: open` is tagged `severity: blocking-for-stated-audience` or `non-blocking`. A dependency the stack *itself* says must be resolved before the stated audience acts — e.g., a placeholder TAM whose own document says "must be replaced before any investor sees it" — is `blocking-for-stated-audience`. This tag drives the Gate 2 verdict below (SHIP vs SHIP-WITH-DECLARED-GAPS); it is the check that stops honest `[ASSUMPTION]` stamping from laundering a self-admitted disqualifier into a clean pass.
- [ ] **Every comparative threshold resolves to a named extractable value (PF-9).** No "healthy CAC payback," "strong margin," "reasonable burn," "conservative growth" left as prose. Each judging threshold names its number, cites its basis, and states where the business lands against it.
- [ ] **Precedence declared and extractable.** The stack's precedence declaration exists as a field in `_selection-record.md`, not buried in prose, and every projection carries "the source document is law; the projection conforms." Confirm each projection cites its L0–L4 sources and restates nothing (a restated figure is a drift risk, not a citation).
- [ ] **Every `requires-signoff-by` document is flagged.** Every authority-boundary document — investor financials, cap table, entity choice, founder/operating agreements, IP, licenses, loan financials — carries its `requires-signoff-by` field naming the professional role. None is marked compliant, final, or blessed.
- [ ] **No orphan earned/excluded documents.** Every document present in `Artifacts/` maps back to a founder-interview answer (BI-n) via `_selection-record.md`; every excluded document class has a recorded exclusion with its triggering BI-answer. An unexplained inclusion is gold-plating; an unexplained exclusion is a defect. The unconditional set (L1 Model + V Verification) is present.
- [ ] **Cross-references resolve within `Artifacts/`.** Every internal reference — document, section, claim ID — points at something present in the frozen folder. The stranger receives only this folder.
- [ ] **No unresolved placeholders** (`[TBD]`, `[UNVERIFIED]`, `<...>`) outside their declared homes (open-questions section, assumptions register with `status: open`, or a `requires-signoff-by` flag).
- [ ] **Non-goals present** in every planning-bearing document (L2 GTM, L4 plan, L5 operations, projections).

Any unchecked box: fix, or founder-waive with a written reason recorded in the cartridge state (`_design-state.md`, or `_ov-manifest.md` for a single-session cartridge). Then re-run. When the checklist is clean, **freeze the stack: compute and record the SHA-256 of every `Artifacts/` file in a freeze record (`_freeze-hashes.md`, kept in the cartridge outside `Artifacts/`), and advance each document to `vcs_Document_Status: audited`.** Gate 2 runs against these exact bytes and the packaging manifest (`06-CLOSE-OUT.md`) re-verifies them — so a figure edited between the audit and the stranger test is caught, not trusted. Freezing on the honor system (declaring the folder frozen without hashing it) is the gap this step closes.

## Gate 2 — The Stranger DECISION Test (the ship gate — the heart)

Operationalizes the stack's defining claim: **a stranger who knows the sector can make the fund / lend / run decision from the frozen stack alone, with no further founder input.** A founding stack's one job is to make someone decide without the founder in the room; a fresh model instance handed only the folder *is* that someone, at negligible cost. If it cannot make the decision the stack asks for, the stack has failed at its one job — and the founder finds out here instead of in the meeting.

### Procedure

1. **Confirm the freeze, then hand over the folder.** Verify every `Artifacts/` file matches its `_freeze-hashes.md` SHA-256 from Gate 1 — the stranger must read the *audited* bytes, not a silently-edited copy. The stranger then receives *only* this folder. The folder **includes the assumptions register** — it is a stack document (Decision 10), because anyone judging the financial model needs the assumptions, owners, and statuses to form a decision. The stranger does **not** receive the founder interview, the selection record, the source log, the decisions log, or any conversation.
2. **A fresh model instance** — no conversation history, ideally a *different model family* than the one that drafted (substrate-agnosticism check) — receives the folder with the fixed prompt below, **verbatim, never augmented with hints**, retargeting only the bracketed audience *role* to the stack's primary audience (from BI-4 / the selection record: investor, lender, or operating partner). The audience *bar* from BI-4b (check size, stage thesis, stated must-sees) is not put in the prompt — it is what the evaluator judges ST-2 against (below), so the prompt stays a fixed template while the decision-plausibility bar is the real one:

   > *"You have been handed the complete founding documents for a business. As the [investor / lender / operating partner] they are meant for: (a) restate what this business is and what it is asking of you; (b) state the decision you would make and why; (c) list every question you would need answered before committing."*

3. **The evaluator** — the founder, or an agent that has read the stack but not the drafting conversation — scores three criteria:
   - **ST-1 · Restatement fidelity.** (a) matches what the business actually is and is asking. A misread is a **stack defect**, not a stranger defect — if the stranger got the business or the ask wrong, the stack failed to communicate it.
   - **ST-2 · Decision plausibility.** (b) is a reasonable decision, consistent with what the stack presents — the stranger can actually take the meeting / fund / lend / commit to run week one, or can articulate a coherent *no* grounded in the stack rather than in missing information. A stranger who cannot form any decision because the stack is too thin fails ST-2. **Judge plausibility against the audience bar from BI-4b** — the stated check size, stage thesis, and declared must-sees — not a generic reader: "plausible for a $25K angel" and "plausible for a $750K lead" are different claims, and the stack must clear the bar its stated audience actually applies. If BI-4b is unrecorded, that is a selection-record gap, not a licence to grade against the easiest reader.
   - **ST-3 · Question classification — the pass rule.** Classify every question in (c) as `operator-only` (the founder's private data, a taste call, a professional sign-off, or a fact genuinely unavailable at ship time) or `stack-should-answer` (something the documents should have established and did not). **Any `stack-should-answer` question is a ship block:** fix the stack, rerun with a fresh instance.
4. **Log** the run in a `VCS_Stranger_Test_Log` (kept in `stranger-test-log.md`, outside `Artifacts/`): stranger model + date, the verbatim prompt used, the verbatim outputs archived, per-criterion results, the full question-classification table, and the rerun count.

### Anti-gaming rules

- **The drafting session never plays the stranger.** The instance that wrote the stack cannot evaluate it — it knows what the documents meant to say, not what they say.
- **Reruns use fresh instances.** No conversation carryover between runs.
- **The fixed prompt is used verbatim and is never augmented.** In particular, do not instruct the stranger to "classify, count, be exhaustive, or be adversarial." That inflates `stack-should-answer` findings and makes the gate unreproducible.
- **Two consecutive reruns blocked by the same question class** → candidate `_portfolio/failure-catalog.md` entry (a recurring blind spot in how the OV generates that document class).

### Evaluator stance (reproducibility — classify CHARITABLY)

Classify **charitably**. A question is `operator-only` if a *competent, sector-literate reader* would naturally take it to the founder — the founder's private numbers not yet disclosed, a taste or strategy call, a professional sign-off the stack already flags `requires-signoff-by`, or a fact genuinely unavailable at ship time (a signed term sheet, a regulatory ruling not yet issued). A question is `stack-should-answer` **only if** the documents' silence would make two competent readers reach *observably different decisions* — a missing revenue model, an unstated raise amount, a market claim with no basis, an unresolved comparative threshold (PF-9). Do not count questions an adversary could invent but a real investor or lender would not ask — pedantic edge cases the stack's non-goals already bound, or diligence a reasonable reader defers until after a positive initial decision. The gate measures whether the stranger can **decide**, not whether the stack is exhaustive. *(Calibration lesson, ported from Baseplate's Linkrot shakedown: an over-adversarial evaluator prompt produced 24 findings on a stack a charitable canonical-prompt run passed cleanly. Over-adversarial evaluation makes the gate un-passable and un-reproducible.)*

### The ship verdict (SHIP vs SHIP-WITH-DECLARED-GAPS)

"SHIP" is **not** binary once honest stamping is possible. Stamping a figure `[ASSUMPTION]` converts every hard question about it to `operator-only`, so a stack can pass ST-1/ST-2/ST-3 cleanly while carrying a self-admitted disqualifier in fine print — a placeholder TAM the market brief itself says "must be replaced before any investor sees it" is exactly this. The severity tag from Gate 1 resolves it. There are two passing verdicts:

- **SHIP** — ST-1 holds, ST-2 is plausible against the BI-4b bar, no `stack-should-answer` questions remain, **and no open dependency is tagged `blocking-for-stated-audience`.** The stack is cleared for close-out unconditionally.
- **SHIP-WITH-DECLARED-GAPS** — the three criteria pass, but **one or more open dependencies are `blocking-for-stated-audience`.** The stack may be packaged, but it is *not* ready for its stated audience as-is: every blocking gap must be surfaced as a pre-use hard stop in `Stack/MANIFEST.md` and in the business `AI-BOOTSTRAP.md`'s operator-input register (with a when-to-resolve trigger). The consumer is told, in the package itself, what must close before they can act — the gap cannot hide in a stamp.

A `stack-should-answer` question still blocks outright under both verdicts (fix and rerun). Record the verdict, the rerun count, and the list of blocking gaps in the `VCS_Stranger_Test_Log`. When the run reaches SHIP or SHIP-WITH-DECLARED-GAPS, advance every document to `vcs_Document_Status: stranger-passed`; the stack is cleared for close-out, and the verdict travels into the manifest.

## DILIGENCE-SIM (optional, NON-GATING)

Gate 2 is charitable and reproducible by design — it measures whether a fair, sector-literate reader can *decide*, not whether an adversary can *poke holes*. That leaves a real gap: nowhere in the pipeline does anyone play the skeptic, yet a founder walking into a room meets exactly that. DILIGENCE-SIM fills the gap **without touching reproducibility, because it never gates**:

- **What it is** — an optional adversarial read. A fresh instance is told to play a sector-literate skeptic (a partner in diligence, a credit committee) and attack the stack: challenge every number, name every risk, find the weakest claim.
- **Why it does not gate** — its findings are *material for the founder's objection map and risk register*, never ship blocks. Feeding adversarial findings into the pass/fail verdict is exactly the over-adversarial-evaluator mistake that made Baseplate's Linkrot run produce 24 false findings; DILIGENCE-SIM is quarantined from the verdict on purpose. The gate stays charitable and passable; the adversarial read stays sharp and useful.
- **When to run it** — after Gate 2 passes, if BI-4 includes investors or lenders. Its output seeds the objection-map / Q&A-prep document, may surface a risk for the risk register, and may reveal a `blocking-for-stated-audience` dependency the charitable gate let pass (routing it to the SHIP-WITH-DECLARED-GAPS verdict).
- **Findings format (one row per attack):** `finding | target (claim-ID / figure / risk) | class (objection / risk / blocking-gap candidate) | routed-to (objection-map row, risk-register row, or severity review)`. Every row lands somewhere — an adversarial finding with no routing is noise — and no row touches the Gate 2 verdict directly.

DILIGENCE-SIM is the adversarial surface the reproducible gate deliberately lacks — kept structurally separate so each does its own job.

## REVISE-STACK (the change-request protocol)

A shipped stack meets reality — a term sheet lands, a market number is disproven, the raise amount changes, a competitor moves — and must change. Do not hand-edit ad hoc. Two kinds of trigger fire the protocol: **event triggers** (a noticed contradiction, accumulated in the package's `Workspace/deviations.md`) and **time triggers** (a source-log row or assumptions-register line passes its `valid-until` date — decay, not contradiction). Time triggers matter because a stack living from a Q4-2026 close toward an H2-2028 raise silently ages: a figure past its `valid-until` is stale whether or not anyone "noticed," and re-opens the stack on the calendar. A material trigger of either kind runs the protocol:

1. **Change spec** — what reality contradicted, and which claims / assumptions / documents it invalidates. Record it (it feeds the failure catalog and, where a number changed, the benchmark library REQ-M2).
2. **Acceptance deltas** — what "fixed" means, expressed as changes to the affected figures, assumptions-register lines, and source-log rows.
3. **Affected-document edits** — edit only the documents the change touches; keep claim IDs stable so reconciliation still resolves. Re-tag any changed figure's provenance and update its `_source-log.md` row and any assumption it drives.
4. **Re-run only the affected gates** — Gate 1's reconciliation over the touched documents and their twins (a changed figure ripples to every document that cites it), and Gate 2 (a full fresh-instance decision test) **if** the change altered what the stranger must understand to decide — the ask, the model, the market claim, or the numbers. A cosmetic or operations-only edit that does not touch the decision re-runs Gate 1 only.
5. **Close-out** — cartridge state write + `_portfolio/failure-catalog.md` update, traced in `_meta/TRACEABILITY.md` in the same change.

## AUDIT-STACK

For a stack of any origin — even one this OV did not produce — run a **read-only** audit and emit a findings report. Do not edit the stack. A foreign stack will not carry Venture Cornerstone's apparatus (no `_selection-record.md`, no BI-answer mapping, no `_source-log.md`, no freeze hashes), so the audit runs in **degraded mode**: apply only the checks that travel, and never report a missing BB artifact as a stack defect. Half of Gate 1 presumes BB scaffolding; running it verbatim against a stranger's deck would degenerate to "you didn't use Venture Cornerstone," which is useless.

**Portable checks (these travel to any stack — they *are* the audit):**
- **Reconciliation** — the same quantity agrees across documents (deck ↔ model ↔ plan). The figures are on the page; no scaffolding needed.
- **Arithmetic identities** — every derived figure recomputes from its drivers (LTV, CAC payback, ARR, runway, ownership %). The single most valuable foreign-stack check: it needs nothing but the numbers.
- **Threshold parameterization (PF-9)** — every "healthy / strong / acceptable" judged against a named number, not an adjective.
- **Authority-boundary / sign-off presence** — every cap table, entity choice, agreement, and investor financial visibly carries, or lacks, a professional-sign-off flag. Absence is a real finding for any stack.
- **Stranger decision test** — the fresh-instance Gate 2 read runs on any folder; `stack-should-answer` questions and the SHIP / SHIP-WITH-DECLARED-GAPS verdict are portable findings.

**BB-native checks (do NOT travel — skip; do not report as defects):** source-log completeness, selection-record exclusion coverage, BI-answer mapping, register single-ownership, freeze-hash presence. A foreign stack lacking these is *un-instrumented*, not *defective*. Note the absence as "Venture Cornerstone provenance/selection apparatus not present — cannot verify," never as a failed check.

Emit findings in two buckets: **portable-check failures** (real defects in any stack) and **instrumentation gaps** (what BB could not verify because the apparatus is absent). This degraded-mode split is what earns the REQ-A2 (graceful scope boundaries) posture claim — AUDIT-STACK is genuinely useful on a stranger's materials, not a checklist that reports its own absence. It is the entry point for stress-testing a founder's existing materials before they walk into a room.

## Close-out (packaging is MANDATORY)

Passing the gates does **not** end the engagement.

**Per session:** end with a state write to `_design-state.md` (or a loud sandbox declaration for a single-session cartridge).

**Per cartridge (after Gate 2 `stranger-passed`):** run the **close-out packaging protocol — `06-CLOSE-OUT.md`.** Restructure the frozen stack into the handoff layout (`AI-BOOTSTRAP.md` + `Stack/` + `Records/` + `Workspace/`), write the `Stack/MANIFEST.md` (inventory, checksums, gate verdicts), write the business's own `AI-BOOTSTRAP.md` with its operator-input register and when-to-ask triggers, verify the package (mechanical check + a fresh-instance orientation probe), then the final state write and an append to `_portfolio/failure-catalog.md` with any new failure mode the engagement surfaced (and any newly-verified benchmark to `_portfolio/`'s benchmark library, REQ-M2), traced in `_meta/TRACEABILITY.md` in the same change. Only after the package verifies does every document advance to `vcs_Document_Status: shipped`. The full procedure is `06-CLOSE-OUT.md`; this pointer is a hard dependency, not a suggestion.
