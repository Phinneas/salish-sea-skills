# Scope Inventory

**What:** Builds a starter Scope 1/2/3 greenhouse gas inventory for a small organization, with every figure labeled measured, estimated, or screened out.
**When:** A funder, client, board, or B Corp assessment asks for your carbon footprint and you've never measured one.
**Output:** A screening-level GHG inventory — Scope 1/2 tables, a materiality-screened Scope 3 table, a total, and a data-quality/limitations section.

## Use Cases

- A grant application or corporate customer's supply-chain questionnaire asks for your organization's GHG emissions and you're starting from zero
- Your board wants to know the org's carbon footprint before setting a reduction goal
- You're prepping for a B Corp assessment or a CDP/SBTi submission and need a defensible starting inventory
- You want to know whether your operations even have material Scope 1 emissions before assuming you need a complicated inventory process

## The Skill

This skill grounds every number in the GHG Protocol Corporate Accounting
and Reporting Standard (Scope 1/2) and the Corporate Value Chain (Scope 3)
Standard — the same framework CDP, SBTi, and most corporate GHG disclosure
programs are built on. Rather than trying to calculate all 15 Scope 3
categories from day one, it screens all 15 for relevance first and
calculates only the ones that are actually material for a small
organization (usually purchased goods/services, waste, business travel,
and commuting), marking the rest "screened out — not applicable" with a
reason instead of silently dropping them.

Every line in the output is labeled Measured, Estimated, or Screened out
— this skill will never hand you a precise-looking number built on a
guess without saying so.

Shares its research grounding with `greenwashing-check` (same build
session) but runs independently. If you plan to make public claims based
on this inventory, run those claims through `greenwashing-check` before
publishing them.

## Prerequisites

- No connectors required — runs on Claude alone.
- You'll be asked for basic org facts (size, facilities, vehicles) and
  whatever activity data you actually have (utility bills, mileage,
  travel, waste). Partial data is fine — the skill uses a disclosed
  estimation fallback for what you don't have, rather than blocking.

## Getting Started

```
Build a starter GHG inventory for [org name]
```

Claude will:
1. Confirm your organizational and operational boundary
2. Screen all 15 Scope 3 categories and tell you which are actually material for your org
3. Ask for the activity data you have for each material category
4. Apply the right emission factors (activity-based where you have data, spend-based as a disclosed fallback where you don't)
5. Hand back a scope-by-scope table, a total, and a data-quality/limitations section

## Time Investment

- **First run:** 30-60 minutes (mostly gathering bills/data you have on hand)
- **Iterations:** a few minutes to update with a new period's data

## Next Steps

- Run any public claims built on this inventory through `greenwashing-check`
- Feed this data into `materiality-interview` for a fuller ESG narrative

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/esg-sustainability/scope-inventory)

## License

MIT. Use freely. Attribute appreciated.
