---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-meta-validation-checklist"
title: "Venture Cornerstone Engine — Validation Checklist (manual gate walkthrough + OV invariants)"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: validation-checklist
scope: subject-agnostic
---

# Validation Checklist (manual gate walkthrough + OV self-consistency invariants)

> **Venture Cornerstone ships no validator by design.** Both gates are runnable by a human with a text editor and a second chat window, and the stranger decision test *cannot* be mechanized — it needs a fresh model instance, ideally of a different family. This file IS the tooling (BNF-1): the manual walkthrough of the two gates in `05-GATES.md`, the close-out packaging in `06-CLOSE-OUT.md`, and — because the engine must also police itself — the **OV self-consistency invariants** run on any engine change (BNF-6). The arithmetic-identities recompute has an optional runnable companion in `_meta/ARITHMETIC-CHECK.md`. Run this before shipping any stack. Every box is a hard check; an unchecked box is a ship block until fixed or waived in writing with a reason.

## Gate 1 — Consistency audit (per stack, run first)

Walk the frozen `Artifacts/` folder with a text editor. These are mechanical checks — no judgment call, just presence, agreement, and arithmetic:

- [ ] **Cross-document figure reconciliation.** Every quantitative claim agrees with its twin everywhere it appears — the deck's ARR = the financial model's ARR = the canvas's = the plan's; the TAM in the market doc = the TAM in the deck. Grep each headline number across all documents; **any figure that disagrees with itself between documents is a block** (PF-6 cross-document number drift).
- [ ] **Arithmetic identities — every derived figure recomputes from its drivers.** Agreement is consistency, not correctness. Recompute at least: LTV = ARPA × GM% ÷ churn (same period both sides); LTV:CAC = LTV ÷ CAC; CAC payback = CAC ÷ (monthly revenue per customer × GM%); ARR = paying units × ARPA (annualized); net burn = gross burn − revenue; runway = cash at t₀ ÷ net burn (cash convention stated as a named register line); ownership % sums to 100%; each year's revenue = prior × (1 + stated growth). A derived figure that does not reconcile with its own stated inputs is a **block** even though no twin disagrees. Manual protocol + optional checker: `_meta/ARITHMETIC-CHECK.md`.
- [ ] **Every figure sourced-or-assumed.** Every market or financial number traces to a dated `_source-log.md` row (with `valid-until`) OR a named `_assumptions-register.md` row. **No un-sourced, un-assumed numbers.** A figure with no source and no owner is a block.
- [ ] **Register single-owned and in-folder.** `_assumptions-register.md` lives inside `Artifacts/`; every in-document assumptions section **cites** register rows by ID and re-authors no value. Two authored copies of one assumption is a block (the OV's own PF-6/PF-8).
- [ ] **Every open dependency carries a severity** — `blocking-for-stated-audience` or `non-blocking`. A dependency the stack itself says must close before its stated audience acts, left untagged or tagged non-blocking, is a block (it feeds the Gate 2 verdict).
- [ ] **Projections cite, never restate.** Each projection (pitch deck, one-pager, executive summary) references its L0–L4 source documents rather than copying their content (PF-8).
- [ ] **Every earned document maps to a BI-answer.** Cross-check each stack document against `_selection-record.md`; **every exclusion is recorded** with its triggering BI-answer (an unexplained exclusion is a defect; an unexplained inclusion is gold-plating). Depth tier and audience bar recorded in the selection record.
- [ ] **Precedence declared and extractable** — the `_selection-record.md` states which document wins on conflict, in canonical `vcs_Doc_Class` values (not filenames), and within a projection "the source document is law."
- [ ] **No unresolved placeholders** (`[TBD]`, `[UNVERIFIED]`, `<...>`) outside their declared homes (open-questions section, register rows with `status: open`, or a `requires-signoff-by` flag).
- [ ] **Sensitivity table present** on every `VCS_Financial_Document`, each row flexing one named register assumption (standard 13).
- [ ] **Authority-boundary flags present** — every `requires-signoff-by` document (investor financials, cap table, entity choice, founder/operating agreements, IP, loan application) carries its professional-sign-off hard stop and is nowhere blessed as compliant.
- [ ] **Non-goals / out-of-scope present** in every planning document — scope is defined by both edges.
- [ ] **Cross-references resolve** — every internal reference (file, section, document ID, figure ID) points at something inside the frozen folder.
- [ ] **FREEZE on pass:** record the SHA-256 of every `Artifacts/` file in `_freeze-hashes.md` (cartridge root, outside `Artifacts/`). Clean documents advance to `vcs_Document_Status: audited`.

Any unchecked box: fix, or founder-waive with a written reason. Then re-run.

## Gate 2 — Stranger decision test (per stack — the ship gate)

- [ ] **Freeze confirmed:** every `Artifacts/` file matches its `_freeze-hashes.md` SHA-256 before hand-over — the stranger reads the audited bytes.
- [ ] The stranger receives **only** the frozen `Artifacts/` folder — which **includes `_assumptions-register.md`** — and *not* the interview, the selection record (or the BI-4b bar), the source log, or any conversation.
- [ ] A **fresh** model instance (no conversation history; ideally a different model *family* than the drafter) got the **verbatim** fixed prompt from `05-GATES.md`, retargeted only in the bracketed audience role. Never augmented with "classify / count / be adversarial."
- [ ] **ST-1 Restatement fidelity** — the stranger correctly restates what the business is and what it is asking. A misread is a **stack** defect.
- [ ] **ST-2 Decision plausibility — judged against the BI-4b audience bar** (check size, stage thesis, stated must-sees), not a generic reader.
- [ ] **ST-3 Question classification** — every question classified **charitably** as `operator-only` or `stack-should-answer`. **Any `stack-should-answer` question = ship block:** fix, rerun with a fresh instance.
- [ ] **Verdict recorded:** **SHIP** (no blocking gaps) or **SHIP-WITH-DECLARED-GAPS** (ST-1/2/3 pass but ≥1 open dependency is `blocking-for-stated-audience` — each listed with its resolve-by trigger, to travel into the manifest and operator-input register).
- [ ] The run is logged in the `VCS_Stranger_Test_Log` (stranger model + date, verbatim prompt, verbatim outputs, per-criterion results, classification table, verdict, blocking gaps, rerun count + rerun log).
- [ ] The drafting session did **not** play the stranger.

On a passing verdict, documents advance to `stranger-passed`. Optional afterward: the non-gating DILIGENCE-SIM (findings routed to the objection map / risk register — never to the verdict).

## Close-out packaging (per stack — after a passing Gate 2 verdict)

Walk the checklist at the end of `06-CLOSE-OUT.md`. Headline items:

- [ ] **Precondition** — Gate 2 verdict SHIP or SHIP-WITH-DECLARED-GAPS with no `stack-should-answer` questions; Gate 1 clean or waived; `_freeze-hashes.md` present.
- [ ] **Final layout exact** — business `AI-BOOTSTRAP.md` + `Stack/` + `Records/` + `Workspace/` at top level, nothing else. The assumptions register is in `Stack/`, **not** `Records/`.
- [ ] **Reference sweep clean** — grep `Stack/` for `Artifacts` (old name) and for every Records filename; no cross-zone dangling reference from a `Stack/` document into `Records/`.
- [ ] **`Stack/MANIFEST.md` written** — SHA-256s + byte sizes **equal to `_freeze-hashes.md`** (hash continuity: packaged = audited bytes); Gate 1 result; Gate 2 verdict + rerun count; every `requires-signoff-by` flag surfaced; on SHIP-WITH-DECLARED-GAPS, the **Blocking gaps** section on the cover.
- [ ] **Business `AI-BOOTSTRAP.md`** — all nine required sections, including the **complete four-category operator-input register** (professional sign-offs, blocking declared gaps, staleness triggers, private data) with when-to-ask/resolve triggers.
- [ ] **`Workspace/` seeded** — `execution-state.md` + the `deviations.md` standing reconciliation rule.
- [ ] **`Records/README.md`** — declares Records is history, not needed to act, immutable.
- [ ] **Packaging verification** — mechanical check green AND fresh-instance orientation probe passed.
- [ ] Every Stack document advanced to `shipped`; benchmarks contributed (anonymized) and failure modes appended to `_portfolio/`.

## OV self-consistency invariants (run on ANY engine change — BNF-6)

The engine polices businesses with gates; this list polices the engine with greps. **Decision 10's remediation edited six files and missed three — the fixed chapters contradicted the untouched ones.** These invariants encode that lesson: whenever any engine chapter, Type, or meta file changes, run every sweep below across `Artifacts/` (engine, Types, `_meta/`, and the worked example); every hit outside its sanctioned home is a defect to fix **in the same change**.

| # | Invariant | Sweep | Sanctioned exceptions |
|---|-----------|-------|----------------------|
| I-1 | The interview set is everywhere "BI-1..BI-13 (+ BI-4b)" | grep `BI-1..12`, `BI-1..BI-12` | design-cartridge history (`_design-decisions.md` D8, `_schema-draft.md`, session logs ≤005) |
| I-2 | The register lives **inside** the stack and is single-owned | grep `register` near `Records`/`cartridge root` in engine files | `06-CLOSE-OUT` step-1 text explaining what does NOT move |
| I-3 | The verdict vocabulary is two-valued | grep `Gate 2 SHIP` / `verdict SHIP` not followed by `or SHIP-WITH-DECLARED-GAPS` | none |
| I-4 | Freeze hashing exists between Gate 1 and Gate 2 | grep `freeze` in `05`, `06`, `BOOTSTRAP-NEW-BUSINESS`, this file — all four must mention `_freeze-hashes.md` | none |
| I-5 | Bare `PF-n` resolves against the **local** catalog | grep `PF-9` / `PF-8` / `PF-6` and check each against `_portfolio/failure-catalog.md` headings | explicit `Baseplate PF-n` prefixes |
| I-6 | `vcs_Doc_Class` values are canonical registry classes, never filenames | grep `vcs_Doc_Class:` across `_types/` + example; each value appears in the `03-SELECTION.md` registry or its doc-class discipline list | — |
| I-7 | Every backbone diagram matches Decision 9 + 10 (register in `Artifacts/`, `_freeze-hashes.md` at root) | eyeball the diagrams in `BOOTSTRAP-NEW-BUSINESS.md` + `06-CLOSE-OUT.md` | — |
| I-8 | The OV's own `Artifacts/MANIFEST.md` is regenerated **in the same change** as any `Artifacts/` edit | recompute SHA-256s; compare | — |
| I-9 | Status-field casing is `vcs_Document_Status` everywhere | grep `vcs_document_status` | none |
| I-10 | Arithmetic identities state their period discipline | grep the identity lists in `04` std 12, `05` Gate 1, this file — each carries the same-period rule | — |

## Overall

- [ ] Gate 1 clean — reconciliation **and** arithmetic identities — or every finding waived in writing; freeze hashes written.
- [ ] Gate 2 passed (verdict SHIP or SHIP-WITH-DECLARED-GAPS; zero `stack-should-answer`) with a fresh instance, against the freeze hashes, judged against the BI-4b bar.
- [ ] **Close-out packaging complete (`06-CLOSE-OUT.md` checklist green) — the engagement is not done at the verdict; it is done when the packaged dossier exists.**
- [ ] Any new failure mode added to `_portfolio/failure-catalog.md`, verified benchmarks contributed (anonymized), and both traced in `_meta/TRACEABILITY.md` in the same change.
- [ ] On any engine change: the OV self-consistency invariants above ran clean and `Artifacts/MANIFEST.md` was regenerated.
