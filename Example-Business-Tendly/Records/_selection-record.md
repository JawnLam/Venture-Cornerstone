---
type: VCS_Selection_Record
Item_ID: "A4C81E52-3B0D-49F7-9E12-6F5A2D0C7B83"
title: "Tendly — Selection Record"
vcs_Business_Slug: "TND"
vcs_Doc_Class: selection-record
vcs_ID_Scheme: "TND-A<n> assumptions / TND-S<n> sources / TND-C<n> claims / TND-D<n> deck slides"
vcs_Precedence_Declaration: "financial-model > market-sizing > lean-canvas > vision-brief > pitch-deck > one-pager (projections conform; they cite, never restate)"
vcs_Financial_Depth_Tier: "full (BI-2 raising + BI-3 equity)"
vcs_Audience_Bar: "$25K-$100K pre-seed angel checks; wants durable retention + a believable market; a lead-sized check wants the round substantially spoken for (BI-4b, founder-supplied read, no signed commitments)"
vcs_Document_Status: shipped
vcs_Precedence_Rank: 0
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Selection Record

> Locked before drafting (F8). Every inclusion **and** every exclusion cites its triggering founder-interview answer (BI-n). An unexplained exclusion is a defect; an unexplained inclusion is gold-plating. Unconditional set: **L1 Model** + **V Verification** (canon rule 1).

## Decisions

| Class | Band | Include / Exclude | Triggering BI-answer | Structural Type |
|---|---|---|---|---|
| Lean Canvas | L1 | **Include** (unconditional) | canon rule 1 | `VCS_Model_Document` |
| vision / problem brief | L0 | **Include** | BI-4 angels must be convinced; BI-1 the story is a compliance-pain narrative | `VCS_Narrative_Document` |
| PR-FAQ | L0 | **Exclude** (vision brief suffices) | BI-1 no product-launch PR story; BI-4 audience is investors, not press/customers | — |
| market sizing (TAM/SAM/SOM) | L2 | **Include** — primary class of the merged market brief (`vcs_Doc_Class: market-sizing`) | BI-3 equity raise; BI-7 a market that must be argued | `VCS_Market_Document` |
| ICP + competitive landscape | L2 | **Include** (folded into the one market brief, `vcs_Merged_Classes`) | BI-5 actively sold; BI-7 named competitor categories | `VCS_Market_Document` |
| go-to-market plan | L2 | **Include** (folded into the market brief) | BI-5 founder-led + inside sales | `VCS_Market_Document` |
| standalone competitive-landscape doc | L2 | **Exclude** (merge into market brief) | BI-7 few competitor categories; one doc suffices | — |
| financial model + unit economics | L3 | **Include** — `vcs_Doc_Class: financial-model`, depth tier **`full`** | BI-3 equity, BI-6 revenue model, BI-11 money crosses a boundary | `VCS_Financial_Document` |
| pricing | L3 | **Fold into** the financial model (merged class, `vcs_Merged_Classes`) | BI-6 single simple `$299`/mo price point | merged into `VCS_Financial_Document` |
| unit economics | L3 | **Fold into** the financial model (merged class) | BI-6 recurring per-center revenue | merged into `VCS_Financial_Document` |
| cap table (economic view) + use of funds | L3 | **Include** (economic view only) — merged into the financial model, band 6 legal carried as flags (`vcs_Merged_Bands: [3, 6]`) | BI-3 equity raised; BI-8 >1 founder | `VCS_Financial_Document` |
| cap table (legal view) / entity choice / founder agreement | L6 | **Include as flag, not as drafted compliant document** — `requires-signoff-by` securities attorney + CPA | BI-8 two founders; BI-11 the SAFE is a security | flag in `VCS_Financial_Document` + this record |
| data-handling / ToS note | L6 | **Include as flag** — `requires-signoff-by` privacy counsel | BI-9 stores children/staff PII | flag in `VCS_Financial_Document` |
| IP / patent assignment | L6 | **Exclude** | BI-9 not IP-heavy, no patents | — |
| investor pitch deck (projection) | L4 | **Include** — `projects-from` L0–L3 | BI-3 equity; BI-4 investor audience | `VCS_Pitch_Document` |
| one-pager / executive summary (projection) | L0/L4 | **Include** — `projects-from` L0–L3 | BI-4 angels need a fast top-of-funnel read | `VCS_Narrative_Document` |
| business plan (SBA 9-section) | L4 | **Exclude** | BI-4 angels decide from deck + one-pager + model; no board/lender requires a formal plan | — |
| SBA / bank loan plan | L4 | **Exclude** | BI-3 no debt sought | — |
| operating plan / org & hiring | L5 | **Exclude** (hiring folds into use-of-funds) | BI-2 pre-scale (12 centers); BI-8 team of two→three | — |
| consistency audit + stranger test + assumptions register + source log | V | **Include** (unconditional) | canon rule 1 | `VCS_Stranger_Test_Log` + registers |

