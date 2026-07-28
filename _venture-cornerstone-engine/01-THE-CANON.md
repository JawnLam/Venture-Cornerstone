---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-01-the-canon"
title: "Venture Cornerstone Engine — 01 The Canon"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: domain-canon
scope: subject-agnostic
---

# 01 — THE CANON (the business founding-document taxonomy)

> **Source-grounded.** This chapter's document classes are grounded in named, verified public frameworks (verified 2026-07-27 against canonical sources; see the OV's `_source-inventory.md`): the **Business Model Canvas** (Osterwalder & Pigneur, 9 blocks), the **Lean Canvas** (Maurya), the **Sequoia** 10-element pitch outline, **Y Combinator**'s seed-deck guidance, the **SBA** 9-section business plan, and the standard **unit-economics** canon (CAC, LTV, LTV:CAC, payback, burn, runway). Treat the taxonomy as authoritative; apply it to select and generate every stack.

## 1. The organizing rule

Every founding document answers **exactly one** business-founding question. Assign each document to its question. When a document tries to answer two, split it; when two documents answer the same question, merge them. The eight bands, in dependency order:

| Band | Question | Changes at the speed of |
|---|---|---|
| L0 | Why does this business deserve to exist? | the market |
| L1 | What is the business model? | the model |
| L2 | Who is the customer and how do we reach them? | the market |
| L3 | Do the numbers work? | the finances |
| L4 | What is the plan and the ask? | the stage/raise |
| L5 | How does it run day-to-day? | operations |
| L6 | What are the legal & ownership facts? | the law |
| V | Does the stack cohere, and can a stranger act on it? | the requirements |

Four structural consequences: (a) bands change at different speeds — binding a fast band (market) to a slow one (legal) in one file couples their change-rates and guarantees staleness; (b) **the V band verifies the decision-bearing documents (L0–L4), never operations (L5)** — a stranger who can't decide from the stack is a stack defect, not an ops defect; (c) no single document serves an investor, a lender, and an operator at once; (d) therefore the **persuasion documents — pitch deck, one-pager, executive summary — are projections, not bands**: audience-specific re-cuts of L0–L4 that must **cite** their source documents, never restate them. A deck that restates the model instead of citing it drifts from it the moment the model changes.

## 2. The menu (document classes per band, grounded in the verified frameworks)

- **L0 — Why.** Vision / problem brief (problem, who hurts, why-now); PR-FAQ (the Amazon "Working Backwards" variant) for a product with a crisp external story. For a solo/bootstrapped founder with no one to convince, L0 collapses into a section of the L1 model document.
- **L1 — Model *(unconditional)*.** The **Business Model Canvas** — 9 blocks: Customer Segments, Value Propositions, Channels, Customer Relationships, Revenue Streams, Key Resources, Key Activities, Key Partnerships, Cost Structure — OR its early-stage adaptation the **Lean Canvas**, which removes four BMC blocks (Key Partners, Key Activities, Key Resources, Customer Relationships) and swaps in Problem, Solution, Key Metrics, Unfair Advantage. *(Note: the SBA "lean startup plan" format is the Business Model Canvas verbatim — the same nine blocks; treat them as one framework, not two.)* Choose Lean Canvas for a pre-product/pre-revenue startup; BMC for a business with an established model to document. Plus a standalone value proposition where the value case is contested.
- **L2 — Market & GTM.** Market sizing (TAM/SAM/SOM); ideal-customer profile (ICP); competitive landscape; go-to-market plan; and, where the business has real traction, a **traction-evidence pack** (the paying customers, revenue, LOIs, and pilots diligence will open — each a founder-supplied source-log row). Every figure here is governed by the data discipline (`04-GENERATION-STANDARDS.md`) — a market size is sourced-and-dated or marked an assumption, never asserted.
- **L3 — Money.** The financial model — **depth-tiered by the ask** (a full model for an equity raise or debt; a summary cash-in/cash-out runway view for a bootstrapped business proving it does not run out of money; keyed to BI-2/BI-3 at selection), and always carrying a **sensitivity table** (how LTV:CAC, runway, and the ask move when a key assumption moves) and its cited assumptions register; 3–5 year projections, the SBA "Financial Projections" section; **unit economics** — CAC = sales-&-marketing spend ÷ new customers; **LTV = margin-adjusted** (ARPA × gross-margin% ÷ churn — *not* raw revenue); LTV:CAC (≈3:1 is a heuristic, not a law); CAC payback in months (often the more meaningful gate than the ratio for short-runway businesses); burn (gross vs net) and runway (cash ÷ net burn); pricing; and the cap table (economic view). The financial model **carries a mandatory assumptions register** — every projection rests on named, auditable assumptions, never buried prose.
- **L4 — Plan & Ask.** The business plan (the **SBA** 9-section traditional format: Executive Summary, Company Description, Market Analysis, Organization & Management, Service/Product Line, Marketing & Sales, Funding Request, Financial Projections, Appendix); the SBA/bank **loan plan** where debt is sought; a **risk register** (adverse events — market, execution, regulatory, competitive, financing — distinct from the assumptions register's input *values*) where a raise or a regulated business must pre-answer risk. **Projections that re-cut L0–L4 for one audience:** the investor **pitch deck** (the **Sequoia** 10-element spine — Company Purpose, Problem, Solution, Why Now, Market Size, Competition, Product, Business Model, Team, Financials — is the rigid, citable arc; **YC**'s seed guidance is prose, ~10 slides framed as questions the deck must answer, quoted from the YC library rather than treated as a fixed template); the one-pager; the executive summary; and an **objection map / Q&A prep** where a live pitch or lender meeting is part of what leaves the room (the meeting is where the stack meets a real skeptic).
- **L5 — Operations.** Operating plan (key processes, suppliers, delivery); org & hiring plan; milestones. Earned when the business actually runs at launch.
- **L6 — Legal & Ownership.** Entity choice; founder / operating agreements; IP assignment; licenses & permits; the cap table (legal view). **Every L6 document carries a `requires-signoff-by` flag** — it is drafted here but must be blessed by an attorney / CPA before use (the authority boundary; `domain_stakes: high`).
- **V — Verification *(unconditional)*.** The consistency audit (figures reconcile *and* derived figures recompute from their drivers — the arithmetic-identities check) + the stranger decision test (`05-GATES.md`); plus their evidence — the assumptions register (which travels *inside* the stack as a decision document) and the source log. An optional, **non-gating** DILIGENCE-SIM (an adversarial skeptic read) sits alongside the gate to feed the risk register and objection map without contaminating the reproducible verdict. Present in every stack.

