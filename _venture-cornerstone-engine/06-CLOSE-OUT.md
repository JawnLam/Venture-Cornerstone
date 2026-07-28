---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-06-close-out"
title: "Venture Cornerstone Engine — 06 Close-Out"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: close-out-packaging-protocol
scope: subject-agnostic
---

# 06 — CLOSE-OUT (package & handoff)

> **A stack that passed both gates is not done until it is packaged.** This procedure turns the working cartridge into a **self-contained decision-and-execution dossier** whose test is one sentence, from the founder who commissioned it: *"There is a folder called `<Business>` — hand it to my investor / lender / operating partner and they can act on it, and hand it to me and I can execute it, with nothing else from me."* The primary consumer makes a decision (fund / lend / run week one); the founder then executes. The package serves both, and it must stand alone — a fresh AI, or a stranger, pointed at the packaged folder gets everything except the operator inputs the package itself registers (private data, taste calls, professional sign-offs — each with a when-to-ask trigger). **The NEW-STACK route is not complete at the Gate 2 SHIP verdict; it is complete when this procedure has run and its checklist is green. A cartridge left in working layout after ship is a defect, not a finished engagement.**

## Precondition

- Gate 2 verdict **SHIP or SHIP-WITH-DECLARED-GAPS** (`05-GATES.md`): the stranger decision test passed with a fresh instance, with **no `stack-should-answer` questions** outstanding. A SHIP-WITH-DECLARED-GAPS verdict may be packaged, but every `blocking-for-stated-audience` open dependency must be surfaced as a pre-use hard stop in the manifest and the operator-input register (steps 2–3).
- Gate 1 (consistency audit) clean, or every finding waived in writing; the `_freeze-hashes.md` freeze record exists.
- Every stack document at `vcs_Document_Status: stranger-passed`; the close-out step advances them to `shipped`.

If any precondition is unmet, do not package. Return to `05-GATES.md`; packaging a stack that has not shipped is the defect this precondition exists to catch.

## The target layout (final shape, exactly this)

The packaged top level contains **only one file plus three subfolders** — nothing else:

```
<Business>/
├── AI-BOOTSTRAP.md      # the BUSINESS's own bootstrap (not Venture Cornerstone's) —
│                        #   what this is, the decision/action it enables, TOC + precedence,
│                        #   operator-input register (with when-to-ask triggers), definition of done
├── Stack/               # the gated founding documents (the working `Artifacts/`, renamed at packaging),
│   │                    #   INCLUDING _assumptions-register.md (a decision document — the consumer needs it)
│   └── MANIFEST.md      #   file inventory with SHA-256s + gate verdicts + blocking-gap list
├── Records/             # non-essential history — founder interview, selection record, source log,
│   │                    #   stranger-test log, sessions (NOT the assumptions register — that lives in Stack)
│   └── README.md        #   declares: not needed to act; immutable
└── Workspace/           # the execution workspace, seeded at packaging
    ├── execution-state.md  # phase / done / next — updated every execution session (state lives in files)
    └── deviations.md       # the standing reconciliation rule (see step 4) → REVISE-STACK feedstock
```

Retargets Baseplate's `Construction/Records/Build` to `Stack/Records/Workspace` (Decision 9): "Stack" is audience-neutral where "construction" reads as software-build, and `Workspace/` exists because the founder also **executes** the stack — the deviations→REVISE-STACK loop needs a home.

## Procedure

### Step 1 — Restructure

1. Rename `Artifacts/` → `Stack/`. The `_assumptions-register.md` is already inside (it is a stack document per Decision 10) and stays in `Stack/`.
2. Move into `Records/`: `_founder-interview.md`, `_selection-record.md`, `_source-log.md`, `stranger-test-log.md`, `_freeze-hashes.md`, `_ov-manifest.md`, `_design-state.md`, and the whole `Sessions/` folder. **Do not move the assumptions register** — it belongs to the consumer, in `Stack/`.
3. Create `Workspace/` and seed its two files (step 4). Create `Records/README.md` (declares Records is history: not needed to act on or execute the stack, and immutable).
4. **Reference sweep on the new layout** (the cross-zone dangling-reference guard, package level): grep `Stack/` for the old folder name (`Artifacts`) and for every Records filename (`_founder-interview`, `_selection-record`, `_source-log`, `stranger-test-log`, `_freeze-hashes`, `_design-state`, `Sessions`). **Any hit inside a Stack document is a defect** — a stack document that reaches into `Records/` is not self-contained, and the consumer never receives `Records/` as decision input. Stack documents may reference only other `Stack/` contents — which now *includes* the assumptions register, so an in-line assumptions section citing `_assumptions-register.md` is legal (both are in `Stack/`). Records files may reference anything (they are history).

### Step 2 — Manifest (`Stack/MANIFEST.md`)

A table: every Stack document with its **SHA-256 and byte size**, plus the package date, the **Gate 1 result**, and the **Gate 2 verdict + rerun count**. Two hardening rules:

