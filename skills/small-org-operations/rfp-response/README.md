# RFP Response

**What:** Turns an RFP or competitive bid request into a compliance matrix, proof-led response draft, and final-submission checklist.
**When:** A bid opportunity lands and you need to be easy to evaluate — every requirement answered, in the evaluator's order, with proof visible.
**Output:** Response draft, compliance matrix, workplan, staffing, budget assumptions, risk register, clarification questions, and submission checklist.

## Use Cases

- A city/county RFP arrives and you need a fast go/no-go read on requirements
- You're drafting a response and want it mirrored to the evaluation criteria
- Mandatory forms, page limits, and attachments keep creating compliance risk
- A second reader needs a rubric-based red team before submission

## The Skill

Treats the RFP as a scoring instrument: extract the control facts (deadline, forms, limits, weights), build a one-row-per-requirement compliance matrix with `not found` marked instead of guessed, choose one buyer-centered win theme, and draft proof-led answers (claim → method → evidence → outcome → fit). Nothing is fabricated — past performance, pricing, certifications, and references are flagged for confirmation. "Compliant" means checklist status, not a legal opinion.

**Part of the small-org operations set.** For grant solicitations specifically, the grant-writing category (`nofo-decoder` → `grant-fit-scorer` → `budget-narrative-writer`) goes deeper on funder requirements.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: the full RFP with amendments and Q&A, your organization profile, evidence, staffing, and pricing inputs. Pasted text or common document formats are fine.

## Getting Started

```
Use the rfp-response methodology on this RFP: [paste RFP + amendments]
```

Claude will:
1. Extract the control facts and deadlines
2. Build the compliance matrix, one row per requirement
3. Draft the win theme and response outline in the evaluator's sequence
4. Write proof-led answers tied to evidence you approve
5. Red-team the draft and produce the final-submission checklist

## Time Investment

- **First run:** 4-8 hours for a full response (driven by evidence gathering)
- **Iterations:** 1-2 hours to adapt the matrix and draft to a new RFP

## Next Steps

- Route clarification questions to the buyer before the Q&A deadline
- Feed awarded work into your project and reporting workflows

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/small-org-operations/rfp-response)

## License

MIT. Use freely. Attribute appreciated.
