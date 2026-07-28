---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-changelog
title: "Venture Cornerstone — Changelog"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Changelog

Format follows [Keep a Changelog](https://keepachangelog.com/); versioning follows [SemVer](https://semver.org/).

## [1.0.0] — 2026-07-27

First public release. The founding-**business**-document sibling to Baseplate, built on Operating-Volume-Engineering.

### Added

- **The engine** (`_venture-cornerstone-engine/`) — `00-START-HERE`, `01-THE-CANON` (the 8-band founding-business-document taxonomy: L0 Why · L1 Model · L2 Market & GTM · L3 Money · L4 Plan & Ask · L5 Operations · L6 Legal & Ownership · V Verification, plus audience projections), `02-ELICITATION` (the BI-1..BI-13 + BI-4b founder interview), `03-SELECTION` (the machine-readable class registry with earning conditions + depth tiers), `04-GENERATION-STANDARDS` (14 gate-criteria standards), `05-GATES` (the two gates), `06-CLOSE-OUT` (the `Stack/Records/Workspace` packaging protocol), and `BOOTSTRAP-NEW-BUSINESS`.
- **10 structural Types** (`_types/`) keyed by a `vcs_Doc_Class` enum — Narrative, Model, Market, Financial, Plan, Pitch, Operations, Legal, Selection-Record, Stranger-Test-Log.
- **The data discipline** — verify-or-flag on every market/financial figure (founder-supplied / sourced-and-dated / `[ASSUMPTION]`), a single-owned assumptions register that travels inside the frozen stack, a mandatory sensitivity table, arithmetic-identities recomputation, and cross-document reconciliation.
- **The two gates** — Gate 1 mechanical consistency audit (figures reconcile *and* recompute from drivers; every figure sourced-or-assumed; freeze hashes recorded); Gate 2 stranger *decision* test with a conditional verdict (SHIP / SHIP-WITH-DECLARED-GAPS), retargeted from Baseplate's "buildable" to "actionable/fundable".
- **The authority boundary** — `requires-signoff-by` hard stops on regulated documents; `domain_stakes: high`; the OV drafts but never blesses a document as compliant.
- **Two moats** — `_portfolio/failure-catalog.md` (PF-1..PF-9) and `_portfolio/benchmark-library.md` (consult + contribute + k-anonymity anonymization).
- **One worked-example cartridge** — `Example-Business-Tendly`, a seed-stage vertical-SaaS packaged into a full `Stack/Records/Workspace` dossier (Gate 2: SHIP-WITH-DECLARED-GAPS, demonstrating the conditional verdict).
- **Meta & tooling** — `_meta/posture.yaml` + `standalone-sufficiency-posture.md` (verdict: Defensible specialist), `_meta/TRACEABILITY.md`, `_meta/golden-session-script.md` (executed PASS, cross-family), `_meta/VALIDATION-CHECKLIST.md`, `_meta/ARITHMETIC-CHECK.md` (optional), `_meta/audit-stack-dry-run.md`, and the OV self-`MANIFEST.md`.
- **Front-door docs** — README, INSTALL, OPERATOR-GUIDE, CONTRIBUTING, LICENSE, UPDATE-PROMPT, this changelog, and `.gitignore`.

### Design provenance

- **Decision 10** — self-audit against the OV's own gates surfaced and fixed 12 defects.
- **Decision 11** — cross-family validation: golden session PASS (all four constitutional articles), AUDIT-STACK foreign-stack dry run, arithmetic-identities checker (caught a seeded units bug), Tendly packaged.
- **Decision 12** — name locked (Venture Cornerstone, namespace `vcs_`).
