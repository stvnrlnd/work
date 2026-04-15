---
title: nobullies.club
type: project
area: "[[allgood-roland]]"
status: active
tags:
  - passion-project
  - community
  - non-profit
created: 2026-04-13
---

# nobullies.club — Overview

## Domains

The site is **The Anti-Bully Club** and runs on three domains, all serving the same website:

- `nobullies.club` (primary)
- `antibullyclub.org`
- `antibullyclub.com`

## What It Is

nobullies.club is a passion project for one of Montanna's children (Steven's step-daughter), who wants to advocate for victims of bullying. The site aims to build an actively anti-bullying community — a place where people can share support, tell their stories, and publicly stand behind the cause.

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

Repo pulled down locally to `~/Work/_code/nobullies.club/`. Core pages and design system are built. Story submission form is wired to Statamic Forms. Pledge counter uses Alpine.js + localStorage. Seed story content (4 stories) is in place.

### Pages Built
- **Home** — Hero, "What is Bullying?" cards (incl. Bullying by Adults card), Stories carousel preview, Pledge section, Resources preview, Start a Club CTA
- **Stories** — Story wall grid + anonymous submission form
- **About** — Founder's message, origin story
- **Resources** — Books, helpful websites, and action tips. Content is hardcoded in `resources.antlers.html`.

### What's Left
- Email notifications for new story submissions

### Done
- Resources page — full content hardcoded in template
- Story submission migration action — CP action in `app/Actions/MigrateStorySubmission.php` migrates approved submissions to stories collection (unpublished)
- Pledge counter — server-backed via `/api/pledge-count` + `/api/pledge` routes; counter stored in `storage/app/pledge_count`; localStorage still gates duplicate pledges
- Footer whitespace — gradient at bottom of "Start a Club" section blends into footer treeline
- Git ignore — new story entries and pledge counter file excluded from git; seed stories remain tracked

---

## Further Reading

- [[nobullies.club/tech-stack|Tech Stack]]
- [[nobullies.club/changelog|Changelog]]
