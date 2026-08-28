# Post-Award Reporting

**What:** Builds the reporting calendar for a federal award and drafts the actual performance and financial reports, grounded in the same logic model and budget the application used.
**When:** You've won an award and need to know what's due when, or you need an actual report drafted from real period data.
**Output:** A computed reporting calendar (every deadline, correctly calculated from the award's period of performance) and, on request, a drafted performance report and financial summary.

## Use Cases

- You just received a Notice of Award and need to know the full reporting obligation, not just the first deadline
- A quarterly, semiannual, or annual report is coming up and you need it drafted from this period's real numbers
- You're not sure whether your closeout deadline is 90 or 120 days out, or from what date
- A program officer or board member asks "are we current on our reporting" and you need a fast, accurate answer

## The Skill

This skill computes every reporting deadline a federal award requires —
performance reports, SF-425 financial reports, and closeout — directly
from 2 CFR Part 200's reporting rules (Subpart D) and the award's actual
period of performance, so dates are real calendar dates, not relative
descriptions. When drafting an actual report, it structures the narrative
around the same outputs and outcomes the application's logic model
claimed, so a program officer can trace this period's results directly
back to what was promised — and it never estimates or invents a
performance or financial figure; real numbers only.

**Seventh skill in the grant-writing chain**, and the only one that runs
after an award is won rather than during the application. It draws
directly on `logic-model-builder`'s outputs/outcomes and
`budget-narrative-writer`'s budget categories.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply the award's period of performance and reporting frequency
  (from the Notice of Award, or from a decoded NOFO's Post-Award
  Requirements section if `nofo-decoder` was run on the opportunity).
- To draft an actual report (not just the calendar), you supply real
  figures for what happened in the period — Claude will not estimate or
  project this data for you.
- Helpful: `logic-model-builder`'s and `budget-narrative-writer`'s output,
  so reports trace directly back to what the application claimed.

## Getting Started

```
Build the reporting calendar for [award] — period of performance [dates], reports [frequency]
```
or, once a period has closed:
```
Draft our [quarterly/annual] performance and financial report for [program], period [dates] — here's what happened: [figures]
```

Claude will:
1. Compute every reporting and closeout deadline from the actual award dates
2. If drafting a report, structure it against the logic model's outputs
   and outcomes and the budget's categories
3. Report honestly on any progress that's behind plan, with a reason and
   next step, rather than smoothing it over
4. Flag anything at risk — a missing figure, an upcoming deadline, a
   budget line running off plan

## Time Investment

- **First run (calendar only):** 5-10 minutes
- **Drafting an actual report:** 30-60 minutes, depending on how complete
  the period's real data already is

## Next Steps

- Set a recurring reminder ahead of each computed deadline — this skill
  builds the calendar but doesn't monitor it on its own
- Revisit `logic-model-builder` if a reporting cycle reveals an outcome
  that isn't materializing as claimed — that's a signal worth addressing
  before the next report, not just noting in this one

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/post-award-reporting)

## License

MIT. Use freely. Attribute appreciated.
