---
name: materiality-interview
description: Conduct a structured, evidence-aware interview to identify and prioritize an organization’s material ESG impact topics. Use when preparing a GRI-informed materiality assessment, interviewing founders, staff, stakeholders, or subject-matter experts, or converting an existing scope inventory into a defensible material-topics shortlist.
---

# Materiality Interview

Use this skill to identify the organization’s most significant impacts on the economy, environment, and people, including human rights. Treat materiality as **impact materiality** in the GRI sense, not merely investor risk or brand relevance. GRI 3 describes a four-step process: understand context, identify actual and potential impacts, assess impact significance, and prioritize the most significant impacts for reporting.[1]

## Prerequisites

No connectors required — runs on Claude alone. You supply the organization profile, interviewee roster, and evidence inputs described below; pasted notes or common document formats are fine.

## Inputs

Accept any combination of a Session 3 scope or ESG inventory, organization profile, interviewee roster, stakeholder groups, known incidents, policies, goals, complaints, certifications, and prior reports. If a scope inventory is present, preserve its IDs and terminology so downstream reporting can trace every topic back to source evidence. If it is absent, create a lightweight impact universe from the organization’s activities and value chain before interviewing.

## Workflow

1. **Set the frame.** Confirm the reporting period, organizational boundary, decision rule, interviewees, confidentiality needs, and intended audience. State that this is not a certification, assurance, legal, or impact-measurement conclusion.
2. **Build an impact universe.** Map activities, products, services, relationships, and geographies to actual and potential positive and negative impacts. Include direct operations and relevant upstream/downstream relationships. Compare the draft list with applicable GRI Sector Standards where available.[1]
3. **Interview in rounds.** Ask open questions first, then probe for affected people, scale, scope, irremediable character, likelihood, time horizon, evidence, management response, and omissions. Use separate prompts for leadership, workers, affected communities/customers, suppliers, and independent experts. Do not lead interviewees toward fashionable ESG topics.
4. **Capture evidence.** For each claim, record source, date, role, confidence, and whether it is an observation, metric, policy, incident, perception, or inference. Separate reported facts from interpretation.
5. **Score significance.** Rate each impact on a 1–5 scale for severity (scale, scope, irremediable character) and likelihood. For actual negative impacts, prioritize severity; for potential negative impacts, combine severity and likelihood. Keep positive impacts as a separate lens rather than allowing them to offset harms.
6. **Calibrate and challenge.** Test the draft ranking with at least one perspective outside management where feasible. Review blind spots: vulnerable groups, labor rights, supply chain, product/customer outcomes, privacy, corruption, climate, pollution, biodiversity, and community effects.
7. **Prioritize topics.** Cluster impacts into plain-language material topics. Record inclusion rationale, excluded topics, uncertainty, affected stakeholders, evidence gaps, and proposed management owner. The shortlist is not complete until omissions are explained.
8. **Package the handoff.** Produce a materiality register and short interview memo that an impact-report ghostwriter can consume without reinterpreting scores.

## Required output schema

Return these sections in order:

1. **Assessment frame**: period, boundary, interviewees, limitations, and framework lens.
2. **Impact universe**: one row per impact with `impact_id`, `activity_or_relationship`, `topic`, `positive_or_negative`, `actual_or_potential`, `affected_stakeholders`, `evidence`, `confidence`, and `source_ref`.
3. **Materiality register**: `topic`, `impact_ids`, `severity`, `likelihood`, `priority`, `rationale`, `management_owner`, `data_gaps`, and `reporting_action`.
4. **Stakeholder voice**: attributed only to consented roles or anonymized groups; never invent quotations.
5. **Blind spots and next questions**.
6. **Handoff block**: a compact YAML or JSON object named `materiality_output` containing the register and traceability fields.

## Guardrails

Do not equate a policy with an outcome. Do not treat an interviewee’s confidence as evidence strength. Do not fabricate stakeholder participation, scores, GRI topic mappings, or sector applicability. If evidence is weak, label the topic `provisional` and specify the validation step. Do not claim that the organization reports “in accordance with” GRI unless all applicable requirements have been checked; use “GRI-informed” or “with reference to GRI” when appropriate.

## References

[1]: https://www.globalreporting.org/pdf.ashx?id=12453 "GRI 3: Material Topics 2021"
[2]: https://www.globalreporting.org/standards/ "GRI Standards overview"

## Example

See `examples/green-thread-materiality/materiality-register.md` for a completed small-organization dry run and the downstream handoff format.
