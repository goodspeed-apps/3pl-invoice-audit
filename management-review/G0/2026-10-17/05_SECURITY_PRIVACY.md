# 05 Security, Privacy and Compliance

## Data handled

| Data | Sensitivity | Handling if built |
|---|---|---|
| 3PL invoices (line items, order and shipment IDs, SKUs, quantities, amounts) | Commercially confidential | Encrypted at rest; retention limit (e.g. 13 months, matching WareAudit) |
| Shopper PII inside invoices or order exports (name, street address, email, phone) | Personal data | **Strip at ingest, before storage.** Keep destination country and ZIP3 only, which is enough for zone checks. |
| Rate cards / MSAs | Highly confidential; may be covered by a confidentiality clause in the brand–3PL contract | Per-tenant isolation; never used across customers without contractual consent |
| 3PL API tokens (ShipBob PAT/OAuth; ShipHero admin token) | High: ShipHero tokens are admin-scope | Encrypted at rest; least-scope; prefer CSV over ShipHero tokens |

## Compliance considerations (not legal advice)

- **Confidentiality of rate cards [U]:** Merchants may be contractually barred from sharing 3PL pricing with third parties. This is a sales objection, and it also blocks the benchmarking moat (W4) unless customers explicitly consent and the data is anonymized. It needs counsel review before any benchmarking feature.
- **Privacy law:** Stripping PII at ingest keeps the product mostly outside consumer-privacy obligations. A privacy policy and DPA would still be needed for B2B customers at G3.
- **Dispute letters:** Must be framed as a draft the merchant sends, not legal advice and not sent on the merchant's behalf. WareAudit uses the same framing.
- **No regulated workflow** (no payments handled for third parties, no HIPAA or PCI scope) as long as payment gating (W2) is not built.

## Security risk at G0

Low if the product is file-based. It rises if the product collects ShipHero admin tokens.
