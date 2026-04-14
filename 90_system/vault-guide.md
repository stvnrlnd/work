---
title: Vault Guide
type: system
tags:
  - system
  - vault
created: 2026-04-13
---

# Vault Guide

How this Obsidian vault is organized and how to use it.

## Folder Structure

```
00_inbox/       — Fleeting ideas, captures, things to process
10_projects/    — One subfolder per project with all project docs
20_areas/       — Ongoing responsibilities: groups, subsidiaries, company
30_resources/   — Reference material shared across projects
40_archives/    — Cold storage: completed/abandoned work; also holds daily notes and meetings
  daily/        — Daily notes (YYYY-MM-DD.md)
  meetings/     — Meeting notes
90_system/      — Claude's working files, not for manual management
```

## Conventions

### Frontmatter

All notes should have YAML frontmatter with at minimum:
```yaml
---
title: Human Readable Title
type: project | area | resource | system | daily
created: YYYY-MM-DD
---
```

Project files also include:
```yaml
area: "[[area-name]]"
status: idea | pre-development | in-development | launched | archived
tags: [list, of, tags]
```

### Internal Links

Use Obsidian wiki links: `[[filename]]` or `[[folder/filename|Display Text]]`.

Do not use relative markdown links like `[text](file.md)` — they don't work consistently in Obsidian.

### Project Structure

Each project uses a named file as the main note, with a same-named folder for supporting docs:
```
10_projects/[project.name].md     ← main note; links to everything else
10_projects/[project.name]/
  changelog.md                    ← dated work log
  roadmap.md                      ← phases and tasks
  tech-stack.md                   ← technology decisions
  [other docs].md
```

Single-file projects (ideas, stubs) are just `10_projects/[project.name].md` with no folder.

### Daily Notes

Daily notes live in `40_archives/daily/YYYY-MM-DD.md`. The Obsidian core Daily Notes plugin is configured to create them there automatically using the template at `30_resources/templates/daily-note`.

### Meeting Notes

Meeting notes live in `40_archives/meetings/`. The Templater template handles naming automatically: `YYYY-MM-DD Meeting Title.md`. The `title` frontmatter holds just the meeting name; the date prefix comes from `created`.

### Tasks

Local task files live in `40_archives/tasks/`. Use the template at `30_resources/templates/task.md`.

**Frontmatter fields:**

| Field | Required | Notes |
|---|---|---|
| `title` | yes | Human-readable task name |
| `type` | yes | Always `task` |
| `task_type` | yes | `task` \| `bug` \| `feature` \| `experimental` \| `maintenance` \| `security` |
| `source` | yes | `abhp` or `dart` |
| `project` | yes | `abhp` or a Segment Holdings project slug (e.g. `homestead.plus`) |
| `status` | yes | `ready` \| `up-next` \| `in-progress` \| `in-review` \| `on-hold` \| `done` \| `left` |
| `created` | yes | When the task was made ready for development (not necessarily when it was created upstream) |
| `updated` | yes | Last time the task file was meaningfully changed |
| `due` | ABHP only | Due date, if set |
| `trello_id` | ABHP only | Numeric Trello card ID; also used as filename prefix (`2343 - Title.md`) |
| `dart_id` | Dart only | Dart task ID for cross-reference |

**Naming conventions:**

- ABHP tasks: `{trello_id} - {Title}.md` (e.g. `2343 - Plan Media Viewer - Milestone 3.md`)
- Dart-mirrored tasks: `{Title}.md` (or `{dart_id} - {Title}.md` if ID is known)

**Important rules:**

- ABHP tasks are **never** created in Dart. They exist only as local reference files.
- Dart-mirrored tasks are created in Dart first; the local file is a copy for vault context.
- `created` on an ABHP task represents when it was made ready for development, not when it was added to Trello.

### Templates

Templates live in `30_resources/templates/`.

**Plugins installed:**
- **Core Templates** — used for simple templates (daily note). Syntax: `{{date:YYYY-MM-DD}}`, `{{title}}`, `{{time}}`
- **Templater** — used for templates requiring logic or prompts (meeting note). Syntax: `<% tp.date.now("FORMAT") %>`, `<%* /* script */ %>`

**Templater settings:** Settings → Templater → Template folder → `30_resources/templates`

To use a Templater template, open the command palette and run **Templater: Open Insert Template Modal**, or configure a hotkey for it.

### Skills (`/brief`)

The `/brief` slash command lives at `.claude/commands/brief.md`. Invoking it reads active project context, delivers a morning brief in chat, and populates the `## Brief` section of today's daily note.

## Dart (Project Management)

Dart is the external project management tool. Claude accesses it via MCP (`mcp__Dart__*`).

### Dartboard Structure

| Space | Dartboard | Purpose |
|---|---|---|
| Leadership | Leadership/Tasks | High-level ideas, directional tasks |
| Engineering | Engineering/Active, /Next, /Backlog, and numbered sprint boards | Dev work |
| Product | Product/Tasks | Product decisions and specs |
| Design | Design/Tasks | Design work |
| Sales | Sales/Tasks | Sales activity |

### Custom Properties

- `project` (multiselect) — links a task to: `sendfeed.to`, `segment.holdings`, `homestead.plus`, `tokidoki.pro`, `nobullies.club`, `openfaith.world`, `stevenroland.com`, `allgood-roland.org`, `theirvoice.blog`, `theoandchar.com`
- `importance` (select) — `Critical`, `Priority`, `Pickup`, `Optional`

### Task Types & Statuses

- **Types:** Task, Bug, Feature, Experimental, Maintenance, Security
- **Statuses:** Ready, Up Next, In Progress, In Review, On Hold, Done, Left
