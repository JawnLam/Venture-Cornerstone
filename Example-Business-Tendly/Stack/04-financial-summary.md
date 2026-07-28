---
type: VCS_Financial_Document
Item_ID: "B6D02F41-7C39-48A5-9E13-0F5A2C8D6B74"
title: "Tendly — Financial Model Summary"
vcs_Business_Slug: "TND"
vcs_Doc_Class: financial-model
vcs_Band: 3
vcs_Merged_Bands: [3, 6]
vcs_Merged_Classes: [unit-economics, cap-table, pricing]
vcs_Financial_Depth_Tier: full
vcs_Document_Status: shipped
vcs_Precedence_Rank: 1
vcs_Requires_Signoff_By: "CPA (financial model), securities attorney (SAFE + cap table), privacy counsel (PII/ToS)"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Financial Model Summary (L3 · Money)

> Answers: **do the numbers work?** This is the **numeric authority** for the whole stack (precedence rank 1). Every figure the deck, one-pager, canvas, or market brief shows traces to a row here or in `_assumptions-register.md` (which travels **inside this stack**). This document **cites** the register by `TND-A<n>`; it never re-authors an assumption's value. **Everything below is `[ASSUMPTION]`-driven and fictional** — its purpose is to demonstrate that the model is auditable, not to assert Tendly is a good investment. **Depth tier: `full`** (equity raise; an auditable selection-time decision), so it carries a sensitivity table (§7). Every derived figure below shows its formula from named driver IDs so it **recomputes** under the consistency audit's arithmetic-identities check — agreement across documents proves the numbers are *consistent*, not that they are *correct*.
>
> **`requires-signoff-by` (the authority boundary):** this model, the cap-table view, and the SAFE terms are **drafted, not blessed.** A CPA must review the model; a **securities attorney** must review the SAFE and cap table before the round closes; **privacy counsel** must review PII handling and the ToS. Venture Cornerstone issues **no** financial, tax, securities, or legal advice.

## 1. Unit economics (per center)

| Metric | Value | Derivation | Anchor |
|---|---|---|---|
| ARPA | **`$3,600`/yr** (`$300`/mo) | list `$299`/mo × 12, rounded | `TND-A1` |
| Gross margin | **80%** | hosting + support | `TND-A2` |
| Blended CAC | **`$2,400`** | early founder + inside sales | `TND-A3` |
| Annual logo churn | **18%** | sticky compliance data | `TND-A4` |
| **Margin-adjusted LTV** | **`$16,000`** | LTV = ARPA × GM ÷ churn = `3,600 × 0.80 ÷ 0.18` | `TND-A1/A2/A4` |
| **LTV:CAC** | **6.7:1** *(flagged optimistic)* | LTV:CAC = LTV ÷ CAC = `16,000 ÷ 2,400` | `TND-A1/A2/A4`, `TND-A3` |
| **CAC payback** | **10 months** | payback = CAC ÷ (ARPA × GM ÷ 12) = `2,400 ÷ 240` | `TND-A3`, `TND-A1/A2` |

**LTV is margin-adjusted, not raw revenue** — and periods match: annual ARPA over annual churn. Each derived figure above is written as its identity from named driver IDs, so the audit recomputes it from the register. **The 6.7:1 ratio is not a selling point — it is a sensitivity warning:** it depends almost entirely on the 18% churn assumption (`TND-A4`); at 30% churn LTV:CAC falls to ~4:1 — the full flex is the **sensitivity table in §7**, no longer a single buried line. The firmer gate is the **10-month CAC payback**, which holds regardless of the churn tail.

## 2. Three-year top line (`TND-A5`, `TND-A9`)

| | Today | End Y1 | End Y2 | End Y3 |
|---|---|---|---|---|
| Paying centers | 12 | 50 | 200 | 600 |
| **ARR** (centers × `$3,600`) | **`$43,200`** | **`$180,000`** | **`$720,000`** | **`$2,160,000`** |

*This is the single ARR series the entire stack reconciles to.* The deck's "`$2.16M` ARR" (`TND-D8/D10`), the one-pager headline, and the canvas revenue block all cite this row — none restates it.

## 3. The raise, burn, and runway