- **Hash continuity.** Each document's SHA-256 in the manifest must equal its `_freeze-hashes.md` value from Gate 1 (allowing only for the `Artifacts/`→`Stack/` rename). This proves the packaged bytes are the *audited-and-stranger-tested* bytes — nothing was edited between the gates and packaging. A mismatch means the stack changed after freeze and must return to Gate 1.
- **The verdict and its blocking gaps travel.** Record whether Gate 2 returned **SHIP** or **SHIP-WITH-DECLARED-GAPS**. On SHIP-WITH-DECLARED-GAPS, the manifest carries a **Blocking gaps** section listing every `blocking-for-stated-audience` open dependency (the assumption-ID, what it blocks, and the when-to-resolve trigger) — so the self-admitted disqualifier is on the cover page, not buried in a stamp. The consumer sees, before acting, exactly what must close first.

The consumer's first instruction (in the business bootstrap) is to verify this inventory — a partial copy, a sync-mangled file, or a tampered figure must be detected **before** anyone acts on the stack. Also record, per document: its Type (`VCS_*`), its band (L0–L6 / V / projection), its precedence rank, and any `requires-signoff-by` flag it carries. On any later revision (REVISE-STACK), regenerate the manifest — and its freeze hashes — in the same change.

### Step 3 — The business `AI-BOOTSTRAP.md`

The single top-level file — the **business's** own bootstrap, not the engine's. Required sections, in order:

1. **What this folder is** — the business one-liner (BI-1); the folder's claim (complete founding documents, both gates passed); the **decision or action it enables** — name the primary audience and the decision (as investor: fund / take the meeting; as lender: lend; as operating partner: run week one) and note that the founder also executes from it.
2. **Verify first** — check `Stack/MANIFEST.md` against the folder before reading further; on any hash or inventory mismatch, stop and report to the founder. Do not act on an unverified stack.
3. **Table of contents + precedence** — the three subfolders' roles, then every Stack document with a one-line purpose, its band, and its precedence rank. State the reading order (dependency-band order, L0→L6 then V, projections last) and where conflicts resolve (**the precedence declaration is law; a projection conforms to its source document, never the reverse**).
4. **Operator-input register** — a table of every input the consumer or executor will ever need from the founder that is **not** in the stack: `item | category | why it is needed | when to ask / resolve (trigger)`. Categories, all of which must appear:
   - **Professional sign-offs** — every `requires-signoff-by` flag (CPA on investor financials, securities attorney on the cap table, attorney on entity choice / operating agreements / IP), each with its trigger (*"before showing the financial model to an investor — CPA sign-off"*; *"before the entity is filed — attorney sign-off"*).
   - **Blocking declared gaps** — on a SHIP-WITH-DECLARED-GAPS verdict, every `blocking-for-stated-audience` open dependency from Gate 2, stated as a hard stop (*"the TAM is a placeholder [ASSUMPTION A-4]; replace with a sourced figure before any investor sees the market brief"*). These are not optional diligence; the stack itself says they must close before its stated audience acts.
   - **Staleness triggers** — every stack figure with a `valid-until` date, stated as a resolve-by trigger (*"CAC benchmark A-7 valid until 2027-01-31; re-verify before reusing the stack after that date — a REVISE-STACK time trigger"*). This keeps a stack that lives across quarters from silently aging.
   - Plus the founder's private/unavailable data, taste calls, and authorization preferences.

   This is the **complete** list: if an actor needs something from the founder that is not in this table, that is a package defect to report.
5. **Definition of done** — for the *consumer*: they can make the fund/lend/run decision from the stack alone (the stranger decision test is the standard, not prose polish). For the *founder executing*: point at the milestones/plan in L4/L5 and require that every `requires-signoff-by` hard stop is cleared by the named professional before the flagged document is used. "It reads well" is not done; the verification layer and the sign-off boundary are.
6. **Workspace rules** — all execution tracking goes in `Workspace/`; `Workspace/execution-state.md` is updated every session (state lives in files); Stack and Records files are never edited during execution — a needed change to the stack is a REVISE-STACK event, not an in-place edit.
7. **Deviations rule** — restate the standing rule from step 4 below.
8. **Records notice** — `Records/` is history (founder interview, selection rationale, source log, stranger-test log, freeze hashes, sessions): useful for *why* the stack is shaped as it is, but **not needed to act on or execute it**, and never to be modified. (The assumptions register is *not* here — it is a Stack decision document.)
9. **Provenance** — produced by Venture Cornerstone `<version>` (`vcs_` namespace); package date; Gate 1 result; Gate 2 verdict + rerun count; drafting-model note; and the **authority-boundary reminder** — this OV drafted these documents and did not bless any regulated document as compliant; the operator-input register's sign-off rows are load-bearing.

Identity discipline applies: the bootstrap names no human (founder, investor, professional) unless the founder explicitly provided a name for that role.

### Step 4 — Seed the execution workspace

