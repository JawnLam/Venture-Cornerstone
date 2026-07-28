---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-portfolio-failure-catalog
title: "Venture Cornerstone — Portfolio Failure Catalog"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-portfolio
role: failure-catalog
scope: cross-cartridge
---

# Venture Cornerstone — Portfolio Failure Catalog

> **The compounding asset (the moat, REQ-M1).** Cross-cartridge failure/lesson log in the PF-code idiom. Loaded at every cartridge session start; guard against every entry. Appended at each cartridge close-out with any new failure mode the engagement surfaced (BFR-11/BFR-12). This file lives in the **Grows-Through-Use Zone** (`_portfolio/`, Decision 5): the release ships the seed entries below; the operator's use grows the rest; `git pull` must merge-not-clobber when the OV eventually ships.

Each entry: name, trigger, why it matters, fix, prevention. Seeded at design time from two sources — the transferable Baseplate failure modes (ported and retargeted to the business domain) and the business-native modes named when the data discipline and the two gates were locked (Decisions 2–4). The founding stack lives or dies on its numbers; most entries here are ways a number goes wrong.

> **PF-namespace resolution rule (Decision 10).** Every bare `PF-n` reference anywhere in this OV — engine chapters, Types, worked examples — resolves against **this** catalog's numbering, NOT Baseplate's. This OV's numbers differ from Baseplate's (here PF-6 = cross-document number drift, PF-8 = projection restatement, PF-9 = unparameterized threshold; in Baseplate PF-9 was enumeration drift and PF-8 was the unparameterized metric). When a cross-reference genuinely means a Baseplate failure mode, it MUST carry the explicit prefix **"Baseplate PF-n"**. A bare `PF-n` that only resolves against Baseplate's catalog is a defect a REVIEW pass corrects.

## PF-1 — Market/financial figure fabrication

*Ported and sharpened from Baseplate PF-1 (dependency fabrication). The single most common stack-poisoner in this domain.*

**Trigger:** A document asserts a market or financial figure — a TAM, a growth rate, a comparable multiple, a churn benchmark, a "market grows 20% a year" — that the founder did not supply and no source backs. The model invented a plausible number and wrote it as fact.

**Why it matters:** The stack's whole job is to survive scrutiny by someone who knows the sector. An invented TAM does not read as a wrong number to that reader — it reads as a founder who does not know their own market, and it costs the raise at the exact moment the business is asking for money. A fabricated figure also poisons everything downstream: the model's revenue line, the deck's ask, the plan's projections all inherit it.

**Fix:** Strip the fabricated figure. Replace it with a founder-supplied number, a sourced-and-dated external figure logged in `_source-log.md`, or an explicit `[ASSUMPTION]`/`[UNVERIFIED]` stamp routed to the founder and entered in `_assumptions-register.md`. Re-run cross-document reconciliation for anything that consumed it.

**Prevention:** The data discipline (`04-GENERATION-STANDARDS.md`, Decision 3): the OV never invents a market or financial figure. Every quantitative claim is founder-supplied, sourced-and-dated, or stamped an assumption. Gate 1 blocks any figure that is neither sourced nor entered in the assumptions register.

## PF-2 — Stale-context carryover

*Ported from Baseplate PF-2. The bursty, one-business-at-a-time cadence makes carryover tempting and staleness invisible.*

**Trigger:** A figure, assumption, competitor fact, or market date is reused from another business's stack (or an earlier session of this one) without re-verification — because it "was true last time." A SaaS churn benchmark from the previous cartridge, a comparable multiple from six months ago, a TAM that has since moved.

**Why it matters:** The operator runs one business at a time; a number carried from the last engagement looks vetted but was verified for a different business, market, or date. It silently propagates into the new stack and detonates in a room where the sector has moved.

**Fix:** Re-verify the carried figure against its current source for *this* business; re-date it in `_source-log.md`, or drop it and re-elicit. An assumption carried over becomes a fresh assumptions-register row owned for this cartridge.

**Prevention:** The anti-staleness generation standard: every imported figure carries its source and verification date at point of use. The founder interview forbids carrying a BI-answer over from a previous business without re-asking. Gate 1's source-log completeness check catches undated carryovers.

## PF-3 — Orphan requirement/verification

*Ported from Baseplate PF-3. The bijection breaks in one direction.*

