---
type: Fleeting
timestamp: "2026-07-27T00:00:00Z"
Item_ID: venture-cornerstone-install
title: "Venture Cornerstone — Install"
Date_Added: 2026-07-27
Date_Modified: 2026-07-27
Needs_Processing: false
---

# Install Venture Cornerstone

## 1. Clone into a version-named folder

```bash
git clone https://github.com/JawnLam/Venture-Cornerstone.git ~/path/to/Venture-Cornerstone-v1.0
cd ~/path/to/Venture-Cornerstone-v1.0
# Disable push so you never accidentally upload your business cartridges
git remote set-url --push origin DISABLED_TO_PREVENT_ACCIDENTAL_PUSH_OF_PERSONAL_WORK
git remote -v   # fetch = real URL; push = DISABLED_...
```

The folder is named `Venture-Cornerstone-v<major>.<minor>`. On a major.minor release, rename it to match (`mv Venture-Cornerstone-v1.0 Venture-Cornerstone-v1.1`); `CHANGELOG.md` announces the transition.

## 2. Point an AI at it

Open the folder in any AI environment that reads local markdown (Claude Code, Cursor, Claude Desktop, ChatGPT/Gemini with file attachments, Obsidian + an AI plugin). Say:

> **"Read `AI-BOOTSTRAP.md` and help me design the founding-document stack for my business."**

The AI will run the founder interview one question at a time before writing anything.

## Updating

```bash
cd ~/path/to/Venture-Cornerstone-v<major>.<minor>
git fetch origin
git log --oneline HEAD..origin/main          # preview incoming

# No local engine edits: clean fast-forward
git pull --ff-only origin main

# Local edits or appended portfolio entries: stash -> pull -> pop
git stash push --include-untracked -m "pre-update state"
git pull --ff-only origin main
git stash pop                                 # resolve any _portfolio/ merge — KEEP your appended entries
```

Your business cartridges (Operator-Extension Zone), `_USER.md`/session logs/source logs (Operator-Private Zone), and appended `_portfolio/` entries (Grows-Through-Use Zone) survive updates. See `OPERATOR-GUIDE.md § Updates and troubleshooting` and `CONTRIBUTING.md § Content zones`.

## Requirements

Any capable AI (Claude / GPT-4-class+ / Gemini 2.x+). No runtime dependencies — Venture Cornerstone ships no required validator; the two gates run manually (`_venture-cornerstone-engine/_meta/VALIDATION-CHECKLIST.md`), and the stranger decision test needs a fresh model instance. The arithmetic-identities checker in `_meta/ARITHMETIC-CHECK.md` is optional convenience tooling, never required.