- `Workspace/execution-state.md`: phase `not-started`; empty done / next / decisions sections; the instruction to update it every session.
- `Workspace/deviations.md`: the **standing reconciliation rule** — *when the founder (or an actor executing the stack) finds that reality has contradicted a stack document — the raise closed at a different valuation, a market figure proved wrong, a competitor moved, a cost came in higher — they do not silently edit the stack to match; they record the finding here and surface it. These entries are the raw material for REVISE-STACK (`05-GATES.md` § Revision), which re-runs only the affected gates and regenerates the manifest.* This is exactly the deviations→REVISE-STACK loop Decision 9 requires a home for.

### Step 5 — Packaging verification (both checks required)

1. **Mechanical:** every path the business bootstrap references exists; every `MANIFEST.md` hash matches its file **and equals its `_freeze-hashes.md` value from Gate 1** (continuity: packaged bytes = audited bytes); the step-1.4 reference sweep is clean (no `Artifacts` or Records-file references inside `Stack/`); every `blocking-for-stated-audience` gap on a SHIP-WITH-DECLARED-GAPS verdict appears in both the manifest and the operator-input register; the top level contains exactly the one file + three subfolders and nothing else.
2. **Fresh-instance ORIENTATION probe:** a fresh instance (no conversation history) receives only the packaged folder and is asked what it would do first. **Pass** = it verifies the manifest, correctly states what the business is and what decision the stack asks its primary audience to make, and identifies where it would start — **using only the bootstrap and the Stack documents**. This is a cheap orientation check, not a rerun of Gate 2 — but any missing or unresolvable reference it hits, or any place it has to reach into `Records/` to understand what to do, is a packaging defect: fix and re-probe.

### Step 6 — Close the cartridge

Advance every Stack document to `vcs_Document_Status: shipped`. Final write to `Records/_design-state.md` (phase: `packaged`; the packaging is the last entry) and a final session log in `Records/Sessions/`. Append any new failure mode this engagement surfaced to `_portfolio/failure-catalog.md` (REQ-M1), and **contribute every figure this engagement *verified* — a real CAC, an achieved LTV:CAC, a confirmed churn, a negotiated multiple — to `_portfolio/benchmark-library.md` (REQ-M2), anonymized per that file's aggregation rule** (never the business's identity, only the sector-tagged metric). Where the OV's own traceability is maintained, trace the new catalog/library entries in `_meta/TRACEABILITY.md` in the same change. This is the contribute half of the REQ-M2 flywheel whose consult half runs in generation (`04-GENERATION-STANDARDS.md`, standard 14). Then stop — the cartridge is closed.

## After packaging

- **The consumer and the founder never need Venture Cornerstone.** The packaged folder stands alone — copy it anywhere, hand it to any agent or any human; **no reference back to the Venture Cornerstone volume, its engine, or its portfolio may exist inside `Stack/` or the business bootstrap.**
- **REVISE-STACK on a packaged cartridge** edits `Stack/` in place (keep document IDs and figure IDs stable), re-runs only the affected gates, regenerates `Stack/MANIFEST.md`, **appends — never rewrites — `Records/`** (a new stranger-test-log entry, an appended assumptions-register row), and updates the business bootstrap only if the operator-input register, the TOC, or precedence changed. The `Workspace/deviations.md` entries are the feedstock for this route.

## Checklist (all boxes before the engagement is called done)

- [ ] Precondition met: Gate 2 verdict SHIP or SHIP-WITH-DECLARED-GAPS with no `stack-should-answer` questions; Gate 1 clean or waived in writing; `_freeze-hashes.md` present
- [ ] Final layout exact: one file (`AI-BOOTSTRAP.md`) + `Stack/` + `Records/` + `Workspace/` at top level, nothing else
- [ ] Reference sweep clean — no old-name (`Artifacts`) or Records-file references inside any `Stack/` document (no cross-zone dangling refs from `Stack/` into `Records/`)
- [ ] `Stack/MANIFEST.md` written; SHA-256s + byte sizes recorded and **equal to `_freeze-hashes.md`** (packaged = audited bytes); Gate 1 result + Gate 2 verdict (SHIP / SHIP-WITH-DECLARED-GAPS) + rerun count recorded; every `requires-signoff-by` flag and every `blocking-for-stated-audience` gap surfaced
- [ ] `_assumptions-register.md` is in `Stack/` (not Records); in-document assumptions sections cite it, not copy it
- [ ] Business `AI-BOOTSTRAP.md` contains all nine required sections, including the **complete operator-input register** with all four categories (sign-offs, blocking declared gaps, staleness triggers, private data) and their when-to-ask/resolve triggers
- [ ] Newly-verified benchmarks contributed to `_portfolio/benchmark-library.md` (anonymized); new failure modes to `_portfolio/failure-catalog.md`
- [ ] `Workspace/` seeded (`execution-state.md` + the `deviations.md` standing reconciliation rule)
- [ ] `Records/README.md` written (declares history, not needed to act, immutable)
- [ ] Mechanical packaging check green
- [ ] Fresh-instance orientation probe passed
- [ ] Every Stack document advanced to `shipped`; final state write + session log; `_portfolio/failure-catalog.md` (and `_meta/TRACEABILITY.md`) updated if anything new surfaced
