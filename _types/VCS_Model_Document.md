---
Item_ID: "<UUID>"
type: VCS_Model_Document
title: "<Business> — <Business Model Canvas | Lean Canvas | Value Proposition>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # business-model-canvas | lean-canvas | value-proposition  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Band: 1                    # L1 — UNCONDITIONAL; every stack carries a model document
vcs_ID_Scheme: ""             # e.g. ACME-L1-<n> for numbered blocks/claims, if used
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Model Document>

> An L1 document — **what the business model is.** UNCONDITIONAL: every stack contains exactly one model document, no business shape exempts it (this is the file L0 collapses into for a solo bootstrapper). Grounded in named public frameworks — the Business Model Canvas (Osterwalder & Pigneur, 9 blocks) or its early-stage adaptation the Lean Canvas (Maurya). Choose the Lean Canvas for a pre-product/pre-revenue startup; the Business Model Canvas for a business with an established model to document. Note: the SBA "lean startup plan" format is the Business Model Canvas verbatim — the same nine blocks; treat them as one framework, not two.

## Required sections (by class)

- **business-model-canvas:** all nine blocks, each a labeled section — Customer Segments; Value Propositions; Channels; Customer Relationships; Revenue Streams; Key Resources; Key Activities; Key Partnerships; Cost Structure. An empty block is a finding, not a blank — either fill it or record why it is genuinely N/A for this business.
- **lean-canvas:** the Lean Canvas nine — Problem; Customer Segments; Unique Value Proposition; Solution; Channels; Revenue Streams; Cost Structure; Key Metrics; Unfair Advantage. (It removes four BMC blocks — Key Partners, Key Activities, Key Resources, Customer Relationships — and swaps in Problem, Solution, Key Metrics, Unfair Advantage.)
- **value-proposition:** the value case where it is contested — Customer job(s); Pains and gains; How the offering relieves each; Why it beats the current alternative (including "do nothing").

## Cross-band consistency

- Revenue Streams / Revenue Model here must agree with the L3 pricing and financial model (`reconciles-with`); the Customer Segments here must agree with the L2 ICP. A model block that contradicts a downstream document is a Gate 1 block.
- Any quantitative claim that appears in a block (a segment size, a unit price) is `sourced-from` a source or a named assumption, on the same terms as the L2/L3 documents.

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`business-model-canvas`, `lean-canvas`, `value-proposition`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `business-model-canvas.md`, `lean-canvas.md`, `value-proposition.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Model_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (unconditional inclusion; the record still names the class chosen — BMC vs Lean Canvas — and the BI-answer that decided it)*.
- `VCS_Market_Document` — *reconciles-with (Customer Segments ↔ ICP; Channels ↔ GTM plan)*.
- `VCS_Financial_Document` — *reconciles-with (Revenue Streams and Cost Structure ↔ the financial model and pricing)*.
- `VCS_Narrative_Document`, `VCS_Pitch_Document` — *projects-from (L0 briefs and the pitch deck re-cut this model; they cite it, never restate it)*.
