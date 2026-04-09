# homestead.plus — Roadmap

## Phase 0 — Architecture Cleanup

Get the foundation right before building features on top of it. Not in production yet, so no data migrations needed.

- [ ] Add `business_type` column to `profiles` table; implement Parental STI for Business subtypes (`Designer`, `Builder`, `GeneralContractor`, `Inspector`, `InteriorDesigner`, `Landscaper`, `Lender`, `Realtor`, `Attorney`, `Other`)
- [ ] Remove `businessType` from the `data` JSON column; backfill `business_type` column
- [ ] Drop `ProfessionalRole` enum; replace with `BusinessType` enum (values are the new Parental discriminators)
- [ ] `status` (pending/approved/rejected) should only be set/read on Business profiles — add guard / scope at the model level
- [ ] Add `commission_rate` column to business profiles (nullable integer cents; null = platform default of 15%)
- [ ] Rename `studio_id` → `business_id` on `products` table and in all related code
- [ ] Add `ProductVariant` model and migration (price, specs, lead_time, download_allowed, files)
- [ ] Add `add_on` product type (STI subclass `Product\AddOn`); link to a parent floor plan variant
- [ ] Update `RegisterBusinessProfile` Filament page to write to the new `business_type` column
- [ ] Update `ProfessionalController` and `ShopController` to use updated model structure
- [ ] Update Statamic Runway resource config if affected

---

## Phase 1 — Commerce Core (MVP)

The minimum needed for money to change hands.

### Payments (Stripe Connect)
- [ ] Integrate Stripe Connect; business onboarding flow (connect bank account, KYC)
- [ ] Product checkout flow: select variant → checkout → Stripe payment with application fee → order created
- [ ] Pre-authorization flow for lead-time orders (auth at purchase, capture on delivery)
- [ ] Stripe webhook handling (payment succeeded, failed, captured, refunded)
- [ ] Per-business commission rate applied from `commission_rate` profile field (default 15%)

### Orders
- [ ] `Order` and `OrderItem` models + migrations
- [ ] Order belongs to a Customer profile; references the purchased ProductVariant and the selling Business
- [ ] **Instant delivery order lifecycle:** Pending → Paid → Fulfilled / Refunded
- [ ] **Lead-time order lifecycle:** Pending → Accepted → In Progress → Ready for Review → Delivered / Refunded
- [ ] `Service` model + migration (title, description, lead_time, price or quoted flag, linked floor plan variant if applicable)

### File Delivery — Viewer
- [ ] Research and select open-source PDF viewer library with browser-level download prevention (right-click, DevTools)
- [ ] Private S3 storage for deliverable files; files never served with public URLs
- [ ] Server-side signed token generation for viewer sessions (raw URL never exposed to browser)
- [ ] Per-variant download permission flag (`download_allowed`); signed PDF download URL if permitted
- [ ] Business file upload UI (upload deliverable files per variant from app panel)

### Emails (transactional)
- [ ] Purchase confirmation to customer (with link to viewer in order history)
- [ ] New order notification to business
- [ ] Lead-time order: accepted / in-progress / ready-for-review / delivered notifications
- [ ] Business application received confirmation
- [ ] Business application approved/rejected notification

---

## Phase 2 — Business App

Give businesses the tools to manage their presence and products.

### Product Management (Filament app panel, business tenant)
- [ ] Floor plan listing page (business sees their own products and variants)
- [ ] Create / edit floor plan form (title, style, specs, teaser, images)
- [ ] Variant management: add/edit/remove variants (price, bedroom/bathroom/sqft specs, lead time, download permission, file upload)
- [ ] Add-on product management: create cost-to-build reports, material lists linked to a variant
- [ ] Publish / unpublish product
- [ ] Orders received view: instant delivery and lead-time orders with separate status flows
- [ ] Lead-time order management: accept, mark in progress, mark ready for review, deliver

### Business Profile Management
- [ ] Public business profile page (visible at `/professionals/{handle}`)
- [ ] Edit business profile from app panel (bio, location, contact info, logo/photos)
- [ ] Contact/inquiry form on public profile → leads stored as `Contact` records + email notification to business

