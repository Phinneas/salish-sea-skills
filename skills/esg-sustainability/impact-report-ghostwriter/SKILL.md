---
name: impact-report-ghostwriter
description: Draft a concise, credible ESG or impact report for a small organization from a scope inventory, materiality register, evidence pack, and management inputs. Use when turning Session 3 inventory results and materiality-interview outputs into a publishable report, web page, annual impact update, or GRI-informed disclosure set.
---

# Impact Report Ghostwriter

Draft an honest report that explains context, material impacts, management, progress, setbacks, and next actions. Use GRI as a framing device: the GRI Standards are modular and cover universal, sector, and topic standards, and GRI 3 asks organizations to disclose the process used to determine material topics, the list of topics, and management of each topic.[1] For a small organization, right-size the report rather than imitating a Fortune 500 ESG report.

## Prerequisites

No connectors required — runs on Claude alone. You supply the inventory, materiality, and evidence inputs described below; CSV, JSON, YAML, Markdown, DOCX, spreadsheets, or pasted notes are all accepted.

## Inputs and precedence

Prefer, in order: approved source evidence, the Session 3 scope/ESG inventory, the materiality-interview `materiality_output`, owner-approved metrics, policies, and clearly labeled narrative context. Preserve source IDs and report-period boundaries. If evidence conflicts, surface the conflict and ask for resolution; never silently reconcile it.

Minimum input fields are organization profile, reporting period, boundary, materiality register, impact/evidence inventory, objectives, metrics with units and baselines, governance/owners, and known limitations. Accept CSV, JSON, YAML, Markdown, DOCX, spreadsheets, or pasted notes after inspecting their structure.

## Workflow

1. **Establish the report contract.** Confirm audience, tone, publication channel, reporting period, organizational boundary, framework claim, language, word/page limit, and approval owner. Default to “GRI-informed” unless conformance has been verified.
2. **Audit the evidence pack.** Build a traceability matrix from every material topic to impacts, source references, metric definitions, period, owner, and confidence. Mark missing data, estimates, restatements, and incomparable periods.
3. **Outline for a small organization.** Use: cover and period; letter or executive summary; organization and impact model; how material topics were determined; material topics and stakeholder groups; one compact section per topic; goals and progress; governance and accountability; limitations and next period; appendix/source notes. Include a content index only when useful.
4. **Write topic sections.** For each material topic, explain why it matters, affected stakeholders, actual/potential impacts, policies and actions, responsibility, targets, current-period results, trend/baseline, setbacks, and next steps. Distinguish outputs, outcomes, and anecdotes.
5. **Use proportional storytelling.** Prefer a few decision-useful metrics with definitions over a dashboard of vanity metrics. Pair positive outcomes with boundary, denominator, method, and uncertainty. Use plain language and short tables.
6. **Draft responsibly.** Never invent numbers, testimonials, stakeholder quotes, assurance, certifications, legal compliance, or causal claims. Use `[DATA NEEDED]`, `[OWNER TO CONFIRM]`, and `[SOURCE NEEDED]` placeholders only in a working draft, and list them in an open-items register.
7. **Quality-control the draft.** Check topic coverage, period consistency, unit consistency, source traceability, balanced treatment of harms and benefits, accessibility, privacy, greenwashing risk, and whether every claim is supported or labeled as context.
8. **Deliver two artifacts.** Provide the report draft and a compact editorial/evidence register for approval. Include a machine-readable `report_output` block with topic IDs, source refs, metrics, caveats, and unresolved items.

## Default output structure

Use the following headings unless the user requests another format:

- **About this report**
- **Our organization and impact context**
- **How we determined material topics**
- **Material topics at a glance**
- **Material topic: [name]** (repeat)
- **Governance, accountability, and remedy**
- **Progress, setbacks, and next-period priorities**
- **Limitations and data notes**
- **Sources and method notes**
- **Open items for approval**

For each topic, include a table with `impact`, `stakeholders`, `management response`, `metric/indicator`, `current result`, `baseline/target`, `source`, and `confidence`. Keep an explicit “what we do not yet know” paragraph.

## Framework boundaries

Do not represent the output as a GRI-compliant or assured report without a documented requirements review. GRI 3’s process is about an organization’s most significant impacts; do not replace it with a materiality matrix based only on financial importance.[1] B Impact Assessment results may inform governance, workers, community, environment, and customers sections, but a B Impact score is not a GRI disclosure and must not be presented as one.[2]

## References

[1]: https://www.globalreporting.org/pdf.ashx?id=12453 "GRI 3: Material Topics 2021"
[2]: https://bcorporation.eu/become-a-b-corp/b-impact-assessment/ "B Impact Assessment structure and process"
[3]: https://www.globalreporting.org/standards/ "GRI Standards overview"

## Example

See `examples/green-thread-impact-report/impact-report.md` for a source-traceable report draft generated from the materiality example.
