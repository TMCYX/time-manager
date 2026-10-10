---
name: time-manager
description: Plan and track your day and week in plain markdown files. Use when the user asks to plan their day or week, triage a task inbox, check what is due or carried over, or run a weekly review. Works with any agent that can read and write files (Claude Code, opencode, etc.). No external services, no API keys — everything is markdown on disk.
---

# time-manager

A tiny, file-based time-management system. Everything lives in plain markdown
under `time/` in the workspace, so it is greppable, diffable, and syncs anywhere
(OneDrive, git, Syncthing, …).

The agent's job is to **capture, plan, and review** — never to invent tasks.

## Layout

```
time/
  inbox.md           # quick capture — one task per line, unfiled
  day/YYYY-MM-DD.md  # daily plan
  week/YYYY-Www.md   # weekly review (ISO week, e.g. 2026-W41)
```

## Conventions

- Tasks are markdown checkboxes: `- [ ] do the thing` / `- [x] done`.
- Optional markers at the end of a line:
  - `#work` `#study` `#home` — category tag
  - `!high` / `!low` — priority
  - `@30m` — rough estimate
- Each day file opens with a **Today** focus block (max 3 items).
- Keep the inbox empty by the end of each week (file or delete every line).

## Workflows

### Capture
Append one line to `time/inbox.md`:

```
- [ ] <task> [#tag] [!priority] [@estimate]
```

### Plan the day
1. Read `time/inbox.md` and the most recent `time/day/*.md` (for carry-over).
2. Create `time/day/<today>.md` from `templates/day.md`.
3. Move the items you intend to do **today** out of the inbox and into "Today".
4. Choose **at most 3 must-do** items; put the rest under "If time allows".

### Review the week
1. Read every `time/day/*.md` in the current ISO week.
2. Create `time/week/<ISO>.md` from `templates/week.md`.
3. Summarize: what got done, what slipped, and a carry-over list.
4. Carry unfinished items forward; close the loop on `time/inbox.md`.

## Rules

- **Never delete history** — move items, don't erase them.
- Keep each task to one line.
- Don't create a day file for a day you never planned.
- The agent proposes; the human decides what is actually "must-do".
