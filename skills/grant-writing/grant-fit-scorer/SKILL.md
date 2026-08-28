---
name: grant-fit-scorer
description: >-
  Score a specific grant opportunity against an organization's actual
  capacity, mission alignment, and competitive strength — producing a
  go/no-go recommendation and a named gap list, not just a gut feeling. Use
  whenever the user asks "should we apply for this grant", "are we a good
  fit for this opportunity", "can we actually win this", "is this worth our
  time", or has a decoded NOFO (from nofo-decoder) and an org description and
  wants a real read on competitiveness before committing writer hours. Second
  skill in the grant-writing chain — takes nofo-decoder's output as input.
---

# Grant Fit Scorer

## Overview

The expensive mistake in grant seeking isn't losing a competitive
application — it's spending 40+ writer-hours on one the org was never
eligible for, or never competitive for, and finding out at submission or
after the rejection. This skill scores a specific opportunity against an
org's actual capacity, mission fit, and competitive position, and returns a
go/no-go recommendation with the specific gaps that would need to close to
make it competitive — not a single confident-sounding number with nothing
behind it.

It is deliberately not a black-box "72% win probability." Win probability
for a specific NOFO depends on the competitive field, which this skill
cannot see. What it can assess honestly: does the org clear eligibility,
does it plausibly fund-match, does its track record speak to the criteria
the reviewers are actually scoring on (from `nofo-decoder`'s output), and
what's the size of the gap between what the org has today and what would be
competitive. Report that composite plainly rather than dressing it up as a
probability the skill has no basis to compute.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** the opportunity, ideally as `nofo-decoder`'s output
  (its Eligibility and Merit review criteria sections are what this skill
  scores against). A raw NOFO or a pasted summary of eligibility + review
  criteria also works — if given a raw NOFO, decode the eligibility and
  review-criteria sections first before scoring, rather than skipping
  straight to a guess.
- **Required input:** an org profile. At minimum: mission/program area,
  nonprofit status (matters directly for eligibility), annual budget
  (matters for cost-share and award-size fit), and any prior grant history
  relevant to the criteria being scored (e.g. if "programmatic capability
  and past performance" is a scored criterion, the org's actual track record
  on similar awards). If the user hasn't supplied this, ask for it — don't
  score fit against an org this skill knows nothing about.

## Process

1. **Gate on eligibility first.** Check the org against every eligibility
   requirement and every threshold/responsiveness criterion from the decoded
   opportunity. If the org fails a hard eligibility requirement (wrong
   entity type, can't meet a mandatory cost-share, missing a required
   registration), stop and report **No-go — ineligible**, naming the
   specific disqualifying requirement. Don't proceed to score fit on an
   opportunity the org can't legally apply to — that wastes the reader's
   time on a moot competitive assessment.

   There is a second, distinct way to land on No-go: an org that clears
   every eligibility gate but whose gap list (step 5) is severe enough
   across the highest-weighted criteria that applying this cycle isn't a
   good use of writer time. Label this **No-go — not competitive this
   cycle** to keep it visibly different from an ineligibility finding —
   the two have completely different implications (one is permanent for
   this opportunity, the other is "try again next cycle after closing
   gaps"). Reserve it for real cases; most eligible-but-imperfect orgs
   should land on Go with gaps, not this.

2. **Score mission/program fit.** How directly does the opportunity's stated
   purpose and required priorities match what the org actually does? Be
   concrete — "we run exactly this kind of program in this population" is a
   strong match; "we could plausibly pivot toward this" is a weak one. Don't
   round a weak match up because the org wants it to be strong.

3. **Score capacity fit.** Can the org actually execute at this award size
   and meet the mechanical requirements — cost-share (does the org have that
   much unrestricted/matchable funding), subaward management (if required,
   does the org have the administrative capacity to manage and report on
   subgrants), reporting burden relative to org size. A $250k award with a
   25% match requirement is a different proposition for a $200k-budget
   org than a $2M-budget org, even if both are otherwise eligible.

4. **Score competitive strength against the actual review criteria.** For
   each scored criterion from the decoded NOFO (not a generic list — the
   *actual* weighted criteria), assess the org's evidence honestly: strong
   (has concrete, specific evidence), partial (has something but it's thin
   or indirect), or absent (nothing to point to). Weight this by the
   criterion's point value — a strong showing on a 5-point criterion matters
   far less than a weak showing on a 30-point one.

5. **Name the gap list.** For every partial or absent showing on a
   meaningfully-weighted criterion, state specifically what's missing and
   what it would take to close it (a partnership letter, a logic model that
   doesn't exist yet, a track record the org needs to build before this
   cycle). This is the most actionable part of the output — it's what turns
   a "no" into "not yet, here's what to build before the next cycle."

6. **Render the recommendation** — Go / Go with gaps / No-go — using the
   Output format below. Never present a single fabricated percentage as the
   entire recommendation; the qualitative reasoning is the point.

## Output format

```markdown
# Fit Assessment: {Org Name} × {Opportunity Title}

**Assessed:** {YYYY-MM-DD} · **Opportunity #:** {number} · **Deadline:** {date}

## Recommendation: {Go / Go with gaps / No-go — ineligible / No-go — not competitive this cycle}
{One-paragraph plain-language summary of why.}

## 1. Eligibility gate
| Requirement | Org status | Result |
|---|---|---|
| {eligible entity type} | {org's actual status} | Pass / Fail |
| {cost-share requirement} | {org's ability to meet it} | Pass / Fail |
| {other threshold criteria} | | |

{If any Fail: stop here, this is a No-go. State the disqualifier plainly.}

## 2. Mission/program fit
{2-4 sentences, concrete, no rounding up}

## 3. Capacity fit
| Factor | Opportunity requires | Org has | Fit |
|---|---|---|---|
| Award size vs. budget | {range} | {org budget} | Strong / Workable / Strained |
| Cost-share | {requirement} | {org's matchable funds} | Strong / Workable / Strained |
| Subaward/admin burden | {if any} | {org's admin capacity} | Strong / Workable / Strained |

## 4. Competitive strength by review criterion
| Criterion (pts) | Org evidence | Strength |
|---|---|---|
| {criterion name} ({n} pts) | {what the org can actually point to} | Strong / Partial / Absent |
| ... | | |

**Weighted read:** {which strong/weak showings matter most given point values — name the 1-2 criteria that will make or break this application}

## 5. Gap list (what would need to close, ranked by criterion weight)
1. {Gap} — needed for {criterion, n pts} — {what it would take to close it}
2. ...

## Bottom line
{2-3 sentences: apply now, apply after closing specific gaps, or skip this cycle and target the next one / a better-fit opportunity.}
```

## Tips

- **Never fabricate a numeric win probability.** This skill has no visibility
  into the competitive field for a specific cycle — don't manufacture false
  precision. A qualitative Go / Go with gaps / No-go plus a weighted read of
  the actual criteria is more honest and more useful than an invented
  percentage.
- **A "Go with gaps" recommendation should always be paired with a
  timeline check** — if the gap list requires a partnership letter or a
  program the org doesn't have time to stand up before the deadline, that's
  effectively a No-go for *this* cycle even if the org would be competitive
  for the next one. Cross-reference the deadline before finalizing.
- **Don't let mission enthusiasm override eligibility gates.** An org that
  desperately wants to apply to a mission-aligned opportunity it's
  ineligible for still gets a hard No-go — say so plainly and, if possible,
  suggest what changes (a fiscal sponsor, a different program structure)
  would make a future cycle viable.
- **Small/new orgs will often score "Absent" on Programmatic Capability and
  Past Performance criteria** — that's real information, not a skill
  failure. Note it plainly in the gap list rather than softening it; per the
  HRSA-style scoring convention, orgs with no track record to cite typically
  get a neutral (not zero) score on this specific criterion — mention that
  convention if the decoded NOFO's own review-criteria text supports it, but
  don't assume it applies universally.
- Hands off from `nofo-decoder` (the opportunity being scored) and forward
  to `grant-deadline-scout` if this is a "Go" or "Go with gaps" — it now
  needs a spot on the deadline calendar.
