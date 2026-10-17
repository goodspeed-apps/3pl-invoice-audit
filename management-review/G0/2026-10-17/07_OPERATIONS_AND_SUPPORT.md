# 07 Operations, Support and Maintenance Burden

## Steady-state maintenance drivers

1. **3PL format drift.** CSV exports change columns or charge names without notice, which breaks mapping silently unless monitored. Estimate: one template fix per active 3PL format every 3–6 months [I].
2. **New 3PL onboarding.** Each new 3PL needs a template and charge vocabulary: about 2–6 founder or Claude hours.
3. **Rate-card interpretation.** Contracts are prose with exceptions. The first setup per customer takes 1–3 h if done for them. Amendments need re-entry.
4. **Finding disputes.** "Is this really an error?" questions are the dominant support topic [I]. They are high-touch and need contract judgment.
5. **ShipBob API versioning.** Minor periodic migrations.

## Scaling estimate

| Distinct 3PL formats | Est. founder/support hours per month |
|---|---|
| 1–3 (ShipBob-heavy) | 3–6 |
| 10 | 10–20 |
| 25+ | 20–40 until the charge dictionary saturates |

Burden scales with **3PL diversity × contract diversity**, not customer count. That partially triggers kill condition 7.

## Manual steps that would remain

Rate-card entry (unless the customer does it), mapping of unknown charge codes, and the special-project fee review queue.
