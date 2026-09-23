---
name: rfp-response
description: Turn an RFP, grant solicitation, or competitive bid request into a compliant, persuasive response plan and draft. Use when extracting requirements, building a compliance matrix, assigning evidence, writing answers, pricing work, or preparing a final submission package.
---

# RFP Response

Win by being easy to evaluate. Treat the RFP as a scoring instrument: mirror its order and vocabulary, answer every requirement, make proof visible, and never trade compliance for eloquence.

## Prerequisites

No connectors required — runs on Claude alone. You supply the RFP text and your organization's evidence; pasted text or common document formats are fine.

## Inputs

Accept the full RFP, amendments and Q&A, evaluation criteria, submission instructions, organization profile, past performance, staff bios, work samples, budget/rates, delivery constraints, and approval deadline. Preserve page/section references and version dates.

## Workflow

1. **Extract the control facts.** Capture buyer, scope, eligibility, mandatory forms, page/word limits, file format, deadline/time zone, questions deadline, evaluation weights, contract terms, insurance/background checks, and submission channel.
2. **Build the compliance matrix.** Create one row per requirement with `req_id`, exact requirement, source_ref, response_location, evidence_owner, mandatory_or_scored`, score_weight, status, and risk. Mark “not found” instead of guessing.
3. **Choose the win theme.** Write one buyer-centered promise supported by no more than three differentiators. Map each differentiator to a requirement, proof point, and measurable buyer outcome.
4. **Outline to the evaluator’s sequence.** Use the RFP’s headings and numbering. Put the answer first, then approach, roles, timeline, deliverables, quality controls, risks/mitigations, relevant experience, and budget. Keep optional innovation in a labeled section.
5. **Draft proof-led answers.** For every scored criterion, use: claim → method → evidence → outcome → fit to this buyer. Use specific examples and metrics with dates, scope, and source. Avoid generic “we are committed” language.
6. **Price and resource.** Tie labor, assumptions, milestones, and deliverables to the scope. State exclusions, dependencies, escalation/change-control, and validity period. Do not invent rates or taxes.
7. **Red-team the submission.** Check every requirement, attachment, signature, limit, form field, cross-reference, and filename. Have a second reader score it against the published rubric and list unsupported claims.
8. **Finalize for submission.** Produce a response draft, compliance matrix, clarification list, evidence request list, and submission checklist. Record owner and approval status for every section.

## Output

Return an executive summary, compliant response outline/draft, compliance matrix, workplan, staffing/roles, budget assumptions, risk register, clarification questions, and final-submission checklist. Separate `mandatory`, `scored`, and `nice_to_have` content.

## Guardrails

Do not fabricate past performance, certifications, references, client names, staff credentials, capacity, pricing, legal compliance, or outcome metrics. Never alter a mandatory form without preserving required fields. Flag conflicts between the RFP and amendments. Treat “compliant” as a checklist status, not a legal opinion.

## Example

See `examples/harbor-light-food-network/rfp-response.md`.
