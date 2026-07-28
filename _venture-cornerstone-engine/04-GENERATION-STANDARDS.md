---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-04-generation-standards"
title: "Venture Cornerstone Engine — 04 Generation Standards"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: generation-standards
scope: subject-agnostic
---

# 04 — GENERATION STANDARDS (enforced on every document, every stack)

> **Generate each selected document from its structural Type and required sections (`03-SELECTION.md` registry). These standards are not style advice — they are gate criteria. The consistency audit (`05-GATES.md`, Gate 1) checks them mechanically; a document that violates them does not advance to `internally-consistent` and does not ship. The taxonomy that decides which documents exist is `01-THE-CANON.md`; this chapter governs how each one is built.**

## The standards

1. **Numbered claims with stable, namespaced IDs.** ID scheme = business slug + document-class tag + number (`ACME-FIN-7`, `ACME-MKT-3`, `ACME-GTM-2`). IDs are never reused or renumbered — reconciliation checks, the assumptions register, and the source log reference them by ID. A claim states *what is true or asked*, never *how it will be executed* (an execution step belongs in the L5 operating plan, not the L1 model or L3 financials).
2. **Explicit non-goals** in every planning-bearing document (L2 GTM, L4 plan, L5 operations, any projection). Scope is defined by both edges: what this business is *not* doing, what market it is *not* addressing, what the raise is *not* for. A scope with only an inside is not bounded, and a stranger reads an unbounded scope as either naïveté or evasion.
3. **Precedence declared** across the stack (which document wins on conflict), and within every projection: **"the source document is law; the projection conforms."** The pitch deck, one-pager, and executive summary re-cut L0–L4; when a projection and its source disagree, the source governs and the projection is corrected — never the reverse. The precedence declaration is an extractable field, set at selection and recorded in `_selection-record.md`.
4. **The DATA DISCIPLINE — the headline standard for this OV.** Every market or financial figure that appears in any document has exactly one of three provenances, and carries it visibly at the point of use:
   - **Founder-supplied** — a number the founder brought (revenue to date, a signed contract value, a known unit cost). Tagged to the founder and logged.
   - **Sourced-and-dated** — a public or purchased figure with an inline citation and a verification date (e.g., *"US SMB payroll TAM $38B (IBISWorld, 2025; verified 2026-07-27)"*). The source and date are mandatory; a figure "everyone knows" with no citation is not sourced.
   - **Stamped `[ASSUMPTION]` or `[UNVERIFIED]` and routed to the founder** — a number the OV needs but cannot source or the founder has not supplied. It is stamped inline, entered in the assumptions register with an owner, and surfaced to the founder as an open decision. It is **never** written as if it were fact.

   The OV **structures founder-supplied data and never invents a market size, growth rate, conversion rate, comparable multiple, or any other quantitative claim on its own authority.** A fabricated market or financial figure is the single most common stack-poisoning failure in this domain — the cost is not a wrong number, it is lost credibility at the exact moment the business is asking for money.
5. **Every external figure and dependency is logged in `_source-log.md`.** Before writing any market number, benchmark, competitor fact, regulatory claim, or named external source into a document, record it. One row per figure, keyed to the claim ID that uses it:

   `claim-ID | quantity/claim | source | date | valid-until | method-of-check | verified? | provenance`

   where `provenance` ∈ {founder-supplied, sourced, assumption}, `verified?` ∈ {yes, no, routed-to-founder}, and `valid-until` is the date past which the figure must be re-verified (a market size or benchmark decays; a signed-contract value may not). A figure with no `_source-log.md` row is a Gate 1 block. A figure whose row says `verified? = no` and `provenance = sourced` is unfinished — it is either verified, downgraded to `[ASSUMPTION]`, or removed. A figure past its `valid-until` at any later session is a REVISE-STACK time trigger (`05-GATES.md`), not a silent carryover — this is the anti-staleness backstop for a stack that lives across quarters.
6. **One single-owned ASSUMPTIONS REGISTER, cited not copied (PF-5 — the buried financial assumption).** Financial and market assumptions — growth rate, churn, CAC, ARPA, gross margin, ramp, close rate, price, TAM basis — are never buried in prose or hidden inside a spreadsheet cell. The cartridge file `_assumptions-register.md` is the **single authored home** for every assumption; each is a named, numbered line:

   `assumption-ID | quantity | value | basis (founder / sourced / estimate) | owner | status | severity | valid-until | drives (claim-IDs)`

   `status` ∈ {open, founder-confirmed, sourced, superseded}; `severity` ∈ {blocking-for-stated-audience, non-blocking} (an open assumption the stack itself says must close before its audience acts is `blocking-for-stated-audience` — it drives the Gate 2 SHIP / SHIP-WITH-DECLARED-GAPS verdict); `valid-until` is the decay date. **Ownership is single:** the register file is law, and a document's in-line assumptions section *cites* register rows by `assumption-ID` — it never re-authors the value. Two authored copies of one assumption is the OV's own PF-6/PF-8 defect. **The register travels inside the frozen stack** (it moves into `Stack/`, not `Records/`, at packaging): for anyone judging the financial model, the register with owners, statuses, and severities *is* a decision document, and the stranger receives it. An assumption at `status: open` and `severity: blocking-for-stated-audience` at Gate 2 does not silently pass — it forces a SHIP-WITH-DECLARED-GAPS verdict. The register is what makes a model auditable rather than a black box: a stranger disputes an assumption, not the arithmetic.
