# nobullies.club — Tech Stack

## Backend

| Layer | Technology |
|---|---|
| Language | PHP 8.x |
| Framework | Laravel |
| CMS | Statamic |

## Frontend

| Layer | Technology |
|---|---|
| JS Framework | Alpine.js (assumed — consistent with other projects) |
| CSS | Tailwind CSS (assumed) |
| Bundler | Vite |

## Additional Packages

- Alpine.js + plugins (collapse, focus, morph, persist, precognition)
- Embla Carousel (story carousel on homepage)
- Statamic Peak (starter kit base)

## Design System

Custom Ghibli/graphic-novel theme (`ghibli.css`):
- **Palette:** Forest green primary, sky blue, cherry blossom pink, golden yellow, cream backgrounds
- **Fonts:** Fredoka (display), Nunito (body), Patrick Hand (comic/handwritten)
- **Components:** `.comic-panel`, `.speech-bubble`, `.soot-sprite`, `.ghibli-btn`, `.topic-badge`, halftone patterns
- **Animations:** float, drift (leaves), twinkle, fade-up (intersection observer), bounce-in, confetti

## Notes

- Anonymous story submissions use Statamic Forms (`share_story` form). Stories are moderated via a CP action (`app/Actions/MigrateStorySubmission.php`) that migrates approved submissions to the stories collection as unpublished entries.
- Pledge counter is server-backed: `GET /api/pledge-count` + `POST /api/pledge` (routes in `routes/web.php`). Counter stored in `storage/app/pledge_count` (flat file, not in git). Rate-limited to 1 pledge/IP/day. localStorage gates the UI so users can only pledge once.
- Honeypot field (`winnie`) included in story submission form for spam protection.
