---
name: b-corp-gap-reader
description: Audit an organization’s policies, practices, evidence, and impact model against the structure of the B Impact Assessment and surface prioritized certification-readiness gaps. Use when reviewing a real organization profile, preparing for a B Impact Assessment, translating ESG inventory evidence into B Lab-style categories, or creating a practical improvement backlog.
---

# B Corp Gap Reader

Use the B Impact Assessment (BIA) as a structured management and gap-analysis lens, not as a substitute for completing the live assessment or B Lab’s review. BIA is organized around five stakeholder-focused Impact Areas—Governance, Workers, Community, Environment, and Customers—with topics covering both day-to-day operations and Impact Business Models.[1] The exact questions depend on the organization’s track, including sector, size, and geography, and B Lab weights questions differently.[1]

## Prerequisites

No connectors required — runs on Claude alone. You supply the organization profile, policies, practices, and evidence described below. WebFetch/WebSearch is optional for checking the current B Lab process and track; the gap review ships without it.

## Inputs

Accept an organization profile, legal structure and ownership, locations, headcount, workforce policies, supplier/community/environment/customer practices, impact business model, metrics, incident history, policies, certifications, evidence links, and reporting period. Also accept a Session 3 inventory or an impact-report draft. Record the BIA version/track if known; otherwise label the review `indicative` and do not estimate an official score.

## Workflow

1. **Define scope and status.** Confirm entity, subsidiaries, geography, size, sector, period, evidence cutoff, and whether the goal is self-assessment, certification preparation, or general improvement. Explain that only B Lab’s current process determines certification eligibility.
2. **Build the evidence ledger.** For each practice, capture area, topic, claim, evidence, owner, effective date, coverage, outcome metric, confidence, and expiration/review date. Separate policy existence from implementation and outcomes.
3. **Map to five Impact Areas.** Classify evidence under Governance, Workers, Community, Environment, and Customers. Also tag `operations` or `impact_business_model`, because an impact model should not be confused with ordinary responsible operations.[1]
4. **Test readiness.** Use statuses: `met—evidence strong`, `partially met—practice or coverage incomplete`, `not evidenced`, `not applicable—justify`, and `unknown—question needed`. Do not infer points from statuses unless the user provides a valid current assessment export and track.
5. **Surface gaps.** Prioritize each gap by likely certification relevance, stakeholder consequence, implementation effort, dependency, and evidence risk. Call out missing legal accountability, worker voice, wage/benefit data, supplier/community safeguards, environmental baselines, customer outcomes, grievance/remedy, and impact-model measurement when relevant.
6. **Recommend actions.** Give a 30/90/180-day backlog with owner, deliverable, evidence needed, dependency, and success measure. Prefer operational controls and measurable outcomes over policy-only fixes.
7. **Prepare verification.** Identify documents to gather, interview questions, data definitions, boundary questions, and claims requiring B Lab clarification. Include a “do not claim” section covering certification, score, and legal compliance.

## Required output

Return:

1. **Organization profile and review boundary**.
2. **Executive gap summary** with strongest evidence, largest risks, and important unknowns.
3. **Area-by-area gap table** with `impact_area`, `topic`, `operations_or_impact_model`, `current_practice`, `evidence`, `status`, `gap`, `priority`, `owner`, and `next_action`.
4. **Evidence request list**.
5. **30/90/180-day action backlog**.
6. **Indicative readiness narrative**, explicitly not an official score.
7. **Handoff block** named `bcorp_gap_output` containing the structured findings.

## Guardrails

Never state or imply that a gap review is an official B Impact Assessment, verification, score, or certification decision. Do not use stale point thresholds as a universal current rule; verify the live B Lab process and track. Do not fabricate BIA questions, weights, points, or legal requirements. Treat customer impact and Impact Business Models as distinct from general product marketing. Flag any claim based only on self-reporting or an undated policy.

## References

[1]: https://bcorporation.eu/become-a-b-corp/b-impact-assessment/ "B Impact Assessment structure, track, and scoring overview"
[2]: https://www.bcorporation.net/programs-and-tools/b-impact/ "B Impact tool overview"

## Example

See `examples/green-thread-bcorp-gap-review/gap-review.md` for a dry run against a fictional but realistic small organization profile.