### Admin Panel
- [ ] Business application queue (list pending, approve/reject with optional note)
- [ ] Product listing review (flag/remove inappropriate listings)
- [ ] User and profile management

---

## Phase 3 — Customer App

Give customers the tools to manage their build journey.

### Project Management (Filament app panel, customer tenant)
- [ ] Project list (create, rename, change status)
- [ ] Project detail: addresses (add/edit), attached floor plans per address
- [ ] Assign a purchased floor plan to a project address
- [ ] Project members: invite by email, set manager/viewer access
- [ ] Project member email invite flow (accept invite → account creation if needed)

### Order History & Viewer
- [ ] Customer order history page: purchased plans and services, receipts
- [ ] In-browser floor plan viewer for purchased variants (PDF viewer, download-prevention enforced)
- [ ] PDF download link in viewer if designer has enabled it for that variant
- [ ] Purchase add-on products from order history (for plans already owned)
- [ ] Lead-time order tracking (status progress visible to customer)

### Teams & Connections
- [ ] `Connection` model + migration (requester, recipient, type, status)
- [ ] Connection types: build_team_member (customer→business), preferred_partner (business→business), co-buyer (customer→customer, mutual), team_member (business internal, mutual)
- [ ] One-way connections created immediately; mutual connections require recipient acceptance
- [ ] Customer build team UI: browse and add professionals to their team
- [ ] Business preferred partners UI: endorse other businesses
- [ ] Team member invitation flow for mutual connections (email invite + accept/decline)

---

## Phase 4 — Marketing Site & Content

Make the public site worth landing on.

### Statamic Content
- [ ] Homepage (hero, featured plans, how it works, directory teaser)
- [ ] How It Works page (for customers and for businesses)
- [ ] About page
- [ ] Blog: initial editorial content about the home-building process
- [ ] FAQ

### Shop Enhancements
- [ ] Floor plan style/attribute filtering (bedrooms, bathrooms, sq ft range, stories, garage bays)
- [ ] Floor plan search
- [ ] Featured plans section on homepage
- [ ] Location-based filtering for professionals directory (city/state from profile data)

### SEO Basics
- [ ] Meta titles/descriptions for shop and professional pages (Statamic SEO addon or custom)
- [ ] Sitemap
- [ ] OG images for floor plan listings

---

## Phase 5 — Production Launch

Infrastructure and operational readiness.

### Hosting & Deployment
- [ ] Choose hosting (Laravel Forge + VPS, or Laravel Vapor)
- [ ] Configure deployment pipeline (GitHub Actions or Envoyer)
- [ ] Environment variables, secrets management
- [ ] Queue workers (Horizon) configured for production

### Data & Storage
- [ ] Production database setup with automated backups
- [ ] S3 bucket (or equivalent) for floor plan files and product images, with private access policy
- [ ] CDN for public assets

### Monitoring
- [ ] Error tracking (Sentry or Flare)
- [ ] Uptime monitoring
- [ ] Horizon dashboard secured and accessible

### Legal / Compliance
- [ ] Terms of Service (covering both customers and businesses)
- [ ] Privacy Policy
- [ ] Refund policy
- [ ] Stripe compliance (business verification for payouts)

### Launch
- [ ] DNS pointed to production
- [ ] SSL configured
- [ ] Seed initial floor plan products (at least a small catalog for launch)
- [ ] Onboard first business profiles manually
- [ ] Soft launch / beta period before public announcement

---

## Deferred / Post-MVP

Things that are valuable but not needed for launch:

- **CAD file viewer** — Browser viewer for DWG/DXF files (significantly harder than PDF; research open-source options)
- **Quoted service pricing** — Services where the designer provides a custom quote before the customer commits (vs. fixed-price services)
- **3D viewer / virtual tour** — Embedded 3D preview of a floor plan
- **Plan comparison** — Side-by-side compare two floor plan variants
- **Automated business approval** — Self-serve verification (e.g., verify business license, auto-approve after checks)
- **Reviews and ratings** — Customer reviews on floor plan variants and professionals
- **Paid placement / advertising slots** — Featured positions in shop and professionals directory (see Leadership task)
- **Gamification / rewards** — Badges, credits for repeat customers
- **Partnerships with suppliers** — Affiliate links to materials/fixtures
- **Mobile app**