- **Current position (pre-raise, BI-13):** **`$120,000`** cash on hand (`TND-A11`) against **~`$18,000`/mo** current net burn (`TND-A12`), where net burn = gross burn − revenue = ~`$21,600` − ~`$3,600`/mo (`$43,200` ARR ÷ 12). → **Current runway** = current cash ÷ current net burn = `120,000 ÷ 18,000 ≈` **~6.7 months.** This is the clock that dates the **Q4-2026** close (BI-10) — the raise is not optional against it. *(Runway is computed from real starting cash, never an implicit `$0`.)*
- **Raise:** **`$750,000`** on a post-money SAFE, **`$6.0M`** post-money cap → **~12.5%** on conversion (`TND-A10`) — *`requires-signoff-by` securities counsel + CPA; the dilution math and instrument are theirs.*
- **Post-raise net burn:** **`$42,000`/mo** (`TND-A6`) — rises from the current `$18,000` as the 2 hires and CAC spend come on.
- **Post-raise runway:** = raise ÷ post-raise net burn = `750,000 ÷ 42,000 ≈` **~18 months** — funds the 12 → 200-center leg (`TND-A5`) to **`$720,000` ARR**, the Series A / default-alive threshold. *Cash convention: raise-only floor (stated in the register's derived-figures section) — existing cash funds the pre-close gap and is conservatively excluded here.*

## 4. Use of funds (`$750,000`)

| Category | Share | Purpose |
|---|---|---|
| Engineering (1 full-stack hire + infra) | ~40% | per-state compliance logic; records vault; reporting |
| Sales & success (1 customer-success lead + CAC spend) | ~40% | fund the 12→200 growth path at CAC `$2,400` |
| Founders + G&A | ~20% | two founders + overhead over ~18 months |

*(Shares are `[ASSUMPTION]` planning allocations under `TND-A6`, not a committed budget.)*

## 5. Cap table — economic view only (`requires-signoff-by`)

Ownership *math* for the investor conversation, not a legal instrument:

| Holder | Pre-round | Post-round (illustrative, on SAFE conversion) |
|---|---|---|
| Founders (2, per founder agreement) | 100% | ~87.5% |
| Angel round (SAFE, `$6.0M` cap) | — | ~12.5% (`TND-A10`) |
| Option pool | not yet established | to be sized with counsel at priced round |

**Hard stop:** the **legal** cap table, the **entity choice**, the **founder agreement**, and the **SAFE instrument** are earned legal documents that this stack **flags and routes to a securities attorney + CPA** — they are not drafted here as compliant documents. Likewise the **PII/ToS handling** (children's and staff records, BI-9) is routed to **privacy counsel**. These flags are features of the stack, not omissions.

## 6. What is deliberately not modeled

No detailed P&L, cohort waterfall, or scenario tree — this is a **summary of the full-tier model** sized to an angel conversation (BI-4), not a Series A data room: it carries the mandated sensitivity table and cited assumptions register, not a month-by-month P&L. When the round warrants the deeper build, it is a REVISE-STACK step on the same `TND-A<n>` assumptions so nothing has to be re-reconciled.

## 7. Sensitivity table (mandatory for a `VCS_Financial_Document`)

The most decision-useful line in a money-band stack is how the answer moves when a load-bearing assumption moves. Each row flexes exactly one register assumption and shows the effect on the headline outputs — **LTV:CAC**, **CAC payback**, **post-raise runway (months of runway on the `$750,000` ask)**, and **when the plan reaches the `$720,000` / 200-center Series-A threshold.** This is the line a sector-literate reader probes first; surfacing it is the opposite of hiding the model's fragility.

| Assumption flexed | Δ from base | LTV:CAC | CAC payback | Post-raise runway | Reaches `$720K` ARR |
|---|---|---|---|---|---|
| **Base case** | — | **6.7:1** | **10 mo** | **~18 mo** | ~Y2 (on plan) |
| **Churn** (`TND-A4`) | 18% → **30%** | **4.0:1** | 10 mo (unch.) | ~18 mo (unch.) | on plan |
| **Churn** (`TND-A4`) | 18% → **12%** | 10.0:1 | 10 mo | ~18 mo | on plan |
| **CAC** (`TND-A3`) | `$2,400` → **`$3,000`** (+25%) | 5.3:1 | 12.5 mo | ~16 mo \* | ~1 qtr later \* |
| **CAC** (`TND-A3`) | `$2,400` → **`$1,800`** (−25%) | 8.9:1 | 7.5 mo | ~20 mo \* | on/ahead of plan |
| **Growth** (`TND-A5`) | new-adds **−25%** | 6.7:1 (unch.) | 10 mo | ~18 mo | **slips ~2 qtrs** |
| **Growth** (`TND-A5`) | new-adds **+25%** | 6.7:1 | 10 mo | shorter (CAC front-load) \* | ~1–2 qtrs earlier |

**Reading it.** LTV:CAC hinges on **churn** (`TND-A4`) — the base 6.7:1 is a churn bet, and at 30% it is a pedestrian 4.0:1; churn moves *cash* not at all, so runway is unaffected by it. **CAC** (`TND-A3`) is the double-lever: it moves both payback and, through acquisition spend, post-raise runway. **Growth** (`TND-A5`) barely moves the ratios but decides *when* the `$720K`/200-center threshold lands, which is what the raise is timed to. `\*` marks a ripple whose exact month a full cash-flow model (a REVISE-STACK deliverable) would pin down; the summary shows direction and names the assumption each output hangs on.

## Non-goals (the edges of this model)

- **Not a valuation.** The `$6.0M` cap is a founder-proposed SAFE term (`TND-A10`), not an appraisal — `requires-signoff-by` counsel/CPA.
- **Not a scenario simulator.** The sensitivity table flexes one assumption at a time; it does not model correlated downside (churn *and* CAC worsening together) — that is the REVISE-STACK full-model job.
- **Not a raise-timing model beyond the 200-center threshold.** Anything past `$720K` ARR / H2-2028 is out of this document's scope (BI-10).
