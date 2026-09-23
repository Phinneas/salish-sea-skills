# ESG Sustainability Reporting Layer

This package contains complementary skills for small-organization ESG and impact work:

| Skill | Role | Handoff |
|---|---|---|
| `scope-inventory` | Build a screening-level Scope 1/2/3 GHG inventory with measured/estimated/data-gap labeling. | emissions table |
| `materiality-interview` | Identify and prioritize significant impacts through structured interviews and evidence review. | `materiality_output` |
| `impact-report-ghostwriter` | Draft a proportionate, source-traceable impact report from inventory and materiality inputs. | `report_output` |
| `b-corp-gap-reader` | Audit evidence against B Impact Assessment areas and create a readiness backlog. | `bcorp_gap_output` |
| `greenwashing-check` | Audit environmental marketing claims against the FTC Green Guides substantiation standard. | per-claim risk ratings + fixes |

The reporting layer shares a GRI-informed impact-materiality frame and a B Impact Assessment lens covering Governance, Workers, Community, Environment, and Customers. The frameworks remain distinct: GRI material topics concern significant impacts, while BIA is an assessment and improvement tool whose questions and weighting depend on the organization’s track.

## Recommended chain

When GHG data is needed, start with `scope-inventory`. Then run `materiality-interview`, pass its `materiality_output` and the inventory to `impact-report-ghostwriter`, and run `b-corp-gap-reader` in parallel or afterward when certification readiness is relevant. Preserve source references and label all indicative findings.

## Test fixtures

The Green Thread Studio examples provide a complete dry-run chain — scope inventory, materiality assessment, and impact report — plus a separate B Corp gap review. They are fictional fixtures designed to test traceability, missing-data handling, framework boundaries, and small-organization proportionality. The `greenwashing-check` example is different by design: a dry run against real, publicly documented claims (the Keurig K-Cup recyclability case), since claims auditing needs real marketing language to be meaningful.

## Framework sources

- [FTC Green Guides (16 CFR Part 260)](https://www.ecfr.gov/current/title-16/chapter-I/subchapter-B/part-260)
- [GHG Protocol Corporate Accounting and Reporting Standard](https://ghgprotocol.org/corporate-standard)
- [GHG Protocol Corporate Value Chain (Scope 3) Standard](https://ghgprotocol.org/corporate-value-chain-scope-3-standard)
- [GRI 3: Material Topics 2021](https://www.globalreporting.org/pdf.ashx?id=12453)
- [GRI Standards overview](https://www.globalreporting.org/standards/)
- [B Impact Assessment overview and structure](https://bcorporation.eu/become-a-b-corp/b-impact-assessment/)
- [B Impact tool overview](https://www.bcorporation.net/programs-and-tools/b-impact/)
