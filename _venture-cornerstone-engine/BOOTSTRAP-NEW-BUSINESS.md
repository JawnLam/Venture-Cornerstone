---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-bootstrap-new-business"
title: "Venture Cornerstone Engine — Bootstrap New Business"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: cartridge-bootstrapping-prompt
scope: subject-agnostic
---

# BOOTSTRAP A NEW BUSINESS (open a business cartridge)

> **The founder wants a founding-document stack for a new business. This is your execution plan for the NEW-STACK route. Elicit before you generate. One question at a time. The deliverable is the packaged dossier, not a passed gate.**

Load `_portfolio/failure-catalog.md` in full at session start, before Step 1 — every step below is written to steer around a catalogued failure mode, and you cannot guard against entries you have not read.

## Step 1 — Open the cartridge

Create `{ROOT}/<Business-Name>/` (Title-Case-Hyphenated), with the working backbone (Decisions 9 + 10):

```
<Business-Name>/
├── _ov-manifest.md           # business identity (from the interview) — overwrite
├── _founder-interview.md     # the BI-1..BI-13 (+ BI-4b) record — append during interview, then frozen
├── _selection-record.md      # inclusions + exclusions with triggering BI-answer + precedence + ID scheme
│                             #   + financial depth tier + the BI-4b audience bar (`vcs_Audience_Bar`)
│                             #   — overwrite until locked at end of SELECT, then frozen (no drafting before it locks)
├── _source-log.md            # external figures/dependencies: claim | source | date | valid-until | method | verified?
│                             #   — append + per-row status; a row past valid-until is a REVISE-STACK time trigger
├── _freeze-hashes.md         # written at Gate 1 pass: SHA-256 of every Artifacts/ file (the freeze record)
├── Sessions/
├── Artifacts/                # THE STACK — the folder the stranger receives at Gate 2, INCLUDING:
│   └── _assumptions-register.md   # the SINGLE authored home for every assumption (owner | status |
│                             #   severity | valid-until); a decision document — it travels with the stack
└── stranger-test-log.md      # the Gate 2 record + verdict (kept at cartridge level, outside Artifacts/)
```

For a multi-session engagement, also add `_design-state.md` (cartridge phase + open threads); for a small single-session business it collapses into the manifest. The `_selection-record.md` (a `VCS_Selection_Record` Type) carries the inclusions/exclusions **and** the ID scheme + precedence declaration + depth tier + audience bar in one file. The `_assumptions-register.md` and `_source-log.md` are the data-discipline spine — populated from BI-12 onward, they are what Gate 1 audits every figure against. **The register lives inside `Artifacts/`** (Decision 10 issue 2): anyone judging the financial model needs the assumptions, owners, statuses, and severities, so the stranger receives it. The BI-4b bar does **not** enter any stack document — it anchors the evaluator, not the stranger.

## Step 2 — Interview (`02-ELICITATION.md`)

Run the founder interview **one question at a time** — never a numbered questionnaire. Capture **BI-1..BI-13, plus BI-4b** in `_founder-interview.md`; for each answer note which selection decision it shapes. Open with BI-1 (one-liner) and BI-2 (stage — the single most selection-shaping answer). **BI-4b (the audience bar)** captures the primary audience's threshold — check size, stage thesis, stated must-sees — and is what Gate 2's ST-2 decision-plausibility is judged against. **BI-13 (current cash on hand + current burn)** is a mandatory financial-model input — without it, runway math silently assumes `$0` starting cash. Probe vague answers; treat every number the founder states as an input to log (source log or assumptions register), not a fact to trust silently. Do not select or draft mid-interview. Reflect the whole picture back in three or four sentences and confirm before proceeding. Then freeze `_founder-interview.md`.

## Step 3 — Select (`03-SELECTION.md`)

