---
name: post-award-reporting
description: >-
  Build the post-award reporting calendar and draft the actual performance
  and financial reports a federal award requires — correct cadence,
  correct deadlines, and content tied back to the logic model's outputs and
  outcomes. Use whenever the user asks "what reports does this grant
  require", "when is our next report due", "help me write our quarterly/
  annual report", "what's a closeout report", or has an active federal
  award and needs to track or draft its reporting obligations — even if
  they only mention one report type and don't yet know the full cadence
  this award requires. Seventh skill in the grant-writing chain — the only
  one that runs after an award is won rather than during the application,
  and it draws on the same logic model and budget used to write the
  proposal.
---

# Post-Award Reporting

## Overview

Federal awards come with reporting obligations that are easy to
underestimate at application time and expensive to miss after the award
is made — a missed or late report can trigger a high-risk designation,
delayed drawdowns, or in repeated cases, an award being closed out early.
This skill does two things: builds the actual reporting calendar for a
specific award (what's due, how often, and when relative to the
award's period of performance), and drafts the reports themselves,
grounded in the same logic model and budget the application was built on
— so performance reports report against the outcomes actually promised,
not a generic status update.

The governing framework is 2 CFR Part 200 Subpart D: performance reports
(200.328), financial reports via the SF-425 (200.329), and closeout
(200.344). Cadence and deadlines are standardized enough to compute
directly once the award's period of performance and reporting frequency
are known — but agencies do vary in report format, so this skill produces
correct-cadence content the user adapts to whatever specific form or
portal their agency requires.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** the award's period of performance (start and end
  date) and its stated reporting frequency (annual, semiannual, or
  quarterly — check the Notice of Award or the original NOFO's Post-Award
  Requirements section, which `nofo-decoder` extracts if it was run on
  this opportunity).
- **Required input (for drafting an actual report, not just the
  calendar):** what actually happened in the reporting period — outputs
  achieved, outcomes observed, budget spent to date. Real figures only;
  this skill does not estimate or project performance data on the user's
  behalf.
- **Helpful input:** `logic-model-builder`'s output, so a performance
  report can report progress against the specific outputs and outcomes
  the application claimed, and `budget-narrative-writer`'s output, so a
  financial report's category breakdown matches what was originally
  budgeted.

## Process

1. **Establish the reporting cadence and compute every deadline.**
   Performance reports are required no less than annually and no more
   than quarterly (200.328); use whichever frequency the specific award
   states. Deadlines: annual performance reports are due no later than 90
   calendar days after the reporting period ends; quarterly or
   semiannual performance reports are due no later than 30 calendar days
   after the period ends. Financial reports (SF-425) follow the same
   cadence and the same deadline structure as the performance reports
   under the award (200.329). Compute every specific date from the
   award's actual period of performance — don't leave dates as relative
   descriptions when the actual calendar dates are computable.

   Anchor each reporting period to the award's own period-of-performance
   start date, in consecutive increments of that cadence (e.g., quarterly
   = 3-month blocks starting from the PoP start date, not calendar-quarter
   boundaries like Jan-Mar/Apr-Jun) — this is standard federal practice
   and keeps every period the same length regardless of when the award
   happens to start. Only use calendar-quarter or calendar-year boundaries
   instead if the award's own documents explicitly say to. When the final
   reporting period ends at or within 30 days of the period-of-performance
   end date, flag that the final periodic report and the closeout package
   may overlap or one may be waived in favor of the other — tell the user
   to confirm with the agency or pass-through entity rather than assuming
   both are separately required.

2. **Add the closeout deadline.** Final/closeout reports (performance,
   financial, and property, as applicable) are due no later than 120
   calendar days after the end of the period of performance for direct
   recipients, or 90 calendar days for a subrecipient reporting to a
   pass-through entity (200.344). Flag which one applies based on the
   award relationship.

3. **If only building the calendar** (not drafting a report yet), render
   it using the Output format's calendar section and stop — confirm with
   the user whether they also want a specific report drafted now.

