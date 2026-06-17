# Handoff: {Short Task Description} (YYYY-MM-DD)

> Previous handoff: {filename} (`docs/handoffs/{filename}.md`). This session focused on {one-line summary of what was done and how it relates to the previous session}.

---

## 一、What Was Completed

### Background

{2-4 sentences on why this work was needed — what was left over from the previous session, what problems were discovered, what infrastructure needed to be built}

### Core Achievements

1. **{Achievement 1}** ({one-line description})
2. **{Achievement 2}** ({one-line description})
3. **{Achievement 3}** ({one-line description})

---

## 二、Changed Files

### {Category, e.g., Backend Changes}

| File | Change |
|---|---|
| `path/to/file1.ts` | {one-line summary of what changed} |
| `path/to/file2.py` | {one-line summary of what changed} |

### {Category, e.g., New Backend Files}

| File | Description |
|---|---|
| `path/to/new1.py` | {description} |
| `path/to/new2.tsx` | {description} |

### {Category, e.g., Test Files}

| File | Description |
|---|---|
| `tests/module/test_x.py` | {description} |

### Documentation Updates

| File | Change |
|---|---|
| `CLAUDE.md` | {what was synced} |
| {other docs} | {description} |

---

## 三、{Core Section Title — varies by session type}

{This is the most important section. Title depends on the nature of the session:}
- Bug fix session → "Verification Results"
- Test infrastructure → "Test Infrastructure Technical Notes"
- Feature implementation → "Implementation Notes"

{Content: key technical decisions, why certain approaches were chosen, pitfalls encountered}

---

## 四、{Results / Findings}

{Title depends on session type:}
- Testing session → "Test Results" + table (ID, title, status)
- Bug fix session → "Verification Results" + ✅/⏳/⚠️ checklist
- Implementation session → "Implementation Status"

{May include subsections like "Design Deviations Found During Testing" (diff table), "Issues Found and Fixed During Debugging"}

---

## 五、{Issues Found / Debugging / Deviations}

{Document problems discovered, root causes, and fixes. Format:}

### {Issue Title}

- **Symptom**: {user-observable behavior}
- **Root cause**: {underlying reason}
- **Fix**: {what was changed}
- **Lesson**: {reusable takeaway}

---

## 六、Next Steps

### By Priority

| Priority | Task | Notes |
|----------|------|-------|
| **P0** | {urgent blocker} | {details} |
| P1 | {high priority} | {details} |
| P2 | {medium priority} | {details} |
| P3 | {low priority} | {details} |

### {Workflow (optional)}

{If subsequent work has a fixed process, list steps:}
1. Step one
2. Step two
3. ...

---

## 七、Environment Notes

{List environment information the next person needs, one bullet each}

- **{Key point}**: {explanation} (`{command/path}`)
- **{Key point}**: {explanation}

---

## 八、Document Sync Status

- `CLAUDE.md`: ✅ Synced ({what was updated})
- {other updated docs}: ✅ {description}
- {unchanged docs}: Unchanged ({reason, e.g., "historical record, not retroactively updated" / "design snapshot"})

---

## Formatting Rules

| Aspect | Rule |
|--------|------|
| Title | Handoff: {Task Name} (YYYY-MM-DD) |
| Opening | Always use `>` blockquote linking to previous handoff |
| Section numbering | Chinese numerals: 一、二、三...八 |
| Section count | Fixed 8 sections |
| Tables | Use for file lists, test cases, priorities, diffs |
| Status markers | ✅ Done / ⏳ Pending / ⚠️ Issue / 🔴 Blocker |
| File paths | Backtick-wrapped, relative to project root |
| Code blocks | Only for commands/config snippets, not long code |
| Commands | Backtick-wrapped inline (e.g., `cd backend && uvicorn ...`) |
| Tone | Objective, concise, written for the next person with no context |

## Section Variants by Session Type

| Session Type | Section 3 (Core) | Section 4 (Results) | Section 5 (Findings) |
|---|---|---|---|
| Bug fix + verification | Verification Results | 🔴 Top unresolved issues | Environment & test data |
| Test infrastructure | Test Infrastructure Technical Notes | Test Results | Design deviations |
| Frontend tests + bug fixes | Test Infrastructure Technical Notes | Test Results | Bugs found and fixed |
| E2E test setup | Test Results | Issues found and fixed during debugging | Technical notes |
| Feature implementation | Implementation Notes | Implementation Status | Issues found during implementation |