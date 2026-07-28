---
Item_ID: "<UUID>"
type: VCS_Financial_Document
title: "<Business> — <Financial Model | Unit Economics | Pricing | Cap Table (Economic)>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # financial-model | unit-economics | pricing | cap-table-economic  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Band: 3                    # L3 — Money
vcs_ID_Scheme: ""             # e.g. ACME-FIN-<n> for numbered figures/claims
vcs_Depth_Tier: ""             # full | summary — set at SELECT, keyed to BI-2 (stage) and BI-3 (funding path); full for an equity raise/debt, summary for a bootstrapped viability check (see 03-SELECTION § Depth tiers)
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
vcs_Requires_Signoff_By: ""    # set for the cap-table-economic class → "CPA / securities counsel"; empty for model/unit-econ/pricing
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Financial Document>

> An L3 document — **do the numbers work.** Effectively unconditional the moment money is involved — raising, borrowing, or proving viability (BI-3, BI-6, BI-11) — with depth scaling to the ask: a VC raise needs the full model plus unit economics; a bootstrap needs enough to prove it does not run out of cash. This is the highest-stakes quantitative band in the stack; every figure is sourced-or-assumed and every figure reconciles across documents, or it does not ship.

## Required sections (by class)

- **financial-model:** 3–5 year projections (the SBA "Financial Projections" section) — revenue build, cost build, headcount, cash. Every driver traces to an assumption-register row.
- **unit-economics:** CAC (fully-loaded sales-and-marketing spend ÷ new customers); **LTV computed margin-adjusted** (ARPA × gross-margin% ÷ churn — *not* raw revenue; a raw-revenue LTV is a defect); LTV:CAC (≈3:1 is a heuristic, not a law); **CAC payback** in months (often the more meaningful gate than the ratio for a short-runway business); burn (gross vs net) and runway (cash ÷ net burn). Show each formula and its inputs.
- **pricing:** the pricing model, the logic behind the number, and the ARPA it implies (which must reconcile with the model's Revenue Streams and the financial model's revenue build).
- **cap-table-economic:** the economic ownership view — who holds what percentage, option pool, and post-money math. **Carries `vcs_Requires_Signoff_By` and the professional-sign-off section below** — the legal cap table lives in L6.

## Sensitivity table (MANDATORY — every class that computes ratios)

Every key assumption gets a stress row: `±Δ` on the driver → the effect on the decision-bearing outputs (LTV:CAC, runway, the ask). This is what a numbers-literate reader reaches for first — it shows which assumption the whole model hangs on.

| Key assumption (driver) | Base value | −Δ → LTV:CAC / runway / ask | +Δ → LTV:CAC / runway / ask | Which output it moves most |
|-------------------------|------------|-----------------------------|-----------------------------|----------------------------|
|                         |            |                             |                             |                            |

- Each driver is an assumption-ID in `_assumptions-register.md`; the sensitivity row cites the ID, it does not re-author the base value.
- A summary-tier model still carries this table wherever it computes a ratio (03-SELECTION § Depth tiers).

## Arithmetic transparency (MANDATORY)

Every **derived** figure shows its formula and the driver assumption-IDs it recomputes from — agreement is not enough for a numbers-first stack; the arithmetic must reproduce from stated drivers (Gate 1's arithmetic-identity check, Decision 10 issue 1).

- `LTV = ARPA × gross-margin% ÷ churn` (margin-adjusted — a raw-revenue LTV is a defect)
- `CAC payback (months) = CAC ÷ (monthly revenue per customer × gross-margin%)`
- `ARR = units × ARPA × 12`
- `runway (months) = cash ÷ net-burn`; `net-burn = gross-burn − revenue`

Each derived figure names the assumption-IDs of its inputs (e.g. `LTV recomputes from FIN-ARPA, FIN-GM, FIN-CHURN`), so the audit can recompute it independently.

## Assumptions register (CITED, not owned — MANDATORY — every class)

> **The single-owned `_assumptions-register.md` is law.** This document does **not** re-author assumption values; its assumptions section **cites the register by assumption-ID** and displays the register's current value. Re-keying a value here is a PF-6 drift source. The register travels **inside** `Stack/` (Decision 10) — for anyone judging the model, the assumptions with owners and statuses are a decision document, not buried history — so an in-line section citing `_assumptions-register.md` is legal (both are in `Stack/`).

| Figure | Assumption-ID (in `_assumptions-register.md`) | Value (as of the register) | Reconciles-with |
|--------|-----------------------------------------------|----------------------------|-----------------|
|        |                                               |                            |                 |

- Every figure is **sourced-or-assumed** in the owned register and logged in `_source-log.md`; no un-sourced, un-assumed number ships.
- Every figure that appears elsewhere (the deck's ARR, the plan's funding request, the model's Revenue Streams) must **reconcile** with its twin — a number that disagrees with itself between documents is a Gate 1 block (PF-6).

## Professional sign-off required (cap-table-economic class)

> **Authority boundary — `domain_stakes: high`.** This OV drafts and flags; it does not bless. The economic cap table and any financials shown to investors must be reviewed by a CPA and, where equity is offered, securities counsel, before use. Set `vcs_Requires_Signoff_By` and record the hard stop; the consistency audit checks that this flag is present and unresolved.

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`financial-model`, `unit-economics`, `pricing`, `cap-table-economic`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `financial-model.md`, `unit-economics.md`, `pricing.md`, `cap-table-economic.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Financial_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (the BI-answer that included each L3 document; exclusions recorded)*.
- `VCS_Model_Document` — *reconciles-with (pricing/ARPA ↔ Revenue Streams; costs ↔ Cost Structure)*.
- `VCS_Market_Document` — *reconciles-with (CAC ↔ the GTM CAC assumption; revenue ramp ↔ SOM)*.
- `VCS_Legal_Document` — *reconciles-with (economic cap table ↔ the legal cap table — same ownership, two views)*.
- `_source-log.md`, `_assumptions-register.md` — *sourced-from (every figure resolves to a source row or a named assumption)*.
- CPA / securities counsel — *requires-signoff-by (cap-table-economic and investor-facing financials)*.