**Trigger:** A claim, requirement, or figure with no check — or a check/reconciliation entry with no claim behind it. A revenue assumption no gate reconciles; a Gate 1 reconciliation row pointing at a figure no document actually states.

**Why it matters:** An unverified claim can silently be wrong; a claimless check tests something no one asserted. The verification layer only works if the map from claim to check is total. An orphan is where an error hides with no record of how it entered.

**Fix:** Add the missing check (a reconciliation row, a source entry, an assumptions-register owner), add the missing claim, or delete the orphan with a recorded reason in the traceability matrix.

**Prevention:** `_meta/TRACEABILITY.md` holds the bijection (BFR-15); Gate 1 checks no orphans in either direction. Every figure `sourced-from` a source or a named assumption; every earned document `earned-by` a BI-answer.

## PF-4 — Gold-plating

*Ported from Baseplate PF-4. Venture Cornerstone applies it to itself: ~10 structural Types keyed by an enum, not one Type per document class.*

**Trigger:** A document is included because it is customary — "every startup has a pitch deck," "a business plan needs a full org chart" — not because a founder-interview answer earned it. It fails the "would the stranger who must decide need this?" test. A bootstrapped solo micro-business handed a cap table and a full investor deck it will never send.

**Why it matters:** Unearned documents cost generation and maintenance effort, couple change-rates that should stay independent, and bury the documents the decision-maker actually needs under ones no audience asked for. A stack padded to look complete reads as unfocused to the person deciding.

**Fix:** Remove the unearned document, or record the BI-answer that earns it in `_selection-record.md`. An inclusion that cannot cite its trigger is gold-plating and comes out.

**Prevention:** Selection protocol (`03-SELECTION.md`): every inclusion AND every exclusion cites its triggering BI-answer. Unconditional set is exactly L1 Model + V; everything else must be earned. Gate 1 checks every earned document maps back to a BI-answer.

## PF-5 — Silent assumption absorption

*Ported from Baseplate PF-5. In the financial domain the absorbed assumption is almost always a number.*

**Trigger:** A financial or market unknown the interview did not settle is filled with a plausible default and written as confident prose — "customers churn at 3% monthly," "gross margin is 70%" — instead of being entered in the assumptions register as a named, owned assumption.

**Why it matters:** The buried assumption looks like a decided fact but no one decided it. The financial model rests on it; the deck's ask inherits it; if it is wrong the whole downstream is wrong and there is no record of where the error entered. This is the failure the mandatory assumptions register exists to prevent.

**Fix:** Lift the buried assumption out of prose into `_assumptions-register.md` as a first-class row with an owner and a status; route it to the founder to confirm, source, or revise. The prose then cites the register, it does not restate the number as fact.

**Prevention:** Every quantitative document carries a first-class assumptions register (the `VCS_Financial_Document` mandate). Generation standard: a number that is neither founder-supplied nor sourced is an assumption and goes in the register — it is never written as bare fact. Gate 1 blocks any figure not sourced-or-assumed.

## PF-6 — Cross-document number drift

*Business-native. The reconciliation failure Gate 1 exists to catch — the domain's headline defect.*

**Trigger:** The same quantity disagrees with itself across documents. The deck's ARR ≠ the financial model's ARR; the plan's headcount ≠ the org chart's; the SOM in the market doc ≠ the revenue the model projects against it. Each figure is locally plausible; together they contradict.

**Why it matters:** A sector-literate reader cross-checks the deck against the model as a matter of course, and a number that disagrees with itself is the fastest possible credibility loss — it says the founder does not have their own numbers straight. Because each copy passes its own document's read, the drift is invisible per-document and only surfaces when someone reads two documents side by side. That someone is the investor, unless it is Gate 1 first.

**Fix:** Establish which document owns the quantity (the financial model owns ARR, burn, runway; the cap table owns ownership %). Every other appearance either cites the owner or restates the identical value; reconcile the drifted copies to the owner. Log the reconciliation.

**Prevention:** The `reconciles-with` relation is Gate 1's spine: every quantitative claim reconciles with its twin across documents; any figure that disagrees with itself is a hard block. Cross-document reconciliation is a first-class generation standard (Decision 3), not a polish pass.

## PF-7 — Missing professional-sign-off flag

*Business-native. The authority-boundary defect — the reason `domain_stakes` is `high` (Decision 4).*