## 3. The selection protocol (the taxonomy is a menu, not a mandate)

Operationalized as the decision procedure and machine-readable registry in `03-SELECTION.md`. The rules, from the canon:

1. **L1 (Model) and V (Verification) are unconditional.** Every stack contains a business-model document and the two gates plus their evidence logs. No business shape exempts these.
2. **L0 earns a standalone document** when anyone beyond the founder must be aligned or convinced (investors, lenders, co-founders); for a solo bootstrapper it collapses into the L1 model.
3. **L2 earns documents** when the business raises equity, enters a market that must be argued, or must actively sell/distribute. A captive first customer with no growth plan earns less.
4. **L3 is effectively unconditional the moment money is involved** — raising, borrowing, or proving viability. Depth scales with the ask: a VC raise needs the full model + unit economics; a bootstrap needs enough to prove it doesn't run out of cash.
5. **L4 scales with the audience and funding path:** a business plan when a formal plan is required; the loan plan iff debt is sought; the pitch deck iff raising equity from investors. Projections are earned by their audience, never included "because decks are customary."
6. **L5 earns a runbook-equivalent** when the business runs continuously at launch; a pre-launch idea defers it.
7. **L6:** entity/agreements/IP/licenses iff the business is formed, takes outside money, has >1 founder, or is IP-heavy/regulated. Every L6 document flags professional sign-off.
8. **Record every inclusion and every exclusion with its triggering founder-interview answer (BI-n).** The exclusion record makes the stack auditable and the selection improvable.
9. **Merging is allowed; splitting the questions is not.** Small businesses may merge L0+L1 or L5+L6 into single files, provided each merged file keeps internally separated per-band sections and the precedence declaration still resolves conflicts.

## 4. Generation standards (enforced on every document — see `04-GENERATION-STANDARDS.md`)

- Numbered requirements/claims with stable, namespaced IDs.
- Explicit non-goals / out-of-scope in every planning document — scope is defined by both edges.
- Precedence declared across the stack (which document wins on conflict); within a projection, "the source document is law; the projection conforms."
- **The data discipline (the headline standard for this OV):** every market or financial figure is founder-supplied, or sourced-and-dated, or stamped `[ASSUMPTION]`/`[UNVERIFIED]` and routed to the founder; logged in `_source-log.md`. Every quantitative document carries a first-class **assumptions register**. Fabricated market/financial figures are the single most common stack-poisoning failure.
- **Cross-document reconciliation:** the same quantity must agree everywhere it appears (the deck's ARR = the model's ARR = the plan's ARR). A figure that disagrees with its twin is a Gate 1 block.
- **The authority boundary:** documents that require professional sign-off (financials shown to investors, cap table, entity choice, agreements) are drafted, flagged `requires-signoff-by`, and never blessed as compliant.
- Write for the stranger: zero conversation context; terms defined in-stack; projections cite, never say "as discussed."

## 5. Why the discipline is worth it (teach, don't just assert)

1. **Why a one-prompt deck is worse than no deck:** a general model will fabricate a market size, a growth rate, a comparable multiple — and the founder walks into a room with someone who knows the sector and gets caught. The verify-or-flag discipline and the assumptions register exist because the cost of a fabricated figure is not a wrong number; it is lost credibility at the exact moment the business is asking for money.
2. **Why the stranger decision test is the right ship gate:** a founding stack's whole purpose is to make someone *decide* — fund, lend, run — without the founder in the room. A fresh model instance handed only the folder *is* that someone, at negligible cost. If it cannot make the decision the stack asks for, the stack has failed at its one job, and the founder finds out here instead of in the meeting.
3. **Why layering beats the all-in-one business plan:** the market moves faster than the legal structure; the pitch is re-cut every raise while the model holds. Binding them into one document means every market update forces a legal-section review and every deck tweak risks contradicting the model. Separation lets each band change at its own speed — and lets the deck be a *projection* that always cites the current model rather than a stale copy of it.
