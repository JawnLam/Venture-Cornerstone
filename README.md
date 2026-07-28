---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-readme
title: "Venture Cornerstone — README"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Venture Cornerstone

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Version](https://img.shields.io/badge/version-v1.0.0-blue.svg)](VERSION.md)

Venture Cornerstone turns the founding-document canon for a **business** into an enforced discipline: point an AI at this folder, describe your business, and it interviews you, selects exactly the documents that business earns, generates them to a verifiable standard — holding every market and financial figure to a verify-or-flag rule — and blocks the ship until a **stranger** (a fresh model instance handed only the folder) can make the decision the stack asks for: *fund it, lend to it, or run it.*

It is the founding-**business**-document sibling to [Baseplate](https://github.com/JawnLam/Baseplate), which does the same for founding **product** documents. Both are built on [Operating-Volume-Engineering](https://github.com/JawnLam/Operating-Volume-Engineering).

## Quick start

> **"Read `AI-BOOTSTRAP.md` and help me design the founding-document stack for my business."**

The AI will start by interviewing you, one question at a time. It will *not* start writing a pitch deck or a financial model from a one-line brief — eliciting before generating is the whole point, and a stack built from a one-liner embarrasses the founder in the room.

## What this is

- An operating volume (OV) — a self-contained markdown corpus an AI loads to run a kind of work.
- One **cartridge per business**. A cartridge's terminal artifact is that business's founding-document **stack** — the self-contained package an investor, lender, co-founder, or operator can act on with no further founder input.
- A layered **canon** grounded in real, named frameworks (the Business Model Canvas, the Lean Canvas, the Sequoia and YC deck outlines, the SBA business-plan structure, standard unit-economics).
- A set of **gates**: a mechanical consistency audit (the numbers reconcile *and* recompute across the deck, model, and canvas) and a **stranger decision test** (a fresh model instance must make the fund/lend/run decision from the frozen folder alone). Plus two compounding assets — a **failure catalog** and a **source-tagged benchmark library** — so business #4's stack benefits from what shipping #1–3 taught.

## What this is not

- Not a document-template pack. Templates are commodity scaffolding; the durable value is the gates, the data discipline, and the accumulating portfolio.
- Not a product builder or a company operating system. The founding stack is the terminal artifact; Venture Cornerstone does not run the business.
- **Not a CPA, securities attorney, or licensed advisor.** It operates at `domain_stakes: high` and drafts every document, but where one needs professional sign-off before use (investor financials, cap table, entity choice, agreements), it hard-stops and routes you to a licensed professional. It never blesses a regulated document as compliant.

## Folder structure

| Path | Contents |
|------|----------|
| `AI-BOOTSTRAP.md` | AI entry point |
| `_venture-cornerstone-engine/` | The canon + protocols: `00-START-HERE`, `01-THE-CANON`, `02-ELICITATION`, `03-SELECTION`, `04-GENERATION-STANDARDS`, `05-GATES`, `06-CLOSE-OUT`, `BOOTSTRAP-NEW-BUSINESS` |
| `_types/` | The 10 structural document Types |
| `_portfolio/` | The cross-cartridge failure catalog + benchmark library (Grows-Through-Use Zone) |
| `_meta/` | Posture, traceability, golden-session script, the manual validation checklist + arithmetic checker |
| `Example-Business-*/` | Worked-example business cartridges (reference implementations) |
| `<Business-Name>/` | Your business cartridges |

The content zones are declared in [`CONTRIBUTING.md`](CONTRIBUTING.md) § Content zones.

## System requirements

- Any capable AI that reads markdown and parses YAML frontmatter (Claude, GPT-4-class+, Gemini 2.x+).
- **No runtime dependencies.** The OV form is plain markdown; a human and an AI run it with zero code execution. The two gates run manually (`_venture-cornerstone-engine/_meta/VALIDATION-CHECKLIST.md`); the stranger decision test *cannot* be mechanized — it needs a fresh model instance. An **optional** arithmetic-identities checker ships inside `_meta/ARITHMETIC-CHECK.md` for convenience, never as a requirement.

## License

CC-BY 4.0. See [`LICENSE.md`](LICENSE.md).

> Built on **Operating-Volume-Engineering** by Jawn Lam — https://github.com/JawnLam/Operating-Volume-Engineering. Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Version

See [`VERSION.md`](VERSION.md). This is **v1.0.0** — the first public release. `CHANGELOG.md` is the authoritative release history.