**Trigger:** A regulated or regulated-adjacent document — cap table, entity choice, founder/operating agreement, investor financials, loan application — is drafted and shipped without its `requires-signoff-by` hard stop naming the professional (securities attorney, CPA, licensed advisor) who must bless it before use.

**Why it matters:** The OV drafts these documents but has no authority to make them compliant. A cap table or an equity split used as if it were vetted is how a founder walks into a securities or tax problem believing they were covered. The flag is the honest authority boundary; its absence lets the founder mistake a draft for a blessed instrument.

**Fix:** Add the `requires-signoff-by` flag to the document, naming the professional role and stating plainly that the document is a draft pending that sign-off. Verify every L6 (Legal & Ownership) document and every investor-facing financial carries it.

**Prevention:** The canon flags every L6 document class and the cap table with `requires-signoff-by` at the schema level (`01-THE-CANON.md`, Decision 4). Generation stamps the flag; Gate 1 checks that every `requires-signoff-by` document carries its professional-sign-off hard stop. The OV never blesses a document as compliant.

## PF-8 — Projection restating instead of citing

*Business-native; the direct analog of Baseplate's PF-9 (cross-document enumeration drift), specialized to the deck-as-projection.*

**Trigger:** A projection — the pitch deck, one-pager, or executive summary — copies content out of its source documents (the model's numbers, the market's TAM, the plan's ask) instead of citing them, and the copy then drifts when the source changes. The deck restates the financial model's ARR verbatim; the model is revised; the deck now silently contradicts it.

**Why it matters:** A projection is defined as an audience-specific re-cut of L0–L4 that must *cite* its sources, never restate them (Decision 7). The moment it restates, it becomes a stale copy that drifts on the next model revision — reintroducing PF-6 (number drift) through the back door, in the single most-scrutinized document in the stack. The deck is what the investor reads first and cross-checks hardest.

**Fix:** Replace the restated content with a citation to the owning document (`projects-from`): the projection names the source figure, it does not re-key it. Where a projection must display a number, it displays the owner's current value and is reconciled to it at Gate 1.

**Prevention:** The canon's projection rule: "the source document is law; the projection conforms" — cite, never restate. Gate 1 reconciles every projection figure against its source document (the restatement-drift check) and flags any projection content that duplicates rather than cites. This is the PF-9/enumeration-drift discipline applied to the projection layer.

## PF-9 — Unparameterized acceptance threshold

*Business-native; ported from Baseplate PF-8 (unparameterized acceptance metric), retargeted to financial success metrics.*

**Trigger:** A success metric or acceptance criterion names a threshold in prose — "healthy CAC payback," "a target gross margin," "acceptable burn multiple," "LTV:CAC in a good range" — that no document, model tab, or assumptions-register row actually names as an extractable value. The prose promises a number lives somewhere; nowhere does.

**Why it matters:** It passes the consistency audit (the sentence is coherent) and usually survives the stranger test (the reader still understands the business). But the threshold is never pinned, so at decision time whoever reads it fills in their own "healthy" — the founder's 12-month CAC payback and the investor's 6-month one both read as "healthy," and the metric silently means nothing. The verification layer exists to prevent exactly this negotiable ambiguity.

**Fix:** Name the threshold as a first-class, extractable value — a row in the assumptions register or a named cell in the financial model ("CAC payback target: 12 months," "gross margin floor: 60%") — marked as an acceptance input. The prose then cites the pinned value.

**Prevention:** During generation of any success-metric or acceptance section, for every comparative phrase ("healthy," "target," "acceptable," "within," "below") ask: *does the number this compares against exist as an extractable field somewhere in the stack?* If it only exists as prose, parameterize it. Gate 1's extractability check catches unpinned thresholds. Kin to PF-3 (bijection breaks at the value level) and PF-5 (an implicit number hiding in confident prose).

## Adding new entries

At each cartridge close-out — and whenever two consecutive stranger-test reruns are blocked by the same `stack-should-answer` question class — add the new failure mode here in the same format: name (PF-n), trigger, why it matters, fix, prevention. Add a dated provenance line naming the cartridge that surfaced it (the pattern the ported entries follow). Trace every new PF into `_meta/TRACEABILITY.md` in the same change (BNF-3). The catalog grows; every new business loads it; the failure recurs less. This is the portfolio's compounding value — business #4 ships cleaner because #1–3 taught this file what goes wrong.
