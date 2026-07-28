---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-operator-guide
title: "Venture Cornerstone — Operator Guide"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Venture Cornerstone — Operator Guide

## Engine vs your work (the content zones)

`git pull` updates the engine without touching your work, because the two never share paths:

- **Engine / Shipped Examples** (release-owned): `_venture-cornerstone-engine/`, `_types/`, `_meta/`, the front-door docs, `Example-Business-*/`. Don't hand-edit — customize via your own cartridges.
- **Your business cartridges** (`<Business-Name>/`): yours; the OV is designed to be extended here.
- **Your private work** (`_USER.md`, `<Business>/Sessions/`, `<Business>/_design-state.md`, `<Business>/_source-log.md`): gitignored, never tracked.
- **The portfolio** (`_portfolio/failure-catalog.md`, `_portfolio/benchmark-library.md`, Grows-Through-Use Zone): ships seeded; your appended entries are preserved on update via stash/merge — never clobbered.

See `CONTRIBUTING.md § Content zones` for the full path patterns.

## Running a stack (symptom → what to do)

| Symptom | What to do |
|---------|-----------|
| The AI starts writing a deck or a financial model from your one-line description | Stop it. That violates elicit-before-generate. Say "run the founder interview first." A correct session opens with the interview. |
| A document states a market size, growth rate, or benchmark you're not sure of | Good — that's the data discipline. Make the AI source-and-date it, or stamp it `[ASSUMPTION]` and route it to you. A fabricated market figure is the fastest way to lose credibility in the room. |
| The consistency audit says a derived figure doesn't recompute | The arithmetic-identities check caught a math error (e.g., annual ARPA divided by monthly churn). Fix the figure or its drivers; re-run reconciliation for every document that cites it. |
| The stranger decision test asks a question the stack should have answered | Ship block. Fix the stack to answer it, then rerun with a *fresh* instance (never the drafting session). |
| Gate 2 returns SHIP-WITH-DECLARED-GAPS | The stack passed, but it carries a `blocking-for-stated-audience` open dependency (e.g., an unsourced TAM). Resolve that gap before showing the stack to its stated audience — it's on the manifest cover and in the operator-input register. |
| A document is a cap table, entity choice, or investor financial | It carries a `requires-signoff-by` hard stop. Venture Cornerstone drafts it but will not bless it — clear the named professional (CPA / securities attorney) before you use it. |
| A shipped stack met reality and is now wrong | Use REVISE-STACK (`05-GATES.md § Revision`), not ad-hoc edits. Record what reality contradicted — it feeds the failure catalog, and any verified numbers feed the benchmark library. |

## Updates and troubleshooting

The update workflow (`INSTALL.md § Updating`) is fetch → preview → ff-only pull, with stash/pop when you have local edits. **The one conflict you will hit repeatedly** is in `_portfolio/`: the release adds seed entries; you added your own. On `git stash pop` (or the pull), resolve by **keeping both** — your appended `PF-n` failure modes and your cartridge-verified benchmarks plus any new seed entries. Never take "theirs" wholesale; that drops your accumulated lessons and numbers (which are the point).

If a fast-forward fails, you have local commits on the engine — move your customizations into your own cartridge instead, reset the engine files to `origin/main`, and re-pull.

## The authority boundary (read this once)

Venture Cornerstone operates at `domain_stakes: high`. It drafts investor financials, cap tables, entity-choice memos, and agreements — and it **never** signs off on them. Every such document carries a `requires-signoff-by` flag naming the professional (CPA, securities attorney, licensed advisor) who must bless it before use, and the business's packaged `AI-BOOTSTRAP.md` lists every one of those sign-offs in its operator-input register. Treat the flag as a hard stop, not a disclaimer.