7. **Cross-document reconciliation — the same quantity agrees everywhere it appears.** ARR in the deck = ARR in the financial model = ARR in the business plan = ARR in the executive summary. Raise amount, valuation, headcount, unit price, margin, runway, TAM: each is authored once in its home document and cited elsewhere by the same claim ID. A figure that disagrees with its twin across documents is a Gate 1 hard block (PF-6 cross-document number drift). This is why projections cite and never restate: a restated number is a second copy that drifts the moment the source changes (PF-8 projection restatement).
8. **The AUTHORITY BOUNDARY — `requires-signoff-by` (`domain_stakes: high`).** This OV drafts every document but issues no authoritative financial, tax, legal, or securities guidance. Any document that must be blessed by a licensed professional before use carries a first-class `requires-signoff-by` field naming the role:
   - investor-facing financials / financial model shown to raise capital → **CPA**
   - cap table (economic and legal view) → **securities attorney / CPA**
   - entity choice → **attorney / CPA**
   - founder & operating agreements → **attorney**
   - IP assignment, licenses & permits, regulated-industry claims → **attorney**
   - loan application financials → **CPA / lender's own underwriting**

   The document is drafted to completion, then flagged; it is **never** marked compliant, blessed, or presented as final legal/financial advice. The flag is a hard stop the founder must clear with a named professional, not a disclaimer. A `requires-signoff-by` document missing its flag is a Gate 1 block.
9. **BEHAVIORAL / DEFINITIONAL COMPLETENESS — every comparative threshold resolves to a named extractable value (PF-9 unparameterized threshold).** Any document that judges, compares, gates, or qualifies against a threshold must define that threshold as a named, extractable value — not as prose. Prose like *"healthy CAC payback,"* *"a strong margin,"* *"acceptable churn,"* *"a reasonable burn multiple,"* *"conservative growth"* is an implicit decision that passes the consistency audit (the document reads fine) and fails the stranger test (as `stack-should-answer` questions: *"healthy by what number?"*). For every such term, resolve it: *"CAC payback target ≤ 12 months (basis: SaaS median, sourced 2026-07-27); this plan projects 9."* Ask of every comparative word: **would two competent readers of this stack put the same number on it?** If not, name the number, cite its basis in the source log or assumptions register, and state where the business lands against it. Front-run this here so the stranger test is a confirmation, not a discovery.
10. **Write for the stranger.** Zero conversation context. The investor, lender, or operating partner reading the stack was not in the founder interview. Every term is defined at first use or in an in-stack glossary; every acronym is expanded once; no "as discussed," no "the usual model," no reference to anything not present in the frozen `Artifacts/` folder. A projection that says "see our earlier conversation" instead of citing a source document fails this standard.
11. **`Item_ID` is a UUID, never a slug (vault conformance).** Every generated document's `Item_ID` frontmatter value MUST be an uppercase 8-4-4-4-12 UUID (Drafts-style, e.g. `3F2A9C41-7B0E-4D6A-9E11-2C8F5A0B7D34`), matching the target vault's `Master_Schema` (Baseplate generation-standard 11, ported). Slugs (e.g. `acme-financial-model`) are not permitted in shipped type-instance artifacts; generate a fresh UUID per document and never reuse one. The `_types/` templates carry an `Item_ID: "<UUID>"` placeholder to enforce this at instantiation. *(Engine chapters like this one are the exception: they use the `venture-cornerstone-engine-<nn-slug>` scheme, because they are subject-agnostic OV infrastructure, not per-business type instances.)*
12. **Every derived figure shows its computation from named drivers (arithmetic transparency).** A derived quantity — LTV, CAC payback, ARR, runway, net burn, blended margin, ownership %, any year-over-year projection — is written with its formula and its driver `assumption-ID`s visible, so the figure recomputes from the register. Do not state a derived number as a bare result: write *"LTV = ARPA $3,600/yr × GM 80% ÷ annual churn 18% (drives from A-1, A-2, A-4) = $16,000"*, not *"LTV $16K"*. **Periods must match:** every identity's inputs enter on the same period — an annual ARPA divided by a monthly churn inflates LTV 12× (the classic *"$3,600 × 0.80 ÷ 1.5%/mo = $192,000"* error; the correct figure is $16,000 at 18%/yr, or equivalently monthly margin ÷ monthly churn). Convert before you divide, and say which period the identity is in. Gate 1's arithmetic-identities check recomputes each derived figure from its drivers (the manual protocol and an optional runnable checker live in `_meta/ARITHMETIC-CHECK.md`); a bare derived number with no shown computation cannot be checked and is a defect. This is the generation-side of the audit's headline check — agreement across documents does not make a number *correct*, only *consistent*.
13. **Every `VCS_Financial_Document` carries a SENSITIVITY TABLE (`domain_stakes: high`).** The most decision-useful artifact in a money-band stack is how the answer moves when a key assumption moves. For each load-bearing assumption (churn, CAC, growth, close rate, price), show ±Δ → effect on the headline outputs (LTV:CAC, runway, months of runway on the ask). A stack that states "LTV:CAC 6.7:1" without showing "at 30% annual churn it falls to ~4:1" hides its own fragility; the sensitivity table surfaces exactly the line a sector-literate reader will probe first. Required today — not parked as a future "scenario-simulation" moat (REQ-E4). Each sensitivity row cites the register assumption it flexes.
14. **Consult the benchmark library when judging an assumption's plausibility (the REQ-M2 flywheel).** Before entering an estimate-basis assumption (a CAC, an LTV:CAC, a churn, a multiple) as plausible, check `_portfolio/benchmark-library.md` for the sector's accumulated, source-tagged range. If the assumption sits outside the library's range, flag it (`status: open`, note the divergence) and route it to the founder. **Consulting** the library — not only contributing to it at close-out — is the actual flywheel: business #4's assumptions are sanity-checked against what #1–3 verified. If the library has no row for the metric, note it as a gap to fill at this cartridge's close-out.

