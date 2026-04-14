Deliver a morning brief and set up today's daily note.

1. Determine today's date from the system.

2. Check whether `40_archives/daily/YYYY-MM-DD.md` exists for today.
   - If it doesn't, create it by copying the template at `30_resources/templates/daily-note.md`, replacing the `{{date:...}}` placeholders with today's actual date.

3. Read `90_system/context.md` to orient yourself.

4. Read the main project file (`10_projects/[project].md`) for each project listed as active in context.md. Skim any relevant changelog entries if you need a sense of recent activity.

5. Read ABHP work items from `40_archives/work_items/`. Surface:
   - Any work items with `status: in-progress` or `status: in-review` (highlight these first)
   - Any work items with `status: up-next` (planned for soon)
   - Any work items with a `due` date (especially those due soon)
   - A general sense of what's in the backlog (count by item_type, notable items)

6. Deliver the brief in this format:
   - **ABHP (day job)** — active/in-progress tasks, anything due soon, notable backlog items
   - **Segment Holdings** — what's actively being built or decided across projects
   - **Blocked / needs a decision** — anything stalled or waiting on input (across both)
   - **Top 3 priorities** — your recommendation for what Steven should focus on today, balancing ABHP obligations with Segment Holdings progress, with a one-line reason for each

7. Write the full brief (all sections, same detail as delivered in chat) into the `## Brief` section of today's daily note, replacing the placeholder text. Use wiki links (`[[filename]]`) when referencing projects, areas, or other linkable notes.
