---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-03-selection"
title: "Venture Cornerstone Engine — 03 Selection"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: selection-protocol
scope: subject-agnostic
---

# 03 — SELECTION (choose the document set)

> **Run after the interview (`02-ELICITATION.md`), before any generation (F8). Map the business's shape to a document set using the registry below. Record every inclusion AND every exclusion with the founder-interview answer that triggered it — an unexplained exclusion is a defect; an unexplained inclusion is gold-plating. Lock the selection before drafting a line of document prose.**

## Decision procedure

1. **Include L1 (Model) and the V (Verification) layer unconditionally.** Every stack contains a business-model document (Business Model Canvas or Lean Canvas) and the two gates plus their evidence logs (consistency audit + stranger test + `_assumptions-register.md` + `_source-log.md`). No business shape exempts these.
2. **Walk each other class against its earning condition** in the registry, citing the founder-interview answer (BI-n) that fires or fails it. L3 (Money) is effectively unconditional the moment BI-11 shows money crossing a boundary — treat it as earned unless the business genuinely moves no money.
3. **For each class, write one line in the `VCS_Selection_Record`:** `class | include/exclude | triggering BI-answer | structural Type`. The exclusion lines are not optional — "no cap table" needs "BI-8: solo founder, no equity split; BI-3: bootstrapped, no raise."
4. **Set the ID scheme and the precedence declaration.** Namespace = the business slug (e.g., `ACME-FIN-3` for the third figure in Acme's financial model). Precedence declares which document wins on conflict — as a default: the L1 model is law for the business model; the L3 financial model is law for every figure; each projection conforms to its source documents ("the source is law; the projection conforms"). These are extractable fields, locked now, not prose later.
5. **Apply merges, not splits.** A small business may merge L0+L1 (why + model) or L5+L6 (operations + legal) into one file, provided the file keeps internally separated per-band sections and precedence still resolves conflicts. Never merge two bands' *questions* into one undifferentiated document. A projection (deck, one-pager, exec summary) never merges into its source — it cites.
6. **Flag every `requires-signoff-by` document at selection time,** so the hard stop is visible before drafting: cap table, entity choice, founder/operating agreements, IP/licenses, and any financials shown to investors (the authority boundary; `domain_stakes: high`).

## The class registry (machine-readable)

Each row: canon class → band, earning condition (the founder-shape signal, citing the BI-answer), structural Type, and the required sections the generated document must contain. This registry is the operational form of the canon's menu (`01-THE-CANON.md` §2) and is grounded in the same verified public frameworks the canon cites — Business Model Canvas / Lean Canvas at L1, the standard unit-economics canon at L3, the SBA 9-section plan and the Sequoia 10-element + YC prose deck at L4. It satisfies the structural-Type requirement without one Type file per class (the `vcs_Doc_Class` enum keys each row to its structural Type).

| Class | Band | Earning condition (cite the BI-answer) | Structural Type | Required sections |
|---|---|---|---|---|
| vision / problem brief | 0 | Standalone iff anyone beyond the founder must be aligned or convinced (BI-4); else collapses into a section of the L1 model | `VCS_Narrative_Document` | Problem; Who hurts; Why now; Vision / success definition |
| PR-FAQ | 0 | Market-facing product with a crisp external story worth pre-writing (BI-1, BI-4) | `VCS_Narrative_Document` | Press release (working-backwards); Anticipated customer FAQs; Anticipated stakeholder FAQs |
| Business Model Canvas | 1 | **Unconditional** — established model to document (BI-2 operating) | `VCS_Model_Document` | The 9 BMC blocks: Customer Segments; Value Propositions; Channels; Customer Relationships; Revenue Streams; Key Resources; Key Activities; Key Partnerships; Cost Structure |
| Lean Canvas | 1 | **Unconditional alternative** — pre-product / pre-revenue startup (BI-2 idea/pre-seed) | `VCS_Model_Document` | Problem; Solution; Key Metrics; Unique Value Proposition; Unfair Advantage; Customer Segments; Channels; Cost Structure; Revenue Streams |
| value proposition | 1 | The value case is contested or non-obvious (BI-1, BI-7) | `VCS_Model_Document` | Customer jobs/pains/gains; Product; Value map; Fit statement |
| market sizing (TAM/SAM/SOM) | 2 | Raising equity (BI-3 equity) OR entering a market that must be argued (BI-7) | `VCS_Market_Document` | TAM; SAM; SOM; Sizing method (top-down and/or bottom-up); Sources & assumptions |
| ICP + competitive landscape | 2 | Any go-to-market beyond a single captive first customer (BI-5, BI-7) | `VCS_Market_Document` | Ideal-customer profile; Segments; Named competitors; Positioning / differentiation |
| go-to-market plan | 2 | Product must be actively sold or distributed (BI-5) | `VCS_Market_Document` | Channels; Motion (sales/self-serve/partner); Funnel; CAC assumptions; Launch sequence |
| traction-evidence pack | 2 | The business has real traction — paying customers, revenue, signed LOIs, pilots (BI-2 raising/operating) — that diligence will open | `VCS_Market_Document` | Traction summary (logos/revenue/retention); Evidence index (contracts, LOIs, usage — each a founder-supplied source-log row); Cohort/retention proof; What is verifiable vs claimed | 
| financial model | 3 | **Effectively unconditional once money is involved** — raising, borrowing, or proving viability (BI-3, BI-6, BI-11). **Depth-tiered** (see § Depth tiers): a full model for an equity raise or debt; a summary model for a bootstrapped idea proving it does not run out of cash | `VCS_Financial_Document` | 3–5 yr P&L projections; Revenue build; Cost build; Cash flow; Burn & runway; **Sensitivity table (mandatory)**; **Assumptions register (cited, mandatory)** |
| unit economics | 3 | Recurring or per-customer revenue exists (BI-6) | `VCS_Financial_Document` | CAC; LTV (margin-adjusted); LTV:CAC; CAC payback (months); Gross margin; Assumptions |
| pricing | 3 | A revenue model exists (BI-6) | `VCS_Financial_Document` | Pricing structure; Tiers/packaging; Rationale/benchmarks; Sensitivity; Assumptions |
| cap table | 3 / 6 | Equity split among >1 party OR equity is raised (BI-3 equity, BI-8) — **`requires-signoff-by` securities counsel / CPA** | `VCS_Financial_Document` | Ownership by holder; Option pool; Pre/post-money; Dilution scenarios; **Sign-off hard-stop flag** |
| business plan | 4 | A formal plan is required by an audience — investors, board, lender, or self-discipline (BI-4) | `VCS_Plan_Document` | The SBA 9 sections: Executive Summary; Company Description; Market Analysis; Organization & Management; Service/Product Line; Marketing & Sales; Funding Request; Financial Projections; Appendix |
| SBA / bank loan plan | 4 | Debt financing sought (BI-3 debt, BI-11) | `VCS_Plan_Document` | SBA 9 sections + Loan request (amount/use/term); Repayment ability; Collateral; Personal financial statement ref |
| investor pitch deck (projection) | 4 | Raising equity from investors (BI-3 equity, BI-4 investors) — `projects-from` L0–L3, **cites, never restates** | `VCS_Pitch_Document` | The Sequoia 10-element spine: Company Purpose; Problem; Solution; Why Now; Market Size; Competition; Product; Business Model; Team; Financials/Ask — each slide citing its source document; YC prose as the framing questions each slide answers |
| one-pager / executive summary (projection) | 0 / 4 | An audience needs a fast top-of-funnel read (BI-4) — `projects-from`, **cites, never restates** | `VCS_Narrative_Document` | What/who/why-now; The ask; Traction/proof; Source-document citations |
| risk register | 4 | Raising equity or debt where risks must be pre-answered, or a regulated/IP-heavy business (BI-3, BI-4, BI-9) — distinct from the assumptions register (risks ≠ assumptions: a risk is an adverse event, an assumption is an input value) | `VCS_Plan_Document` | Key risks (market, execution, regulatory, competitive, financing); Likelihood/impact; Mitigation; Owner — each risk cites the document it threatens |
| objection map / Q&A prep | 4 (projection) | A live pitch or lender meeting is part of what leaves the room (BI-4 investors/lenders) — the meeting is where the stack is stress-tested by a real skeptic | `VCS_Narrative_Document` | Anticipated hard questions; The honest answer (citing a stack document); Where the stack is genuinely weak and the founder's response — `projects-from`, cites its sources |
| operating plan | 5 | Business runs continuously with real operations at launch (BI-2 operating, BI-5) | `VCS_Operations_Document` | Key processes; Suppliers/delivery; Milestones; Roles; Failure modes & responses |
| org & hiring plan | 5 | Team will grow beyond the founders (BI-8) | `VCS_Operations_Document` | Org structure; Roles to hire; Sequence; Comp bands; Assumptions |
| entity choice | 6 | Business will be legally formed / take outside money (BI-9, BI-11) — **`requires-signoff-by` attorney / CPA** | `VCS_Legal_Document` | Options considered (LLC/C-corp/S-corp/etc.); Recommendation rationale; Tax/liability tradeoffs; **Sign-off hard-stop flag** |
| founder / operating agreements | 6 | >1 founder (BI-8) — **`requires-signoff-by` attorney** | `VCS_Legal_Document` | Roles & responsibilities; Equity & vesting; Decision rights; Exit/departure terms; **Sign-off hard-stop flag** |
| IP / licenses & permits | 6 | IP-heavy or regulated industry (BI-9) — **`requires-signoff-by` attorney** | `VCS_Legal_Document` | IP assignment; Registrations needed; Licenses/permits by jurisdiction; **Sign-off hard-stop flag** |
| consistency audit + stranger test + assumptions register + source log | V | **Unconditional** — the ship gates and their evidence, every stack | `VCS_Stranger_Test_Log` (+ `_assumptions-register.md`, `_source-log.md`) | Gate 1 reconciliation table; Gate 2 restatement/decision/questions; Question classification; Rerun log |

## Depth tiers (the financial class scales with the ask)

The financial class is not one-size; its depth keys to **BI-2 (stage)** and **BI-3 (funding path)** at selection time, recorded in the selection record so it is an auditable decision, not improvised at draft time:

- **Full model** — equity raise (BI-3 equity) or debt (BI-3 debt): 3–5 yr projections, revenue/cost build, cash flow, unit economics, sensitivity table, cap table.
- **Summary model** — bootstrapped / pre-revenue proving viability (BI-3 bootstrapped/none): a cash-in/cash-out runway view and a unit-economics sketch — enough to show the business does not run out of money. Still carries the assumptions register and (where it computes ratios) the sensitivity table.

Record the tier as a field: `financial model | include | BI-3 equity | full`. (The worked example originally improvised "summary, not model" in prose — that decision belongs here, keyed to BI-2/BI-3, not invented at draft time.)

## Doc-class discipline (enum + merges)

- `vcs_Doc_Class` is a **canonical registry class** (the Class column above, slugified: `financial-model`, `market-sizing`, `pitch-deck`, `traction-evidence-pack`, `risk-register`, `objection-map`, …), **not a filename**. A document's filename is free (`04-financial-summary.md`); its `vcs_Doc_Class` must be a registry value. A class value that names a file rather than a canon class (e.g. `financial-summary`) is a defect.
- **Merged documents** (procedure step 5) carry the `vcs_Doc_Class` of their **primary band** plus a `vcs_Merged_Bands` field listing the others (an L0+L1 file: `vcs_Doc_Class: business-model-canvas`, `vcs_Merged_Bands: [0, 1]`). The enum never needs a synthetic "merged" value.
- **The V-band instruments** — `_assumptions-register.md` and `_source-log.md` — are cartridge **instruments**, not instances of the eight document Types: `type: Fleeting`, `vcs_Doc_Class: assumptions-register` / `source-log`, `vcs_Band: V`. The assumptions register travels in `Stack/` (a decision document, Decision 10); the source log stays in `Records/`. `VCS_Stranger_Test_Log` is the only V-band document *Type*.

## Output

- A locked `VCS_Selection_Record` in the cartridge (inclusions + exclusions + triggering BI-answers + precedence declaration + ID scheme + financial depth tier), frozen at the end of SELECT (Decision 9 — no drafting before it locks).
- The document set to generate, each mapped to its structural Type and required sections, in dependency-band order (L0→L6, projections after their sources, V last).

## Do not

- **Do not skip the exclusion record.** "We didn't build a cap table" needs the reason ("BI-8: solo founder, no equity split; BI-3: bootstrapped, no equity raise"). Every excluded class earns one line citing the BI-answer that excused it.
- **Do not include a document because it is customary.** "Every startup has a deck" is not an earning condition; raising equity from investors (BI-3 + BI-4) is. Customary-but-unearned is gold-plating — a named failure mode.
- **Do not split a band's question across files or merge two questions into one.** Merge whole small bands (L0+L1) with internally separated sections when warranted; never let one file answer two founding questions without separation, and never let a projection swallow its source.
- **Do not draft a `requires-signoff-by` document without its hard-stop flag set at selection.** The authority boundary is declared here, before a word is written.
