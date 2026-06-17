# Handoff Documents / 接手文档

> A Claude Code skill for seamless session-to-session handoff in large projects.
> 一个用于大型项目中 AI 会话之间无缝交接的 Claude Code Skill。

---

## 解决的问题 / The Problem

当在大型项目中跨多个 AI 会话工作时，每个新会话启动时都是盲的——它读了 CLAUDE.md，但不知道上一轮刚完成了什么、改了哪些文件、下一步该做什么。AI 会浪费约 5 分钟和 40-50% 的上下文窗口来探索整个项目环境。

When working on large projects across multiple AI sessions, each new session starts blind — it reads CLAUDE.md but doesn't know what was just completed, what files were changed, or what to do next. The AI wastes ~5 minutes and 40-50% of the context window exploring the entire project.

## 解决方案 / The Solution

**接手文档（Handoff Documents）**——每个会话结束时生成的一份 8 节结构化快照。下一个会话只需读取 CLAUDE.md + 最新接手文档即可立即开始工作。

**Handoff documents** — a structured 8-section snapshot generated at the end of every session. The next session reads CLAUDE.md + the latest handoff document and starts working immediately.

## 指令 / Commands

| 指令 / Command | 作用 / What it does |
|---------|-------------|
| `/handoff:generate <任务简述>` | 会话结束时生成接手文档 / Generate a handoff document at end of session |
| `/handoff:read <接手文档路径>` | 读取并接手上一轮工作 / Read and onboard from a handoff document |

## 实测效果 / Results

在一个全栈项目（~50 端点、13 张表、9 个页面）上，200k 上下文窗口实测：

| 指标 / Metric | 无接手文档 / Without | 有接手文档 / With | 提升 / Improvement |
|--------|---------|------|-------------|
| 上手时间 / Onboarding | ~5 min | ~1 min | **5× 更快** |
| 上下文消耗 / Context | 40-50% | 15-20% | **~60% 减少** |

## 安装 / Installation

将 `handoff-documents/` 目录复制到你的 skills 目录：

Copy the `handoff-documents/` directory into your skills directory:

- **Claude Code**: `~/.claude/skills/`
- **Codex / Copilot CLI / Gemini CLI**: `~/.agents/skills/`

## 结构 / Structure

```
handoff-documents/
├── SKILL.md      # 主 skill 文件 / Main skill file
└── template.md   # 接手文档模板（8 节）/ Handoff document template (8 sections)
```