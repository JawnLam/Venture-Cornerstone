---
Item_ID: "<UUID>"
type: VCS_Narrative_Document
title: "<Business> — <Vision Brief | PR-FAQ | One-Pager | Executive Summary | Objection Map | Founder Interview>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # vision-brief | pr-faq | one-pager | executive-summary | objection-map | founder-interview  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Merged_Bands: []           # optional — canonical doc_class = the primary band; list merged bands here (an L0+L1 merge on the model side carries the merge; a projection never merges into its source)
vcs_Band: 0                    # L0 for the vision brief, PR-FAQ, objection map, and founder-interview record; one-pager and executive summary are projections re-cut from L0–L4
vcs_ID_Scheme: ""             # e.g. ACME-L0-<n> for numbered claims, if the brief carries any
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Narrative Document>

> An L0 document — **why this business deserves to exist, for whom, and why now** — or one of its two projections (one-pager, executive summary), which re-cut L0–L4 for a fast top-of-funnel read. The L0 brief earns a standalone file only when someone beyond the founder must be aligned or convinced (BI-4); for a solo bootstrapper with no audience, L0 collapses into a section of the L1 model document and that exclusion is recorded in the selection record. A projection **cites** its source documents, never restates them — a one-pager that copies the model's numbers drifts from them the moment the model changes (PF-8 projection-restatement guard).

## Required sections (by class)

- **vision-brief:** Problem (who hurts, how badly, what it costs them today); Why-now (the change that makes this possible/urgent now); Who it's for; What success looks like. State the problem before the solution; a brief that opens with the product has skipped its own job. (The vision brief and the problem brief are one canonical class — `vision-brief`; do not split them into two doc-classes.)
- **pr-faq:** Press release (the finished-business announcement, written as if launched — headline, sub-head, the customer's before/after); Anticipated FAQs (the hard questions a skeptic asks, answered plainly).
- **objection-map (projection):** Anticipated hard questions; the honest answer (each **citing** the stack document that grounds it); where the stack is genuinely weak and the founder's response. `projects-from` its sources — cites, never restates.
- **founder-interview:** the BI-1..BI-13 record (the `_founder-interview.md` cartridge record), the elicited founder-shape that earns every other document; appended during the interview, then frozen.
- **one-pager (projection):** A single page — one-liner, problem, solution, market, traction/ask — each figure **citing** its source document (the L2 market doc, the L3 model), never re-derived here.
- **executive-summary (projection):** A ~one-page condensation of the L4 plan for a reader who will not open the plan; every claim traceable to its source band.

## Projection discipline (one-pager, executive-summary only)

- Declare `projects-from` in the relationships block, listing the L0–L4 documents this re-cut draws from.
- Within a projection, the source document is law; the projection conforms. On any conflict between this file and its source, the source wins and this file is corrected.
- Every quantitative claim carries the source-document reference it was lifted from, so Gate 1 can reconcile it against the twin figure.

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`vision-brief`, `pr-faq`, `one-pager`, `executive-summary`, `objection-map`, `founder-interview`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `vision-brief.md`, `pr-faq.md`, `one-pager.md`, `executive-summary.md`, `objection-map.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Narrative_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (the BI-answer that included this L0 document, or recorded its collapse into L1)*.
- `VCS_Model_Document`, `VCS_Market_Document`, `VCS_Financial_Document`, `VCS_Plan_Document` — *projects-from (one-pager and executive summary re-cut these; cite, never restate)*.
- `VCS_Stranger_Test_Log` — *verified-by (the stranger's restatement in output (a) is scored against this narrative's framing — a misread here is a stack defect)*.
