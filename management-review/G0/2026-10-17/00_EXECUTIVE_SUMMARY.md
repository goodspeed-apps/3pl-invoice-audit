# 00 Executive Summary: 3PL Invoice Audit, G0

**Prepared by:** Claude (development organization), 2026-10-17
**Input:** Opportunity Brief dated 2026-10-16 ([docs/OPPORTUNITY_BRIEF.md](../../../docs/OPPORTUNITY_BRIEF.md)), Business Manager disposition "CONDITIONAL G0, HIGH COMPETITIVE RISK"
**Scope of this gate:** feasibility and red-team only. No application code was written.

## Current Gate

G0 Opportunity Feasibility.

## Overall Status

**RED.** Do not proceed to G1. The product is easy to build, but nothing technical sets it apart from tools that already exist.

## Recommendation

**KILL** the opportunity as briefed.

If management wants to keep an option open, the acceptable alternative is a **HOLD** with no engineering spend and explicit reopen triggers (see [10_DECISIONS_REQUIRED.md](10_DECISIONS_REQUIRED.md)). Claude does not recommend GO, GO WITH CHANGES, or a technical PIVOT.

## What Management Needs to Know

1. **We found no technically meaningful wedge versus WareAudit.** All six candidate wedges from the brief were tested (detail in [11_COMPETITIVE_AND_WEDGE_ANALYSIS.md](11_COMPETITIVE_AND_WEDGE_ANALYSIS.md)). Each one is either something an incumbent already does or has announced, a configuration change an incumbent could copy in days or weeks, structurally blocked by how the largest 3PL collects payment, or a data-network effect that only appears after hundreds of customers. The two that remain plausible, partner distribution and cross-customer benchmarks, are distribution or scale bets. They are not technical advantages.
2. **WareAudit already covers our proposed MSP.** Verified on wareaudit.com, 2026-10-17: ShipBob API, ShipHero API, CSV as "a first-class path," 14 deterministic checks, dispute letters, promised-credit tracking, dispute-by date, PII stripped at ingest, and the $149/$299/$599 price ladder. Our MSP as written would be a clone. That triggers the brief's kill conditions 1 and 2.
3. **Competitive velocity is rising, not stabilizing.** In roughly 60 days the space has gained WareAudit (live, around August 2026), Auditario (prelaunch, same $150/$300/$600 ladder), billsharp (live on ShipBob), at least one public indie repo, and FreightOptics, which launched an enterprise 3PL audit product on 2026-09-30. Contingency-fee audit services also exist. That triggers kill condition 6.
4. **Data access is the real technical constraint, and the easy part is already taken.** ShipBob is the only 3PL with a clean merchant billing API, and WareAudit and billsharp already use it. ShipHero billing data needs an admin-level token and has gaps. ShipMonk, Flexport, Extensiv-based regional 3PLs and others send CSV or PDF files only. Any "underserved 3PL" angle therefore becomes CSV mapping, which WareAudit already offers, or PDF/AI extraction, which the brief excludes as a wedge and Auditario and FreightOptics already target.
5. **Demand is unproven for every self-serve player.** No competitor publishes real customer recoveries. WareAudit's sample report uses a generated corpus. All error-rate figures (3–15%) are vendor marketing. The crowded supply side is not evidence of demand.
6. **There is a structural retention risk.** A first audit finds old errors, and the 3PL then corrects its billing. After that, findings and perceived value decline. 3PL-side vendors also claim 3PLs underbill 5–10% of billables, so an honest audit can find money owed to the 3PL. Both effects work against a recurring subscription.
7. **The economics are fine but irrelevant.** Infrastructure would cost about $25–60/mo fixed, with technical gross margin above 95%. The real cost is founder and support time spent encoding rate cards and mapping 3PL charge vocabularies. That cost grows with the number of distinct 3PLs and contracts, which is kill condition 7.

## Decisions Required

1. Accept KILL, choose HOLD with reopen triggers, or override.
2. If HOLD: confirm that no engineering spend is authorized and approve the reopen triggers.

Details in [10_DECISIONS_REQUIRED.md](10_DECISIONS_REQUIRED.md).

## Business Impact

| Area | Assessment |
|---|---|
| Time to launch | Short. A file-based MSP takes about 3–5 weeks of build effort. This is not a reason to proceed. |
| Revenue potential | Capped by direct competitors already at the same price points with an earlier start, and by unproven demand. |
| Pricing | No room to differentiate. The category ladder is public and identical across two competitors. Competing on price is kill condition 5. |
| Gross margin | Technical margin above 95%. Real margin depends on support labor (see 07). |
| Support burden | Moderate to high, driven by rate-card interpretation and per-3PL charge mapping. It grows with 3PL diversity. |
| Founder attention | High relative to revenue during the first 6–12 months, because each new customer can bring a new 3PL format and a new contract structure. |
| Scalability | Technically trivial. Operationally limited by the long tail of 3PL formats. |
| Risk | High competitive risk, high demand-validation risk, and moderate confidentiality risk for rate cards. Technical delivery risk is low. |

## Claude Recommendation and Reasons

**KILL.** The brief set a clear bar: proceed only with a concrete wedge beyond UX, AI parsing, price, CSV support, free audits and ShipBob/ShipHero integrations. Engineering analysis found none that is technical, durable and available at launch. Building anyway would mean entering a contested, unproven niche as the fourth or fifth near-identical entrant, with a product competitors can match within weeks of seeing it.

- **Stop:** this product as briefed.
- **Cut:** nothing further, since no build is proposed.
- **Delay:** any 3PL-related work until there is independent evidence of paying demand, such as a competitor showing traction, or a partner who commits to distributing it.
- **Redirect:** founder attention and build capacity to the other G0 candidates (AuditReady, Rebate Control), subject to their own packages.
