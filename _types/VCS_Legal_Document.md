---
Item_ID: "<UUID>"
type: VCS_Legal_Document
title: "<Business> — <Entity Choice | Founder/Operating Agreement | IP & Licenses | Cap Table (Legal)>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # entity-choice | founder-operating-agreement | ip-licenses | cap-table-legal  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Band: 6                    # L6 — Legal & Ownership
vcs_ID_Scheme: ""             # e.g. ACME-LEG-<n>
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
vcs_Requires_Signoff_By: ""    # REQUIRED for every L6 document → e.g. "attorney", "attorney / CPA", "securities counsel"
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Legal Document>

> An L6 document — **the legal and ownership facts.** Earned when the business is formed, takes outside money, has more than one founder, or is IP-heavy/regulated (BI-8, BI-9, BI-11). **Every L6 document carries `vcs_Requires_Signoff_By` and the professional-sign-off section below — this is the authority boundary, `domain_stakes: high`.** This OV drafts and flags; it never blesses a legal document as compliant. Names in agreements and attribution are founder-provided strings only — never inferred from a username, path, or email.

## Required sections (by class)

- **entity-choice:** The options considered (LLC / C-corp / S-corp / partnership / sole prop), the recommendation and its reasoning, and the tax/liability/fundraising consequences of each. Flag `requires-signoff-by: attorney / CPA`.
- **founder-operating-agreement:** Ownership split; vesting and cliffs; roles and decision rights; what happens on a founder departure; IP assignment to the entity. Flag `requires-signoff-by: attorney`.
- **ip-licenses:** IP and licenses/permits in one document — IP assignment (founders → entity), what is proprietary vs licensed, any filings contemplated (trademark/patent); and the licenses and permits the business shape/industry requires, jurisdiction by jurisdiction, with their status. Flag `requires-signoff-by: attorney` (or the relevant regulator's counsel).
- **cap-table-legal:** the legal ownership view — shareholders/members of record, share classes, option pool as authorized, and the instruments (SAFEs/notes) outstanding. Must reconcile with the L3 economic cap table (same ownership, two views). Flag `requires-signoff-by: securities counsel / CPA`.

## Professional sign-off required (MANDATORY — every L6 document)

> **Authority boundary — `domain_stakes: high`.** This document is drafted for the founder's understanding and to brief the professional; it is not legal advice and must not be executed without review. Set `vcs_Requires_Signoff_By` to the required role and record the hard stop. Gate 1 checks that every L6 document carries this flag, unresolved — an L6 document without a sign-off flag is a consistency-audit block.

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`entity-choice`, `founder-operating-agreement`, `ip-licenses`, `cap-table-legal`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `entity-choice.md`, `founder-operating-agreement.md`, `ip-licenses.md`, `cap-table-legal.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Legal_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (the BI-answer that included each L6 document; exclusions recorded)*.
- `VCS_Financial_Document` — *reconciles-with (legal cap table ↔ economic cap table — same ownership, two views)*.
- `VCS_Operations_Document` — *reconciles-with (entity/roles ↔ the org plan)*.
- attorney / CPA / securities counsel — *requires-signoff-by (mandatory on every L6 document)*.
