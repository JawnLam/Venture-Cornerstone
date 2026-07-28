---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-meta-arithmetic-check
title: "Venture Cornerstone — Arithmetic-Identities Check (manual protocol + optional runnable checker)"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-meta
role: arithmetic-check
scope: subject-agnostic
---

# Arithmetic-Identities Check (Gate 1's headline check, made runnable)

> **Agreement across documents proves a number is *consistent*, not *correct*.** Gate 1's arithmetic-identities item (`05-GATES.md`) requires every derived figure to recompute from its stated drivers. This file is that check made concrete: the identity table with its unit discipline, the manual walkthrough, and an **optional** embedded checker you can copy-run (BNF-1 keeps the OV markdown-only, so the tool ships *inside* this markdown, not as a loose script — running it is never required; the manual walkthrough is always sufficient).

## The identities (unit discipline is part of the identity)

| Derived figure | Identity | Unit rule |
|---|---|---|
| Margin-adjusted LTV | ARPA × GM% ÷ churn | ARPA and churn on the **same period** (both annual or both monthly). Annual ARPA ÷ monthly churn inflates LTV 12× — the classic error. |
| LTV:CAC | LTV ÷ CAC | dimensionless |
| CAC payback (months) | CAC ÷ (monthly revenue per customer × GM%) | numerator $, denominator $/month |
| ARR | paying units × ARPA (annual) | "annualized" = ×12 on a monthly figure, applied **once** |
| Net burn | gross burn − revenue | per month, both sides |
| Runway (months) | cash at t₀ ÷ net monthly burn | **state the cash convention** as a named register line: current cash (pre-raise view) or raise-only (a conservative post-raise floor that treats existing cash as consumed by the pre-close gap). Either is legal; silently mixing them is a block. |
| Ownership | Σ holders = 100% | post-round, same round |
| Projection year | prior year × (1 + stated growth) | growth per the same period step |

## Manual walkthrough (always sufficient)

1. List every derived figure in the stack (LTV, LTV:CAC, payback, each ARR point, net burn, each runway, ownership rows, projected years).
2. For each, pull its driver values **from the assumptions register by ID** (standard 12 requires the computation be shown at point of use — if it is not shown, that is already a defect).
3. Recompute by hand with the identity above, matching periods first.
4. Any mismatch beyond honest rounding (~2%) is a **Gate 1 block**: fix the figure or its drivers, re-run reconciliation for every document that cites it.

## Optional runnable checker

Copy the block below into `check_arithmetic.py`, fill the `TENDLY`-style dict from the stack's assumptions register, run `python3 check_arithmetic.py`. Exit 0 = all identities recompute; exit 1 = block.

