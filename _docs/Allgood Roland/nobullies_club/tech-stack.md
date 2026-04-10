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

- Anonymous story submissions use Statamic Forms (`share_story` form). Stories need CP moderation before going live.
- Pledge counter is currently localStorage-only (baseCount hardcoded at 847). Needs a real database-backed endpoint.
- Honeypot field (`winnie`) included in story submission form for spam protection.
