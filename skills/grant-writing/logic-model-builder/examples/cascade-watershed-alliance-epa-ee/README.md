# Dry run: Cascade Watershed Alliance × EPA Environmental Education

This example continues the same illustrative organization and opportunity
used in `grant-fit-scorer`'s dry run
(`../grant-fit-scorer/examples/cascade-watershed-alliance-epa-ee/`) and
`nofo-decoder`'s dry run (`../nofo-decoder/examples/epa-ee-region10-2020/`)
— Cascade Watershed Alliance, a fictional-but-realistic small Oregon
nonprofit, applying to EPA Region 10's real (archived) Environmental
Education Local Grants Program.

The fit assessment's bottom line was "apply, but at the lower-middle of
the award range ($50,000-65,000)" and flagged a missing logic model as a
5-point gap. This dry run builds that logic model — the next real
artifact the org would need before submitting — using `logic-model-builder`
against the org's actual program (youth stream monitoring across 3
schools) and the NOFO's stated priorities and required outcomes.

**Input given to the skill:** the program description from the fit
assessment (3 partner schools, monthly stream monitoring, quarterly
restoration workdays, 2 part-time staff), the NOFO's required educational
priority (Community Projects) and environmental priority (clean and safe
water), and its required outcomes (increased environmental/conservation
literacy; encouragement of stewardship behavior) — pulled from
`nofo-decoder`'s decode.

See [logic-model.md](./logic-model.md) for the output.
