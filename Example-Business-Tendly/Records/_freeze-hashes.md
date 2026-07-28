---
type: Fleeting
Item_ID: "2B9E7C41-0A63-4D58-9F12-7C4A0E5B3D86"
title: "Tendly — Gate-1 Freeze Hashes"
vcs_Business_Slug: "TND"
vcs_Doc_Class: freeze-record
vcs_Band: V
vcs_Freeze_Date: 2026-07-27
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Gate-1 Freeze Hashes

> Freeze integrity: when Gate 1 (the consistency audit) passed, the stack was **frozen** — the SHA-256 of every stack file recorded here. Gate 2 (`stranger-test-log.md`) runs against these exact bytes, and the packaging manifest re-verifies them (hash continuity), so a figure edited between the audit and the stranger test — or between the test and packaging — is *caught*, not trusted. Freezing on the honor system is the gap this record closes. Kept with the history records, outside the stack, so it is not part of what it hashes.
>
> Recompute check: `cd Stack && shasum -a 256 *` (excluding `MANIFEST.md`, which carries these same digests) must reproduce the table below. Any mismatch re-opens Gate 1 for the changed file and its reconciliation twins.

| Stack file | SHA-256 |
|---|---|
| `01-vision-brief.md` | `c47773f0ace1a777ccf1f1ed83f5e53669309f44ae77f4eee5585d99ccbff39c` |
| `02-lean-canvas.md` | `d1ac1ce400b86395073d0380c5fcecf7355793f557e0948928da578038a84f10` |
| `03-market-brief.md` | `0cd8f16334eeef258002af936fb16e4933ea90fa81435f33a466132b0b9a0004` |
| `04-financial-summary.md` | `16d744bf88d48956ca2803d2176cf7ff3206a6f6d34b642e948dd90c928b0964` |
| `05-pitch-deck.md` | `66130f2c2b4396886a6db6e86e51958e8d016ccc93ff5197bd09cc57d3433472` |
| `06-one-pager.md` | `653a84d0f2e075dd10509e0fa48dc41b0ffcca1d58c8a1b0642bbfc951f3f9da` |
| `_assumptions-register.md` | `a4312a15aca7d4364ac6050243f78d5c5170da6f5dd33e2f6d768c9a15134d50` |

**Frozen 2026-07-27 at Gate 1 pass; re-frozen 2026-07-27** after the Decision-11 follow-through edits (self-containment rewording, pre/post-raise burn qualifier, BI-4b bar relocated out of the traveling register, stated cash convention). The edits are non-decisional: Gate 1 was re-run (reconciliation + arithmetic identities recompute clean — reference run in the OV's `_meta/ARITHMETIC-CHECK.md`) and the Gate 2 verdict (**SHIP-WITH-DECLARED-GAPS**, run 1) carries per the REVISE-STACK cosmetic rule. Seven files — the six founding documents plus the assumptions register, which travels inside the stack. The stranger test's verdict is provably against audited bytes; the package manifest must equal this table. **Re-frozen again 2026-07-27 after the Decision-12 rename** (Business-Baseplate → Venture Cornerstone; `biz_`→`vcs_`): a pure namespace/name substitution, non-decisional, so the verdict carries under the REVISE-STACK cosmetic rule; hashes above regenerated from the renamed bytes.
