# homestead.plus — Project Overview

## What It Is

homestead.plus is a multi-vendor marketplace for house floor plans. Businesses list and sell floor plan products; customers browse, purchase, and organize those plans into build projects tied to specific properties. The platform also surfaces a directory of home-building professionals that customers can engage during their build journey.

Inspiration: America's Best House Plans (houseplans.net).

Domain: **homestead.plus** (registered, not yet in production)

---

## Business Model

- **Customers** — Browse the shop, purchase floor plans, and organize them into Projects. A project tracks the land address, chosen floor plan(s), and collaborating professionals.
- **Business profiles** — Any user can apply for a business profile. All businesses require admin approval before becoming active. A business profile is required to sell products, offer services, or appear in the professionals directory.
  - **Some businesses sell products** (floor plan files) — e.g., design studios, architects
  - **Some businesses offer services** — e.g., builders, GCs, realtors, lenders
  - **Some businesses do both** — e.g., an architect who designs and sells plans and also takes on builds
- **Professionals directory** — Approved business profiles are surfaced in a searchable public directory. Not a transactional marketplace (no platform fee on services); it's a lead-gen layer.

Revenue model: platform takes a percentage of product sales (floor plan purchases). Services are out-of-band (no transaction on platform).

---

## Tech Stack

| Layer | Technology |
|---|---|
| Backend | Laravel 12, PHP 8.5 |
| CMS / Marketing | Statamic v6 (Antlers templating) |
| App UI | Filament v5 (multi-tenant panel) |
| Reactive components | Livewire v4 |
| Frontend | Tailwind CSS v4, Alpine.js v3 |
| Queue / Jobs | Laravel Horizon v5 |
| Database | MySQL (via Eloquent) |
| Runway | StatamicRadPack Runway (Eloquent models in Statamic CP) |

---

## Data Model

### Profiles — two levels of STI (via Parental)

All profiles share a single `profiles` table. The `type` column is the first-level discriminator (customer vs. business). The `business_type` column is the second-level discriminator for business subtypes.

```
Profile
├── Profile\Customer          type = 'customer'   (auto-created for every user on registration)
└── Profile\Business          type = 'business'   (user-applied, requires admin approval)
    ├── Profile\Business\Designer             Sells floor plan products; may also offer design services
    ├── Profile\Business\Builder
    ├── Profile\Business\GeneralContractor
    ├── Profile\Business\Inspector
    ├── Profile\Business\InteriorDesigner
    ├── Profile\Business\Landscaper
    ├── Profile\Business\Lender
    ├── Profile\Business\Realtor
    ├── Profile\Business\Attorney
    └── Profile\Business\Other
```

**Designer** covers anyone who creates or modifies floor plans — individual architects, drafting firms, and design studios alike. The term matches industry convention (ABHP calls all plan creators "Designers"). Whether someone is a licensed architect is a profile attribute (credential/badge), not a separate business type, since the distinction doesn't meaningfully change what a customer is buying from the marketplace.

**Customer profile:** Created automatically when a user registers (`UserObserver`). One per user.

**Business profile:** User-initiated. Requires admin approval (`status`: pending → approved / rejected). A user may hold multiple business profiles. Business profiles store contact info, bio, city, state in a `data` JSON column.

**Key columns:**
- `type` — `customer` | `business` (Parental level 1)
- `business_type` — `designer` | `builder` | `general_contractor` | etc. (Parental level 2, null for customers)
- `status` — `pending` | `approved` | `rejected` (meaningful only for business profiles)
- `handle` — unique URL slug
- `data` — JSON for type-specific fields

### Products — STI (via Parental)

| Type | Class | Data fields |
|---|---|---|
| `floor_plan` | `Product\FloorPlan` | style, stories, bedrooms, bathrooms, square_feet, garage_bays, teaser |

Products belong to a `business_id` (any approved Business profile — not restricted to a specific business type). Additional product types may be added in the future.

Managed in the Statamic CP via Runway, and via the Filament app panel by the owning business.

**Product statuses:** Draft → Published. Products can be marked `featured`. Price stored as unsigned integer cents.

### Projects

Customer-owned build project. One user may have many projects.

- `status`: Planning → Active → Complete / Paused
- `addresses` — multiple `ProjectAddress` records (a project can span multiple lots)
- `members` — collaborators (other users) with `manager` or `viewer` access
- `floor_plans` — `ProjectFloorPlan` pivot linking a purchased floor plan to a specific address within the project

### Contacts

`Contact` model — used for professional inquiry / lead capture from the professionals directory (details TBD).

---

## Application Structure

### Public Site (Statamic / Antlers)

- **Marketing pages** — Statamic collections/entries (homepage, about, how it works, pricing)
- **Blog** — Educational content about the home-building process
- **Shop** (`/shop`) — `ShopController`: list (filter by style, sort by price/new, paginate 12) + detail
- **Professionals** (`/professionals`) — `ProfessionalController`: list (filter by role, paginate 24) + detail

### App Panel (`/app`, Filament multi-tenant)

Tenant = `Profile` (identified by `handle`). A user switches between their profiles using the tenant menu. The active tenant determines what the app panel shows.

- **Customer tenant:** project management, order history, floor plan browser
- **Business tenant:** product management (if applicable), orders received, profile/listing management

**Currently built:**
- Auth: register, login, password reset, email verification
- Auto-create customer profile on registration
- Register Business Profile flow (with pending approval state)
- Profile settings
- Dashboard (stub)

**To build:**
- Customer: project list, project detail, purchase flow
- Business: product management UI, sales dashboard
- Shared: order history

### Admin Panel (`/admin`, Filament)

- Business application review (approve / reject)
- User and profile management
- Product moderation
- Platform analytics

---

## Current State (as of 2026-04-08)

**Done:**
- Database schema: profiles, products, projects, project_addresses, project_members, project_floor_plans, contacts
- Profile system: Customer/Business STI (level 1); business_type needs to move to a proper column (currently stored in JSON — see roadmap)
- Product system: FloorPlan STI; Statamic Runway integration
- Project system: model layer only, no UI
- Public shop: list + detail views
- Professionals directory: list + detail views
- Filament app panel: auth, multi-tenant by profile, business registration, profile settings
- Filament admin panel: scaffolded, resources TBD

**Architecture cleanup needed before building further (see roadmap):**
- Add `business_type` column to `profiles`; implement Business subtype STI
- Remove `businessType` from `data` JSON
- Scope `status` column meaning to business profiles only
- Rename `studio_id` → `business_id` on `products` table

---

## Key Decisions

- **Two-level Parental STI for profiles** — `type` distinguishes customer vs. business; `business_type` distinguishes business subtypes. Keeps the schema flat while enabling type-specific model logic.
- **Any approved business can list products** — no restriction by business type. Authorization is approval-based, not type-based.
- **Statamic Runway** — exposes Eloquent product models in the Statamic CP for admin/content management. Business owners manage their own listings via the Filament app panel.
- **Multi-tenant Filament panel** — a single user can hold a customer profile and multiple business profiles, switching between them via the tenant menu.
- **Integer cents for pricing** — `price` column on `products` is an unsigned integer (e.g., `49900` = $499.00).
- **Manual business approval initially** — admin reviews all business applications. Intended to be automated (or self-serve with light verification) once volume warrants it.

---

## Further Reading

- [Roadmap](roadmap.md)
- [Changelog](changelog.md)
