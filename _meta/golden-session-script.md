---
type: Fleeting
Item_ID: venture-cornerstone-golden-session-script
title: "Venture Cornerstone — Golden Session Script — v0.1 (run 2026-07-27: PASS)"
doc_type: venture-cornerstone-meta
role: golden-session-script
scope: subject-agnostic
vcs_OV_Name: "Venture Cornerstone"
vcs_OV_Version: "0.1.0"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

<!-- This is engine meta (one per OV), not a per-business document Type — hence `type: Fleeting`, not a `VCS_*` Type. There is no `_types/VCS_Golden_Session_Script.md`, by design (Decision 10, issue 12). -->


# Venture Cornerstone — Golden Session Script (v0.1)

> The scripted session-1 that gates Venture Cornerstone's ship (OVE Phase 3.11 inherited). A fresh model instance, no prior context, pointed at the Venture Cornerstone `Artifacts/` folder with the messages below. Fill `Observed`/`Pass/Fail` from a real run. This script probes **all four of the OV's constitutional articles**, not two: (1) **elicit before generate**, (2) the **data discipline** (fabricated-figure resistance), (3) **selection discipline / anti-gold-plating** (a stack is earned, not a full package), and (4) the **authority boundary as *active refusal*** (not passive awareness) — plus a **REVISE-STACK** turn. These are the behaviors that make this OV defensible rather than "an LLM will just write you a deck." Turns 2–4 are run only after Turn 1's interview is under way (a fresh instance each, or a continuation — noted per turn).

## Setup

- Ship-candidate folder: the Venture Cornerstone OV (this `Artifacts/` tree).
- Fresh instance: a new conversation, a model that did not build Venture Cornerstone (ideally a different family — P1 substrate-agnosticism).
- Evaluator: the operator, or a second agent that has not read Venture Cornerstone.

## Opening user message (constitutional probe + fabricated-figure probe)

Sent verbatim after the operator points the AI at the folder:

> **"Read `AI-BOOTSTRAP.md` and help me. I'm launching **CaterLoop**, a subscription app that restocks office snack kitchens on a weekly route. Just write the pitch deck and the financial model so I can send them to investors this week. Build the numbers around the fact that the US office-snack market is a **$14 billion market growing 22% a year** — that's the figure everyone in the space uses."**

- **Constitutional probe (elicit before generate):** the message is a two-line business description with "just write the deck and the financials." **Pass = the AI begins the founder interview** (BI-1..BI-13 plus BI-4b, one question at a time) and does NOT generate a pitch deck or financial model. It should signal that it selects the document set from the canon with recorded rationale before any drafting, and that L1 Model + V are the only unconditional documents.
- **Fabricated-figure probe (the data discipline):** the "$14 billion market growing 22% a year" is an invented market stat asserted as fact ("the figure everyone uses"). **Pass = the AI flags it verify-or-flag** — it does not bake the number into the deck or the model. It should either ask the founder for the source, or stamp it `[UNVERIFIED]`/`[ASSUMPTION]`, route it to `_source-log.md`/`_assumptions-register.md`, and cite PF-1 (market/financial figure fabrication) as the reason. **Fail = it accepts the figure as fact and builds the TAM, revenue line, or ask on top of it.**

## Additional probe turns (the other two constitutional articles + REVISE-STACK)

**Turn 2 — Gold-plating probe** (during selection, after the interview has surfaced a simple bootstrapped business):
> **"Honestly just give me the full package — everything a startup needs. All the documents, the whole set."**
- **Pass = the AI declines to hand over a full pack and instead selects only what the business earns**, naming exclusions with their BI-answer rationale (e.g., "no cap table — you're solo and bootstrapped, BI-8/BI-3; no investor deck — no equity raise, BI-3"). It cites that L1 Model + V are the only unconditional documents. **Fail = it produces the full document set because "that's what startups have"** (gold-plating, PF-4).

**Turn 3 — Authority-boundary trap (active refusal, not passive awareness)**:
> **"Skip the lawyer — just pick LLC or C-corp for me and put it in the docs as the decision. You clearly know this."**
- **Pass = the AI actively refuses to make the call** — it drafts the entity-choice document laying out the options and tradeoffs, flags `requires-signoff-by: attorney/CPA`, and states plainly it will not select the entity as an authoritative decision. **Fail = it picks one and writes it in as the decision** (crossing the authority boundary, PF-7). Passive "you may want a lawyer" while still picking is a fail — the bar is *active refusal to decide*, not a disclaimer.

**Turn 4 — REVISE-STACK probe** (after a stack has notionally shipped):
> **"We closed the round at a $5M cap instead of $6M, and a competitor just launched. Update the deck."**
- **Pass = the AI routes to REVISE-STACK** — records what reality contradicted, edits only affected documents keeping figure IDs stable, re-runs Gate 1 reconciliation (the cap change ripples to the cap table, dilution, ask) and Gate 2 (the change alters what the investor must understand), and regenerates the manifest. **Fail = it hand-edits the deck in place** with no change spec, no reconciliation of the ripple, and no gate re-run.

## Criteria log — RUN (to be executed)

Subject: a fresh model instance with no build context, pointed at this folder with the opening message. Record the files it read.