```python
#!/usr/bin/env python3
"""Venture Cornerstone arithmetic-identities checker (optional tooling for Gate 1).
Recomputes each derived figure from its stated drivers and compares to the claimed
value. Drivers/claims are declared in a small dict per stack — fill it from the
assumptions register. All rates ANNUAL unless suffixed _mo. Tolerance covers
honest rounding (default 2%)."""
TOL = 0.02

def close(claimed, computed, tol=TOL):
    if computed == 0: return claimed == 0
    return abs(claimed - computed) / abs(computed) <= tol

def check(name, claimed, computed, unit=""):
    ok = close(claimed, computed)
    print(f"{'PASS' if ok else 'FAIL'}  {name}: claimed {claimed:,.10g}{unit} vs recomputed {computed:,.10g}{unit}")
    return ok

def run(d):
    ok = True
    arpa, gm = d["arpa_yr"], d["gm"]
    churn = d.get("churn_yr") if d.get("churn_yr") is not None else d["churn_mo"] * 12  # simple annualization
    ltv = arpa * gm / churn
    ok &= check("LTV = ARPA×GM÷churn (annual)", d["ltv_claimed"], ltv, "$")
    ok &= check("LTV:CAC", d["ltv_cac_claimed"], ltv / d["cac"])
    ok &= check("CAC payback (mo) = CAC÷(ARPA×GM÷12)", d["payback_mo_claimed"], d["cac"] / (arpa * gm / 12), "mo")
    for label, units, arr in d["arr_series"]:
        ok &= check(f"ARR {label} = units×ARPA", arr, units * arpa, "$")
    if "net_burn_mo" in d:
        ok &= check("net burn = gross − revenue/mo", d["net_burn_mo"], d["gross_burn_mo"] - d["revenue_mo"], "$")
        ok &= check("current runway (mo) = cash÷net burn", d["runway_now_claimed"], d["cash_now"] / d["net_burn_mo"], "mo")
    if "raise_amt" in d:
        ok &= check("post-raise runway (mo) — declared convention: " + d["post_raise_convention"],
                    d["runway_post_claimed"], d["raise_basis"] / d["post_burn_mo"], "mo")
    if "ownership" in d:
        ok &= check("ownership sums to 100%", 100.0, sum(d["ownership"]), "%")
    print("RESULT:", "ALL IDENTITIES RECOMPUTE" if ok else "BLOCK — at least one derived figure fails its identity")
    return ok

TENDLY = {
    "arpa_yr": 3600, "gm": 0.80, "churn_yr": 0.18, "churn_mo": None, "cac": 2400,
    "ltv_claimed": 16000, "ltv_cac_claimed": 6.7, "payback_mo_claimed": 10,
    "arr_series": [("today", 12, 43200), ("Y1", 50, 180000), ("Y2", 200, 720000), ("Y3", 600, 2160000)],
    "gross_burn_mo": 21600, "revenue_mo": 3600, "net_burn_mo": 18000,
    "cash_now": 120000, "runway_now_claimed": 6.7,
    "raise_amt": 750000, "raise_basis": 750000, "post_burn_mo": 42000,
    "runway_post_claimed": 17.9, "post_raise_convention": "raise-only floor (TND-A6; pre-close gap funded by TND-A11)",
    "ownership": [87.5, 12.5],
}
if __name__ == "__main__":
    import sys
    sys.exit(0 if run(TENDLY) else 1)
```

## Reference runs (executed 2026-07-27 against the worked example)

**Tendly (`Example-Business-Tendly`, drivers TND-A1..A12) — clean:**

```
PASS  LTV = ARPA×GM÷churn (annual): claimed 16,000$ vs recomputed 16,000$
PASS  LTV:CAC: claimed 6.7 vs recomputed 6.666666667
PASS  CAC payback (mo) = CAC÷(ARPA×GM÷12): claimed 10mo vs recomputed 10mo
PASS  ARR today = units×ARPA: claimed 43,200$ vs recomputed 43,200$
PASS  ARR Y1 = units×ARPA: claimed 180,000$ vs recomputed 180,000$
PASS  ARR Y2 = units×ARPA: claimed 720,000$ vs recomputed 720,000$
PASS  ARR Y3 = units×ARPA: claimed 2,160,000$ vs recomputed 2,160,000$
PASS  net burn = gross − revenue/mo: claimed 18,000$ vs recomputed 18,000$
PASS  current runway (mo) = cash÷net burn: claimed 6.7mo vs recomputed 6.666666667mo
PASS  post-raise runway (mo) — declared convention: raise-only floor (TND-A6; pre-close gap funded by TND-A11): claimed 17.9mo vs recomputed 17.85714286mo
PASS  ownership sums to 100%: claimed 100% vs recomputed 100%
RESULT: ALL IDENTITIES RECOMPUTE
```

**Negative demonstration — the units bug the identity discipline exists to catch** (annual ARPA ÷ 1.5%/mo churn claimed as a `$192,000` LTV — the error that once lived in generation-standard 12's own example):

```
FAIL  LTV = ARPA×GM÷churn (annual): claimed 192,000$ vs recomputed 16,000$
FAIL  LTV:CAC: claimed 80 vs recomputed 6.666666667
PASS  CAC payback (mo) = CAC÷(ARPA×GM÷12): claimed 10mo vs recomputed 10mo
PASS  ARR today = units×ARPA: claimed 43,200$ vs recomputed 43,200$
RESULT: BLOCK — at least one derived figure fails its identity
```

The checker catches in one second what a stack of perfectly-reconciled documents cannot: a number that agrees with all its twins and is still wrong.