4. **If drafting a specific report**, gather what actually happened in the
   period: outputs achieved (countable, against the logic model's Outputs
   column if available), outcomes observed (against the Outcomes columns,
   noting honestly where an outcome hasn't yet materialized rather than
   implying it has), and budget spent to date by category (against
   `budget-narrative-writer`'s categories if available). Never estimate or
   invent performance figures — ask for the real numbers, and if a figure
   isn't available yet, say so in the report rather than filling the gap.

5. **Draft the performance report narrative**, structured by the same
   outputs/outcomes framework the application used, so a reviewer or
   program officer can directly trace this period's results back to what
   was promised. Where progress is behind plan, say so plainly and name
   the reason and any corrective step — a report that only shows good
   news reads as unreliable the moment a program officer cross-checks it
   against other data (drawdowns, site visits).

6. **Draft the financial report summary** using SF-425-aligned categories,
   cross-checked against the original budget's categories so a reviewer
   can see planned-vs-actual by line, not just a single spend total.

7. **Render the output** using the Output format below.

## Output format

```markdown
# Post-Award Reporting: {Program Name}

**Prepared:** {YYYY-MM-DD} · **Award/Opportunity #:** {number}
**Period of performance:** {start date} – {end date}
**Reporting frequency:** {Annual / Semiannual / Quarterly}
**Recipient type:** {Direct recipient / Subrecipient of {pass-through entity}}

## Reporting calendar
| Report | Period covered | Due date | Basis |
|---|---|---|---|
| Performance report | {period} | {date, computed: period end + 30 or 90 days} | 2 CFR 200.328 |
| SF-425 financial report | {period} | {date, same cadence} | 2 CFR 200.329 |
| ... | | | |
| Closeout (final performance + financial) | Full period of performance | {date, computed: PoP end + 120 (recipient) or 90 (subrecipient) days} | 2 CFR 200.344 |

{Only include this section below if drafting a specific report, not just the calendar.}

## Performance report — {period covered}

### Outputs achieved
| Output (from logic model) | Target | Actual | Status |
|---|---|---|---|
| {output} | {planned figure, if stated} | {real figure} | On track / Behind / Ahead |

### Outcomes observed
| Outcome (from logic model) | Evidence this period | Status |
|---|---|---|
| {outcome} | {what was actually observed/measured} | Achieved / In progress / Not yet observable this period |

### Narrative summary
{2-4 paragraphs: what happened, honest characterization of progress
against plan, reasons for any variance, corrective steps if behind.}

## Financial report — {period covered}
| Budget category | Budgeted (full award) | Expended to date | Remaining |
|---|---|---|---|
| Personnel | {amount} | {amount} | {amount} |
| ... | | | |
| **Total** | {amount} | {amount} | {amount} |

## Flags
{Anything at risk — an upcoming deadline with data not yet available, an
outcome that's behind schedule with no clear corrective step yet, a
budget category tracking well over or under plan.}
```

Save as `post-award-report-{program-slug}-{period}.md` if the user wants a
file; otherwise deliver in chat.

## Tips

- **Compute real calendar dates, not relative ones.** "90 days after the
  period ends" is correct but less useful than the actual date — always
  do the arithmetic against the award's real period of performance.
- **Never fill in a performance or financial figure the user hasn't
  provided.** A report with an honest "data not yet available for this
  line" is far safer than one with a plausible-looking invented number —
  federal reports are certified as accurate by the recipient's authorized
  official, and a fabricated figure is a real compliance risk, not just a
  writing shortcut.
- **Behind-plan progress should be reported plainly, with a reason and a
  corrective step**, not smoothed into vague positive language — program
  officers cross-check narrative reports against financial drawdowns and
  site visit data, and a report that doesn't match reality erodes trust
  fast.
- **Subrecipients get a shorter closeout window (90 days) than direct
  recipients (120 days)** — confirm which relationship applies before
  computing the closeout deadline; this is an easy date to get wrong.
- **The Flags section belongs in a calendar-only output too**, not just a
  drafted report — a calendar run can still surface something worth
  flagging (a period/closeout overlap, a missing award number). Only the
  Performance report and Financial report sections are conditional on
  actually drafting a report.
- **If the award/opportunity number isn't known yet**, write "Not yet
  assigned" or "Not provided" rather than leaving the field blank or
  blocking on it — it's useful to have but isn't required input.
- **Cost warning:** none — this is Claude-only.
- Hands off from `logic-model-builder` (the outputs/outcomes being
  reported against) and `budget-narrative-writer` (the budget categories
  the financial report tracks against) — this skill is the only one in
  the chain that runs after the award, not during the application.

