Deliver a morning brief and set up today's daily note.

1. Determine today's date from the system.

2. Check whether `40_archives/daily/YYYY-MM-DD.md` exists for today.
   - If it doesn't, create it by copying the template at `30_resources/templates/daily-note.md`, replacing the `{{date:...}}` placeholders with today's actual date.

3. Read `90_system/context.md` to orient yourself.

4. Read the main project file (`10_projects/[project].md`) for each project listed as active in context.md. Skim any relevant changelog entries if you need a sense of recent activity.

5. Deliver the brief in this format:
   - **In flight** — what's actively being built or decided across projects
   - **Blocked / needs a decision** — anything stalled or waiting on input
   - **Top 3 priorities** — your recommendation for what Steven should focus on today, with a one-line reason for each

6. Write a condensed version of the brief (2–4 sentences, no headers) into the `## Brief` section of today's daily note, replacing the placeholder text.
