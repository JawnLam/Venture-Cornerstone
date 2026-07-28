---
Item_ID: "<UUID>"
type: VCS_Pitch_Document
title: "<Business> — Investor Pitch Deck"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # pitch-deck  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Band: 4                    # L4 PROJECTION — re-cuts L0–L4 for investors; not a band of its own
vcs_ID_Scheme: ""             # e.g. ACME-SLIDE-<n>
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — Pitch Document

> A projection, not a band — the investor pitch deck **`projects-from` L0–L4**, re-cutting the vision (L0), model (L1), market (L2), money (L3), and ask (L4) for one audience: investors. Earned only when raising equity from investors (BI-3 equity, BI-4 investors); a deck included "because decks are customary" is gold-plating. **The deck cites its source documents, it never restates them** — a slide that copies the model's numbers drifts from the model the moment the model changes (PF-8 projection-restatement guard). On any conflict between a slide and its source document, the source is law and the slide conforms.

## The spine — Sequoia 10-element arc (rigid, citable)

The deck's structure is the Sequoia 10-element outline; each slide is one element, each citing the source band it re-cuts:

1. Company Purpose — from L0.
2. Problem — from L0.
3. Solution — from L1.
4. Why Now — from L0.
5. Market Size — from L2 (TAM/SAM/SOM, citing the market-sizing figures, not re-derived).
6. Competition — from L2.
7. Product — from L1.
8. Business Model — from L1 / L3 (revenue model, pricing).
9. Team — from L5 (org) and the founder interview.
10. Financials — from L3 (the model's ARR, burn, runway, ask — cited, must reconcile).

## YC guidance (quoted, not templated)

Y Combinator's seed-deck guidance is prose, ~10 slides framed as questions the deck must answer. Treat it as **quoted guidance, never a fixed template** — quote the relevant YC line where it sharpens a slide (e.g. "make the deck skimmable in under three minutes"), and keep the Sequoia arc as the structural spine. Do not manufacture YC "rules"; cite the library.

## Projection discipline (mandatory)

- Declare `projects-from` in the relationships block with the specific L0–L4 documents each slide draws from.
- Every quantitative slide carries the source-document reference for its figure, so Gate 1 can reconcile the deck's number against the twin in the model / market doc. A deck figure that disagrees with its source is a Gate 1 block.
- The deck defines its own terms for a cold reader — zero conversation context, no "as discussed."

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — the value is the registry class `pitch-deck` (03-SELECTION Class column, slugified), not the filename. The filename below is free.
- **Filename:** `pitch-deck.md` in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Pitch_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (raising equity from investors; if excluded, the record says why)*.
- `VCS_Narrative_Document`, `VCS_Model_Document`, `VCS_Market_Document`, `VCS_Financial_Document`, `VCS_Plan_Document` — *projects-from (the L0–L4 sources each slide cites; the source is law, the slide conforms)*.
- `_source-log.md`, `_assumptions-register.md` — *sourced-from (every deck figure resolves to a source row or a named assumption via its source document)*.
- `VCS_Stranger_Test_Log` — *verified-by (a deck-primary stack is scored by an investor-role stranger at Gate 2)*.
