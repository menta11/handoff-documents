---
name: handoff-documents
description: Use when working on large projects across multiple AI sessions, when starting a new session that needs to continue previous work, when context windows are limited and full project exploration is too expensive, or when handing off work between AI terminals
---

# Handoff Documents

## Overview

**A handoff document is a structured snapshot of the current session's work, generated at the end of every session.** It lets the next AI session pick up immediately without re-exploring the entire project.

Combined with an up-to-date CLAUDE.md, handoff documents form a linked chain of session history. Each document references the previous one, creating a navigable trail of project progress.

## When to Use

```
New AI session starting?
  ├─ Yes → Read CLAUDE.md + latest handoff document first
  └─ No → Continue working
Session ending?
  ├─ Yes → Generate a handoff document
  └─ No → Nothing to do
```

**Triggers:**
- Starting a new AI session on a project with prior work
- About to end a session that made meaningful changes
- Context window is filling up and you need to hand off
- Multi-session feature development spanning days

**Do NOT use when:**
- The session made no changes (read-only exploration)
- The project is trivial (single file, few hundred lines)

## Core Pattern

### Reading: `/handoff:read <path-to-handoff.md>`

When invoked with a handoff document path, follow this procedure EXACTLY:

**Step 1 — Read the essentials (two files only):**
1. Read `CLAUDE.md` — project overview, tech stack, architecture, conventions
2. Read the specified handoff document — last session's work

**Step 2 — Extract and present:**
- What was completed last session
- What files were changed
- Current project state
- Environment notes (ports, accounts, dependencies)
- Document sync status

**Step 3 — Identify actionable next steps:**
- Extract the priority table from the handoff document (Section 6)
- Map each priority item to a concrete next action
- Present as a structured task list

**CRITICAL RULE: Do NOT explore the project.** Do not run `ls`, `find`, `grep`, or read files beyond CLAUDE.md and the handoff document. The handoff document IS the exploration. Trust it.

**If CLAUDE.md references other docs** (e.g., `docs/reference/api.md`), only read them when a specific task requires it — not during onboarding.

### Generating: `/handoff:generate <short-task-description>`

When invoked, generate a handoff document at `docs/handoffs/YYYY-MM-DD-{description}.md`. Use the template in [template.md](template.md). The document has 8 fixed sections:

| Section | Content | Purpose |
|---------|---------|---------|
| **一、What was completed** | Background + core achievements (bullet list) | Tells next session what got done |
| **二、Changed files** | Tables grouped by category (backend/frontend/tests/docs) | Tells next session what was touched |
| **三、Key technical points** | Architecture decisions, tricky implementation details, gotchas | Prevents next session from repeating mistakes |
| **四、Results/Findings** | Test results, verification status, design deviations | Shows what was validated |
| **五、Issues found & fixed** | Phenomenon → Root cause → Fix → Lesson | Captures debugging knowledge |
| **六、Next steps** | Priority table (P0-P3) + workflow steps if applicable | Guides next session's work |
| **七、Environment notes** | Ports, accounts, dependencies, migration state | Prevents environment confusion |
| **八、Document sync status** | CLAUDE.md sync status, other doc updates | Tracks documentation consistency |

### CLAUDE.md Synchronization

After generating the handoff document, update CLAUDE.md:

1. **Implementation status** — update the project status section with new capabilities
2. **Bug fix records** — add notable fixes to the changelog
3. **Timestamp** — update to current date

### Naming Convention

```
docs/handoffs/YYYY-MM-DD-{short-task-description}.md
```

The first line of each document must reference the previous handoff document with a `>` blockquote.

## Quick Reference

| Task | Action |
|------|--------|
| Start new session | `/handoff:read docs/handoffs/<latest>.md` |
| End session | `/handoff:generate <task-description>` → update CLAUDE.md |
| Find previous work | Follow the handoff reference chain |
| Check environment | Read Section 7 of latest handoff |
| See what's next | Read Section 6 priority table |

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Exploring the whole project on startup | Read ONLY CLAUDE.md + handoff doc |
| Skipping CLAUDE.md update | Always sync after generating handoff |
| Writing narrative instead of structured data | Use tables, bullet lists, status markers |
| Assuming next reader has context | Write for someone who knows nothing about this session |
| Forgetting environment notes | Ports, test accounts, manual migration steps — record everything |
| Not referencing previous handoff | Always link to the prior document in the opening blockquote |

## Real-World Impact

Measured on a full-stack knowledge management system (~50 API endpoints, 13 database tables, 9 frontend pages) with 200k context window:

| Metric | Without Handoff | With Handoff | Improvement |
|--------|----------------|--------------|-------------|
| Onboarding time | ~5 minutes | ~1 minute | **5× faster** |
| Context consumed | 40-50% | 15-20% | **~60% reduction** |

The saved context capacity translates directly to more productive work per session.