## Non-goals of this OV (state the edges)

- **Not a compliance authority.** It does not certify financials, opine on securities law, choose your entity for you, or replace a CPA, attorney, or licensed advisor. See standard 8.
- **Not a market-research oracle.** It does not generate market sizes, growth rates, or comparables from its own authority; it structures and stress-tests the founder's data and sourced facts. See standard 4.
- **Not a template dispenser.** It does not hand every business the same document pack; documents are earned per-business by the selection registry (`03-SELECTION.md`). An unearned document is gold-plating; an unexplained exclusion is a defect.
- **Not a persuasion engine that invents a story.** Projections re-cut what the source documents already establish; they do not manufacture traction, logos, or claims the stack cannot support.

## Per-document generation sequence

For each selected document, in dependency-band order (L0 → L1 → L2 → L3 → L4 → L5 → L6, projections after their sources, V last):

1. **Instantiate the structural Type's required sections** — the source of truth is the `03-SELECTION.md` class registry ("Required sections" column) plus the Type definition in `_types/`. There is no separate `_templates/` directory; the registry + Type files *are* the templates.
2. **Fill numbered claims** with stable, namespaced IDs (standard 1).
3. **Apply the data discipline as you write every figure** (standard 4): tag each number founder-supplied / sourced-and-dated / `[ASSUMPTION]`, and log its `_source-log.md` row (standard 5) at the moment you write it — not in a later pass.
4. **Build the assumptions register** for any quantitative document (standard 6): cite the single-owned `_assumptions-register.md` by ID, consult `_portfolio/benchmark-library.md` for each estimate's plausibility (standard 14), and write every derived figure with its computation from named drivers (standard 12). For a `VCS_Financial_Document`, add the sensitivity table (standard 13).
5. **Resolve every comparative threshold to an extractable value** (standard 9); add the non-goals section (standard 2).
6. **Reconcile against sibling documents** (standard 7): each shared quantity is authored once and cited by ID elsewhere; if this document is a projection, confirm it cites its source and restates nothing.
7. **Flag `requires-signoff-by`** on any authority-boundary document (standard 8).
8. **Run the document's internal consistency pass:** every claim ID unique; every in-document cross-reference resolves; every figure has a provenance and a `_source-log.md` row; every assumption is in the register; no `[TBD]`/`[UNVERIFIED]`/`[ASSUMPTION]` outside its declared home; every threshold named.
9. **Advance the document's `vcs_Document_Status` to `internally-consistent`.**

Only when **every** selected document is `internally-consistent` do you run the stack-level consistency audit (`05-GATES.md`, Gate 1). The status ladder is `drafting → internally-consistent → audited → stranger-passed → shipped`; this chapter carries a document from `drafting` to `internally-consistent` only. Gate 1 advances it to `audited`; Gate 2 to `stranger-passed`; close-out (`06-CLOSE-OUT.md`) to `shipped`.

## Do not

- Do not invent a market size, growth rate, conversion rate, or comparable multiple. Structure the founder's numbers; source or stamp everything else (standard 4).
- Do not bury a financial assumption in prose or a spreadsheet cell. It goes in the assumptions register with an owner and a status (standard 6).
- Do not restate a figure a source document already owns. Cite it by ID; a second copy drifts (standards 3, 7).
- Do not leave a comparative threshold as an adjective. "Healthy," "strong," "reasonable" each resolve to a named number with a cited basis (standard 9).
- Do not mark any authority-boundary document compliant, final, or blessed. Draft it, flag `requires-signoff-by`, route it (standard 8).
- Do not carry a figure from a previous cartridge or a prior conversation without re-verifying and re-dating it at the point of use.
