# homestead.plus — Data Model

## Profiles — Two-Level STI (via Parental)

All profiles share a single `profiles` table. The `type` column is the first-level Parental discriminator (customer vs. business). The `business_type` column is the second-level discriminator for business subtypes.

```
Profile
├── Profile\Customer          type = 'customer'   (auto-created on registration)
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

**Designer** covers anyone who creates or modifies floor plans — individual architects, drafting firms, and design studios. Whether someone is a licensed architect is a profile credential/badge, not a separate business type.

**Customer profile:** Created automatically when a user registers (`UserObserver`). One per user.

**Business profile:** User-initiated. Requires admin approval (`status`: pending → approved / rejected). A user may hold multiple business profiles. Business profiles store contact info, bio, city, state in a `data` JSON column.

### Key columns (`profiles`)

| Column | Type | Notes |
|---|---|---|
| `type` | tinyint | Parental level 1: `1` = customer, `2` = business |
| `business_type` | string | Parental level 2: `designer`, `builder`, `general_contractor`, etc. Null for customers. |
| `status` | string | `pending` / `approved` / `rejected`. Meaningful only for business profiles. |
| `commission_rate` | int (nullable) | Override platform fee in basis points (e.g., `1000` = 10%). Null = platform default (15%). |
| `handle` | string | Unique URL slug. Used as Filament tenant identifier. |
| `name` | string | Display name |
| `data` | json | Type-specific fields: bio, city, state, phone, email, website |

---

## Products — STI (via Parental)

Products belong to a `business_id` (any approved Business profile). Products have **variants** — distinct configurations of the same design defined by the business upfront.

```
Product
├── Product\FloorPlan    type = 'floor_plan'
└── Product\AddOn        type = 'add_on'
```

### FloorPlan

The core product. Has one or more variants representing different configurations (e.g., 2BR vs. 3BR, with/without garage). Specs (style, stories, bedrooms, bathrooms, square_feet, garage_bays, teaser) live in the `data` JSON column at the product level and can be overridden per variant.

### AddOn

Supplementary product linked to a specific `ProductVariant` of a floor plan (e.g., a cost-to-build report or material list generated for that design). Add-ons can be purchased alongside the floor plan or independently by customers who already own that variant.

### Key columns (`products`)

| Column | Type | Notes |
|---|---|---|
| `type` | string | Parental discriminator: `floor_plan`, `add_on` |
| `business_id` | FK | Owning business profile |
| `title` | string | |
| `slug` | string | Unique; used as route key |
| `status` | string | `draft` / `published` |
| `featured` | bool | |
| `data` | json | Product-level specs |

---

## Product Variants

Each product has one or more variants. Variants are the purchasable unit — the customer buys a variant, not the product directly.

### Key columns (`product_variants`)

| Column | Type | Notes |
|---|---|---|
| `product_id` | FK | Parent product |
| `title` | string | e.g., "2 Bedroom", "3 Bedroom — Expanded" |
| `price` | uint | Unsigned integer cents (e.g., `49900` = $499.00) |
| `lead_time` | int (nullable) | Production days required before delivery. Null = instant. |
| `download_allowed` | bool | Whether the customer can download the file after viewing |
| `data` | json | Variant-level spec overrides (bedrooms, bathrooms, sq ft, etc.) |

Variant files are stored privately on S3; the file reference lives on the variant record.

---

## File Delivery — Viewer Model

Files are delivered via an **in-browser PDF viewer** (CAD support planned post-MVP). The viewer is the primary and default experience. Download is a secondary option controlled per-variant by the designer (`download_allowed`).

**Security model:** Files are stored privately on S3. The raw storage URL is never exposed to the browser. The viewer is served bytes via a server-side authenticated streaming endpoint, preventing right-click save and DevTools extraction of the underlying URL. A short-lived signed token authorizes each viewer session.

---

## Services

Services are on-demand offerings from businesses requiring designer involvement and a production period.

### Key columns (`services`)

| Column | Type | Notes |
|---|---|---|
| `business_id` | FK | Offering business |
| `variant_id` | FK (nullable) | Linked floor plan variant (e.g., "modify this plan"); null for standalone services |
| `title` | string | |
| `description` | text | |
| `price` | uint (nullable) | Null if quoted (quote flow TBD) |
| `lead_time` | int | Estimated production days |
| `status` | string | `active` / `inactive` |

**Service order lifecycle:** Pending → Accepted → In Progress → Ready for Review → Delivered

**Billing:** Pre-authorized at order placement; captured on delivery.

---

## Orders

| Column | Type | Notes |
|---|---|---|
| `customer_profile_id` | FK | Purchasing customer profile |
| `business_profile_id` | FK | Selling business profile |
| `status` | string | See lifecycles below |
| `stripe_payment_intent_id` | string | |
| `total` | uint | Integer cents |

**Instant delivery lifecycle:** Pending → Paid → Fulfilled / Refunded

**Lead-time lifecycle:** Pending → Accepted → In Progress → Ready for Review → Delivered / Cancelled / Refunded

### Order Items

Each `OrderItem` references either a `ProductVariant` or a `Service`, plus the price paid and quantity.

---

## Projects

Customer-owned build project. One user may have many projects.

| Column / Relation | Notes |
|---|---|
| `status` | `planning` / `active` / `complete` / `paused` |
| `addresses` | `ProjectAddress` records — a project can span multiple lots |
| `members` | `ProjectMember` — collaborators with `manager` or `viewer` access |
| `floor_plans` | `ProjectFloorPlan` — links a purchased `OrderItem` (variant) to a specific address |

---

## Teams & Connections

Profiles form typed connections with other profiles.

### Connection types and acceptance

| Type | From → To | Acceptance |
|---|---|---|
| `build_team_member` | Customer → Business | One-way, immediate |
| `preferred_partner` | Business → Business | One-way, immediate |
| `co_buyer` | Customer → Customer | Mutual — recipient must accept |
| `team_member` | Business → Business (internal) | Mutual — recipient must accept |

### Key columns (`connections`)

| Column | Type | Notes |
|---|---|---|
| `requester_profile_id` | FK | |
| `recipient_profile_id` | FK | |
| `type` | string | One of the four types above |
| `status` | string | `active` (one-way) / `pending` / `accepted` / `declined` (mutual) |

---

## Contacts

`Contact` records are created when a customer submits an inquiry through a business's public profile page. Stored for the business to see and manage in their app panel; triggers an email notification to the business.

---

## Architectural Notes

- **Parental** package used for STI on both `Profile` and `Product`. The discriminator column must match the `$childTypes` map on the parent model.
- **Statamic Runway** exposes `Product` (and potentially `Profile`) Eloquent models in the Statamic CP for admin/editorial use.
- **Filament multi-tenant** — tenancy is scoped to `Profile` by `handle`. The active tenant determines which profile's data is visible in the app panel.
- All prices are stored as **unsigned integer cents** throughout (products, variants, orders, services).
