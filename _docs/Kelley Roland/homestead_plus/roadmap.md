# homestead.plus — Roadmap

## Phase 0 — Architecture Cleanup

Get the foundation right before building features on top of it. Not in production yet, so no data migrations needed.

- [ ] Add `business_type` column to `profiles` table; implement Parental STI for Business subtypes (`Designer`, `Builder`, `GeneralContractor`, `Inspector`, `InteriorDesigner`, `Landscaper`, `Lender`, `Realtor`, `Attorney`, `Other`)
- [ ] Remove `businessType` from the `data` JSON column; backfill `business_type` column
- [ ] Drop `ProfessionalRole` enum; replace with `BusinessType` enum (values are the new Parental discriminators)
- [ ] `status` (pending/approved/rejected) should only be set/read on Business profiles — add guard / scope at the model level
- [ ] Rename `studio_id` → `business_id` on `products` table and in all related code
- [ ] Update `RegisterBusinessProfile` Filament page to write to the new `business_type` column
- [ ] Update `ProfessionalController` and `ShopController` to use updated model structure
- [ ] Update Statamic Runway resource config if affected

---

## Phase 1 — Commerce Core (MVP)

The minimum needed for money to change hands.

### Payments (Stripe)
- [ ] Integrate Stripe (Laravel Cashier or direct Stripe SDK)
- [ ] Product checkout flow: add to cart → checkout → Stripe payment → order created
- [ ] Stripe webhook handling (payment succeeded, failed, refunded)
- [ ] Payout/connect model for businesses (Stripe Connect or manual payout — decide)

### Orders
- [ ] `Order` and `OrderItem` models + migrations
- [ ] Order belongs to a Customer profile; references the purchased Product and the selling Business
- [ ] Order status: pending → paid → fulfilled / refunded

### File Delivery
- [ ] Floor plan file storage (S3 or compatible — store deliverable files per product)
- [ ] Secure signed URL generation for purchased file downloads (time-limited)
- [ ] Business can upload/replace deliverable files for their products

### Emails (transactional)
- [ ] Purchase confirmation to customer (with download link)
- [ ] New order notification to business
- [ ] Business application received confirmation
- [ ] Business application approved/rejected notification

---

## Phase 2 — Business App

Give businesses the tools to manage their presence and products.

### Product Management (Filament app panel, business tenant)
- [ ] Floor plan listing page (business sees their own products)
- [ ] Create / edit floor plan form (title, price, style, specs, teaser, images, deliverable file upload)
- [ ] Publish / unpublish product
- [ ] Orders received view (per product and overall)

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

### Order History
- [ ] Customer order history page: purchased plans, download links, receipts
- [ ] Re-download previously purchased files (authenticated signed URL)

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

- **Plan customization tools** — Let customers request modifications to floor plans (requires a design workflow)
- **3D viewer / virtual tour** — Embedded 3D preview of a floor plan
- **Plan comparison** — Side-by-side compare two floor plans
- **Automated business approval** — Self-serve verification (e.g., verify business license, auto-approve after checks)
- **Reviews and ratings** — Customer reviews on floor plans and professionals
- **Services marketplace** — Transactional layer for professional services (quotes, bookings)
- **Gamification / rewards** — Badges, credits for repeat customers
- **Partnerships with suppliers** — Affiliate links to materials/fixtures
- **Mobile app**
