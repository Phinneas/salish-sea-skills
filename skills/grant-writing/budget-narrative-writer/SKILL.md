---
name: budget-narrative-writer
description: >-
  Turn a line-item budget into a funder-ready budget narrative — a
  justification for every dollar, tied explicitly to the program's
  activities, plus a correctly calculated indirect cost rate and cost-share
  figure. Use whenever the user asks to "write a budget narrative", "justify
  this budget", "build a budget justification", needs the SF-424A budget
  detail explained in prose (nearly every federal NOFO requires this as a
  distinct attachment from the budget form itself), or has line-item numbers
  and needs them turned into the paragraph-by-category explanation reviewers
  expect — even if they call it a "budget justification" or "cost narrative"
  (same document, different names by agency). Fifth skill in the
  grant-writing chain — typically follows logic-model-builder; the budget
  this skill justifies should fund exactly what that model claims it funds.
---

# Budget Narrative Writer

## Overview

A budget narrative is not a restatement of the budget form in sentence
form — it's the justification a reviewer reads to decide whether the
numbers are real and reasonable, or padded and disconnected from the work
plan. Reviewers who score "budget reasonableness" as a criterion are
checking one thing above all: does every dollar trace to an activity the
proposal actually describes. A line item with no narrative connection to
the program description is the single fastest way to lose points here, no
matter how well-justified the number itself is.

This skill writes that narrative against the standard federal budget
categories (SF-424A Section B: Personnel, Fringe Benefits, Travel,
Equipment, Supplies, Contractual, Construction, Other, Total Direct
Charges, Indirect Charges, Total), computes indirect costs correctly under
2 CFR 200.414, and — the check most budget narratives skip — cross-references
every funded line against the program's logic model so the budget and the
program description can't quietly diverge.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** the org's budget figures, at whatever level of detail
  exists. Ideally a line-item budget already broken into SF-424A
  categories; if the user only has rough totals or a description of what
  needs funding, help build the line items from the program description or
  logic model first (Process step 1) rather than writing narrative for
  numbers that don't exist yet.
- **Required input:** a description of the program's activities — ideally
  `logic-model-builder`'s output, since its Activities and Resources/Inputs
  columns are exactly what each budget line should trace to. A plain
  program description works if no logic model exists yet, but the
  cross-check in step 6 is weaker without one.
- **Helpful input:** the org's indirect cost situation — whether it has a
  Negotiated Indirect Cost Rate Agreement (NICRA) and its rate, or whether
  it will elect the de minimis rate. If unknown, ask; don't assume.
- **Helpful input:** the opportunity's cost-share/match requirement (from
  `nofo-decoder`'s Eligibility section), if applicable.

## Process

1. **Establish or confirm the line-item budget.** If the user has one,
   confirm it maps to the SF-424A categories (Personnel, Fringe Benefits,
   Travel, Equipment, Supplies, Contractual, Construction, Other). If they
   don't, build one from the program's resources/inputs and activities —
   ask for real figures (salaries, rates, quantities) rather than
   inventing plausible-sounding numbers; a fabricated budget is worse than
   an incomplete one flagged as such.

2. **Determine the indirect cost treatment.** Ask (if not already known)
   whether the org has a NICRA. If yes, use that rate and note that all
   federal agencies and pass-through entities must accept it per 2 CFR
   200.414(c). If no NICRA, the org may elect the de minimis rate — up to
   15% of Modified Total Direct Costs (MTDC) — with no additional
   documentation required, but once elected it must be applied
   consistently across all federal awards until the org negotiates a real
   rate. State the rate and its basis explicitly; never assume 10% — the
   de minimis cap rose to 15% of MTDC effective for awards issued on or
   after October 1, 2024.

3. **Calculate MTDC correctly**, since indirect costs apply to MTDC, not
   the full direct-cost total. MTDC includes direct salaries and wages,
   applicable fringe benefits, materials, supplies, services, travel, and
   the first $25,000 of each subaward (regardless of the subaward's
   period of performance). MTDC excludes equipment, capital expenditures,
   patient care charges, tuition remission, rental costs, scholarships and
   fellowships, participant support costs, and the portion of each
   subaward above $25,000. Flag any line that falls in the excluded set so
   the indirect calculation isn't silently wrong. Neither participant
   support costs nor rental/facilities costs have a dedicated line in the
   SF-424A category list below — when the org's costs include either,
   place them under **Other**, label them explicitly by name ("Other —
   Participant support: ..." / "Other — Facilities lease: ..."), and note
   in that line's narrative that they're excluded from MTDC. (Some
   funders' own budget forms do break participant support out as its own
   distinct category, separate from Other — if the user names the specific
   form they're using, match its categories instead of defaulting to
   Other.)

4. **Write the narrative for each category with a nonzero line item**, in
   this order: Personnel, Fringe Benefits, Travel, Equipment, Supplies,
   Contractual, Construction, Other, then Indirect Charges. For each:
   - State the figure and how it's calculated (FTE % × annual salary; rate
     × nights × travelers; unit cost × quantity).
   - Name the specific activity or activities (from the logic model or
     program description) this line funds. A justification that doesn't
     name an activity is not yet a justification.
   - Skip categories with no cost — don't write empty narrative to pad
     length.

