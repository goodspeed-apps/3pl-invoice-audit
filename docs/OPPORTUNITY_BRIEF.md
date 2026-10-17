# Opportunity Brief — 3PL Invoice Contract Audit

**Date:** 2026-10-16  
**Business Manager Disposition:** CONDITIONAL G0 — HIGH COMPETITIVE RISK  
**Current Rank:** #3  
**Working Product Name:** Fulfillment Audit (working name only)

## 1. Target Buyer

Primary ICP:

- U.S. Shopify / DTC / ecommerce brands using an external 3PL
- Initial target roughly 500–15,000 orders per month
- Prefer brands large enough that billing errors matter but small enough not to have enterprise freight-audit/AP teams
- Initial technical focus could be brands using common 3PLs with exportable billing data

Primary buyers:

- COO
- Head / Director of Operations
- Supply Chain leader
- CFO / Finance leader
- Founder at smaller brands

## 2. Core Recurring Problem

3PL bills can contain thousands of line items covering:

- pick/pack
- storage
- receiving
- returns
- materials
- accessorials
- minimums
- special-project fees
- shipping-related pass-through charges
- surcharges

The customer has a contracted rate card plus operational data.

The economically important question is:

> Did our 3PL bill us according to the contract and what actually happened?

## 3. Current Workaround

Typical:

- trust the invoice total
- spot check
- spreadsheet audit
- manual comparison to rate card
- outsource to an audit/recovery firm
- internal script/tool at larger brands

## 4. Economic Consequence

Potential:

- recurring overcharges
- rate drift
- uncontracted fees
- duplicate billing
- wrong quantities
- storage errors
- missed credits
- failure to dispute inside contractual windows
- finance/operations labor

The value proposition is direct cost recovery / cost control.

## 5. Proposed Value Proposition

> Every 3PL invoice checked against your rates and operations before the dispute window closes.

Output must be evidence-backed and dispute-ready.

## 6. Minimum Sellable Product Thesis

Inputs:

- 3PL rate card / contract
- 3PL invoice export
- optional order/activity export

Checks may include:

- billed rate vs contracted rate
- uncontracted fee
- duplicate charge
- quantity mismatch
- minimum/threshold rule
- rate drift
- promised-credit follow-up
- storage rule check where data supports it
- unmapped charge requiring review

Output:

- finding
- expected amount
- billed amount
- difference
- supporting source
- dispute deadline if known
- draft dispute text / evidence packet

Core financial checks should be deterministic.

## 7. Market Evidence

ShipBob's 2026 fulfillment report surveyed 416 ecommerce leaders and reported that 84% use third-party fulfillment for at least some orders.

ShipBob's public case-study directory alone exposes many identifiable DTC brands using outsourced fulfillment.

Recent ecommerce/3PL discussions continue to describe manual invoice reconciliation and specific errors found through line-by-line review.

## 8. Competitive Landscape

### Critical Phase 3 finding

This is now the highest-velocity competitive market of the three finalists.

WareAudit currently offers almost the exact proposed product:

- ShipBob / ShipHero connections
- CSV path for other 3PLs
- deterministic audit checks
- evidence-backed findings
- dispute letters
- promised-credit tracking
- free audit
- $149 / $299 / $599 monthly plans
- $299 one-off audit
- optional dispute-support subscription

Auditario is also emerging with an evidence-first audit approach.

Additional developers are publicly piloting similar tools.

This is serious overlap, not adjacent competition.

## 9. Differentiation Requirement

Do not proceed to G1 unless we can identify a concrete wedge beyond:

- prettier UX
- AI parsing
- lower price
- generic CSV support
- free first audit
- ShipBob/ShipHero integrations

Possible areas worth technical/business investigation:

1. Specific underserved 3PL/provider ecosystem not well covered.
2. Pre-payment AP control rather than post-invoice recovery.
3. Specialized audit rules for a high-value ecommerce vertical.
4. Cross-3PL benchmarking / cost allocation unavailable to incumbents.
5. Contract-version + operational-event reconciliation materially deeper than current tools.
6. Embedded workflow through an ecommerce operations/accounting partner channel.

