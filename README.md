# Handoff Documents

A Claude Code skill for seamless session-to-session handoff in large projects.

## The Problem

When working on large projects across multiple AI sessions, each new session starts blind — it reads CLAUDE.md but doesn't know what was just completed, what files were changed, or what to do next. The AI wastes ~5 minutes and 40-50% of the context window exploring the entire project.

## The Solution

**Handoff documents** — a structured 8-section snapshot generated at the end of every session. The next session reads CLAUDE.md + the latest handoff document and starts working immediately.

## Commands

| Command | What it does |
|---------|-------------|
| `/handoff:generate <task-description>` | Generate a handoff document at end of session |
| `/handoff:read <path-to-handoff.md>` | Read and onboard from a handoff document |

## Results

Measured on a full-stack project (~50 endpoints, 13 tables, 9 pages) with 200k context:

| Metric | Without | With | Improvement |
|--------|---------|------|-------------|
| Onboarding time | ~5 min | ~1 min | **5× faster** |
| Context consumed | 40-50% | 15-20% | **~60% reduction** |

## Installation

Copy the `handoff-documents/` directory into your skills directory:

- **Claude Code**: `~/.claude/skills/`
- **Codex / Copilot CLI / Gemini CLI**: `~/.agents/skills/`

## Structure

```
handoff-documents/
├── SKILL.md      # Main skill file
└── template.md   # Handoff document template (8 sections)
```