5. **Calculate cost-share/match if the opportunity requires it.** State the
   required percentage or ratio, show the calculation against the total
   project cost (not just the award amount, unless the NOFO specifies
   otherwise), and name the actual source of the match (cash, in-kind
   staff time at a stated rate, donated space at fair market value) —
   "in-kind support" with no source named is not a defensible match
   calculation.

6. **Cross-check against the logic model.** Walk the funded activities list
   and confirm every activity in the logic model has a corresponding
   budget line, and every budget line traces to a named activity. Flag
   both directions of mismatch explicitly: an activity with no funding
   behind it (the program as described can't actually run on this budget)
   and a funded line with no activity behind it (a cost a reviewer will
   read as padding). This cross-check is the single highest-value output
   of this skill — most budget narratives fail reviewers not because a
   number is wrong but because the budget and the program description
   quietly describe two different projects.

   If no logic model and no independent activity list exists — only the
   budget itself and a bare program description — there is nothing
   external to check the budget against, and building an "activities"
   list purely by relabeling the budget's own line items produces a
   cross-check that will always come back clean by construction. Don't
   present that as a real check. Either ask for a real activity
   description first, or if producing the table anyway, mark it
   plainly as **provisional / not independently verified** and say why —
   a clean-looking cross-check table is worse than none if it's silently
   circular.

   Separately, reconcile the budget's own total against the amount
   requested plus any stated cost-share: if the line items sum to more
   or less than that total, flag the mismatch explicitly (e.g., an
   uncovered gap, or an unnamed additional funding source) rather than
   letting a reviewer discover it first.

7. **Render the narrative** using the Output format below.

## Output format

```markdown
# Budget Narrative: {Program Name}

**Prepared:** {YYYY-MM-DD} · **For opportunity:** {opportunity name, if applicable}
**Total project cost:** {amount} · **Amount requested:** {amount} · **Cost share:** {amount or "Not required"}

## Indirect cost rate
**Basis:** {NICRA at {rate}% (agreement # / period, if known) | De minimis rate, elected at {≤15}% of MTDC}
**MTDC calculation:** {total direct costs} − {excluded items: equipment, subaward amounts over $25k, etc., itemized} = **{MTDC}**
**Indirect costs:** {MTDC} × {rate}% = **{amount}**

## Budget narrative by category

### Personnel — {amount}
{For each position: role, % FTE or hours, annual/hourly rate, calculation, and
the specific activities this position performs — named from the logic model.}

### Fringe Benefits — {amount}
{Rate or basis (e.g. "28% of salaries, per the org's standard fringe rate"), and what it covers.}

### Travel — {amount}
{Purpose of each trip type, # travelers, # trips/nights, rate basis, tied to a named activity.}

### Equipment — {amount}
{Item, unit cost, quantity, why it's necessary for a named activity. Note: excluded from MTDC.}

### Supplies — {amount}
{Category and basis for the estimate, tied to a named activity.}

### Contractual — {amount}
{Each contractor/subrecipient, scope of work, basis for the cost, and — if a
subaward — note how much of it falls inside vs. outside the $25,000 MTDC-inclusion cap.}

### Construction — {amount}
{Only if applicable.}

### Other — {amount}
{Itemized; anything that doesn't fit the categories above, each tied to a named activity.}

## Cost share / match
{If required: source(s), calculation, and how each source will be documented/verified.
If not required: state that plainly rather than omitting the section.}

## Cross-check against the logic model
| Logic model activity | Funded by budget line(s) | Status |
|---|---|---|
| {activity} | {line item(s)} | Funded / **Gap — no budget line covers this activity** |
| — | {line item with no matching activity} | **Flag — no named activity justifies this cost** |

{If both columns are clean, say so plainly — that's the check working, not
nothing to report.}
```

Save as `budget-narrative-{program-slug}-{YYYY-MM-DD}.md` if the user wants
a file; otherwise deliver in chat.

## Tips

- **Never invent a NICRA rate or a de minimis election the org hasn't
  confirmed.** If the indirect cost basis is unknown, ask — don't default
  silently to 15%, since an org with an existing NICRA below or above that
  figure is required to use its own negotiated rate, not the de minimis
  cap.
- **The MTDC exclusions are the most commonly missed step.** Equipment and
  the portion of subawards over $25,000 are especially easy to leave in
  the indirect-cost base by mistake, which overstates indirect costs and
  is exactly the kind of error a federal reviewer or post-award auditor
  catches.
- **A budget line with no named activity behind it is a finding, not a
  detail to smooth over.** Say so in the cross-check table rather than
  writing generic narrative that avoids naming what the cost is actually
  for.
- **In-kind match needs a real valuation basis** (a stated hourly rate for
  donated staff time, a documented fair-market rental value) — "we'll
  contribute in-kind support" with no source or valuation won't survive a
  reviewer's or auditor's scrutiny.
- **Cost warning:** none — this is Claude-only.
- Hands off from `logic-model-builder` (the activities this budget funds)
  and typically pairs with `letter-of-support-kit` when contractual or
  subaward lines involve a named partner organization.

