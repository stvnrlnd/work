# homestead.plus — Tech Stack

## Dependencies

| Layer | Technology | Version |
|---|---|---|
| Backend framework | Laravel | 12 |
| Language | PHP | 8.5 |
| CMS / Marketing site | Statamic | v6 |
| Statamic templating | Antlers | — |
| App UI framework | Filament | v5 |
| Reactive components | Livewire | v4 |
| CSS framework | Tailwind CSS | v4 |
| JS framework | Alpine.js | v3 |
| Queue / job monitoring | Laravel Horizon | v5 |
| Database ORM | Eloquent (MySQL) | — |
| Eloquent in Statamic CP | StatamicRadPack Runway | — |

## Application Layers

**Public site (Statamic / Antlers)** — Marketing pages, blog, public shop, and professionals directory. Content managed in the Statamic CP. Floor plan products are surfaced in Statamic via Runway, which bridges Eloquent models into the Statamic content pipeline.

**App panel (`/app`, Filament — multi-tenant)** — Authenticated area for customers and businesses. Tenancy is scoped to a `Profile` by `handle`. A single user can hold a customer profile and multiple business profiles; the active tenant is switched via the tenant menu. The app panel context (customer vs. business) determines what is shown.

**Admin panel (`/admin`, Filament)** — Internal tooling: business application review, product moderation, user and profile management, platform analytics.

## Key Integrations

| Integration | Purpose |
|---|---|
| Stripe Connect | Payment processing; application fee collection; business payouts |
| S3 (or compatible) | Private file storage for deliverable floor plan files |
| PDF viewer (TBD) | Browser-based viewer with download prevention for purchased plan files |
| Transactional email (TBD) | Order confirmations, approvals, lead-time notifications |