## Resulting stack (in `Artifacts/`)

`01-vision-brief.md`, `02-lean-canvas.md`, `03-market-brief.md`, `04-financial-summary.md`, `05-pitch-deck.md`, `06-one-pager.md`, **and `_assumptions-register.md`** — the register now **travels inside the stack** (Decision 10 issue 2: it is a decision document for anyone judging the financial model, so the stranger receives it at Gate 2; it moves to `Stack/` at packaging). The remaining V evidence stays at cartridge root — `_source-log.md` (→ `Records/`), `_freeze-hashes.md` (Gate-1 SHA-256s), and `stranger-test-log.md`.

## Financial depth tier (recorded at selection, not improvised at draft)

`financial model | include | BI-3 equity | full` — a full-tier model (3–5 yr build, unit economics, **sensitivity table**, cap table, cited assumptions register), keyed to **BI-2 (raising)** and **BI-3 (equity)** per the depth-tier rule (`03-SELECTION.md` → Depth tiers). Not the summary tier (that is for a bootstrapped/pre-revenue viability proof). This is the decision the worked example previously improvised as "summary, not model" in prose — it belongs here, as an auditable field.

## ID scheme

Business slug **`TND`**. `TND-A<n>` named assumptions; `TND-S<n>` source-log rows; `TND-C<n>` numbered claims inside documents; `TND-D<n>` deck slides. Every figure that appears in more than one document is anchored to a `TND-A<n>` or `TND-S<n>` — that anchor is the reconciliation spine Gate 1 walks.

## Precedence declaration

Canonical classes (mirrors `vcs_Precedence_Declaration`): `financial-model` > `market-sizing` > `lean-canvas` > `vision-brief` > `pitch-deck` > `one-pager`.

Resolution rules: on any **numeric** conflict, the financial model (`04-financial-summary.md`, class `financial-model`) wins — it is the numeric authority, computing from the register's `TND-A<n>` rows. On **market** figures, the market brief (`03-market-brief.md`, class `market-sizing`) wins, and its figures must reconcile with the register's `TND-A7..A9` rows (the register is the authored home of every assumption; each document cites, never re-authors). On the **model**, `02-lean-canvas` wins. The two **projections** (`05-pitch-deck`, `06-one-pager`) own **no** figures: they cite the source document's `TND-` anchor and conform to it; a projection that disagrees with its source is a Gate 1 block, not a rounding choice.

## Audience bar (BI-4b — the ST-2 anchor; stays in Records, never in the stack)

The target angels write **`$25,000`–`$100,000` checks on a pre-seed thesis**; several have told the founder they want to see **durable retention** and **a market they can believe** before committing; a lead-sized check would want the round substantially spoken for. Founder-supplied read of specific target angels, no signed commitments. Gate 2's ST-2 decision-plausibility is judged against this bar; it is recorded **here** (mirrored in `vcs_Audience_Bar`) and deliberately absent from every document the stranger receives — the stranger must not be handed the rubric it is graded against. *(Formerly register row TND-A13, relocated; the register travels in-stack, this record does not.)*

## Authority-boundary note (Decision 4)

The L6 cap-table legal view, entity choice, founder agreement, and PII/ToS handling are **within scope and earned**, but Venture Cornerstone does **not** issue them as compliant documents. They are represented here and in `04-financial-summary.md` as `requires-signoff-by` hard stops routed to a securities attorney, a CPA, and privacy counsel. The economic cap-table view (ownership math for the raise) is drafted for the investor conversation; the legal instrument is not.
