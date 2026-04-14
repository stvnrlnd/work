# homestead.plus — Revenue Model

## Platform Fee

homestead.plus takes a percentage of each product and service sale via a Stripe Connect application fee.

- **Standard rate: 15%** — applied to all transactions by default
- **Reduced rate: 10%** — available to qualifying businesses; conditions TBD
- Rate is stored as `commission_rate` on the business profile (nullable integer in basis points; null = platform default of 15%). This allows per-business overrides without hardcoding.

## What Is and Isn't Monetized

| Activity | Fee |
|---|---|
| Floor plan product sale | 15% (or 10% reduced rate) |
| Add-on product sale (cost-to-build report, material list) | Same rate |
| Service sale (plan modification, custom design) | Same rate |
| Professional directory listing | Free — all approved businesses |
| Paid placement / featured slot | Flat fee (design TBD) |
| Services conducted off-platform | Not applicable |

## Business Subscription

No subscription fee for businesses at launch. Pure commission model keeps onboarding friction low. May revisit if a subscription tier (e.g., lower commission rate in exchange for a monthly fee) makes sense at scale.

## Paid Placements

Featured slots in the shop and sponsored positions in the professionals directory are a secondary revenue stream. Organic discovery is the default and must remain the primary experience. Full design is deferred post-MVP.

## Payment Infrastructure

**Stripe Connect** (marketplace model). homestead.plus collects the full purchase amount, Stripe deducts the platform application fee, and the remainder is paid out to the business's connected Stripe account. Businesses must complete Stripe Connect onboarding (bank account linkage, KYC) before receiving payouts.

**Lead-time orders** (services, custom/modified products): the full amount is pre-authorized at order placement and captured on delivery. If the order is cancelled before delivery, the authorization is released.

## Open Questions

- Conditions for the 10% reduced commission rate (volume threshold, founding business status, exclusive arrangement, or other)
- Paid placement pricing and format (fixed fee, time-based, auction)
- Whether off-platform service referrals should ever carry a fee (currently: no)
