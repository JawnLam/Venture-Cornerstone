---
Item_ID: "<UUID>"
type: VCS_Plan_Document
title: "<Business> — <Business Plan | SBA/Bank Loan Plan | Risk Register>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # business-plan | loan-plan | risk-register  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Band: 4                    # L4 — Plan & Ask
vcs_ID_Scheme: ""             # e.g. ACME-PLAN-<n> for numbered claims
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Plan Document>

> An L4 document — **the plan and the ask.** Earned when a formal plan is required by an audience — investors, a board, a lender, or self-discipline (BI-4); the loan plan is earned only when debt financing is sought (BI-3 debt, BI-11). Grounded in the SBA traditional 9-section format. This document aggregates the decision-bearing bands into one narrative; it does not re-derive their numbers — every figure it carries reconciles with its source in L2/L3.

## Required sections (by class)

- **business-plan (SBA 9-section, all required):** Executive Summary; Company Description; Market Analysis; Organization & Management; Service / Product Line; Marketing & Sales; Funding Request; Financial Projections; Appendix. Each section draws from its source band (Market Analysis from L2, Financial Projections from L3, Organization & Management from L5) and states figures consistent with them.
- **loan-plan (SBA / bank):** the 9-section plan plus the lender-specific additions — use of funds (line by line), repayment ability (the debt-service coverage the projections support), collateral, and the personal-guarantee posture. The Funding Request is a debt ask, not an equity ask.
- **risk-register:** Key risks (market, execution, regulatory, competitive, financing); Likelihood / impact; Mitigation; Owner — each risk **cites the document it threatens**. Distinct from the assumptions register (a risk is an adverse event; an assumption is an input value); earned when equity/debt is raised or the business is regulated/IP-heavy (BI-3, BI-4, BI-9).

## Non-goals / out of scope

Explicit statements of what this plan does *not* cover — scope is bounded by both edges. A plan with only an inside is not bounded.

## Cross-band consistency

- The Funding Request must reconcile with the L3 financial model (the number asked for matches the runway/use-of-funds the model shows).
- The Market Analysis figures must reconcile with the L2 market documents; the Organization section with the L5 org & hiring plan.
- No figure is re-derived here — if this document and its source disagree, the source wins and this document is corrected (Gate 1).

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`business-plan`, `loan-plan`, `risk-register`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `business-plan.md`, `loan-plan.md`, `risk-register.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Plan_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (the BI-answer that required a formal plan or debt financing; exclusions recorded)*.
- `VCS_Market_Document`, `VCS_Financial_Document`, `VCS_Operations_Document` — *reconciles-with (the plan aggregates these bands; figures must agree with source)*.
- `VCS_Narrative_Document` — *reconciles-with (the plan's Executive Summary section ↔ any standalone executive-summary projection)*.
- `_source-log.md`, `_assumptions-register.md` — *sourced-from (every figure resolves to a source row or a named assumption)*.
