# Starter GHG Inventory — Green Thread Studio

**Reporting period:** 1 January – 31 December 2025
**Organizational boundary:** Operational control — Green Thread Studio (single leased Portland, OR studio; 11 workers)
**Operational boundary:** Scope 1, Scope 2, and Scope 3 (screened)
**Prepared:** 2026-08-29 | **Status:** Screening-level, not third-party assured

*Fictional test fixture. Green Thread Studio is not a real organization; all activity data below is invented for the dry run and emission factors are illustrative EPA 2024-style values, not verified current figures.*

## Scope 1 — Direct Emissions

No Scope 1 sources identified — Green Thread Studio owns no vehicles and has no on-site fuel combustion. (Studio heat is provided by the landlord and included in the lease — see Scope 3, Category 8.)

## Scope 2 — Purchased Electricity/Heat

| Method | Activity data | Data quality | Emission factor source | tCO2e |
|---|---|---|---|---|
| Location-based | 9,800 kWh (2025 utility bills, electric heat paid by studio) | Measured | eGRID subregion NWPP (illustrative ~0.28 kg CO2e/kWh) | ~2.7 |
| Market-based | — | Not available | No supplier-specific rate, green tariff, or REC documentation provided | — |

## Scope 3 — Value Chain (screened)

**Two plausibly material categories are not quantified for lack of data (Categories 1 and 5). The total below is therefore a partial total, not a complete footprint.**

| Category | Status | Data quality | Method | tCO2e |
|---|---|---|---|---|
| 1. Purchased goods & services | Included — not quantified (data gap) | — | No spend-by-category data; supplier list exists without spend detail | — |
| 2. Capital goods | Screened out — not applicable | — | No significant 2025 capital purchases | — |
| 3. Fuel- and energy-related activities | Included — estimated | Estimated | ~3% uplift on Scope 1+2 activity | ~0.1 |
| 4. Upstream transportation & distribution | Screened out — de minimis | — | Inbound freight is included in supplier pricing; no data and small relative to Cat 1 gap | — |
| 5. Waste generated in operations | Included — not quantified (data gap) | — | No waste-weight baseline (solvent/dye waste streams undocumented) | — |
| 6. Business travel | Included — estimated | Estimated | ~2,900 reimbursed personal-vehicle miles for supply pickup/client visits (IRS-rate reimbursement); activity-based, passenger-car factor | ~0.9 |
| 7. Employee commuting | Included — estimated | Estimated | 11 workers × ~7-mile round trip × ~230 operating days (46 operating weeks × 5 days); mostly personal vehicle per staff survey | ~5.3 |
| 8. Upstream leased assets | Included — estimated | Estimated | Landlord-provided gas heat for leased studio, ~300 therms/yr benchmark estimate for small commercial space | ~1.6 |
| 9–13. Downstream categories | Screened out — not applicable | — | Service business; no sold physical products, no downstream leased assets | — |
| 14. Franchises | Screened out — not applicable | — | No franchises | — |
| 15. Investments | Screened out — not applicable | — | No investment portfolio | — |

## Total

| Scope | tCO2e | % of quantified total |
|---|---|---|
| Scope 1 | 0 | 0% |
| Scope 2 (location-based) | ~2.7 | ~26% |
| Scope 3 (quantified categories only) | ~7.9 | ~74% |
| **Total (PARTIAL — excludes material but unquantified Categories 1 and 5)** | **~10.6** | **100%** |

## Data quality summary

- **Measured:** Scope 2 electricity (utility bills, kWh).
- **Estimated:** Category 3 (uplift method), Category 6 (reimbursed-mileage activity data), Category 7 (commute-pattern survey × operating days), Category 8 (benchmark therms for leased-space heating).
- **Included but not quantified (data gap):** Category 1 (purchased goods & services — likely material; no spend-by-category data) and Category 5 (waste — likely material given solvent/dye use; no waste baseline). These are data gaps, not immateriality findings.
- **Screened out — not applicable:** Categories 2, 4, 9–15 (reasons in table).

## Limitations

This is a screening-level starter inventory: not third-party verified, not assured, and not a substitute for a formal CDP/SBTi or regulatory-grade inventory if one is required. The total is partial — it excludes two plausibly material Scope 3 categories for lack of data. A formal inventory would need spend-by-category purchasing data, a waste baseline (weighing or hauler records), verified current EPA/eGRID factors for the reporting year, fuller Scope 3 category coverage, and typically third-party assurance. Commuting and Category 8 figures are estimates with wide uncertainty bands and should be replaced with surveyed/metered data before any public use.

## Next steps

- To make public claims based on this inventory, run them through `greenwashing-check` first.
- For a materiality-driven narrative around this data, use `materiality-interview` (the Green Thread materiality dry run consumes an inventory of this shape).

*Output saved per skill convention as `scope-inventory-green-thread-studio-2026-08-29.md` in a real run; renamed `scope-inventory.md` here for the example folder.*
