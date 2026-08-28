# Budget Narrative Writer

**What:** Turns a line-item budget into a funder-ready narrative — every cost justified, indirect costs correctly calculated, cost-share computed if required.
**When:** You have (or need to build) a budget and need the prose justification reviewers expect as a separate attachment from the budget form itself.
**Output:** A category-by-category budget narrative, an MTDC-based indirect cost calculation, and a cross-check confirming the budget actually funds the activities the program describes.

## Use Cases

- A NOFO requires a budget narrative or budget justification as a distinct attachment from the SF-424A form
- You have rough cost estimates and need them turned into defensible, activity-linked line items
- You're not sure whether to use a negotiated indirect cost rate or the de minimis rate, or whether your MTDC calculation is right
- A reviewer or program officer flagged that your budget and your program description don't obviously match, and you need to find and fix the gap

## The Skill

This skill writes budget narrative against the standard federal SF-424A
categories (Personnel, Fringe Benefits, Travel, Equipment, Supplies,
Contractual, Construction, Other), calculates indirect costs correctly
under 2 CFR 200.414 — including the Modified Total Direct Costs (MTDC)
base and its specific exclusions (equipment, the portion of subawards over
$25,000, and several others) — and then cross-checks every funded line
against the program's logic model in both directions: activities with no
funding behind them, and funded lines with no activity behind them. That
cross-check is the part most budget narratives skip, and it's usually
where reviewers actually lose confidence in a budget.

**Fifth skill in the grant-writing chain.** Typically follows
`logic-model-builder` — the budget should visibly fund exactly what that
model claims it funds.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply the budget figures (line items if you have them; rough
  estimates or a program description if you don't — Claude will help
  build line items from real figures, not invented ones).
- You'll need to know whether your org has a Negotiated Indirect Cost Rate
  Agreement (NICRA) or plans to use the de minimis rate — if you're not
  sure, say so and Claude will ask what it needs to determine this rather
  than assuming a default.
- Helpful: `logic-model-builder`'s output, so the cross-check step has
  something real to check against.

## Getting Started

```
Write a budget narrative for [program], budget: [figures or description]
```

Claude will:
1. Confirm or help build the line-item budget
2. Determine the indirect cost basis (NICRA or de minimis) and calculate
   MTDC correctly, excluding equipment, capital costs, and other excluded
   items
3. Write category-by-category narrative, naming the specific activity each
   line funds
4. Calculate cost-share/match if the opportunity requires it
5. Cross-check every budget line against the program's activities in both
   directions and flag any mismatch

## Time Investment

- **First run:** 30-60 minutes, more if line items need to be built from scratch
- **Iterations:** 15-20 minutes to revise once figures or activities change

## Next Steps

- If the cross-check flags a gap, revisit `logic-model-builder`'s output or
  the budget itself before submitting — don't let a flagged mismatch ship
- Pair with `letter-of-support-kit` if any contractual or subaward line
  involves a named partner organization

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/budget-narrative-writer)

## License

MIT. Use freely. Attribute appreciated.
