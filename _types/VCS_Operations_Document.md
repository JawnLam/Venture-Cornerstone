---
Item_ID: "<UUID>"
type: VCS_Operations_Document
title: "<Business> — <Operating Plan | Org & Hiring Plan>"
vcs_Business_Slug: ""
vcs_Doc_Class: ""              # operating-plan | org-hiring-plan  — a canonical registry class (03-SELECTION Class column, slugified), NEVER a filename
vcs_Merged_Bands: []           # optional — canonical doc_class = the primary band; list merged bands here (a small business may merge L5 operations with L6-adjacent legal/ownership into one file with internally separated per-band sections)
vcs_Band: 5                    # L5 — Operations
vcs_ID_Scheme: ""             # e.g. ACME-OPS-<n>
vcs_Document_Status: drafting  # drafting | internally-consistent | audited | stranger-passed | shipped
vcs_Precedence_Rank:           # integer; lower wins on conflict per the stack precedence declaration
Date_Added:
Date_Modified:
Needs_Processing: false
AI_Instructions: ""
---

# <Business> — <Operations Document>

> An L5 document — **how the business runs day-to-day.** Earned when the business runs continuously with real operations at launch (BI-5); the org & hiring plan is earned when the team will grow beyond the founders (BI-8). A pre-launch idea defers this band, and that exclusion is recorded. Note the canon rule: **the V layer verifies L0–L4, never L5** — a stranger who cannot decide from the stack is a stack defect, but an ops gap is an operations matter, not a ship blocker for the founding decision.

## Required sections (by class)

- **operating-plan:** Key processes end to end (how the product/service is delivered — each as inputs, steps, owner, and failure/response, enough for an operator to run it, not a full SOP library); suppliers and dependencies; milestones; capacity and cadence; roles; failure modes & responses; the day-one operating footprint. Credentials and vendor secrets are referenced, never embedded.
- **org-hiring-plan:** Roles at launch and the first hires after; the sequence and triggers for each hire; comp bands; who owns what; the headcount that must reconcile with the L3 financial model's cost build.

## Cross-band consistency

- Headcount and hiring timing here must reconcile with the L3 financial model (the org plan's hires match the model's cost build and the runway they consume).
- The delivery process here must be consistent with the L1 model's Key Activities / Key Resources.

## Naming

- **`vcs_Doc_Class` is a canonical registry class, never a filename** — its value must be one of the slugified Class-column values in `03-SELECTION.md` (`operating-plan`, `org-hiring-plan`). The filename below is free.
- **Filename:** `<doc-class>.md` (e.g. `operating-plan.md`, `org-hiring-plan.md`) in the cartridge `Artifacts/`.
- **Type value:** `type: VCS_Operations_Document`.

## Relationships

- `VCS_Selection_Record` — *earned-by (the BI-answer that included L5; a pre-launch deferral is recorded)*.
- `VCS_Model_Document` — *reconciles-with (delivery ↔ Key Activities / Key Resources)*.
- `VCS_Financial_Document` — *reconciles-with (headcount/hiring ↔ the cost build and runway)*.
- `VCS_Plan_Document` — *reconciles-with (the plan's Organization & Management section draws from here)*.
