# 06 Unit Economics and Cost Assumptions

All figures are estimates and are pre-revenue.

## Fixed infrastructure (pre-revenue)

| Item | Est. $/mo |
|---|---|
| Vercel Pro | 20 |
| Managed Postgres (Neon/Supabase base) | 0–25 |
| Sentry, PostHog, Resend (free tiers) | 0 |
| Object storage | <5 |
| Domain (annualized) | ~1–2 |
| **Total** | **≈ $25–55/mo**, within the $100/product cap; no vendor over $50 |

## Variable cost per active customer

- **Compute and storage:** under $1/mo. Invoices are tens of thousands of rows per month.
- **ShipBob API:** free.
- **AI:** $0 at MSP. If PDF extraction were added, the estimate is about $0.05–0.50 per invoice, depending on page count.
- **Stripe:** about 2.9% + $0.30.

## Margin

- At ~$299 ARPU, technical COGS is under 1% of revenue, and technical gross margin is above 95%.
- **The real cost driver is labor:**
  - 1–3 h of rate-card setup per new customer, if done for them;
  - 2–6 h per new 3PL format;
  - finding-explanation support.
- At 1–2 h per customer per month of founder time early on, the business has fewer than 150 revenue dollars per founder hour, which is weak for this portfolio's Return on Founder Attention goal.

## Revenue context

The brief's planning figures (34, 84 and 168 customers for $10K, $25K and $50K MRR) assume share taken from 3–4 entrants with identical offers and a head start. Claude has no technical basis to assume we would reach those numbers faster than competitors.