At present, no differentiation thesis is strong enough to authorize G1.

## 10. Customer Acquisition Hypothesis

### Customer #1

Prospect sources:

- public ShipBob customer stories
- Shopify brands known to use external fulfillment
- ecommerce operator communities
- DTC brand directories
- fractional COO / supply-chain consultants

Entry offer:

A free recent-invoice audit is economically compelling, but competitors already use the exact same entry motion.

Therefore this is not itself differentiation.

### Customer #10

Potential channels:

- fractional COO / operations consultants
- ecommerce finance firms
- Shopify agencies
- fulfillment consultants
- provider-specific educational content

### Customer #100

Potential:

- Shopify ecosystem
- ecommerce operations partnerships
- SEO around specific 3PL invoice problems
- integrations
- consultant/referral channels

## 11. First-100-Prospect Feasibility

STRONG PASS.

Public 3PL case studies and ecommerce ecosystems make target brands unusually easy to identify.

Distribution access is not the main concern.

Differentiation and competitive velocity are.

## 12. Pricing Hypothesis

Current category benchmark is already highly transparent.

Working range only:

- $149–$199/month small
- $299–$399/month growth
- $599+ scale

A competitor already occupies essentially this exact ladder.

Do not compete primarily on price.

## 13. Planning Economics

At ~$299 blended ARPU:

- $10K MRR: ~34 customers
- $25K MRR: ~84 customers
- $50K MRR: ~168 customers

Economics are attractive if support is low.

## 14. Expected Sales Friction

Low to medium.

Positive:

- highly understandable ROI
- buyer can often act without enterprise procurement
- CSV can avoid integration
- self-service is plausible

Concerns:

- rate cards/contracts
- order/customer data
- API-token security
- provider-specific data quality

PII should be minimized or stripped wherever possible.

## 15. Founder-Attention Risk

Moderate.

Main risk is maintaining audit logic for many 3PL formats and contract structures.

Provider-specific support questions could become significant.

## 16. Defensibility Concern

Current feature-level moat is weak.

A durable business would need accumulated:

- provider mappings
- contract/rate-card rule models
- invoice schemas
- operational-data mappings
- historical billing patterns
- credit/dispute behavior
- partner distribution

The first version alone is highly cloneable.

## 17. Kill / Pivot Conditions

Do not advance to G1 if:

1. We cannot articulate a specific differentiated segment/channel/product wedge.
2. Technical analysis shows our MSP is materially equivalent to WareAudit.
3. New-provider support requires custom development for every customer.
4. Rate cards require constant human interpretation.
5. We would need to compete primarily through lower pricing.
6. Competitive velocity continues to increase without an identifiable moat.
7. Steady-state support scales with number of 3PLs rather than number of standardized integrations.

## 18. Questions for Claude at G0

This G0 is partly a red-team exercise.

Claude should specifically answer:

1. Is there a technically meaningful opportunity that is NOT simply a WareAudit clone?
2. Which 3PL/provider/data format appears underserved but technically tractable?
3. Can a generic configurable rate-rule model support multiple 3PLs without custom coding?
4. Which checks can run from invoice + rate card alone?
5. Which checks require operational/order data?
6. What PII can be stripped before storage?
7. What would it take to build provider adapters efficiently?
8. Could the product operate fully file-based for initial customers?
9. What technical assets could compound into a moat?
10. Estimate support/maintenance burden as provider count grows.
11. If no strong differentiated technical wedge exists, recommend HOLD or KILL rather than forcing a build.
12. Recommend GO / GO WITH CHANGES / HOLD / PIVOT / KILL for G1.

## 19. Business Manager G0 Instruction

G0 only.

Do not write production application code.

Create the private product repository, store this Opportunity Brief, perform technical/business-feasibility red teaming required by the governance documents, produce the G0 management-review package, and stop for management approval.

This candidate is explicitly conditional. A technically easy build is not sufficient reason to advance.
