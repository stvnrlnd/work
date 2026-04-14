# homestead.plus — Revenue Forecast

*Speculative model. All figures are estimates based on market assumptions, not actual data. Revisit after launch with real traffic and conversion data.*

---

## Model Inputs & Assumptions

### Average Order Value (AOV)

| Component | Estimate | Basis |
|---|---|---|
| Floor plan base price | $750 | Mid-range PDF set; ABHP PDF sets range $400–$2,500+ |
| Add-on attach rate | 20% at avg $150 | Cost-to-build report or material list added at checkout |
| Blended AOV | ~$780 | Weighted average including add-on contribution |
| Platform revenue per sale | ~$117 | 15% of $780 |

Services (plan modifications, custom design) are excluded from Year 1 projections — the service flow won't be ready at launch and takes time to establish trust with customers. Modeled as a small Year 2+ contributor.

### Demand Driver: SEO

Floor plan purchases are high-intent and low-frequency (most people build once). Paid acquisition is unlikely to be profitable at a 15% margin in the early years. Organic search is the primary channel — each floor plan listing is a long-tail keyword ("3 bedroom craftsman floor plan", "farmhouse plans under 2000 sq ft", etc.).

**SEO ramp assumption:** A new domain with no authority takes 12–18 months to rank competitively against established players like ABHP. Traffic in Year 1 is mostly direct, designer-referred, and early-adopter. SEO starts compounding meaningfully in Year 2.

### Conversion Rate

1% of shop visitors purchase. Floor plans are high-consideration purchases with long decision cycles — customers often browse multiple times before buying. 1% is standard for high-AOV e-commerce and may be conservative once the catalog is deep and the viewer experience differentiates the product.

### The Catalog Problem

Without a compelling catalog (100+ quality plans), organic customers won't discover the shop. Without customers, designers won't prioritize listing. **The pre-launch period is primarily about building designer supply.** The first 50–100 listings should be onboarded manually before the platform goes public.

---

## Traffic & Sales Model

| Period | Monthly visitors | Conversion | Sales / month | Notes |
|---|---|---|---|---|
| Launch (Month 1) | 2,000 | 1% | 20 | Direct / designer-referred |
| Month 3 | 4,000 | 1% | 40 | Early content + outreach |
| Month 6 | 8,000 | 1% | 80 | SEO starting to surface |
| Month 12 (end of Year 1) | 15,000 | 1% | 150 | Growing catalog, early rankings |
| Month 18 | 25,000 | 1% | 250 | SEO compounding |
| Month 24 (end of Year 2) | 40,000 | 1% | 400 | Meaningful organic presence |
| Month 36 (end of Year 3) | 80,000 | 1% | 800 | Established player in niche |

---

## Three-Year Revenue Forecast

### Base Scenario

| Year | Sales | GMV | Platform Revenue (15%) |
|---|---|---|---|
| Year 1 | ~1,000 | ~$780K | **~$117K** |
| Year 2 | ~3,600 | ~$2.8M | **~$420K** |
| Year 3 | ~7,200 | ~$5.6M | **~$840K** |

*Year 1 revenue is low by design — it's the year of building supply, SEO authority, and product quality.*

### Conservative Scenario

Slower SEO ramp, thinner catalog, harder designer onboarding.

| Year | Sales | Platform Revenue |
|---|---|---|
| Year 1 | ~400 | ~$47K |
| Year 2 | ~1,500 | ~$176K |
| Year 3 | ~3,500 | ~$410K |

### Optimistic Scenario

Strong early designer partnerships, content marketing working faster, teams/connections driving referral loops among professionals, higher-than-average plan prices.

| Year | Sales | Platform Revenue |
|---|---|---|
| Year 1 | ~2,200 | ~$257K |
| Year 2 | ~8,000 | ~$936K |
| Year 3 | ~18,000 | ~$2.1M |

---

## Key Swing Factors

**Upside:**

- **Designer supply quality** — each high-quality listing is a long-tail SEO asset and a conversion driver. 200+ quality plans at launch vs. 50 could meaningfully change Year 1.
- **Viewer as differentiator** — if the in-browser viewer becomes a talking point among designers (better IP protection) and customers (better experience), word-of-mouth could accelerate growth.
- **Teams/connections referral loop** — professionals recommending each other to their clients, all within the platform, could create compounding organic acquisition that doesn't exist in the current market.
- **Higher AOV** — if homestead.plus attracts premium designers with plans priced at $1,200–$2,000+, the 15% cut is significantly more per transaction.
- **Services revenue** — modifications, custom designs, and made-to-order reports in Year 2+ could add meaningful revenue on top of product sales.

**Downside:**

- **ABHP entrenched SEO** — ranking against an established player with years of domain authority is slow. If Google's algorithms heavily favor ABHP, organic growth could be materially slower than modeled.
- **Catalog chicken-and-egg** — if designer onboarding is slow, the catalog is thin, SEO surface area is small, and customers don't convert. This is the most likely early constraint.
- **High-consideration buying cycle** — customers often visit multiple times over weeks or months before purchasing. Low-repeat purchase frequency means every sale depends on new traffic.
- **Stripe Connect friction** — requiring businesses to complete KYC/banking onboarding before receiving payouts could slow designer adoption.

---

## What to Watch Post-Launch

Once real data is available, the most important metrics to track:

1. **Listings added per month** — health of designer supply
2. **Shop visitors / organic search traffic** — demand signal
3. **Conversion rate** — is the catalog and viewer experience converting?
4. **Average order value** — are customers upgrading to higher-tier variants or adding add-ons?
5. **Repeat purchase rate** — are customers coming back (add-ons, services, second home)?
6. **Designer-to-sale ratio** — how many active designers does it take to generate X sales per month?

---

## Operating Cost Notes

Not modeled in detail here, but key cost items to keep in mind:

- Stripe fees: ~2.9% + $0.30 per transaction (in addition to the platform's 15% cut — the 15% is gross platform revenue before Stripe fees)
- Hosting: Laravel Forge + VPS or Vapor — modest cost at this scale
- S3 storage: grows with catalog size; minimal early
- Steven's time is the dominant cost — no separate salary modeled for a solo founder

At the base scenario Year 2 revenue (~$420K), the business is likely profitable given the low infrastructure overhead of a SaaS/marketplace at this scale.
