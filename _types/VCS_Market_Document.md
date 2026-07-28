---
Item_ID: "<UUID>"
type: VCS_Market_Document
title: "<Business> — <Market Sizing | ICP & Competitive | Go-to-Market | Traction-Evidence Pack>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # market-sizing | icp-competitive | go-to-market | traction-evidence-pack  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Band: 2                    # L2 — Market & GTM
vcs_ID_Scheme: ""             # e.g. ACME-MKT-<n> for numbered figures/claims
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Market Document>

> An L2 document — **who the customer is and how the business reaches them.** Earned when the business raises equity, enters a market that must be argued, or must actively sell/distribute (BI-3, BI-5, BI-7); a captive first customer with no growth plan earns less. This band is the front line of the data discipline: a market size is the single most common fabricated figure in a founding stack, and the founder gets caught by the one person in the room who knows the sector. Every figure here is founder-supplied, or sourced-and-dated, or stamped `[ASSUMPTION]` / `[UNVERIFIED]` — never asserted.

## Required sections (by class)

- **market-sizing:** TAM / SAM / SOM, each a figure with its derivation shown (top-down vs bottom-up), its source or assumption, and its date. Show the arithmetic — a market size with no visible derivation is treated as unsourced.
- **icp-competitive:** the ideal-customer profile and the competitive landscape in one document — who they are, the job they are hiring the product for, where they are found, what triggers a purchase, who is explicitly *not* the target (both edges); named competitors and substitutes (including "do nothing"), the axes of comparison, and where this business wins and where it does not. Naming no competitor is a finding, not a moat.
- **go-to-market:** Channels, motion (self-serve / sales-led / partner), first-90-days acquisition plan, and the CAC assumption it implies (which must reconcile with the L3 unit economics).
- **traction-evidence-pack:** Traction summary (logos / revenue / retention); Evidence index (contracts, LOIs, usage — each a founder-supplied `_source-log.md` row); Cohort / retention proof; What is verifiable vs claimed. Every claim is founder-supplied evidence, never asserted — diligence will open this.

## Assumptions register (MANDATORY — every class)

Every quantitative claim in this document rests on a named, auditable assumption. List them here, do not bury them in prose. Each row: the claim, the assumption behind it, its owner, and its status.

| Claim / figure | Underlying assumption | Source or `[ASSUMPTION]` | Owner | Status |
|----------------|-----------------------|--------------------------|-------|--------|
|                |                       |                          |       |        |

- Every figure is **sourced-or-assumed** and logged in `_source-log.md` (`claim | source | date | method | verified?`); no un-sourced, un-assumed number ships.
- Every figure that also appears in another document (the deck's TAM, the model's segment size) must **reconcile** with its twin — a market size that disagrees with itself between documents is a Gate 1 block.

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`market-sizing`, `icp-competitive`, `go-to-market`, `traction-evidence-pack`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `market-sizing.md`, `icp-competitive.md`, `go-to-market.md`, `traction-evidence-pack.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Market_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (the BI-answer that included each L2 document; excluded classes recorded too)*.
- `VCS_Model_Document` — *reconciles-with (ICP ↔ Customer Segments; GTM channels ↔ Channels block)*.
- `VCS_Financial_Document` — *reconciles-with (the GTM CAC assumption ↔ the unit-economics CAC; SOM ↔ the revenue ramp)*.
- `_source-log.md`, `_assumptions-register.md` — *sourced-from (every figure resolves to a source row or a named assumption)*.
- `VCS_Stranger_Test_Log` — *verified-by (Gate 1 reconciliation + Gate 2 stranger decision)*.