Walk the class registry against the interview answers. **Unconditional:** the L1 Model document and the V layer (consistency audit + stranger test + assumptions register + source log). Everything else is earned — record every inclusion **and every exclusion** with its triggering BI-answer (an unexplained exclusion is a defect; an unexplained inclusion is gold-plating). Lock the ID scheme, the precedence declaration, the **financial depth tier** (`full` vs `summary`, keyed to BI-2/BI-3 — an auditable field, not a drafting-time improvisation), and the **audience bar** (`vcs_Audience_Bar`, from BI-4b) in the `VCS_Selection_Record`. Flag every `requires-signoff-by` document (L6 legal, investor financials, cap table) here so the authority boundary is visible before drafting. **Selection locks before any drafting** — no document prose exists until the selection record is frozen.

## Step 4 — Generate (`04-GENERATION-STANDARDS.md`)

Draft each selected document from its structural `VCS_*` Type and required sections, in **dependency-band order** (L0→L6, then V; projections last, because a projection cites its L0–L4 source documents and cannot precede them). Enforce the data discipline on every figure: founder-supplied, or sourced-and-dated, or stamped `[ASSUMPTION]`/`[UNVERIFIED]` and routed to the founder — logged in `_source-log.md` (with `valid-until`) and `_assumptions-register.md` (with `severity` + `valid-until`). **The register is single-owned:** in-document assumptions sections cite `_assumptions-register.md` rows by ID and never re-author a value. **Every derived figure shows its computation from named driver IDs** (standard 12 — periods matched), every `VCS_Financial_Document` carries its **sensitivity table** (standard 13), and every estimate is **checked against `_portfolio/benchmark-library.md`** before it is entered as plausible (standard 14). The same quantity must agree everywhere it appears (deck ARR = model ARR = plan ARR). End each document with its internal consistency pass; advance it to `vcs_Document_Status: internally-consistent`.

## Step 5 — Gate (`05-GATES.md`)

Run **Gate 1** (the consistency audit): every figure reconciles across documents **and every derived figure recomputes from its drivers** (the arithmetic-identities check — agreement is not correctness); every figure sourced-or-assumed; the register single-owned and in-folder; every open dependency severity-tagged; every earned document maps to a BI-answer and every exclusion is recorded; precedence declared; every `requires-signoff-by` hard stop flagged. On a clean audit, **freeze the stack: record the SHA-256 of every `Artifacts/` file in `_freeze-hashes.md`**, and advance clean documents to `audited`. Then run **Gate 2** (the stranger decision test): confirm the freeze hashes, then a fresh model instance — ideally a different family — gets only the frozen folder (register included) and the verbatim, never-augmented audience-targeted prompt. ST-2 is judged against the **BI-4b bar**, not a generic reader. **Any `stack-should-answer` question blocks ship** — fix and rerun with a fresh instance. The gate emits **SHIP** or **SHIP-WITH-DECLARED-GAPS** (one or more `blocking-for-stated-audience` open dependencies — packageable, but every blocking gap must travel to the manifest and operator-input register as a pre-use hard stop). Classify questions charitably; the drafting session never plays the stranger. Log the run and verdict in the `VCS_Stranger_Test_Log`; on a passing verdict, advance documents to `stranger-passed`. Optionally run the non-gating **DILIGENCE-SIM** afterward to seed the objection map and risk register.

## Step 6 — Close-out packaging (mandatory — the engagement is not done without it)

Run **`06-CLOSE-OUT.md`** in full. **The deliverable of this route is the packaged dossier, not a passed stranger test** — a stack left in working layout after a passing Gate 2 verdict is a defect. Restructure the cartridge to the handoff layout (top level = the business `AI-BOOTSTRAP.md` + `Stack/` + `Records/` + `Workspace/`; the assumptions register stays in `Stack/`); write `Stack/MANIFEST.md` (SHA-256s **equal to the freeze hashes** — hash continuity — plus the Gate 2 verdict and, on SHIP-WITH-DECLARED-GAPS, the blocking-gaps section); write the business bootstrap (what this is + the decision it enables, TOC + precedence, the complete operator-input register with all four categories — professional sign-offs, blocking declared gaps, staleness triggers, private data — each with its when-to-ask/resolve trigger; definition of done; deviations rule; provenance); seed `Workspace/` (`execution-state.md` + the `deviations.md` standing reconciliation rule); run the packaging verification (mechanical check + fresh-instance orientation probe); advance documents to `shipped`; final state write; append any new failure mode to `_portfolio/failure-catalog.md` and **contribute every verified figure to `_portfolio/benchmark-library.md`** (anonymized per its aggregation rule). Then stop — the cartridge is closed.

