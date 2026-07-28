---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: "venture-cornerstone-engine-02-elicitation"
title: "Venture Cornerstone Engine — 02 Elicitation"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
doc_type: venture-cornerstone-engine
role: interview-protocol
scope: subject-agnostic
---

# 02 — ELICITATION (the founder interview)

> **Run this before selecting or generating anything (the constitutional behavior; `00-START-HERE.md`). One question at a time — never a numbered questionnaire. Each answer becomes a citable line that a downstream selection decision rests on. Record answers in the cartridge's `_founder-interview.md`.**

## The rule

Ask one question. Wait. Probe if the answer is thin. Reflect it back. Then ask the next. A bulk questionnaire gets bulk answers and produces a generic stack — the exact failure this OV exists to prevent. If you catch yourself dumping a list, stop and reset: *"I'll take these one at a time."* A founder who is asked the whole list at once gives you a page of shallow answers; a founder asked one real question at a time gives you the number, the name, the date you can actually cite.

## What the interview must capture (minimum set)

Capture each with enough specificity that a selection decision can cite it. For every answer, note in one clause **which selection decision it shapes** — that is what makes the `_selection-record` auditable later.

- **BI-1 · One-liner.** What the business is, in one sentence a stranger understands, no jargon. *Captures:* the subject of every document. *Shapes:* whether L0 (the why/problem brief) has enough of a story to stand alone.
- **BI-2 · Stage.** Idea / pre-seed / raising / operating / loan-seeking. *(This is the single most selection-shaping answer — the analog of Baseplate's PI-2 "builder.")* *Captures:* where the business is on the maturity ladder. *Shapes:* nearly everything — L3 financial depth, whether L5 operations is earned yet, whether a raise-facing L4 exists, the progress ladder the stack starts on.
- **BI-3 · Funding path.** Bootstrapped / equity (angel or VC) / debt (SBA or bank) / none. *Captures:* how the business will be capitalized. *Shapes:* the pitch deck (equity), the loan plan (debt), the cap table (equity), and how much rigor L3 must carry.
- **BI-4 · Document audience.** Investors / lenders / co-founders / self / operators — who reads the stack and scrutinizes it. *Captures:* who must be convinced or aligned. *Shapes:* whether L0 earns a standalone alignment document, and which projections (pitch deck, one-pager, executive summary) are earned.
- **BI-4b · Audience bar.** For the primary audience in BI-4: what is their *threshold*? A specific check size or loan amount, their stage thesis (pre-seed vs Series A; SBA 7(a) vs a line of credit), and anything they have already said they need to see (traction minimum, a named market, unit-economics proof). *Captures:* the decision bar the stack must clear, not just who reads it. *Shapes:* nothing at selection — but it is the anchor for the **Gate 2 ST-2 decision-plausibility** judgment (`05-GATES.md`): "plausible for a $25K angel" and "plausible for a $750K lead" are different claims, and without this the gate grades against a generic reader instead of the real one. If the founder does not yet know their audience's bar, that is itself worth surfacing — a stack aimed at an unknown bar is aimed at no one. **Record the bar in the selection record (`vcs_Audience_Bar`), never in the assumptions register or any document that travels in the stack:** the register goes to the stranger at Gate 2, and the stranger must not receive the bar it is being judged against.
- **BI-5 · Business shape.** Software/SaaS / physical product / services / marketplace / brick-and-mortar / franchise. *Captures:* the operating model. *Shapes:* the L2 go-to-market plan and the L5 operating plan (a marketplace and a brick-and-mortar shop earn very different ops documents).
- **BI-6 · Revenue model & pricing.** How it makes money; is pricing known or still open? *Captures:* the revenue engine. *Shapes:* the L3 pricing document and the L1 model's revenue-streams block.
- **BI-7 · Market.** Known TAM? Named competitors? A market that must be argued, or a captive first customer? *Captures:* the market case. *Shapes:* the L2 market sizing and competitive-landscape documents.
- **BI-8 · Team.** Solo / co-founders / a hiring plan. *Captures:* who owns and staffs the business. *Shapes:* the cap table (equity split among >1 party), the L6 founder/operating agreements (>1 founder), and the L5 org & hiring plan (team will grow).
- **BI-9 · Regulatory & IP exposure.** Regulated industry? IP-heavy? *Captures:* the legal surface area. *Shapes:* the L6 entity choice, licenses/permits, and IP-assignment documents — every one of which carries a `requires-signoff-by` flag.
- **BI-10 · Timeline.** Raise date, launch date, hard milestones. *Captures:* the sequencing constraints. *Shapes:* the L4 plan's funding-request framing and the milestones section of the L5 operating plan.
- **BI-11 · Money crossing a boundary.** Investor capital / a loan / customer pre-sales — is real money about to change hands? *Captures:* the point where the stakes become financial and regulated. *Shapes:* the securities/legal hard-stop flags on the cap table and entity documents, and confirms L3 is no longer optional.
- **BI-12 · Founder-supplied assets.** Numbers, research, prior docs, spreadsheets the founder already has. *Captures:* the ground-truth inputs. *Shapes:* nothing is selected by this, but **every figure it surfaces enters `_source-log.md` (sourced-and-dated) or `_assumptions-register.md` (named assumption)** — this is the data discipline's front door.
- **BI-13 · Current cash on hand.** How much cash the business has today, and its current monthly burn if operating. *Captures:* the starting balance every runway calculation depends on. *Shapes:* nothing is selected by this, but it is a **mandatory financial-model input** — runway = current cash ÷ net burn, and without BI-13 the model silently assumes $0 starting cash (or invents one), which is exactly the buried-assumption failure the data discipline exists to stop. Enters `_assumptions-register.md` as a founder-supplied figure. If the founder will not disclose it, that is an explicit open assumption, not a default.

## How to run it

- Open with BI-1 and BI-2 — the one-liner and the stage. Everything downstream is easier once you know what the business is and how mature it is. BI-2 in particular gates whether whole bands (L5 operations, a raise-facing L4) are even in play.
- Probe vague answers. "We sell software" is not an answer to BI-5; "a B2B SaaS billed per seat per month, sold via outbound to mid-market ops teams" is. "A big market" is not an answer to BI-7; "US mid-market restaurants, roughly N locations, with named competitors X and Y" is.
- Treat every number the founder says as an input to log, not a fact to trust silently — you will route it to the source log or the assumptions register at BI-12 and throughout. A figure with no source and no owner is a Gate 1 block later; catch it now.
- When the minimum set is captured, reflect the whole picture back in three or four sentences — one-liner, stage, funding path, audience, shape — and confirm before moving to selection.

## Output

Write `_founder-interview.md` (Type `VCS_Narrative_Document`, `vcs_Doc_Class: founder-interview`). Every BI answer is a labeled, citable line. The selection protocol (`03-SELECTION.md`) cites these labels by ID when it records why each document was included or excluded. Once the minimum set is captured and reflected back, the file is frozen (Decision 9): later corrections are a REVISE-STACK event, not an in-place edit.

## Do not

- **Do not begin selecting or drafting documents mid-interview.** Elicit fully first, then select, then generate. A thin business description is not a license to start writing a pitch deck.
- **Do not carry an answer over from another business's interview without re-asking.** Stale-context carryover is a named failure mode; every business earns its own full set of answers (BI-1 through BI-13, plus BI-4b).
- **Do not invent figures the founder did not give.** An unknown TAM, an unknown price, an unknown burn rate is an *open question*, not a plausible default. Route it to `_assumptions-register.md` as a named, owned assumption or leave it explicitly open — never fill it with a number you made up. A silent assumption absorbed here detonates in front of the investor or lender who knows the sector.
- **Do not answer regulated questions authoritatively.** If BI-9 or BI-11 surfaces an entity-choice, securities, tax, or licensing question, capture it and flag the professional sign-off (the authority boundary; `domain_stakes: high`) — do not advise.