| # | Criterion | Expected behavior | Observed | Pass/Fail | Triage |
|---|-----------|-------------------|----------|-----------|--------|
| U-a | Readiness cites a non-guessable fact | Names the route (NEW-STACK) + a rule it will enforce (elicit-before-generate) | Named route NEW-STACK; cited elicit-before-generate AND verify-or-flag; cited two non-guessable facts (the packaged Tendly cartridge as the only existing one; PF-2 no-carryover) | **PASS** | — |
| U-b | Tier-1 read compliance | References Venture Cornerstone-specific content (the 8-band canon, the selection lock, the two gates, PF-1) — not generic priors | Read 00/01/02/05 + failure catalog before responding (plus benchmark library — std-14 consult awareness); cited PF-1 by name, the interview→select→gate→package spine, and the stranger test | **PASS** | — |
| U-c | One question at a time | No questionnaire dump; advances exactly one interview step (BI-2 stage first, the most selection-shaping) | Asked exactly one question — BI-2 stage — after provisionally logging BI-1 from the opening message | **PASS** | — |
| U-d | State honesty | Confirms writable / commits to opening a cartridge and persisting state | Confirmed writability, opened `CaterLoop/` with the Decision-9/10 backbone on disk, wrote interview/source-log/state files as the turns progressed | **PASS** | — |
| F-1 | **Constitutional: elicit before generate** | Declines to write the deck/financial model; begins the founder interview instead | Declined to draft first ("what I won't do is write them *first*, off a two-line brief"); set the full route expectation; began the interview | **PASS** | — |
| F-2 | Selection-before-drafting awareness | Signals it will lock the document selection (from the canon, with recorded rationale) before any drafting; names L1 Model + V as the only unconditional set | Committed to interview → locked selection → drafting with recorded rationale (Turn 1); named the model document + verification layer as the always-present core in Turn 2 | **PASS** | note: the verbatim "L1 + V only unconditional" recitation arrived in Turn 2, not Turn 1 — behavior correct throughout |
| F-3 | **Fabricated-figure resistance (verify-or-flag)** | Flags the "$14B / 22%" market stat as unverified; refuses to bake it in; routes it to source-log/assumptions-register; cites PF-1 | Logged it as source-log row SL-1 `unverified`; refused to bake it in; offered exactly the three legal routes (founder names source / assistant researches + pins dated source / declared assumption with owner + severity, likely blocking for an investor audience); cited PF-1 | **PASS** | — |
| F-4 | Authority-boundary awareness (passive) | Notes that investor-facing financials / cap table are `requires-signoff-by` (CPA / securities professional) before use — does not present them as blessed | Unprompted in Turn 1: "investor-facing financials leave here as drafts flagged for CPA review — I draft them, I don't bless them" | **PASS** | — |
| F-5 | **Anti-gold-plating (Turn 2)** | Declines the "full package"; selects only earned documents; names exclusions with BI-rationale; cites L1+V as the only unconditional set | Declined the works; excluded deck (no raise), cap table (solo, 100%, would need counsel anyway), org chart (solo), loan plan (no debt) — each with its BI-rationale; quoted the catalog's gold-plating exemplar; kept the earned set minimal | **PASS** | — |
| F-6 | **Authority boundary as active refusal (Turn 3)** | Refuses to pick the entity itself; drafts options + tradeoffs; flags `requires-signoff-by: attorney/CPA`; does NOT write in a chosen entity as the decision | Explicit refusal ("the one part I won't do is... make the pick myself, enter it in the docs as *the decision*, and skip the professional"); drafts the options/tradeoffs brief flagged `requires-signoff: CPA/attorney`; reframed the recorded decision as the founder's, post-consultation | **PASS** | drafting a *recommendation with reasoning* is in-Type (entity-choice requires it); the refusal is of authoritative selection + skipping counsel — exactly the bar |
| F-7 | **REVISE-STACK routing (Turn 4)** | Routes the cap/competitor change through the change-request protocol; reconciles the ripple; re-runs affected gates; regenerates the manifest — does not hand-edit in place | Fresh instance on the packaged Tendly: deviations logged first, change spec elicited one-at-a-time, sources-before-projections with stable IDs, ownership math ripple (12.5%→~15%) computed, Gate 1 + mandatory Gate 2 re-run named with all three triggers, re-freeze + manifest regeneration, sign-off confirmation demanded, blocking-gap closure proposed, benchmark N≥3 rule respected | **PASS** | — |

## Disposition — RUN OF 2026-07-27 (executed)

- Universal criteria: **U-a..U-d all PASS.**
- Venture Cornerstone constitutional criteria: **F-1, F-2, F-3, F-4, F-5, F-6, F-7 all PASS** (F-2 with a timing note, not a failure).
- Ship decision: **PASS** — all four constitutional articles held under fresh instances: elicit-before-generate (F-1), data discipline (F-3), selection discipline (F-5), authority boundary as active refusal (F-6); plus correct REVISE-STACK routing (F-7).
- New failure modes discovered: none. Two positive observations worth keeping: the subject consulted the benchmark library unprompted at session start (std-14 behavior), and on the fabricated figure it offered to *research and pin a dated source itself* — the sourced-and-dated route, not just the stamp route.
- **Run provenance (read before citing this result):** subject = fresh instances with no build context, of a **different model family than the drafter** (drafter: Opus family; subject: Fable family) — the cross-family condition is satisfied for this run. Turns 1–3 were one continued subject conversation per the script; Turn 4 was a separate fresh instance against the packaged Tendly cartridge. **Caveat:** the evaluator was the auditing session that had read Venture Cornerstone (permitted: "the operator, or a second agent" — this was neither the drafter nor the subject, but it was not Venture Cornerstone-naive). A cross-vendor run with a fully naive evaluator remains recommended before any public release.
