---
type: Fleeting
Item_ID: venture-cornerstone-portfolio-benchmark-library
title: "Venture Cornerstone — Portfolio Benchmark Library"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-portfolio
role: benchmark-library
scope: cross-cartridge
---

# Venture Cornerstone — Portfolio Benchmark Library

> **The second compounding asset (the moat, REQ-M2).** A cross-cartridge, source-tagged store of the benchmark figures the operator has actually verified — real CAC, achieved LTV:CAC, confirmed churn, negotiated multiples, observed conversion rates — accumulated one business at a time. It lives in the **Grows-Through-Use Zone** (`_portfolio/`, Decision 5): the release ships it near-empty (seed rows below are illustrative and marked as such); the operator's use grows it; `git pull` must merge-not-clobber. A general LLM pointed at the same task has no such accumulated, founder-owned reference set — that is the moat.

## The flywheel has two halves — both are specified

1. **CONSULT (generation-time, `04-GENERATION-STANDARDS.md` standard 14).** Before entering an estimate-basis assumption (a CAC, an LTV:CAC, a churn, a multiple) as plausible, check this library for the sector's accumulated range. If the assumption sits outside the range, flag it in the assumptions register (`status: open`, note the divergence) and route it to the founder. This is the half that makes the library *useful* — business #4's numbers are sanity-checked against what #1–3 verified. A library that is only ever written to and never read is not a flywheel.
2. **CONTRIBUTE (close-out, `06-CLOSE-OUT.md` step 6).** At each cartridge close, append every figure this engagement *verified* — not assumed, verified: an actual CAC the business achieved, a real churn it measured, a multiple it was actually offered. Assumptions are not benchmarks; only confirmed figures enter.

## Schema (one row per benchmark)

`benchmark-ID | metric | value / range | sector | stage | basis | source | date | valid-until | provenance | anonymized-from`

- `metric` — CAC, LTV:CAC, monthly churn, gross margin, CAC payback, ARPA, conversion rate, revenue multiple, etc.
- `value / range` — a point or a range; ranges are preferred once ≥2 observations exist.
- `sector` / `stage` — the tags a consult query matches on (e.g., `vertical-B2B-SaaS` / `seed`). A benchmark is only meaningful within its sector and stage.
- `basis` — how it was verified (achieved-in-a-cartridge, sourced-public, negotiated-term).
- `valid-until` — benchmarks decay; a CAC from 2026 is not a 2029 CAC. Past this date the row is stale and must be re-verified before it is consulted as current.
- `provenance` — `cartridge-verified` (grown from a real engagement) or `sourced` (a public benchmark added as a seed).
- `anonymized-from` — the anonymization tag (see below), never the business's name.

## The anonymization rule (resolves the M4 / confidentiality contradiction)

REQ-M4 (cross-operator cohort effects) is `n-a` precisely because founder stacks are confidential — yet REQ-M2 harvests founder-derived CAC/LTV into a cross-cartridge store. That is safe for a single operator's own portfolio, but a **leak-by-design the moment a second founder's data enters the same library**. The rule that makes M2 safe:

1. **No business identity ever enters a row.** `anonymized-from` carries a sector/stage tag and an opaque cartridge counter (`vertical-B2B-SaaS·seed·#3`), never the business name, the founder, or any identifying specific.
2. **Aggregate before you expose (k-anonymity).** A metric is only published as a *range across ≥ N=3 contributing cartridges* in the same sector/stage. A single cartridge's number is held privately (in that cartridge's own records) and does not appear as a library row until two more join it — one observation is identifying; a range over three is not.
3. **Single-operator scope by default.** This library is the *operator's own* accumulated store across *their own* businesses. If it is ever shared across operators (a future, opt-in cohort mode), only the k-anonymized ranges travel, never the underlying rows — and that is the only form in which REQ-M4 could ever be reconsidered.

Consulting always reads the aggregated ranges, never a raw single-cartridge figure. This is what lets the moat compound without becoming a confidentiality breach.

## Seeds (illustrative — marked; not cartridge-verified)

*These are public rules-of-thumb seeded so the CONSULT step has something to check against on day one. They are `provenance: sourced`, not `cartridge-verified`, and carry no operator data. Replace/augment with real verified figures as cartridges close.*

| benchmark-ID | metric | value / range | sector | stage | basis | source | date | valid-until | provenance | anonymized-from |
|---|---|---|---|---|---|---|---|---|---|---|
| BM-seed-1 | LTV:CAC (healthy) | ~3:1 (floor ~1:1; >5:1 may signal under-investment) | generic SaaS | any | sourced-public | HBS Online | 2026-07-27 | 2027-07-27 | sourced | n/a (public) |
| BM-seed-2 | CAC payback (healthy) | < 12 months (< 18 tolerated) | generic SaaS | early | sourced-public | SaaS unit-economics canon | 2026-07-27 | 2027-07-27 | sourced | n/a (public) |
| BM-seed-3 | monthly churn (SMB SaaS, rough) | ~3–5% / mo | SMB SaaS | early | sourced-public | SaaS unit-economics canon | 2026-07-27 | 2027-07-27 | sourced | n/a (public) |

## Do not

- Do not enter an assumption as a benchmark. Only verified figures contribute; the assumptions register is where *unverified* numbers live.
- Do not publish a single cartridge's figure as a library row before N=3 aggregation — that is the confidentiality leak the anonymization rule exists to prevent.
- Do not consult a row past its `valid-until` as if it were current — re-verify or treat as stale.
