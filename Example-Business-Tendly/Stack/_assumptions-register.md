---
type: Fleeting
Item_ID: "7B2F9D64-1C40-4A85-8E3B-D0F6C1A29E54"
title: "Tendly — Assumptions Register"
vcs_Business_Slug: "TND"
vcs_Doc_Class: assumptions-register
vcs_Band: V
vcs_Document_Status: shipped
vcs_Precedence_Rank: 0
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Assumptions Register

> The data-discipline spine. **Every** financial or market figure in this stack is founder-supplied, sourced-and-dated, or a named `[ASSUMPTION]` here. No number lives only inside prose. This file is the **single authored home** for every assumption — a document's in-line assumptions section **cites** a `TND-A<n>` row and never re-authors its value; two authored copies of one assumption is a drift defect. That anchor is also how the consistency audit proves the deck's number and the model's number are the *same* number.
>
> **This register travels inside the stack.** For anyone judging the financial model, the register with owners, statuses, **severities**, and **valid-until** dates *is* a decision document, so it ships with the founding documents rather than with the history.
>
> Two columns beyond owner/status carry the discipline: **`severity`** ∈ {blocking-for-stated-audience | non-blocking} — an open assumption the stack itself says must close before its audience acts is `blocking-for-stated-audience` and forces a **SHIP-WITH-DECLARED-GAPS** verdict at the decision test; **`valid-until`** — the date past which the figure must be re-verified (a REVISE-STACK time trigger). All values below are **fictional** to this worked example.

| ID | Assumption | Value | Basis | Owner | Status | Severity | Valid-until |
|---|---|---|---|---|---|---|---|
| **TND-A1** | Blended ARPA per center | **`$3,600`/yr** (`$300`/mo) | `$299`/mo founder-supplied list price × 12, rounded up for occasional multi-room add-ons | Founder | `[ASSUMPTION]` — confirm against blended actual as annual plans and add-ons mix in | non-blocking | 2027-01-31 |
| **TND-A2** | Gross margin | **80%** | SaaS hosting + support cost against subscription revenue | Founder | `[ASSUMPTION]` — validate at scale; support cost is the swing factor | non-blocking | 2027-07-27 |
| **TND-A3** | Blended CAC per center | **`$2,400`** | Early founder-led + inside sales + high-touch compliance onboarding | Founder | `[ASSUMPTION]` — high sensitivity; no cohort-level attribution yet | non-blocking | 2026-12-31 |
| **TND-A4** | Annual logo churn | **18%** | Compliance-critical, switching-resistant software | Founder | `[ASSUMPTION]` — **the single biggest LTV sensitivity.** Pilot data (11/12 retained ≥6 mo, `TND-S2`) is directional only, n=12 | non-blocking | 2026-12-31 |
| **TND-A5** | New-center growth path | **12 → 50 → 200 → 600** (today, end-Y1, end-Y2, end-Y3) | Founder growth plan off current 12 paying centers | Founder | `[ASSUMPTION]` — the raise is sized to fund the 12→200 leg | non-blocking | 2026-12-31 |
| **TND-A6** | Average net burn (post-raise) | **`$42,000`/mo** → **~18 months** runway on `$750,000` | 2 founders + 2 post-raise hires + infra + CAC spend | Founder | `[ASSUMPTION]` — hiring-pace dependent; `750,000 ÷ 42,000 ≈ 17.9` | non-blocking | 2026-12-31 |
| **TND-A7** | TAM — US licensed center-based childcare facilities | **~130,000 centers** → **`$468M`** at ARPA `TND-A1` | Founder recollection, **no source** (BI-7) | `[ASSUMPTION / UNVERIFIED]` — **MUST be replaced** with a sourced figure (Child Care Aware of America / IBISWorld / state licensing registries) before any investor use | **blocking-for-stated-audience** | 2026-09-30 |
| **TND-A8** | SAM — independent (1–5 location) centers in 6 launch states | **~28,000 centers** → **`$100M`** | Derive from `TND-A7` by state share × independent-operator filter | Founder | `[ASSUMPTION]` — derived from an unverified TAM; inherits `TND-A7`'s flag | **blocking-for-stated-audience** | 2026-09-30 |
| **TND-A9** | SOM — obtainable by end-Y3 | **600 centers** → **`$2.16M`** ARR (~2% of SAM) | Ties directly to `TND-A5` end-Y3 | Founder | `[ASSUMPTION]` — a plan target tied to the growth path, not a bottom-up sales-capacity model; the "~2% of SAM" framing inherits `TND-A7`'s flag but the 600-center count is a plan number | non-blocking | 2026-12-31 |
| **TND-A10** | Round terms — post-money SAFE cap | **`$6.0M`** post-money cap on `$750,000` → **~12.5%** on conversion | Founder-proposed terms | Founder | `[ASSUMPTION / founder-proposed]` — **`requires-signoff-by` securities counsel + CPA.** Not advice; the actual instrument and dilution math are counsel's | non-blocking | 2026-10-31 |
| **TND-A11** | Current cash on hand (BI-13) | **`$120,000`** | Founder — internal bank/accounting balance | Founder | `founder-confirmed` — real balance; external verification is operator-only (diligence) | non-blocking | 2026-10-31 |
| **TND-A12** | Current net burn (pre-raise, BI-13) | **~`$18,000`/mo** | 2 founders, pre-hire: gross burn ~`$21,600`/mo − current revenue ~`$3,600`/mo (`$43,200` ARR ÷ 12) | Founder | `founder-confirmed` — the pre-raise phase; rises to `TND-A6` `$42,000`/mo post-raise | non-blocking | 2026-10-31 |

