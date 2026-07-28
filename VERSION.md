---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-version
title: "Venture Cornerstone — Version"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
vcs_Version: "1.0.0"
schema_status: "FROZEN"
release_date: 2026-07-27
---

# Venture Cornerstone — Version

This is Venture Cornerstone **v1.0.0** — the first public release. It ships the full engine (the 8-band founding-business-document canon + 6 protocol chapters + the new-business bootstrap), 10 structural Types keyed by a `vcs_Doc_Class` enum, the two ship gates (a mechanical consistency audit with arithmetic-identities recomputation, and the stranger *decision* test), the data discipline (verify-or-flag + a single-owned assumptions register + a mandatory sensitivity table), the authority boundary (`requires-signoff-by` hard stops; `domain_stakes: high`), two compounding moats (the failure catalog and the source-tagged benchmark library), and one worked-example cartridge (`Example-Business-Tendly`).

**Provenance.** Designed inside Operating-Volume-Engineering and passed through its gauntlet (interview → schema → cartridge-shape → artifact-draft → review → ship-prep). Self-audited against its own gates (Decision 10: 12 defects found and fixed) and cross-family validated (Decision 11: the golden session PASSED all four constitutional articles with a fresh instance of a different model family than the drafter; an AUDIT-STACK dry run caught every seeded defect on a foreign stack; the arithmetic-identities checker ran clean on the worked example and blocked a seeded units bug). Named in Decision 12. `CHANGELOG.md` is the authoritative release history; this file and `README.md` derive their version from it.

| Identifier | Value | Notes |
|---|---|---|
| **Software** | v1.0.0 | Engine (canon + 6 protocol chapters + bootstrap), 10 structural Types + doc-class registry, consistency-audit + stranger-decision-test gates + close-out packaging, failure catalog + benchmark library, manual VALIDATION-CHECKLIST + optional ARITHMETIC-CHECK |
| **Schema** | v1.0 (FROZEN) | The 10 structural Types + their required sections (`_types/`), the document-class registry (`03-SELECTION.md`), and the stranger-test pass rule (`05-GATES.md` Gate 2 ST-3) are frozen as of this first public release. See § Schema policy |
| **Engine** | v1.0 | `_venture-cornerstone-engine/` chapters 00–06 + BOOTSTRAP-NEW-BUSINESS |
| **Built on** | OVE v2.7 | Provenance only — Venture Cornerstone has no runtime dependency on OVE once shipped |
| **Sibling** | Baseplate | Founding *product* documents; Venture Cornerstone is the founding *business* documents sibling |
| **Knowledge source** | self_contained | The canon is baked into `01-THE-CANON`, grounded in public named frameworks (see `_source-inventory` provenance in the design cartridge) |
| **Release date** | 2026-07-27 | |

## Schema policy

**The schema is FROZEN** as of v1.0.0. The frozen surface is: the ten structural Types and their required sections (`_types/`), the document-class registry (`03-SELECTION.md`), and the stranger-test pass rule (`05-GATES.md` Gate 2 ST-3). After this point, per `CONTRIBUTING.md`:

- **Additive** (patch/minor): new document classes on the menu that map to an existing structural Type; new failure-catalog or benchmark entries; documentation; the optional tooling.
- **Major bump + migration note:** changing a structural Type's required sections, removing/renaming a Type or engine chapter, or changing the stranger-test pass rule.

## Naming

The OV is named **Venture Cornerstone**; the `vcs_` namespace is settled (Decision 12). A future rename would be a major bump (it renames the namespace).

Original work by Jawn Lam. Built on Operating-Volume-Engineering (CC-BY 4.0).
