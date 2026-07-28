---
type: VCS_Market_Document
Item_ID: "3A7C9E20-5D18-4B64-9F02-6E1B8C4D0A59"
title: "Tendly — Market Brief (Sizing, ICP, Competition, GTM)"
vcs_Business_Slug: "TND"
vcs_Doc_Class: market-sizing
vcs_Merged_Classes: [icp-competitive, go-to-market]
vcs_Band: 2
vcs_Document_Status: shipped
vcs_Precedence_Rank: 2
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Market Brief (L2 · Market & GTM)

> Answers: **who is the customer and how do we reach them?** Owns market figures — which are **all `[ASSUMPTION]`** and reconcile with `_assumptions-register.md` `TND-A7..A9`. **Read this warning first:** not one market-size number below is sourced. The founder has done no third-party sizing (BI-7). These are placeholders the founder must replace before any investor sees them; they are shown as assumptions precisely so nobody mistakes them for research.

## 1. Market sizing (all `[ASSUMPTION / UNVERIFIED]`)

| Layer | Definition | Centers | At ARPA `$3,600` (`TND-A1`) | Anchor |
|---|---|---|---|---|
| **TAM** | US licensed center-based childcare facilities | ~130,000 | **`$468M`** | `TND-A7` |
| **SAM** | Independent (1–5 location) centers in 6 launch states | ~28,000 | **`$100M`** | `TND-A8` |
| **SOM** | Obtainable by end-Y3 | 600 | **`$2.16M`** ARR (~2% of SAM) | `TND-A9` |

**Method + gap:** top-down. TAM is the founder's recollected count of US licensed centers (`TND-A7`) — **no source** — and SAM/SOM are filtered down from it, so they inherit the same unverified flag. This gap is tagged **`severity: blocking-for-stated-audience`** in the assumptions register and source log: because this brief itself says the figure must be replaced before an investor sees it, that open dependency drives a **SHIP-WITH-DECLARED-GAPS** verdict at the decision test rather than a clean SHIP — honest `[ASSUMPTION]` stamping does not launder a self-admitted disqualifier into a pass. **Before investor use:** replace `TND-A7` with a dated figure from Child Care Aware of America, IBISWorld, or state licensing registries, then rebuild SAM bottom-up from the launch states' registries. The SOM (600 centers) is a plan target tied to the growth path (`TND-A5`), not a sales-capacity model.

## 2. Ideal customer profile (ICP)

- **Firmographic:** independent, owner-operated childcare center; 1–3 locations; ~40–120 licensed capacity; located in a licensing-heavy state with unannounced, records-first inspections.
- **Buyer:** the owner or center director — the person personally accountable when an inspector finds a gap.
- **Trigger to buy:** a recent citation or corrective-action plan, an upcoming renewal inspection, or a new director inheriting a paper binder they do not trust.
- **Disqualifiers:** large multi-site chains with in-house compliance staff and custom systems (different sale, deferred); home-based/family childcare (too small for `$299`/mo).

## 3. Competitive landscape (categories, not fabricated share)

- **Childcare-management suites** (a Brightwheel-class category, `TND-S6`): own billing, attendance, and parent communication; compliance is a shallow checkbox. **Tendly's edge:** compliance *depth* built around per-state licensing rules — the part they treat generically. Tendly can sit alongside them rather than replace them. *(No market-share or revenue figure is asserted for any named competitor — none is known, so none is claimed.)*
- **Spreadsheets + paper binders + "do nothing"** (`TND-S7`): the real status quo and the true competitor. **Edge:** the whole product is the reduction of this manual, high-anxiety, high-risk work.
- **Horizontal HR / certification-tracking tools:** track expirations generically but do not encode childcare ratio rules or produce inspection-ready childcare reports. **Edge:** vertical fit.

## 4. Go-to-market

- **Motion:** founder-led outbound (the CEO is a former director, which opens director-to-director conversations the incumbents cannot) → inside sales as volume grows. High-touch compliance onboarding is the wedge that also drives the low churn assumption (`TND-A4`).
- **Beachhead:** 6 launch states chosen for licensing intensity and registry accessibility; expand state-by-state because compliance logic is per-state.
- **Loops:** referrals between neighboring centers and within local director networks and licensing-prep groups.
- **Unit-economics tie-in:** the motion must hold blended CAC near **`$2,400`** (`TND-A3`) for the 10-month payback in `04-financial-summary.md` to hold; CAC is the metric this GTM plan is accountable to.
