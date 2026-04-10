# nobullies.club — Overview

## What It Is

nobullies.club is a passion project for Steven's 10-year-old step-daughter, who wants to advocate for victims of bullying. The site aims to build an actively anti-bullying community — a place where people can share support, tell their stories, and publicly stand behind the cause.

## Origin

The step-daughter is personally dealing with a bullying situation involving her father, and wants to do something meaningful about it. This project is her initiative, built with Steven's help.

## Target Audience

- Kids and young people dealing with bullying
- Parents, advocates, and supporters
- Accessible to a broad age range — the community should feel safe and welcoming

## Core Features

- **Anonymous story submissions** — Visitors can submit their own story in support of others, without needing an account. Stories are submitted anonymously.
- **Pledge / support indicator** — A simple, low-friction action where visitors click to indicate they support the cause. No account required.
- **Community feel** — The site should feel warm, active, and supportive — not clinical or institutional.

## Status

Repo pulled down locally to `_sites/nobullies.club/`. Core pages and design system are built. Story submission form is wired to Statamic Forms. Pledge counter uses Alpine.js + localStorage. Seed story content (4 stories) is in place.

### Pages Built
- **Home** — Hero, "What is Bullying?" cards (incl. Bullying by Adults card), Stories carousel preview, Pledge section, Resources preview, Start a Club CTA
- **Stories** — Story wall grid + anonymous submission form
- **About** — Founder's message, origin story
- **Resources** — (page exists, content TBD)

### What's Left
- Moderation workflow for story submissions (CP review before stories go live)
- Real pledge counter backed by a database/endpoint (currently localStorage only)
- Resources page content
- Navigation and footer polish
- Email notifications for new story submissions

---

## Further Reading

- [Tech Stack](tech-stack.md)
- [Changelog](changelog.md)
