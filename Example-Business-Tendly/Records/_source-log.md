---
type: Fleeting
Item_ID: "C1E60A38-9D22-4F71-B4A6-2E8C5B0D3F17"
title: "Tendly — Source & Dependency Log"
vcs_Business_Slug: "TND"
vcs_Doc_Class: source-log
vcs_Band: V
vcs_Document_Status: shipped
vcs_Precedence_Rank: 0
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Source & Dependency Log

> Every external figure or dependency the stack rests on: claim | source | date | **valid-until** | method | verified? For a fictional pre-scale business the honest answer is that the **operating numbers are founder-supplied** (real internal data the founder owns) and the **market numbers are unverified assumptions** with no external source yet — and saying so plainly is the discipline. A general model handed this brief would fabricate a cited TAM; Venture Cornerstone refuses and logs the gap instead. The **`valid-until`** column (Decision 10 issue 7) is the anti-staleness backstop: a row past its date at any later session is a REVISE-STACK time trigger, not a silent carryover — a cash balance decays in months, a category read in a year.

| ID | Claim | Source | Date | Valid-until | Method | Verified? |
|---|---|---|---|---|---|---|
| **TND-S1** | 12 paying centers, `$43,200` ARR run-rate today | Founder — internal billing export | 2026-07-27 | 2026-10-31 | Founder-supplied operating data | Founder-verified; **external verification is operator-only** (investor diligence on the billing system) |
| **TND-S2** | 11 of 12 pilot centers retained ≥6 months | Founder — internal account history | 2026-07-27 | 2026-10-31 | Founder-supplied; directional (n=12) | Founder-verified; not statistically load-bearing — feeds `TND-A4` as a prior only |
| **TND-S3** | List price `$299`/center/month | Founder — published pricing page | 2026-07-27 | 2027-07-27 | Founder-supplied | Verified (public) |
| **TND-S4** | ARPA `$3,600`/yr, gross margin 80%, CAC `$2,400`, churn 18%, burn `$42K`/mo | See `_assumptions-register.md` `TND-A1..A6` | 2026-07-27 | 2026-12-31 | Named assumptions, not external sources | **No** — `[ASSUMPTION]`, owned by founder |
| **TND-S5** | TAM ~130,000 US licensed centers; SAM ~28,000; SOM 600 | See `TND-A7..A9` | 2026-07-27 | **2026-09-30** | Founder recollection, **no source** | **No** — `[ASSUMPTION / UNVERIFIED]`; **`severity: blocking-for-stated-audience`** — **open dependency**: replace with Child Care Aware of America / IBISWorld / state licensing registries before investor use |
| **TND-S6** | Competitor category: childcare-management suites (billing/attendance/parent-comms) treat compliance as a checkbox | Founder — category knowledge | 2026-07-27 | 2027-07-27 | Named as a **market category** (Brightwheel-class), not a share statistic | Category asserted; **no market-share or revenue figure is claimed** for any named competitor |
| **TND-S7** | Competitor category: spreadsheets / paper binders / "do nothing" (the status quo) | Founder — field observation | 2026-07-27 | 2027-07-27 | Named category | Directional |
| **TND-S8** | Post-money SAFE cap `$6.0M`, ~12.5% dilution | See `TND-A10` | 2026-07-27 | 2026-10-31 | Founder-proposed terms | **No** — `requires-signoff-by` securities counsel + CPA |
| **TND-S9** | `$120,000` cash on hand; ~`$18,000`/mo current net burn (pre-raise) → ~6.7 mo current runway | Founder — internal bank/accounting balance (BI-13) | 2026-07-27 | 2026-10-31 | Founder-supplied; drives `TND-A11`/`TND-A12` and the current-runway math | Founder-verified; external verification operator-only (diligence). **Short shelf life — a cash position decays fast, hence the near valid-until** |

## Open dependencies (the honest gaps)

1. **`TND-S5` — no sourced market size (`severity: blocking-for-stated-audience`).** The entire market brief runs on `[ASSUMPTION]` until the founder pulls a real, dated figure, and the market brief itself says it must be replaced before an investor sees it — so at Gate 2 this open dependency forces a **SHIP-WITH-DECLARED-GAPS** verdict, not a clean SHIP (`stranger-test-log.md`). This is logged, not hidden, and the stranger test treats "get the sourced TAM" as an operator-only next step — the stack does not pretend to know it.
2. **`TND-S8` / `TND-A10` — the SAFE and cap table** require professional sign-off before the round closes. Venture Cornerstone drafts the economic view for the conversation and hard-stops on the legal instrument.
3. **`TND-S1` traction** is founder-verified internal data; an investor will verify it in diligence — that verification is theirs to do, not the stack's to assert.
