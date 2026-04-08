# tokidoki.pro — Overview

## What It Is

tokidoki.pro is a team operating tool that blends project management with meeting intelligence. It sits between Dart (task/project management) and ninety.io (organizational cadence), without requiring teams to adopt a rigid framework like EOS.

The core loop: teams track work and log KPIs, and the tool uses that data to auto-generate meeting agendas. Over time, meetings become shorter, more structured, and eventually optional — because the information that drives decisions is always visible.

## Origin

Built out of frustration with two gaps:

1. **Dart** has no concept of a meeting cadence and conflates teams and projects into a single "spaces" construct.
2. **ninety.io** solves the meeting cadence problem well but requires full EOS adoption and is priced for commitment to that framework.

The goal is the value of ninety.io's meeting discipline without the framework lock-in, layered on top of actual project and task work.

## Core Thesis

Most software tries to eliminate meetings. tokidoki.pro tries to transform them — starting with smarter sync meetings, evolving toward a model where well-structured agendas can be run asynchronously, with only unresolved decisions requiring live discussion.

## Target Audience

- **Primary:** Small-to-medium teams working across multiple projects who feel meetings are unproductive and disconnected from actual work.
- **Secondary:** Disorganized companies trying to establish communication rhythms and connect team output to business outcomes.

## Key Concepts

- **Team** — A group of people. Separate from projects; a team can own multiple projects.
- **Project** — A scoped body of work. Belongs to one or more teams. Has tasks, milestones, and linked KPIs.
- **KPI** — A custom metric manually entered by team members (e.g. sales numbers, external analytics). Manual entry is intentional for v1; automation and integrations are future scope.
- **Meeting** — A generated agenda built from KPI deltas, task status, blockers, and carry-over decisions. The tool makes meeting prep automatic.
- **Async Meeting** — A future mode where the agenda is sent for async review and comment; only unresolved items require a sync call.

## Differentiators

- Teams and projects are explicitly separate entities — no conflation.
- Meeting agendas are generated from real work data, not templates.
- No framework required — teams bring their own operating rhythm.
- KPI tracking is lightweight and connected to meeting output, not a separate BI tool.

## Layout

Dashboard with a persistent sidebar containing two sections: **Teams** and **Projects**. The main pane adapts to context — project board, KPI dashboard, or meeting view.

## Status

Ideation. Domain registered: `tokidoki.pro`. No code started.

---

## Further Reading

- [Changelog](changelog.md)
