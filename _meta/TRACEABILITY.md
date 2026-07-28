---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-meta-traceability
title: "Venture Cornerstone — Traceability Matrix"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-meta
role: traceability-matrix
scope: subject-agnostic
---

# Venture Cornerstone — Traceability Matrix

> **Walk this, not memory, when auditing Venture Cornerstone itself (BNF-3, inherited from OVE's Convention 13). Each row traces one Venture Cornerstone requirement through the engine mechanism that enforces it, the gate/verification that checks it, and the failure mode it prevents. When you add or amend a BFR/BNF requirement, a gate, a Type, or a PF failure mode, update this file in the same change.**

Requirement families: **BFR-n** functional (the Baseplate OFR analog), **BNF-n** non-functional (the ONF analog). The data-discipline and authority-boundary requirements (BFR-17..27) are the business-native additions Baseplate has no equivalent of; they exist because `domain_stakes: high` and the stack lives or dies on its numbers.

## Requirements → enforcement → verification → failure prevented

| Requirement | Enforcement (engine) | Verification | Failure prevented |
|---|---|---|---|
| BFR-1 founder interview one-at-a-time (BI-1..BI-13 + BI-4b) | `02-ELICITATION.md` | golden-session constitutional criterion (elicit-before-generate); stranger test | PF-2 (carryover) |
| BFR-2 interview record cited by selection | `02-ELICITATION.md`; `VCS_Selection_Record` | Gate 1 (selection cites BI-answers) | PF-4; PF-5 |
| BFR-3 apply selection protocol (menu, not mandate) | `03-SELECTION.md` registry | Gate 1; stranger test | PF-4 (gold-plating) |
| BFR-4 record inclusions + exclusions with BI-trigger | `03-SELECTION.md`; `VCS_Selection_Record` | Gate 1 (every doc maps to a BI-answer) | PF-4 |
| BFR-5 precedence declared + extractable | `VCS_Selection_Record` (extractable field) | Gate 1 (precedence present, no unresolved placeholders) | PF-6; PF-8 |
| BFR-6 generation standards; data discipline (verify-or-flag) | `04-GENERATION-STANDARDS.md`; `_source-log.md` | Gate 1 (every figure sourced-or-assumed) | PF-1 (fabrication); PF-2 |
| BFR-7 write for the stranger (self-contained, terms in-stack) | `04-GENERATION-STANDARDS.md` std 8 | stranger test (ST-1/ST-3) | PF-5 |
| BFR-8 sequence — selection locks before drafting (F8) | `00-START-HERE.md`; `BOOTSTRAP-NEW-BUSINESS.md` | golden session (lock order) | — |
| BFR-9 Gate 1 consistency audit | `05-GATES.md` Gate 1 | run per cartridge (incl. arithmetic identities + freeze hashing; `_meta/ARITHMETIC-CHECK.md`) | PF-1/2/3/5/6/7/8/9 |
| BFR-10 Gate 2 stranger DECISION test = ship gate | `05-GATES.md` Gate 2 | run per cartridge; `VCS_Stranger_Test_Log` (verdict: SHIP / SHIP-WITH-DECLARED-GAPS) | — |
| BFR-11 triage + catalog-feed at close-out | `05-GATES.md`; `_portfolio/failure-catalog.md` | close-out check | — |
| BFR-12 portfolio failure catalog (moat REQ-M1) | `_portfolio/failure-catalog.md` (Grows-Through-Use Zone, Decision 5) | seeded PF-1..PF-9; loaded at session start | all PF |
| BFR-13 persist per-cartridge state | backbone state files; Q11 contract (Decision 9) | close-out state write | PF-2 |
| BFR-14 revision mode (REVISE-STACK) | `05-GATES.md § Revision`; Workspace deviations feedstock | revision pass | — |
| BFR-15 quantitative completeness — every threshold parameterized, bijection total | `04-GENERATION-STANDARDS.md`; `_meta/TRACEABILITY.md` (this file) | Gate 1 (extractability + no orphans); stranger test (ST-3) | PF-3 (orphans); PF-9 (unparameterized threshold) |
| BFR-16 close-out packaging — shipped stack → self-contained dossier (`AI-BOOTSTRAP` + `Stack/`+`Records/`+`Workspace/` + MANIFEST, Decision 9) | `06-CLOSE-OUT.md`; pointed at from `00-START-HERE.md`, `05-GATES.md § Close-out`, `BOOTSTRAP-NEW-BUSINESS.md` | `06-CLOSE-OUT.md` checklist: mechanical packaging check + fresh-instance orientation probe | un-handoffable "finished" cartridges; cross-zone dangling reference at package level |
| BFR-17 cross-document numeric reconciliation (`reconciles-with`) | `04-GENERATION-STANDARDS.md` (one owning document per quantity) | Gate 1 (every figure reconciles with its twin) | PF-6 (number drift) |
| BFR-18 single-owned assumptions register — cited, never copied; travels in the stack | `04-GENERATION-STANDARDS.md` std 6; `_assumptions-register.md` (in `Artifacts/`→`Stack/`) | Gate 1 (single-owner + no un-sourced, un-assumed numbers) | PF-5 (silent absorption); PF-1; the OV's own PF-6/PF-8 (register authored twice) |
| BFR-19 source log + verify-or-flag on every external figure | `04-GENERATION-STANDARDS.md`; `_source-log.md` (claim\|source\|date\|valid-until\|method\|verified?) | Gate 1 (source-log complete; figures dated); REVISE-STACK time trigger past `valid-until` | PF-1; PF-2 (incl. in-cartridge decay) |
| BFR-20 projections cite, never restate (`projects-from`) | `01-THE-CANON.md` projection rule ("source is law; projection conforms") | Gate 1 (projection figures reconciled to source; restatement-drift check) | PF-8 (projection restating) |
| BFR-21 professional-sign-off flag on regulated docs (`requires-signoff-by`) | `01-THE-CANON.md` (L6 + cap table + investor financials flagged); authority boundary (Decision 4) | Gate 1 (every requires-signoff-by doc carries its hard stop) | PF-7 (missing sign-off flag) |
| BFR-22 benchmark/comparables library (moat REQ-M2) | `_portfolio/benchmark-library.md` — CONSULT (`04` std 14) + CONTRIBUTE (`06` step 6) + k-anonymity N≥3 | generation-time consult; close-out contribution check | PF-1 (reuse vetted numbers, not invented ones); M4 confidentiality leak |
| BFR-23 arithmetic identities — every derived figure recomputes from its drivers, periods matched | `04-GENERATION-STANDARDS.md` std 12; `05-GATES.md` Gate 1 | Gate 1 recompute; `_meta/ARITHMETIC-CHECK.md` (manual protocol + optional checker) | consistent-but-wrong numbers (agreement ≠ correctness) |
| BFR-24 sensitivity table on every financial document | `04-GENERATION-STANDARDS.md` std 13; `03-SELECTION.md` required sections | Gate 1 (table present; each row cites its register ID) | fragility hidden behind a point estimate |
| BFR-25 dependency severity + conditional ship verdict | `04-GENERATION-STANDARDS.md` std 6; `05-GATES.md` Gates 1–2; `06-CLOSE-OUT.md` manifest | Gate 2 verdict (SHIP / SHIP-WITH-DECLARED-GAPS); manifest blocking-gaps section | honest `[ASSUMPTION]` stamping laundering an unready stack |
| BFR-26 freeze-hash integrity — audited bytes = stranger-tested bytes = packaged bytes | `05-GATES.md` Gate 1 freeze + Gate 2 step 1; `06-CLOSE-OUT.md` hash continuity | `_freeze-hashes.md` ↔ `Stack/MANIFEST.md` equality | honor-system freeze; silent edits between gates |
| BFR-27 audience bar recorded and anchoring ST-2 — never inside the stack | `02-ELICITATION.md` BI-4b; `VCS_Selection_Record`/`VCS_Stranger_Test_Log` `vcs_Audience_Bar` | Gate 2 ST-2 judged against the bar; bar absent from the frozen folder | unanchored decision-plausibility; grading rubric leaked to the stranger |
| BNF-1 markdown-only, manual gates | whole engine; `_venture-cornerstone-engine/_meta/VALIDATION-CHECKLIST.md` | manual gate walkthrough | — |
| BNF-2 context-budget / tiered reads | `00-START-HERE.md` read tiers | read-tier compliance (golden session) | — |
| BNF-3 Venture Cornerstone traces in its own matrix | this file | audit walks this matrix | orphan requirement/check |
| BNF-4 P7 identity discipline throughout | `AI-BOOTSTRAP.md`; Type attribution rules | scrub at SHIP-PREP | identity inference |
| BNF-5 complete cartridge self-contained — stranger gets only the frozen `Artifacts/` folder (which includes the assumptions register; the selection record and BI-4b bar stay behind) | `05-GATES.md` (Artifacts-only at Gate 2) | stranger test (freeze hashes confirmed before hand-over) | cross-zone dangling reference |
| BNF-6 engine cross-file invariants hold on any engine change | `_venture-cornerstone-engine/_meta/VALIDATION-CHECKLIST.md` § OV self-consistency invariants | grep sweep per invariant; OV `MANIFEST.md` regenerated in the same change | propagation drift (edited chapters contradicting untouched ones) |

## Failure modes (portfolio catalog)

Every `PF-n` in `_portfolio/failure-catalog.md` (PF-1..PF-9 seeded at design time — the transferable Baseplate modes ported and the business-native modes named when the data discipline and the two gates were locked) appears above as a "failure prevented." New PF entries added at cartridge close-out must be traced here in the same change (BNF-3).

- **PF-1 (market/financial figure fabrication)** — prevented by BFR-6/BFR-19 (the data discipline: the OV never invents a figure; every figure sourced-or-assumed) and caught at Gate 1.
- **PF-2 (stale-context carryover)** — prevented by BFR-19's anti-staleness rule (every imported figure carries source + verification date) and BFR-1 (no BI-answer carried without re-asking).
- **PF-3 (orphan requirement/verification)** — prevented by BFR-15 (the bijection is total; every figure sourced-from a source or a named assumption, every document earned-by a BI-answer) and caught at Gate 1 in both directions.
- **PF-4 (gold-plating)** — prevented by BFR-3/BFR-4 (every inclusion AND exclusion cites its triggering BI-answer; unconditional set = L1 Model + V only).
- **PF-5 (silent assumption absorption)** — prevented by BFR-18 (mandatory assumptions register; a number neither supplied nor sourced is an assumption, entered as a first-class row, never bare prose).
- **PF-6 (cross-document number drift)** — prevented by BFR-17 (`reconciles-with` is Gate 1's spine; one owning document per quantity; any figure that disagrees with its twin is a hard block).
- **PF-7 (missing professional-sign-off flag)** — prevented by BFR-21 (canon flags every L6 document + cap table + investor financials `requires-signoff-by`; Gate 1 checks the hard stop is present; the OV never blesses a document as compliant).
- **PF-8 (projection restating instead of citing)** — prevented by BFR-20 (projections `projects-from` their sources and cite, never restate; Gate 1 reconciles projection figures to their source and flags duplicated content). Baseplate's PF-9 (enumeration-drift) discipline applied to the projection layer — locally this failure mode is PF-8.
- **PF-9 (unparameterized acceptance threshold)** — prevented by BFR-15 extended to L4 financial values: every comparative phrase in a success metric ("healthy," "target," "acceptable") must resolve to a named, extractable field (an assumptions-register row or a model cell); checked during generation and at Gate 1's extractability check.

## Orphans

Goal: empty. Disposition each: `gap — needs enforcement`, `gap — needs verification`, or `intentional`.

- **O-1 · REQ-M1 flywheel — SEEDED, not yet demonstrated (2026-07-27).** The moat mechanism (`_portfolio/failure-catalog.md`) is committed and seeded with PF-1..PF-9, but no real business cartridge has yet run end-to-end to grow a use-derived entry (the analog of Baseplate's Linkrot/Datestamper first catches). The compounding loop — real cartridge → new failure mode → catalog entry → loaded at next session start → failure recurs less — is designed and seeded but not yet fired. Disposition: **intentional (design phase)**; demote to "demonstrated" after the first cartridge close-out grows the catalog. Discharged the same way Baseplate discharged its O-1.
- **O-2 · REQ-M2 benchmark library — MECHANISM BUILT, store not yet populated (updated 2026-07-27, Decision 10 issue 4).** The store now exists as `_portfolio/benchmark-library.md` with a full mechanism: a schema, a CONSULT step (generation standard 14), a CONTRIBUTE step (close-out step 6), and a k-anonymity (N≥3) aggregation rule resolving the M4/confidentiality contradiction. What remains is *population* — no cartridge has yet contributed verified figures. Disposition: **intentional (design phase)** — the mechanism is specified and both halves of the flywheel are wired; the store fills per engagement. Upgraded from "committed, no mechanism" to "mechanism built, awaiting first contribution."
- Gap count: **0** structural gaps (O-1 and O-2 are intentional design-phase seeds, not enforcement/verification gaps). Every BFR/BNF row above has a named enforcement mechanism and a named verification.

## Decision 10 — self-audit remediation traceability (2026-07-27)

The OV's own gates were turned on the OV (a Gate-1-style consistency check + a stranger read against Venture Cornerstone as if it were a cartridge). Twelve defects surfaced; each fix is traced here — new mechanism → enforcement site → verification → failure it prevents.

| # | New mechanism | Enforcement site | Verification | Prevents |
|---|---|---|---|---|
| 1 | Arithmetic-identities check (derived figures recompute from drivers) | `04` std 12 (transparency) + `05` Gate 1 | Gate 1 recomputes each derived figure | A stack whose numbers agree everywhere but are arithmetically wrong |
| 2 | Single-owned assumptions register, travels in `Stack/` | `04` std 6 + `05` Gate 1 + `06` step 1 | Gate 1 (single-owner, cited-not-copied); packaging (in Stack) | The OV's own PF-6/PF-8 (register authored twice); a decision doc buried in Records |
| 3 | Dependency severity + SHIP / SHIP-WITH-DECLARED-GAPS verdict | `05` Gate 1 (severity) + Gate 2 (verdict) + `06` manifest | Gate 2 verdict; manifest surfaces blocking gaps | Honest `[ASSUMPTION]` stamping laundering an unready stack |
| 4 | Benchmark library (consult + contribute + k-anonymity) | `_portfolio/benchmark-library.md`; `04` std 14; `06` step 6 | Close-out contribution; generation consult | REQ-M2 being a commitment with no mechanism; M4 confidentiality leak |
| 5 | Sensitivity table + BI-13 current cash | `04` std 13; `02` BI-13; `03` financial required sections | Gate 1 (financial docs carry the table); interview captures BI-13 | Fragility hidden behind a point estimate; runway silently assuming $0 cash |
| 6 | BI-4b audience bar → ST-2 anchor | `02` BI-4b; `05` Gate 2 ST-2 | ST-2 judged against the stated bar | Unanchored "decision plausibility" (angel vs lead conflated) |
| 7 | `valid-until` + time-based REVISE triggers | `04` std 5/6; `05` REVISE; `06` operator register | REVISE time trigger; operator-register staleness rows | A stack silently aging across quarters |
| 8 | Risk register, traction pack, objection map, depth tiers, DILIGENCE-SIM (non-gating) | `01` menu; `03` registry + depth tiers; `05` DILIGENCE-SIM | Selection registry; non-gating sim feeds risk/objection docs | No adversarial surface anywhere; improvised financial depth |
| 9 | AUDIT-STACK degraded mode (portable vs BB-native) | `05` § AUDIT-STACK | Two-bucket findings report | AUDIT reporting "you didn't use Venture Cornerstone"; earns REQ-A2 |
| 10 | Golden session = 4 articles; freeze-hash before Gate 2 | `golden-session-script.md`; `05` Gate 1 freeze + Gate 2; `06` continuity | 4 constitutional probes; hash continuity check | Two untested constitutional articles; honor-system freeze |
| 11 | PF-namespace resolution rule | `_portfolio/failure-catalog.md` header | Every bare PF-n resolves locally or carries "Baseplate PF-n" | A fresh session resolving PF-9 to the wrong failure mode |
| 12 | Enum discipline + OV self-MANIFEST | `03` doc-class discipline; `_types/*` enums; `Artifacts/MANIFEST.md` | Enum lists every emitted class; the OV ships its own manifest | The engine breaking its own enum/packaging mandates |

*(Decision 11 follow-through: the D10 mechanisms above are now also first-class requirement rows — BFR-23..27 and BNF-6 — per this file's own update-in-same-change mandate, and the propagation gap D10 itself exhibited is encoded as BNF-6.)*