## Quality gates before the engagement is called done

- [ ] Interview BI-1..BI-13 (+ BI-4b) captured one at a time; `_founder-interview.md` frozen
- [ ] Selection locked with inclusions **and** exclusions recorded against their triggering BI-answers; ID scheme + precedence + depth tier + audience bar declared; `requires-signoff-by` flags set
- [ ] Every selected document `internally-consistent`; every derived figure shows its computation from register IDs (periods matched); every financial document carries its sensitivity table
- [ ] Every figure sourced-and-dated (with `valid-until`) or stamped as a named assumption (with `severity`); register single-owned, cited not copied, inside `Artifacts/`
- [ ] Gate 1 clean — reconciliation **and** arithmetic identities — or every finding waived in writing; `_freeze-hashes.md` written at freeze
- [ ] Gate 2 run against the freeze hashes with a fresh instance; ST-2 judged against the BI-4b bar; verdict **SHIP** or **SHIP-WITH-DECLARED-GAPS** with zero `stack-should-answer` questions; logged in the `VCS_Stranger_Test_Log`
- [ ] Authority boundary honored — no regulated document blessed as compliant; every sign-off in the operator-input register
- [ ] **Close-out packaging complete — the full `06-CLOSE-OUT.md` checklist is green** (final `Stack/`+`Records/`+`Workspace/` layout, manifest with hash continuity + verdict + blocking gaps, business bootstrap with the four-category operator-input register, seeded `Workspace/`, packaging verification incl. orientation probe)
- [ ] `_portfolio/failure-catalog.md` updated and verified benchmarks contributed to `_portfolio/benchmark-library.md` at close if anything new surfaced

## Failure modes to avoid — load the full `_portfolio/failure-catalog.md` at session start

The catalogued modes this route is built to prevent (the full entries, with their guards, live in the portfolio — load it before Step 1, not from this summary):

- **Market/financial fabrication (PF-1)** — an invented TAM, growth rate, or comparable multiple that detonates in front of an audience who knows the sector. Guard: verify-or-flag on every figure; benchmark-library consult.
- **Silent assumption absorption (PF-5)** — a buried financial-model assumption treated as fact. Guard: the single-owned assumptions register, cited not copied.
- **Projection restatement (PF-8)** — a projection (deck, one-pager, exec summary) that restates rather than cites its sources and drifts. Guard: projections cite; Gate 1 checks restatement drift.
- **Cross-document figure disagreement (PF-6)** — the deck's ARR ≠ the model's ARR. Guard: cross-document reconciliation is a Gate 1 block.
- **Consistent-but-wrong numbers** — every twin agrees and the arithmetic is still wrong. Guard: the arithmetic-identities recompute (Gate 1; standard 12).
- **Stamping-as-laundering** — an honest `[ASSUMPTION]` hiding a self-admitted disqualifier. Guard: severity tags + the SHIP-WITH-DECLARED-GAPS verdict.
- **Gold-plating (PF-4)** — a document included "because it's customary" (a bootstrapped micro-business does not earn a cap table). Guard: every inclusion cites its BI-answer.
- **Orphan documents / exclusions (PF-3)** — a document with no triggering BI-answer, or an exclusion left unrecorded. Guard: the selection record captures both edges.
- **Stale-context carryover (PF-2)** — reusing another business's interview answers or figures, or a figure aging past its `valid-until` inside this cartridge. Guard: every business earns its own answers; time-triggered REVISE-STACK.
- **Authority-boundary breach (PF-7)** — blessing a regulated document as compliant. Guard: flag the professional sign-off; never advise.
