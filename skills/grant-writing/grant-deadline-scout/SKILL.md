---
name: grant-deadline-scout
description: >-
  Turn a scattered list of grant opportunities into a single prioritized
  deadline calendar — flagging what's urgent, what's already closed, and
  where deadlines cluster badly enough to overload writer capacity. Use
  whenever the user asks "what grants are closing soon", "what should we
  prioritize this month", "build us a grant calendar", "are we about to miss
  a deadline", or hands over multiple NOFOs/opportunities (pasted, linked, or
  already decoded by nofo-decoder) and wants to know what to work on first —
  even if they only mention one opportunity and want to know where it fits
  against everything else already on the list. Third skill in the
  grant-writing chain — consumes nofo-decoder output and, ideally,
  grant-fit-scorer's Go/No-go calls.
---

# Grant Deadline Scout

## Overview

Small development teams don't usually lose a grant because they didn't know
about it — they lose it because three deadlines landed the same week and
nobody realized until it was too late to prioritize. This skill takes
whatever list of opportunities the user has — pasted, linked, or already
decoded by `nofo-decoder` — and turns it into one prioritized calendar:
sorted by real urgency (not just chronological deadline order), with
capacity conflicts flagged explicitly.

This is a point-in-time compilation the user runs when they want a current
read, not a standing background monitor — it has no way to watch grants.gov
on its own between runs. If the user wants ongoing tracking, the Tips section
below covers how to set that up as a recurring check rather than a one-off.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** a list of opportunities — at minimum each one's name
  and deadline. More is better: award range, whether `grant-fit-scorer` has
  already called Go/No-go on it, and the org's estimated writer-hours to
  complete each application (if known).
- **Optional tool:** `WebFetch`/`WebSearch`, only if the user asks Claude to
  go find currently-open opportunities in a given space rather than
  supplying a list. When used this way, say plainly that the result is a
  snapshot of what search surfaced, not a comprehensive scan of every
  federal, state, and foundation funder — grants.gov alone lists thousands
  of opportunities and this skill has no dedicated feed into it.
- **Today's date**, to compute urgency tiers — use the actual current date,
  never assume or ask the user to restate it unless genuinely ambiguous.

## Process

1. **Normalize the list.** For every opportunity, extract (or ask for, if
   critically missing) name, deadline (exact date + time if known), award
   range, and Go/No-go status if `grant-fit-scorer` has already been run on
   it. If an opportunity has no clear deadline (rolling, or "TBD"), keep it
   in a separate bucket rather than forcing it into the dated calendar.

2. **Compute urgency tiers relative to today's date** (boundaries are
   inclusive of their lower edge — e.g. exactly 14 days out counts as
   Urgent, not Near-term):
   - **Past deadline** — already closed. Keep visible but move to the bottom
     — closed opportunities still matter for tracking next year's cycle, but
     shouldn't crowd out what's actionable now.
   - **Urgent (0-14 days out)** — anything here needs a decision today, not
     this week.
   - **Near-term (15-42 days out)** — writing should already be underway or
     starting imminently.
   - **Upcoming (43-84 days out)** — time to decide Go/No-go and start
     prep if not already scored.
   - **Long-lead (85+ days out)** — worth knowing about, not yet
     actionable.
   - **Rolling/no fixed deadline** — separate bucket, sorted by opportunity
     name.

3. **Flag capacity conflicts.** If two or more opportunities in the Urgent
   or Near-term tiers land within the same ~2-week window, flag it
   explicitly — this is the specific failure mode the skill exists to catch.
   Don't just list them adjacently in the table and assume the reader will
   notice; name the conflict and ask which one wins if the user hasn't
   already prioritized.

4. **Fold in fit status where available.** A No-go opportunity with a
   deadline that's already **passed** goes in the Closed section like
   everything else there — don't give it a second table. A No-go
   opportunity with a deadline still in the **future** stays in its normal
   urgency tier (don't invent a new bucket for it or drop it silently) but
   its Action column reads "Skip — {reason}" so it's visibly inert rather
   than competing for attention against real decisions. Either way, a
   No-go entry should never be the thing that makes a tier look busier than
   it actually is. If a Go/Go-with-gaps opportunity is in the Urgent tier
   and its gap list isn't closed yet, flag that explicitly — it's a
   sharper problem than a plain deadline.

5. **Render the calendar** using the Output format below.

## Output format

```markdown
# Grant Deadline Calendar — as of {YYYY-MM-DD}

## ⚠ Capacity conflicts
{Only if any exist. Name each cluster: "{Opportunity A} ({date}) and
{Opportunity B} ({date}) both need writer time in the same window — pick
one or plan to split capacity."}

## Urgent (≤ 2 weeks)
| Opportunity | Deadline | Award range | Fit status | Action |
|---|---|---|---|---|
| {name} | {date} | {range} | {Go/Go w. gaps/No-go/Not yet scored} | {what to do this week} |

## Near-term (2-6 weeks)
| Opportunity | Deadline | Award range | Fit status | Action |
|---|---|---|---|---|

## Upcoming (6-12 weeks)
| Opportunity | Deadline | Award range | Fit status | Action |
|---|---|---|---|---|

## Long-lead (12+ weeks)
| Opportunity | Deadline | Award range | Fit status |
|---|---|---|---|

## Rolling / no fixed deadline
| Opportunity | Award range | Notes |
|---|---|---|

## Closed
| Opportunity | Deadline (passed) | Notes for next cycle |
|---|---|---|
```

Save as `grant-deadline-calendar-{YYYY-MM-DD}.md` if the user wants a file;
otherwise deliver in chat. Because this is a point-in-time snapshot, always
date-stamp the output prominently — a calendar without a visible "as of"
date becomes actively misleading the moment it's reused a week later.

## Tips

- **This is not a live monitor.** Each run reflects only what was fed in or
  found at that moment — it doesn't watch for new postings or notice a
  deadline that got extended after this run. If the user wants standing
  monitoring rather than a one-off compile, tell them this needs to be
  re-run periodically (or set up as a recurring scheduled task in whatever
  tool they're running Claude through) — don't imply the skill itself is
  watching anything in the background.
- **Urgency tiers matter more than raw deadline order.** A far-off deadline
  attached to a huge, slow-moving application (a multi-year federal award
  with a partnership-letter requirement) can need attention sooner than a
  closer deadline for something the org could turn around in two days.
  Consider stated writer-hours-to-complete when available, not just the
  calendar date.
- **Don't silently drop closed opportunities.** They're low-priority for
  action but valuable for planning next year's cycle — keep them visible in
  their own section rather than deleting them from the list.
- **When Fit status is "Not yet scored,"** say so plainly rather than
  guessing at priority — an unscored opportunity in the Urgent tier is
  itself a flag: there may not be time left to run `grant-fit-scorer`
  properly before the deadline.
- Hands off from `nofo-decoder` (deadlines) and `grant-fit-scorer` (Go/No-go
  status) — this skill is the synthesis point for the whole trio, not a
  standalone deadline list.
