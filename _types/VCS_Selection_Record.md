---
Item_ID: "<UUID>"
type: VCS_Selection_Record
title: "<Business> — Selection Record"
vcs_Business_Slug: ""
vcs_Doc_Class: "selection-record"
vcs_Band: "—"                          # the selection record is meta — it governs the stack, it is not a band of it
vcs_ID_Scheme: ""                      # e.g. ACME-<BAND>-<n> — extractable, stable, never renumbered
vcs_Financial_Depth_Tier: ""           # full | summary — the financial-class depth chosen at SELECT, keyed to BI-2 (stage) + BI-3 (funding path); an auditable decision, not improvised at draft time (03-SELECTION § Depth tiers)
vcs_Audience_Bar: ""                    # BI-4b — the primary audience's threshold (check size, stage thesis, what they've said they need to see); Gate 2's ST-2 decision-plausibility is anchored to it
vcs_Precedence_Declaration: ""         # ordered list of doc classes, lower index wins on conflict — extractable
vcs_Document_Status: drafting          # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — Selection Record

> The locked output of the selection stage (`03-SELECTION.md`). Records the document set for this business with **every inclusion AND every exclusion tied to its triggering founder-interview answer (BI-n)**, plus the ID scheme and precedence declaration as extractable fields. Locked before any document is drafted (F8 — no drafting before it locks); overwrites once, never edits in place afterward.

## Decisions (inclusions and exclusions)

Every class from the selection registry gets a row. An unexplained exclusion is a defect; an unexplained inclusion is gold-plating. Every row cites a BI-answer by ID.

| Band | Class | Include / Exclude | Triggering BI-answer | Structural Type |
|------|-------|-------------------|----------------------|-----------------|
| 1 | Business Model Canvas / Lean Canvas | Include (unconditional) | — | `VCS_Model_Document` |
| V | Consistency audit + stranger test (`VCS_Stranger_Test_Log` — the only V-band Type) | Include (unconditional) | — | `VCS_Stranger_Test_Log` |
| 0 | Vision brief, PR-FAQ | | | `VCS_Narrative_Document` |
| 2 | Market sizing (TAM/SAM/SOM) | | | `VCS_Market_Document` |
| 2 | ICP + competitive landscape | | | `VCS_Market_Document` |
| 2 | Go-to-market plan | | | `VCS_Market_Document` |
| 2 | Traction-evidence pack | | | `VCS_Market_Document` |
| 3 | Financial model + unit economics *(record depth tier: full / summary)* | | | `VCS_Financial_Document` |
| 3 | Pricing | | | `VCS_Financial_Document` |
| 3/6 | Cap table (economic / legal) | | | `VCS_Financial_Document` / `VCS_Legal_Document` |
| 4 | Business plan | | | `VCS_Plan_Document` |
| 4 | SBA/bank loan plan | | | `VCS_Plan_Document` |
| 4 | Risk register | | | `VCS_Plan_Document` |
| 4 | Investor pitch deck (projection) | | | `VCS_Pitch_Document` |
| 4 | Objection map / Q&A prep (projection) | | | `VCS_Narrative_Document` |
| 0/4 | One-pager / executive summary (projection) | | | `VCS_Narrative_Document` |
| 5 | Operating plan | | | `VCS_Operations_Document` |
| 5 | Org & hiring plan | | | `VCS_Operations_Document` |
| 6 | Entity choice | | | `VCS_Legal_Document` |
| 6 | Founder/operating agreements | | | `VCS_Legal_Document` |
| 6 | IP & licenses | | | `VCS_Legal_Document` |

> **The V-band instruments** — `_assumptions-register.md` and `_source-log.md` — are cartridge **instruments** (`type: Fleeting`, `vcs_Band: V`), **not** instances of any of the eight document Types. The assumptions register travels in `Stack/` (a decision document, Decision 10); the source log stays in `Records/`. `VCS_Stranger_Test_Log` is the only V-band document *Type*.

## Financial depth tier (extractable)

The financial class is depth-tiered; the tier is decided **here**, at selection, keyed to BI-2 (stage) and BI-3 (funding path) — not improvised at draft time. Record it as an extractable field: `financial model | include | BI-3 equity | full`. **full** = equity raise or debt (full projections, revenue/cost build, cash flow, unit economics, sensitivity, cap table); **summary** = bootstrapped / pre-revenue viability check (cash-in/cash-out runway + unit-economics sketch, still carrying the assumptions register and any ratio's sensitivity table). Mirror the value in `vcs_Financial_Depth_Tier`.

## Audience bar (BI-4b — extractable)

The primary audience's threshold — check size, stage thesis, what they have said they need to see. Recorded here and mirrored in `vcs_Audience_Bar`; Gate 2's ST-2 (decision plausibility) is judged against this bar, so it must be a stated, extractable value, not an implied one.

## ID scheme (extractable, stable)

`<BUSINESS>-<BAND>-<n>` — e.g. `ACME-MKT-3`, `ACME-FIN-7`, `ACME-LEG-2`. Stable, never reused, never renumbered.

## Precedence declaration (extractable)

Ordered list — the document that wins on conflict comes first. Within a projection (deck, one-pager, executive summary): the source document is law; the projection conforms. Every quantitative document ranks above the projections that cite it.

1. …

## Requires-signoff-by declarations

List every included document that carries a `requires-signoff-by` flag and the professional role required — Gate 1 verifies each is present and unresolved.

| Document | Role required |
|----------|---------------|
| Cap table (economic/legal) | CPA / securities counsel |
| Entity choice | attorney / CPA |
| Founder/operating agreements | attorney |
| IP & licenses | attorney |

## Naming

- **Filename:** `_selection-record.md` in the cartridge root (not inside `Artifacts/` unless the stranger should see it).
- **Type value:** `type: VCS_Selection_Record`.

## Relationships

- Every `VCS_*_Document` Type — *earned-by (each included document cites the BI-answer recorded here; each excluded class is recorded with its reason)*.
- `VCS_Stranger_Test_Log` — *verified-by (Gate 1 checks that every earned document maps back to a BI-answer and every exclusion is recorded)*.
