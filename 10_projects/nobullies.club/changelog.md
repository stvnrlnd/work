# nobullies.club — Changelog

## 2026-04-14 (Code + Docs)

- Created `app/Actions/MigrateStorySubmission.php` — CP action that appears on `share_story` form submissions; migrates selected submissions into the stories collection as unpublished entries (auto-discovered by Statamic from `app/Actions/`)
- Added pledge counter API routes (`GET /api/pledge-count`, `POST /api/pledge`) to `routes/web.php`; counter stored in `storage/app/pledge_count` flat file with flock; rate-limited to 1 pledge/IP/day via `throttle:pledge` limiter registered in AppServiceProvider
- Added `<meta name="csrf-token">` to `layout.antlers.html` for CSRF token access in fetch requests
- Rewrote `pledgeWall` Alpine component in `site.js` to fetch count from server on init and POST on pledge; localStorage still prevents duplicate pledges client-side
- Added gradient (`from-transparent to-primary-dark`) at bottom of "Start a Club" section on homepage to blend into footer treeline
- Updated `.gitignore` to exclude new story entries (`/content/collections/stories/*.md`) and pledge counter file (`/storage/app/pledge_count`) from git; seed stories remain tracked
- Updated `overview.md` and `tech-stack.md` to reflect actual state

---

## 2026-04-09 (Code + Docs)

- Pulled repo down locally to `~/Work/_code/nobullies.club/`
- Built custom Ghibli/graphic-novel design system (`ghibli.css`, `site.css`) — palette, fonts, comic panel, speech bubble, soot sprite, animated buttons, halftone patterns, keyframe animations
- Built homepage (`home.antlers.html`) — hero with floating elements/treeline, "What is Bullying?" cards, stories carousel (Embla), pledge section (Alpine/localStorage), resources preview, Start a Club CTA
- Built Stories page (`stories.antlers.html`) — story wall grid with topic/age badges + anonymous submission form with honeypot spam protection
- Built About page (`about.antlers.html`) — founder's message section
- Wired story submission to Statamic Forms (`share_story` form)
- Added 4 seed stories to `content/collections/stories/`
- Initialized project documentation
- Updated `overview.md` and `tech-stack.md` to reflect actual built state

---
