# homestead.plus — Changelog

## 2026-04-09

- Collapsed `Architect` and `Studio` business types into a single `Designer` type, following ABHP's industry convention; whether someone is a licensed architect is a profile credential/badge, not a separate business type

## 2026-04-08

- Created project documentation (`project-overview.md`, `changelog.md`, `roadmap.md`)
- Removed initial brainstorming doc (raw Ollama chat log, no longer needed)
- Clarified business profile model: Customer auto-created on registration; Business profile is opt-in with admin approval; any approved business can sell products or offer services regardless of business type
- Decided on two-level Parental STI for profiles: `type` (customer/business) + `business_type` column for business subtypes
- Decided to rename `studio_id` → `business_id` on products table; "studio" is a business type, not a special role
- Architecture cleanup tasks captured in roadmap Phase 0 (pre-production, no data migration needed)

## 2026-03-24

- Added `products` table and `project_floor_plans` table (migrations)
- Implemented `Product` model with STI via Parental; `Product\FloorPlan` subtype
- `FloorPlan` data fields: style, stories, bedrooms, bathrooms, square_feet, garage_bays, teaser
- Integrated Statamic Runway for managing products in the Statamic CP
- Implemented `ProjectFloorPlan` model (links project + address + product)
- Implemented `ShopController` (index with style/sort filtering, paginated; show with publish gate)
- Implemented `ProfessionalController` (index with role filtering; show with approval gate)

## 2026-03-23

- Added `projects`, `project_addresses`, `project_members`, `contacts` tables (migrations)
- Implemented `Project`, `ProjectAddress`, `ProjectMember`, `Contact` models
- `Project` statuses: Planning, Active, Complete, Paused
- `ProjectMember` access levels: Manager, Viewer

## 2026-02-26

- Added `profiles` table (migration)
- Implemented `Profile` model with STI via Parental; `Profile\Customer` and `Profile\Business` subtypes
- `Business` profile: status (pending/approved/rejected), 11 professional role types, JSON data for bio/location/contact
- Set up Filament app panel (`/app`): auth, multi-tenant by profile handle, business profile registration, profile settings page
- Set up Filament admin panel (`/admin`)
