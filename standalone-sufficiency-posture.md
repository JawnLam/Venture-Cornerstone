---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-posture-render
title: "Venture Cornerstone — Standalone Sufficiency Posture"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Venture Cornerstone — Standalone Sufficiency Posture

> Why use Venture Cornerstone instead of a general LLM? The answer rests on the substrate (the 47-requirement standalone-sufficiency framework), not a sales pitch. Source of truth: `_meta/posture.yaml`. This file is the human-readable render of that YAML.

## The two master tests (answered)

- **Displacement** (*can a ten-minute prompt reproduce this?*): a prompt can produce *a* pitch deck, and a good one a decent financial model. What it cannot do is refuse to invent the market size. A general model handed "write my deck and base it on the $14B market growing 22%" writes the deck and bakes the number in; the credibility loss lands in the investor meeting. Venture Cornerstone's durable core is the discipline a prompt will not impose on itself: verify-or-flag on every figure, a mandatory assumptions register, cross-document reconciliation as a gate, a stranger DECISION test as a ship block, the authority boundary that hard-stops regulated documents for professional sign-off, and a portfolio failure catalog so business #4 ships cleaner than #1. The templates are commodity; the gates and the accumulating catalog are not.
- **Absorption** (*will platforms ship this in ~12 months?*): partially — generic "deck/plan modes" are becoming table stakes, so template-quality generation is commodity. What platforms will not ship: the operator's selection doctrine (a menu earned per-business, not a fixed template pack), the data discipline enforced as a gate rather than a disclaimer, per-stack cross-document reconciliation as a ship block, the stranger decision test as a ritual the founder cannot unconsciously game, and the two founder-owned compounding assets — the failure catalog and the source-tagged benchmark library. Investment is weighted toward the gates, the data discipline, and the two moats; templates are treated as commodity scaffolding.

## Domain stakes

`high` — the OV's documents drive irreversible, regulated-adjacent decisions: securities (investor financials, cap table, equity splits), debt (SBA/bank loan plans), and tax/entity choice. The OV drafts every document but never issues authoritative financial, legal, tax, or securities advice. Where a document needs professional sign-off before use, it hard-stops and routes the founder to a licensed professional (CPA / securities attorney / financial advisor) via the `requires-signoff-by` flag. Declaring `high` makes the authority boundary explicit rather than timid — a real, defensible distinction from "an LLM will just write you a deck." Because stakes are high, the 8 TG conditional gates (REQ-I calibration/escalation/auditability, REQ-K data governance/privacy/ownership) are **applicable, not `n-a`**, and must each reach `met` or an explicit waiver before ship.

## T0 hard gates (current dispositions — filled 2026-07-27; final pass at SHIP-PREP 3.10)

| Gate | Disposition | Evidence |
|------|-------------|----------|
| REQ-A1 Capability Parity | **met** | Plain-markdown engine, manual gates (BNF-1); golden session executed 2026-07-27 with a fresh instance of a different family than the drafter |
| REQ-A2 Graceful Scope Boundaries | **met** | AUDIT-STACK degraded mode + executed foreign-stack dry run (`_meta/audit-stack-dry-run.md`): portable checks caught every seeded defect; absent BB apparatus reported as instrumentation gaps, not failures |
| REQ-A3 No Artificial Lobotomy | **met** | Refusal is confined to authoritative sign-off; golden-session Turn 3 shows active entity-choice refusal *while* drafting the full options brief |
| REQ-B1 Persistent User Model | **met** | Per-cartridge backbone state (Decision 9/10) + `_portfolio/` catalog loaded at session start and benchmark library consulted at generation |
| REQ-D4 Authority Boundary | **met** | `requires-signoff-by` hard stops on L6 + cap table + investor financials; Gate 1 checks them; golden Turn 3 verifies refusal is active, not a disclaimer |
| REQ-H4 Time-to-First-Value | **met** | Session one of NEW-STACK yields a locked selection record + the unconditional L1 model and V instruments |

The applicable high-stakes TG gates now stand: **I1/I3/I4 and K1/K3 `met`** with in-volume evidence (verify-or-flag + severity calibration; sign-off routing with when-to-ask triggers; register/log/freeze-hash/manifest audit chain; cartridge-confined founder data with k-anonymized-only exposure; operator-owned, self-contained packages). **I2/I5/K2 remain `deferred`** with an explicit waiver — their requirement text lives in OVE's substrate `requirements.yaml`, not in this volume, and guessing a requirement to mark it met would be this OV's own fabrication failure. Source of truth for every row: `_meta/posture.yaml`.

## Moat commitments

- **REQ-M1 Data Flywheel** (`partial` — mechanism live, flywheel not yet fired) — `_portfolio/failure-catalog.md`: seeded PF-1..PF-9, loaded at every session start, appended at every close-out. A general LLM pointed at the same task has no such accumulated catalog. `partial` until the first real cartridge grows a use-derived entry (orphan O-1).
- **REQ-M2 Legitimate Switching Cost** (`partial` — mechanism built, store unpopulated) — `_portfolio/benchmark-library.md` with both flywheel halves specified and wired: **CONSULT** at generation (standard 14, sanity-checking every estimate against accumulated ranges) and **CONTRIBUTE** at close-out (verified figures only), under a k-anonymity rule (N≥3, identity stripped) that keeps the moat from ever becoming a confidentiality leak. `partial` until real cartridges populate it (orphan O-2). Leaving the OV means leaving the accumulated, vetted numbers behind.

## Validation executed (2026-07-27 — no longer a promise)

The defensibility claims above are now backed by executed artifacts, not pending scripts: the **golden session PASSED all 11 criteria** (constitutional elicit-before-generate, fabricated-figure refusal, anti-gold-plating, active authority refusal, REVISE-STACK routing — cross-family subject; provenance caveats in `_meta/golden-session-script.md`); the **AUDIT-STACK dry run** caught every seeded defect class on a foreign stack; the **arithmetic-identities checker** ran clean on the worked example and blocked a seeded units bug (`_meta/ARITHMETIC-CHECK.md`); and the worked example **Tendly is a fully packaged dossier** whose orientation probe passed with independent hash verification. Remaining before any public release: a cross-vendor golden rerun with a naive evaluator, and a real (non-synthetic) foreign-stack audit.

## Verdict

**Defensible specialist** — the moat rests on accumulated proprietary portfolio state (the failure catalog and the benchmark library) and on enforced gates (the consistency audit's cross-document reconciliation, the stranger decision test as ship block, and the authority-boundary hard stop), not on promptable behavior. The templates a general model can match in ten minutes; the discipline, the state, and the two compounding assets it cannot.
