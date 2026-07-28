---
type: Fleeting
Item_ID: "D48A1C6F-2E97-4B05-8A31-6C0D9F4E2B57"
title: "Tendly — Stack Manifest"
vcs_Business_Slug: "TND"
vcs_Doc_Class: stack-manifest
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Tendly — Stack Manifest

> **Verify this inventory before acting on anything in this folder.** Recompute each file's SHA-256 (`shasum -a 256 Stack/*` excluding this manifest) and compare; on any mismatch or missing file, stop and report to the founder — a partial copy, a sync-mangled file, or a tampered figure must be caught before a decision rests on it.

- **Package date:** 2026-07-27
- **Gate 1 (consistency audit):** clean — reconciliation and arithmetic identities recompute from register drivers (re-run at re-freeze 2026-07-27)
- **Gate 2 (stranger decision test):** **SHIP-WITH-DECLARED-GAPS**, run 1, rerun count 0 (fresh isolated instance, angel-investor role, verbatim fixed prompt, executed against the freeze hashes)
- **Hash continuity:** the digests below equal the Gate-1 freeze record kept with the history records — the packaged bytes are the audited, stranger-tested bytes.

## ⚠ Blocking gaps (why the verdict is not a clean SHIP — resolve BEFORE the stated audience acts)

| Gap | Register ID | What it blocks | Resolve by |
|---|---|---|---|
| **Unsourced TAM/SAM** — market sizing is founder recollection with no external source; the market brief itself says it must be replaced before an investor sees it | `TND-A7` (TAM; `TND-A8` SAM inherits) | Showing `03-market-brief.md` or deck slide `TND-D5` to any investor as-is | Replace with a sourced, dated figure (Child Care Aware of America / IBISWorld / state licensing registries) and rebuild SAM bottom-up — **before any angel meeting**; past `TND-A7` valid-until 2026-09-30 this is also a REVISE-STACK time trigger |

Everything else the decision test surfaced is `operator-only` (founder's private data or a professional's signature) and is listed in the bootstrap's operator-input register — not a blocking gap.

## Inventory

| File | SHA-256 | Bytes | Type | Class | Band | Precedence | requires-signoff-by |
|---|---|---|---|---|---|---|---|
| `01-vision-brief.md` | `c47773f0ace1a777ccf1f1ed83f5e53669309f44ae77f4eee5585d99ccbff39c` | 3236 | VCS_Narrative_Document | vision-brief | L0 | 4 | — |
| `02-lean-canvas.md` | `d1ac1ce400b86395073d0380c5fcecf7355793f557e0948928da578038a84f10` | 4204 | VCS_Model_Document | lean-canvas | L1 | 3 | — |
| `03-market-brief.md` | `0cd8f16334eeef258002af936fb16e4933ea90fa81435f33a466132b0b9a0004` | 4587 | VCS_Market_Document | market-sizing (merged: icp-competitive, go-to-market) | L2 | 2 | — |
| `04-financial-summary.md` | `16d744bf88d48956ca2803d2176cf7ff3206a6f6d34b642e948dd90c928b0964` | 9195 | VCS_Financial_Document | financial-model (merged: unit-economics, cap-table, pricing; depth: full) | L3 (merged band 6 flags) | 1 | CPA (model) / securities attorney (SAFE + cap table) / privacy counsel (PII/ToS) |
| `05-pitch-deck.md` | `66130f2c2b4396886a6db6e86e51958e8d016ccc93ff5197bd09cc57d3433472` | 3894 | VCS_Pitch_Document | pitch-deck (projection) | L4 projection | 5 | — |
| `06-one-pager.md` | `653a84d0f2e075dd10509e0fa48dc41b0ffcca1d58c8a1b0642bbfc951f3f9da` | 2370 | VCS_Narrative_Document | one-pager (projection) | L0/L4 projection | 6 | — |
| `_assumptions-register.md` | `a4312a15aca7d4364ac6050243f78d5c5170da6f5dd33e2f6d768c9a15134d50` | 7366 | Fleeting (V-band instrument) | assumptions-register | V | 0 (numeric authority feeds rank 1) | — |

Reading order: L0→L4 then the register (V); projections (`05`, `06`) last — they cite, never restate. Precedence: lower rank wins on conflict; the source document is law and a projection conforms. On any later revision (REVISE-STACK), regenerate this manifest and the freeze hashes in the same change.
