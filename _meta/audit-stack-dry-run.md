---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-meta-audit-stack-dry-run
title: "Venture Cornerstone — AUDIT-STACK Dry Run (foreign stack, executed 2026-07-27)"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-meta
role: audit-dry-run-record
scope: subject-agnostic
---

# AUDIT-STACK Dry Run — foreign stack, degraded mode (executed 2026-07-27)

> **Why this file exists.** REQ-A2 (graceful scope boundaries) claims AUDIT-STACK is genuinely useful on a stranger's materials. Until now that claim had a spec (`05-GATES.md` § AUDIT-STACK) and no execution. This is the execution: a synthetic foreign stack with **seeded defects**, audited read-only in degraded mode, including a fresh-instance lender decision read. The waiver on REQ-A2 is discharged by this record.

## The fixture ("CrumbCraft Bakery" — synthetic, three files, no Venture Cornerstone apparatus)

A wholesale bakery seeking a `$250,000` SBA 7(a) loan; one-pager + financial summary + expansion plan. Defects seeded on purpose:

| # | Seeded defect | Class |
|---|---|---|
| S1 | ARR `$480K` (one-pager) vs `$520K` (financials); per-account `$1,275`/mo vs `$400`/mo vs `$4,800`/yr; a "see note" pointing at nothing | reconciliation / dangling ref |
| S2 | Account LTV `$210,000` from "revenue × margin ÷ churn" with mixed units; LTV:CAC `150:1` inheriting it | arithmetic identity (period mismatch) |
| S3 | Runway "14 months" vs `$60K ÷ $5K/mo` = 12 | arithmetic identity |
| S4 | "healthy" payback, "comfortably covered" repayment (no DSCR anywhere), "retention is strong" vs 2%/mo churn | unparameterized thresholds |
| S5 | "$9B market, fastest-growing segment" — no source, no date | unsourced market figure |
| S6 | Loan financials with no CPA/underwriting flag; owner draw/equity explicitly "not shown" | sign-off / authority-boundary absence |

## Findings — bucket 1: portable-check failures (real defects in any stack)

Run per the degraded-mode checklist. The stranger read (below) independently caught **every seeded class** plus two unseeded findings:

- **Reconciliation (S1): CONFIRMED.** All three revenue inconsistencies caught, including the phantom "see note."
- **Arithmetic identities (S2, S3): CONFIRMED.** LTV recomputed at ~`$37K` on consistent monthly units — the claimed `$210K` is ~6× inflated by an annual/monthly mix; `150:1` shown to be exactly `210,000 ÷ 1,400`, i.e. the ratio inherits the error; runway recomputed to 12 months. *(The same failure class the OV's own generation-standard-12 example once contained — the check works on strangers and on ourselves.)*
- **Thresholds (S4): CONFIRMED.** "Comfortably covered" resolved against an actual ~`$3,300–3,450`/mo debt-service estimate → current DSCR is negative; ≥1.25× named as the bar. "Healthy"/"strong" rejected as spin against 2%/mo ≈ 21.5%/yr churn.
- **Sign-off / underwriting absence (S6): CONFIRMED.** Missing P&L/balance sheet/tax returns, personal financial statement, personal guarantee, eligibility screen; owner-draw omission called out as materially favorable to the borrower.
- **Stranger decision test (S5 + overall): CONFIRMED useful.** Coherent, stack-grounded decision — **decline as presented; invite resubmission** — with the unsourced `$9B` market claim routed to verification. Two unseeded findings: the growth plan contradicts its own historical win rate (~3 gross adds/mo needed vs ~1.3 historical, with CAC spend exceeding the working-capital allocation), and a 10-year term against a van's useful life.

## Findings — bucket 2: instrumentation gaps (absent apparatus — reported, NOT failed)

No selection record or BI-answer mapping (inclusion/exclusion rationale unverifiable); no source log (no provenance, dates, or valid-until on any figure); no assumptions register (no single ownership to check); no freeze hashes (no audited-bytes chain). Each reported as "Venture Cornerstone provenance/selection apparatus not present — cannot verify," per the degraded-mode rule. None counted as a stack defect.

## Disposition

- **Read-only honored:** the fixture was not edited.
- **Degraded-mode split held:** portable checks produced every real finding; BB-native checks produced zero false "failures."
- **REQ-A2:** waiver discharged — disposition `met` in `_meta/posture.yaml` cites this record.
- **Caveat, stated plainly:** the fixture is synthetic and its defects were seeded by the auditor's own session (the stranger reader was a fresh instance and blind to the seeding). A dry run on a real third-party stack the session did not construct remains worth doing at SHIP-PREP; this record demonstrates mechanism, not field history.
