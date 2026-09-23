# Materiality Interview

**What:** Runs a structured, evidence-aware interview to identify and prioritize an organization's material ESG impact topics.
**When:** You're preparing a GRI-informed materiality assessment and need a defensible material-topics shortlist, not a list of fashionable ESG themes.
**Output:** An impact universe, a scored materiality register, stakeholder-voice notes, and a machine-readable `materiality_output` handoff block.

## Use Cases

- A small organization needs its first materiality assessment before writing an impact report
- You're refreshing a prior assessment for a new reporting period
- You have a scope/ESG inventory and need to turn it into interview prompts and priorities
- Leadership wants stakeholder-informed prioritization documented, not just asserted

## The Skill

Follows the four-step impact-materiality logic from GRI 3: understand context, identify actual and potential impacts, assess significance, prioritize for reporting. Interviews run in rounds by stakeholder group, every claim is captured with source and confidence, and significance is scored on severity and likelihood — with positive impacts kept as a separate lens rather than netted against harms.

**First skill in the ESG reporting layer.** Its `materiality_output` handoff feeds directly into `impact-report-ghostwriter`, and it pairs with `b-corp-gap-reader` when certification readiness is relevant.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: organization profile, reporting period and boundary, interviewee roster, known incidents and policies, and any scope inventory or prior report. Pasted notes are fine.

## Getting Started

```
Use the materiality-interview methodology to identify our material ESG topics: [org profile + evidence]
```

Claude will:
1. Set the assessment frame (period, boundary, interviewees, limitations)
2. Build an impact universe from your activities and value chain
3. Interview in rounds, capturing evidence and confidence per claim
4. Score significance and calibrate the ranking against blind spots
5. Hand back the register plus a `materiality_output` block for the report writer

## Time Investment

- **First run:** 2-4 hours (driven mostly by how much evidence you've gathered)
- **Iterations:** under an hour to re-run for a new period or added evidence

## Next Steps

- Feed the `materiality_output` into `impact-report-ghostwriter` to draft the report
- Run `b-corp-gap-reader` in parallel if B Corp readiness matters

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/esg-sustainability/materiality-interview)

## License

MIT. Use freely. Attribute appreciated.
