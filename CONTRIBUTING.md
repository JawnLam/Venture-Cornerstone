---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-contributing
title: "Venture Cornerstone — Contributing"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Contributing to Venture Cornerstone

Venture Cornerstone ships at v1.0.0. This document says what is in-scope without a major bump, what requires one, and the content-zone boundary that keeps `git pull` from clobbering your work.

## Content zones

Venture Cornerstone declares the four OVE-canonical content zones plus a **fifth zone** for the Grows-Through-Use portfolio.

### Engine Zone — release-owned; updated by `git pull`

| Path pattern | Notes |
|--------------|-------|
| `README.md`, `AI-BOOTSTRAP.md`, `INSTALL.md`, `OPERATOR-GUIDE.md`, `CONTRIBUTING.md`, `LICENSE.md`, `VERSION.md`, `CHANGELOG.md`, `UPDATE-PROMPT.md` | Front-door docs |
| `_venture-cornerstone-engine/**` | Engine prose (the canon, elicitation, selection, generation standards, gates, close-out) + `_meta/` (the manual `VALIDATION-CHECKLIST.md`, the optional `ARITHMETIC-CHECK.md`) |
| `_types/**` | The 10 structural Type definitions |
| `_meta/**` | Posture, traceability, golden-session script, audit dry run, OV manifest |
| `.gitignore` | Defines the Operator-Private patterns below |

Operators do not hand-edit Engine-Zone files.

### Operator-Private Zone — gitignored; never tracked

| Pattern | Why |
|---------|-----|
| `_USER.md` | Operator profile; never auto-inferred (P7) |
| `<Business>/Sessions/*.md` | Per-cartridge session logs |
| `<Business>/_design-state.md`, `<Business>/_source-log.md` | Operator's active per-business working state |
| `.DS_Store`, `.obsidian/` | Filesystem/workspace noise |

These patterns apply to **your own** business cartridges. The release-owned `Example-Business-*/` cartridges are **not** operator-private — a `.gitignore` carve-out re-includes their working files so the worked example ships complete.

### Operator-Extension Zone — operator-created; survives `git pull`

| Pattern | Notes |
|---------|-------|
| `<Business-Name>/` at the OV root | Your own business cartridges — the OV is designed to be extended here |

### Shipped Examples Zone — release-owned; updated by `git pull`

| Path | Notes |
|------|-------|
| `Example-Business-*/` | Worked-example business cartridges (packaged dossiers) demonstrating the pipeline — they ship in full |

### Grows-Through-Use Zone — release-seeded, operator-appended *(the fifth zone)*

| Path | Notes |
|------|-------|
| `_portfolio/failure-catalog.md` | The cross-cartridge failure/lesson catalog. The release ships the seed entries (PF-1..PF-9); your use appends more. |
| `_portfolio/benchmark-library.md` | The source-tagged benchmark/comparables library. The release ships public seeds; your use grows the cartridge-verified rows. |

**The tension this zone names:** these files are *neither* pure engine (the release doesn't own your appended lessons or benchmarks) *nor* pure operator content (the seeds are release doctrine). On update, `git pull` must **merge, not clobber**. `UPDATE-PROMPT.md` uses a stash/append-merge that preserves operator-appended entries. The benchmark library's k-anonymity rule (N≥3, identity stripped) governs what may ever leave a single operator's store.

## What requires a major version bump

Renaming or removing an engine chapter; changing the cartridge backbone or packaging layout; changing a structural Type's required sections such that existing stacks no longer validate; changing the stranger-test pass rule; renaming the `vcs_` namespace. Major bumps require a migration note in `CHANGELOG.md`.

## Release identity

`CHANGELOG.md`'s top entry is the single source of truth for the version; `VERSION.md` and `README.md` derive from it and must agree at ship.

## Voice

Engine content is subject-agnostic (the engine never names a specific business) and written in the precise engineering-spec register: directive, term-defining, non-goal-stating, numerate, explicit about the authority boundary, no flattery, no emojis.
