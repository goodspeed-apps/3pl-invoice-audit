# 09 Risk Register

Likelihood (L) and Impact (I) are rated H/M/L.

| # | Risk | L | I | Notes / mitigation |
|---|---|---|---|---|
| R1 | No differentiated wedge; MSP is a WareAudit clone | H | H | Confirmed at G0 (see 11). No technical mitigation found. |
| R2 | Competitive velocity: 4 entrants in about 60 days plus an enterprise launch; features copied within weeks | H | H | No moat available at launch. |
| R3 | Demand unproven: no entrant shows real recoveries; error rates are vendor claims | M | H | Validation needed outside engineering, such as interviews or competitor traction signals. |
| R4 | Price compression: identical ladders and a $49 indie entrant | M | H | Brief forbids competing on price. |
| R5 | Value decay: the first audit fixes errors, the 3PL corrects, findings fall, the customer churns | M | H | Structural to post-invoice audit. Partly offset by drift monitoring, which is too weak to anchor a subscription [I]. |
| R6 | Underbilling: audits find money owed to the 3PL (3PL vendors claim 5–10% under-capture) | M | M | Damages the pitch and the brand–3PL relationship. Must be reported honestly. |
| R7 | Data-access dependency on ShipBob API terms; ShipBob could ship its own audit view | L–M | H | The only clean API is a single point of failure. |
| R8 | ShipHero access needs admin tokens | H | M | Security and sales objection. Use CSV instead. |
| R9 | Rate-card confidentiality clauses block sharing or benchmarking | M | M | [U] Needs counsel. Blocks the W4 moat. |
| R10 | Support scales with 3PL × contract diversity | M | M | See 07. Hurts Return on Founder Attention. |
| R11 | Format drift breaks audits silently | M | M | Needs schema-change detection. Ongoing cost. |
| R12 | Opportunity cost: founder attention diverted from the other G0 candidates | H | M | Strongest argument for KILL over HOLD. |

## Important unknowns (unresolved at G0)

1. Do any self-serve competitors have paying customers? Unknown; no public traction found.
2. Real, independent 3PL billing error prevalence and recovery value per customer.
3. Will partner firms (bookkeepers, fractional COOs, audit firms) adopt and resell a tool? This is the only plausible wedge (W6).
4. Are 3PL rate cards typically under NDA such that sharing them with a SaaS vendor is restricted?
5. How often do 3PL CSV export formats change?
