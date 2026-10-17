# 02 Proposed Technical Approach (if authorized; not recommended)

This section shows feasibility and cost. It is not a build plan. Its main conclusion: the build is easy, so ease of build gives no protection against competitors.

## 1. Approach

- Portfolio default stack:
  - Next.js and TypeScript (strict), pnpm
  - Postgres and Prisma, on Neon or Supabase
  - Vercel, Stripe, Sentry, Resend, PostHog
  - Managed object storage for uploaded files
- One monolith. No queue at MSP; audits of up to about 70k lines run in a single serverless invocation, or in a scheduled function for API pulls.
- The audit engine is a pure, deterministic TypeScript module (rate rules in, findings out). It is unit-testable and has no AI in the money path.

## 2. Minimum technically viable workflow (file-based)

1. The customer uploads their rate card. MSP option: a structured form, or a spreadsheet template we provide. The customer enters the rates, as WareAudit does.
2. The customer uploads 1–3 invoice CSVs. The system detects or selects a known 3PL template; unknown formats go to a column-mapping step.
3. Charge lines are mapped to normalized charge categories. Unmapped charge codes are flagged for review.
4. The engine runs checks and produces findings: expected, billed, difference, source line, and dispute-by date.
5. The customer downloads a dispute letter and evidence CSV, and marks each finding disputed, credited or declined. Later invoices are auto-matched against open credits.

## 3. Integrations and external dependencies

| Dependency | Access | Limits and risks |
|---|---|---|
| ShipBob Billing API | OAuth/PAT with `billing_read`; `/invoices`, `/transactions:query`, `/transaction-fees` [V] | Fees can post up to 6h after the label [V]. API versioning (2026-07) means periodic migrations. Already used by two competitors. |
| ShipHero GraphQL | Needs a full or admin user token; billing queries were "not available for third-party developers" (Jan 2025) [V] | Asking customers for admin tokens is a security and sales objection. Line-item bill data is incomplete [V]. Prefer CSV. |
| ShipMonk, Flexport, Red Stag, Extensiv-based 3PLs | Portal CSV or PDF only [V/U] | Format drift without notice. Each needs a template. |
| PDF extraction (LLM) | Would need an AI provider | Excluded at MSP (brief: not a wedge; adds cost and hallucination risk). |
| Shopify Admin API (optional ops data) | OAuth app | App review and maintenance; adds PII exposure. Defer. |

**Lock-in and strategic dependency.**
- A ShipBob-centric product depends on one 3PL's API terms. ShipBob could launch its own billing-audit view, or restrict billing data, which would remove the value overnight [I].
- 3PLs have no incentive to make their bills easier to audit.

## 4. Generic rate-rule model

About nine primitives cover the bulk of 3PL rate cards [I, based on public rate cards: WareAudit docs, Amazon MCF and WFS rate cards cited by Auditario]:

1. **Per-unit flat:** pick fee per order or unit, label fee
2. **Tiered by volume:** price breaks by monthly orders or units
3. **Per-unit with min/max:** packaging, receiving per carton
4. **Time-based:** receiving or labor per hour, with free allowances
5. **Periodic storage:** per bin, shelf, pallet or cubic foot, per period, optional long-term tiers
6. **Monthly minimum:** a floor on total fulfillment spend
7. **Percentage surcharge:** fuel, card fees, peak surcharge, within effective date windows
8. **Pass-through with markup cap:** postage, materials
9. **Effective dating and precedence:** rate-card versions plus amendments

The per-3PL **charge vocabulary map** links the 3PL's charge code (e.g. "B2C Pick Fee – Addl Unit") to a normalized category and rule. This is configuration, not code, but it needs a human to interpret it the first time.

The residual that can never be automated: special projects, ad-hoc labor, negotiated one-offs. These are always flagged for manual review.

## 5. Check matrix by data needed

| Check | Invoice only | + Rate card | + Ops/order data |
|---|---|---|---|
| Arithmetic (qty × rate = amount) | ✓ | | |
| Duplicate lines / same reference billed twice | ✓ | | |
| New or unseen charge type | ✓ (vs history) | | |
| Rate drift / fee spikes vs prior invoices | ✓ | | |
| Promised-credit follow-up | ✓ (+ dispute log) | | |
| Billed rate vs contracted rate | | ✓ | |
| Uncontracted fee / surcharge | | ✓ | |
| Monthly minimum applied correctly | | ✓ | |
| Peak or surcharge outside effective window | | ✓ | |
| Free allowance (e.g. receiving hours) not credited | | ✓ | |
| Tier applied correctly | | ✓ (+ volume from invoice) | |
| Picks/units billed vs order lines | | | ✓ |
| Cancelled orders billed | | | ✓ |
| Storage quantity vs inventory snapshots | | | ✓ |
| Receiving units vs inbound receipts | | | ✓ |
| Returns billed vs returns processed | | | ✓ |
| Label zone/weight overcharge | Partly (if the invoice carries zone and weight) | ✓ | ✓ otherwise |

## 6. Estimated implementation complexity (Claude build effort)

| Component | Complexity | Estimate |
|---|---|---|
| Auth, orgs, billing, base app (portfolio template) | Low | 3–4 days |
| Rate-card entry (form/template) and versioning | Medium | 3–5 days |
| CSV ingest, column mapping, template registry | Medium | 4–6 days |
| Charge vocabulary mapping and review UI | Medium | 3–4 days |
| Rule engine and the invoice + rate-card checks | Medium | 5–7 days |
| Findings, dispute letter, evidence export, credit tracker | Low–Medium | 3–5 days |
| ShipBob API adapter | Low–Medium | 3–5 days |
| Ops-data reconciliation checks | Medium–High | 5–10 days (defer) |
| PDF/LLM extraction | High (accuracy) | Excluded |

Total file-based MSP plus ShipBob is about 3–5 weeks. This is low and is not a reason to proceed.

## 7. Recommended simplifications (only if management overrides)

- File-based only at launch. Add the ShipBob API only after customers pull for it.
- Customer-entered rate cards via template. No contract parsing.
- No PDF, no AI, no Shopify app, no auto-sending of disputes.
- One 3PL template per paying customer, built from their real file.
