---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "9F3C1A70-4B22-4E88-A1D6-7C0E5F2B9A41"
title: "Tendly — Business Cartridge Manifest"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-cartridge-manifest
vcs_Business_Slug: "TND"
vcs_Funding_Path: "equity — angel round, post-money SAFE"
---

# Tendly — Business Cartridge Manifest

> **The reference worked example.** This is an **invented** seed-stage business built to demonstrate Venture Cornerstone end-to-end: founder interview → selection (earned inclusions + recorded exclusions) → generation in band order → Gate 1 consistency audit → Gate 2 stranger decision test → package. Every market and financial figure in this cartridge is **fictional** and is stamped either `founder-supplied` or `[ASSUMPTION]` — that stamping *is* the demonstration of the data discipline (Decision 3). No number here is a real-world market statistic and none should be reused as one.

> **Updated to the post-Decision-10 standards (2026-07-27).** This example was reworked so it now *demonstrates* the twelve self-audit fixes rather than violating them. It shows: **arithmetic identities** (every derived figure — LTV, LTV:CAC, CAC payback, ARR, net burn, both runways — recomputes from its named driver IDs); the **mandatory sensitivity table** (churn/CAC/growth ±Δ → LTV:CAC, payback, runway); the **assumptions register travelling inside the stack** (`Artifacts/_assumptions-register.md`) with per-row **`severity`** and **`valid-until`**; **BI-4b** (the `$25K`–`$100K` pre-seed angel bar Gate 2 ST-2 is judged against) and **BI-13** (`$120,000` current cash, so runway is never an implicit `$0`); canonical `vcs_Doc_Class` values with depth tiers and merged-band/class fields; Gate-1 **freeze hashes** (`_freeze-hashes.md`); local **PF-namespace** discipline (PF-6 number-drift, PF-8 projection-restatement); and — the headline — a **SHIP-WITH-DECLARED-GAPS** Gate-2 verdict, because the unsourced TAM (`TND-A7`) is `blocking-for-stated-audience` and honest `[ASSUMPTION]` stamping must not launder a self-admitted disqualifier into a clean SHIP.

## Business

**Tendly** — the compliance operating system for independent childcare centers. It tracks staff certification expiry, licensed staff-to-child ratios, immunization and background-check records, incident logs, and state-inspection prep, so an owner-operated center never walks into a licensing visit with a paper binder and a gap it did not know about. B2B vertical SaaS; sold founder-led + inside sales; `$299` per center per month (founder-supplied list price).

## Stage & ask

Raising a **`$750,000`** angel round on a post-money SAFE (BI-2, BI-3). Live traction: **12 paying centers**, **`$43,200` ARR** run-rate (founder-supplied, BI-12). **`$120,000` cash on hand today** against ~`$18,000`/mo current burn — ~6.7 months of runway (BI-13), the clock dating the Q4-2026 close. The raise funds ~18 months of post-raise runway (at `$42,000`/mo) to ~200 centers (`$720,000` ARR) and a Series A conversation. Angel audience bar: `$25K`–`$100K` pre-seed checks (BI-4b).

## Why this business earns a real spread (what it exercises)

- **L3 Money with a mandatory assumptions register:** unit economics (CAC, margin-adjusted LTV, LTV:CAC, payback, burn, runway) built *entirely* on named assumptions — the register is the point.
- **A pitch deck as a projection:** the Sequoia-arc deck `projects-from` the model, market, and financials and **cites** them; it restates no figure it does not own (PF-8 projection-restatement guard).
- **The authority boundary made concrete:** equity crosses a boundary (a SAFE is a security) and there are two founders, so the cap table + entity + founder agreement are **earned but flagged `requires-signoff-by`** a securities attorney and a CPA — drafted-as-flag, never blessed as compliant (Decision 4).
- **Cross-document reconciliation:** the deck's ARR = the financial summary's ARR = the canvas's revenue math = the one-pager's headline. One raise number, one price, one traction figure, everywhere (Gate 1).

## Cartridge contents

- `_founder-interview.md` — the BI-1..BI-13 record incl. **BI-4b** (audience bar) and **BI-13** (current cash); each answer a citable line.
- `_selection-record.md` — documents earned + excluded, each citing a BI-answer; precedence declaration; **financial depth tier** (`full`); the `TND-` ID scheme.
- `_source-log.md` — every figure/dependency: claim | source | date | **valid-until** | method | verified? (`TND-S<n>`). Now in `Records/` (packaged).
- `Stack/` (working name `Artifacts/`, renamed at packaging) — THE STACK the stranger received at Gate 2: vision brief, lean canvas, market brief, financial summary, pitch deck, one-pager, **and `_assumptions-register.md`** — every named assumption behind a figure (`TND-A<n>`) with owner, status, **severity**, and **valid-until**; it now travels inside the stack (Decision 10 issue 2).

## Close-out record (2026-07-27 — the cartridge is CLOSED)

`06-CLOSE-OUT.md` ran to completion; this cartridge is now the packaged dossier:

- **Layout:** top level = `AI-BOOTSTRAP.md` + `Stack/` (7 documents + `MANIFEST.md`) + `Records/` (this file, interview, selection record, source log, stranger-test log, freeze hashes, `README.md`) + `Workspace/` (`execution-state.md`, `deviations.md`). Nothing else.
- **Verdict packaged:** Gate 2 **SHIP-WITH-DECLARED-GAPS** (run 1, rerun count 0); the one blocking gap (unsourced TAM, `TND-A7`) is surfaced on the `Stack/MANIFEST.md` cover and as the first row of the bootstrap's operator-input register — a pre-use hard stop, not a footnote.
- **Hash continuity verified:** `Stack/MANIFEST.md` digests = `_freeze-hashes.md` = bytes on disk (re-freeze of 2026-07-27 after the non-decisional Decision-11 edits; Gate 1 re-run clean, verdict carried per the REVISE-STACK cosmetic rule).
- **Reference sweep clean:** no `Stack/` document reaches into `Records/` (one live hit — the market brief citing the stranger-test log — was caught by the sweep and fixed before packaging; the sweep works).
- **Packaging verification:** mechanical check green; fresh-instance **orientation probe** result recorded below.
- **Status:** every Stack document advanced to `vcs_Document_Status: shipped` — now true by the ladder's own definition, because the package exists.

### Orientation probe (fresh instance, packaged folder only)

**PASS (2026-07-27).** A fresh instance (no prior context) was given only the packaged folder and asked what it would do first. It (1) went to `AI-BOOTSTRAP.md` as the self-announced entry point, (2) **verified `Stack/MANIFEST.md` before acting** — recomputed all seven SHA-256s and byte counts, all matching — (3) correctly stated the business (compliance OS for independent childcare centers, `$299`/center/mo, 12 centers / `$43,200` ARR, fictional worked example), the decision asked (angel: take the meeting / fund / pass on the `$750,000` SAFE), the verdict (**SHIP-WITH-DECLARED-GAPS**) and the blocking gap (unsourced TAM/SAM before investor use), and (4) started reading at `01-vision-brief.md` per the declared order, using only the bootstrap and Stack documents. No reach into `Records/`, no unresolvable reference. Packaging verification step 5.2: **green**.

- `_freeze-hashes.md` — Gate-1 SHA-256 of every `Artifacts/` file; Gate 2 ran against these exact bytes (kept outside `Artifacts/`).
- `stranger-test-log.md` — the Gate 2 record: verdict **SHIP-WITH-DECLARED-GAPS** (blocking gap: the unsourced TAM `TND-A7`), kept outside `Artifacts/`.
