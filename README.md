# time-manager

A tiny, file-based **time-management skill** you can drop into an AI coding agent
(Claude Code, opencode, …). It keeps your tasks and plans in plain markdown so
they are greppable, diffable, and sync anywhere — no app, no account, no API.

Everything lives under a `time/` folder:

```
time/inbox.md          quick capture
time/day/2026-10-10.md daily plan
time/week/2026-W41.md  weekly review
```

The skill tells the agent how to **capture → plan the day → review the week**,
using simple conventions (markdown checkboxes, `#tag`, `!priority`, `@estimate`).

## Files

| File | Purpose |
|---|---|
| `SKILL.md` | The skill instructions (frontmatter `name` + `description`, then the workflow). |
| `templates/day.md` | Daily-plan template. |
| `templates/week.md` | Weekly-review template. |

## Install

**Claude Code**

```bash
cp -r time-manager ~/.claude/skills/time-manager
```

**opencode**

```bash
cp -r time-manager ~/.config/opencode/skills/time-manager
# or project-local: .opencode/skills/time-manager
```

Then just ask the agent: *"plan my day"*, *"triage my inbox"*, or *"run my weekly
review"*.

## Example

```
You: add "finish the report #study !high @2h" to my inbox
You: plan my day
Agent: created time/day/2026-10-10.md — Today: 1) finish the report 2) …
```

## Notes

- This is a convention + templates, not code. Adapt the tags and file layout to
  taste.
- No binaries, no external dependencies.

## License

MIT — see [LICENSE](LICENSE).
