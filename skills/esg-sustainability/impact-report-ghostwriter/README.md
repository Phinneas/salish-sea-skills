# Impact Report Ghostwriter

**What:** Drafts a concise, source-traceable ESG or impact report for a small organization from inventory, materiality, and evidence inputs.
**When:** You have a materiality register and evidence pack and need a publishable report, web page, or annual impact update — without inventing a single number.
**Output:** A report draft with per-topic traceability tables, an open-items register, and a machine-readable `report_output` block.

## Use Cases

- Turning a finished materiality assessment into an annual impact report
- Drafting an ESG web page or stakeholder update from existing evidence
- Preparing a funder-facing impact narrative that needs claim-level sourcing
- Converting a scope inventory plus interviews into a GRI-informed disclosure set

## The Skill

Uses GRI as a framing device, right-sized for a small organization — no Fortune 500 report theater. Every material topic gets a compact section with stakeholders, management response, metrics, baselines, and setbacks, and every claim traces back to a source ID or is marked `[DATA NEEDED]` in an open-items register. It defaults to "GRI-informed" language and will not claim conformance, assurance, or avoided-impact numbers the evidence doesn't support.

**Second skill in the ESG reporting layer.** It consumes the `materiality_output` handoff from `materiality-interview` and preserves source IDs through drafting.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: organization profile, reporting period and boundary, materiality register, metrics with units and baselines, owners, policies, and evidence. CSV, JSON, YAML, Markdown, DOCX, spreadsheets, or pasted notes are all accepted.

## Getting Started

```
Use the impact-report-ghostwriter methodology to draft our 2025 impact report: [materiality_output + evidence pack]
```

Claude will:
1. Establish the report contract (audience, period, boundary, framework claim)
2. Audit the evidence pack into a topic-to-source traceability matrix
3. Outline a proportionate small-organization structure
4. Write each topic section with metrics, baselines, and setbacks
5. Deliver the draft plus an editorial/evidence register for approval

## Time Investment

- **First run:** 3-6 hours (mostly assembling and approving the evidence pack)
- **Iterations:** 1-2 hours per reporting period once the register exists

## Next Steps

- Route the open-items register to owners for approval before publishing
- Run `b-corp-gap-reader` if you also want a certification-readiness backlog

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/esg-sustainability/impact-report-ghostwriter)

## License

MIT. Use freely. Attribute appreciated.