*(TND-A13 is retired, not reused: the BI-4b audience bar it once held is evaluator-side material and must not travel inside the stack the stranger is judged on — it now lives in the selection record, in `Records/`.)*

## Derived figures (computed from the above — every formula cites its driver IDs so the arithmetic is auditable)

The consistency audit's arithmetic-identities check recomputes each of these from its drivers; a bare derived number with no shown computation is a block.

- **Margin-adjusted LTV** = ARPA × gross margin ÷ annual churn = `$3,600` × 0.80 ÷ 0.18 = **`$16,000`** (`TND-A1`, `TND-A2`, `TND-A4`).
- **LTV:CAC** = LTV ÷ CAC = `$16,000` ÷ `$2,400` = **6.7:1** (`TND-A1/A2/A4`, `TND-A3`). *Flagged optimistic:* it rests almost entirely on the 18% churn assumption (`TND-A4`); at 30% churn it falls to ~4:1 (see the sensitivity table in `04-financial-summary.md` §7). Treat CAC payback as the firmer gate.
- **CAC payback** = CAC ÷ (ARPA × gross margin ÷ 12) = `$2,400` ÷ (`$3,600` × 0.80 ÷ 12) = `$2,400` ÷ `$240` = **10 months** (`TND-A3`, `TND-A1/A2`).
- **ARR by end of year** = centers × ARPA (`TND-A5`, `TND-A1`): **Y1 `$180,000`** (50 × 3,600), **Y2 `$720,000`** (200 × 3,600), **Y3 `$2,160,000`** (600 × 3,600). Current: 12 × 3,600 = **`$43,200`**.
- **Current runway** = current cash ÷ current net burn = `$120,000` ÷ `$18,000` = **~6.7 months** (`TND-A11`, `TND-A12`) — the pre-raise clock dating the Q4-2026 close.
- **Post-raise runway** = raise ÷ post-raise net burn = `$750,000` ÷ `$42,000` = **~18 months** (`TND-A6`) — funds the 12→200-center leg to `$720,000` ARR. **Cash convention (named here so the identity is auditable): raise-only floor** — the `$120,000` on hand (`TND-A11`) funds the ~5-month gap to the Q4-2026 close at `$18,000`/mo (`TND-A12`) and is conservatively treated as consumed by close; cash surviving the close only extends this floor.

Every figure in `04-financial-summary.md`, `03-market-brief.md`, `05-pitch-deck.md`, and `06-one-pager.md` traces to a row above. If a document shows a number that is not here, it is an orphan and a Gate 1 block.
