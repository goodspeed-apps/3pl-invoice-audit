# 01 Scope and Status

## Status

- G0 feasibility and red-team analysis is complete.
- No application code exists, and none is proposed until management decides.
- The private repo `goodspeed-apps/3pl-invoice-audit` holds only the brief and this package.

## What was done

1. Read the canonical governance set and the Opportunity Brief.
2. Researched the competitive set and 3PL data access, and verified the load-bearing claims at source on 2026-10-17: WareAudit features and pricing, and ShipBob's ToS dispute window and payment collection.
3. Tested all six candidate wedges from the brief (see [11](11_COMPETITIVE_AND_WEDGE_ANALYSIS.md)).
4. Produced the technical feasibility assessment that would apply if the product proceeded (see [02](02_ARCHITECTURE.md)). It exists so management can see the build is easy, and that ease is not the constraint.

## Answers to the brief's section 18 questions

| # | Question | Short answer | Detail |
|---|---|---|---|
| 1 | A technically meaningful opportunity that is not a WareAudit clone? | **No.** | 11 §3–4 |
| 2 | Underserved but tractable 3PL or format? | Regional 3PLs on Extensiv or Packiyo, plus Flexport and ShipMonk CSVs, are underserved by APIs but tractable via CSV. WareAudit already accepts CSV from any 3PL, so this is not a gap. | 11 W1, 02 §3 |
| 3 | Can a generic configurable rate model cover multiple 3PLs without custom code? | **Yes, for about 85–90% of charge lines** [estimate], using about 9 rule primitives plus a per-3PL charge-code mapping. The mapping is configuration, but it needs human judgment for each new 3PL. The remainder (special projects, ad-hoc fees) always goes to manual review. | 02 §4 |
| 4 | Checks from invoice + rate card alone? | Rate match, arithmetic, uncontracted fee, duplicates, minimums, peak windows, surcharge recurrence, rate drift, free allowances, credit follow-up. | 02 §5 |
| 5 | Checks needing ops or order data? | Quantity reconciliation (picks, receiving, returns), billed-but-cancelled orders, storage quantity vs inventory, packaging per order, label zone/weight when the invoice lacks package data. | 02 §5 |
| 6 | PII to strip? | Shopper name, street address, email and phone, at ingest. Keep order and shipment IDs, SKU, quantities, weights and dimensions, destination country and ZIP3. | 05 |
| 7 | Efficient provider adapters? | Two adapter types. **API:** ShipBob only, about 3–5 days of effort. **CSV template:** a declarative column map plus a charge vocabulary, a few hours per 3PL once a real sample exists. Avoid PDF at MSP. | 02 §3 |
| 8 | Fully file-based for initial customers? | **Yes.** Competitors already run free audits from CSV alone. | 02 §2 |
| 9 | Technical assets that could compound? | Cross-3PL charge-code dictionary, rate-card corpus for benchmarking, and dispute-outcome history by 3PL and charge type. All require scale that incumbents are already ahead on. | 11 W4, 09 |
| 10 | Support burden as provider count grows? | Grows roughly linearly with distinct 3PL formats and contract structures until the dictionary saturates. About 2–6 founder hours per new 3PL format, and 1–3 hours per done-for-you rate-card setup. | 07 |
| 11 | No wedge → HOLD or KILL? | Applied. Recommendation is **KILL**. | 00, 10 |
| 12 | Recommendation for G1 | **KILL** (alternative: HOLD with triggers). | 00, 10 |

## Product-specific overrides (Technical Standard §31)

None proposed. If the product ever proceeded, the default stack fits without exception.
