# B Corp Gap Reader

**What:** Audits an organization's policies, practices, and evidence against the B Impact Assessment's five Impact Areas and produces a prioritized certification-readiness backlog.
**When:** You're preparing for a B Impact Assessment and want to know what's actually evidenced — and what's missing — before touching the live assessment.
**Output:** An area-by-area gap table, evidence request list, 30/90/180-day action backlog, and a machine-readable `bcorp_gap_output` block.

## Use Cases

- Pre-assessment readiness check before starting the BIA
- Translating an existing ESG inventory into B Lab-style categories
- Building a governance/workers/community/environment/customer improvement backlog
- Sanity-checking which claims are evidence-ready and which are self-reported only

## The Skill

Uses the BIA as a structured gap-analysis lens across Governance, Workers, Community, Environment, and Customers — and keeps the crucial distinction between day-to-day **operations** and **Impact Business Models** that the assessment itself makes. Every practice gets a readiness status (`met`, `partially met`, `not evidenced`, `not applicable`, `unknown`) and gaps are prioritized into a 30/90/180-day backlog with owners and success measures.

**Third skill in the ESG reporting layer.** It runs standalone, or alongside `materiality-interview` → `impact-report-ghostwriter` when certification readiness is part of the goal. It never estimates an official score: without a current BIA track and assessment export, all findings are labeled `indicative`.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: entity profile, legal structure, size/sector/geography, policies, practices, metrics, impact model, and evidence links. WebFetch/WebSearch is optional for checking the current B Lab process and track.

## Getting Started

```
Use the b-corp-gap-reader methodology to review our readiness: [org profile + policies + evidence]
```

Claude will:
1. Define the review scope and status (and what only B Lab can decide)
2. Build an evidence ledger separating policy existence from outcomes
3. Map evidence to the five Impact Areas, tagged operations vs. impact model
4. Test readiness and surface prioritized gaps
5. Hand back the backlog, evidence requests, and a "do not claim" list

## Time Investment

- **First run:** 2-4 hours (driven by how organized your policies and evidence are)
- **Iterations:** about an hour to re-run after closing backlog items

## Next Steps

- Work the 30/90/180-day backlog, then complete the live B Impact Assessment
- Feed strong evidence areas into `impact-report-ghostwriter` for public reporting

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/esg-sustainability/b-corp-gap-reader)

## License

MIT. Use freely. Attribute appreciated.
