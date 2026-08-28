---
name: nofo-decoder
description: >-
  Extract requirements, eligibility, review/scoring criteria, and deadlines
  from a federal (or federal-style) Notice of Funding Opportunity (NOFO) and
  turn them into one structured brief a grant writer can actually work from.
  Use whenever the user pastes or links a NOFO/RFA/funding announcement and
  asks "what does this grant require", "can we even apply for this", "decode
  this notice", "what's the deadline and how is it scored", or shares a
  grants.gov/agency solicitation and wants to know what it takes to compete —
  even if they don't use the word "NOFO" (RFA, RFP, solicitation, funding
  opportunity, and "grant notice" all mean the same thing here). This is the
  first skill in the grant-writing chain — run it before grant-fit-scorer or
  grant-deadline-scout, both of which consume its output.
---

# NOFO Decoder

## Overview

Federal funding notices bury the decision-relevant information — deadline,
eligibility, and exactly how reviewers score an application — inside dense,
inconsistently organized legal text that can run 20-40 pages. This skill
extracts that information into one short, structured brief: eligibility
(with the specific disqualifiers that would sink an application before it's
even read), the review criteria with their point values or weights (so a
writer knows where the actual points are, not just what sounds important),
and every hard date. It's the first skill in the grant-writing trio — its
output is what `grant-fit-scorer` scores an org against, and what
`grant-deadline-scout` pulls deadlines from.

Federal NOFOs are not free-form documents — 2 CFR Part 200, Appendix I
requires eight standard sections (Basic Information, Eligibility, Program
Description, Application Contents and Format, Submission Requirements and
Deadlines, Application Review Information, Award Notices, Post-Award
Requirements). Agencies vary in how they label and order these — EPA numbers
sections differently than HRSA or FEMA — but the eight categories are always
present in some form. Decode into that canonical structure rather than
mirroring whatever headings the specific notice happens to use — that's what
makes output from two different agencies' notices comparable to each other,
and what `grant-fit-scorer` and `grant-deadline-scout` can rely on.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** the NOFO's text. The user can paste it directly, paste
  a large excerpt (at minimum the eligibility and review-criteria sections —
  these are the two sections that most change the go/no-go decision), or
  give a URL.
- **Optional tool:** `WebFetch`, to pull the NOFO directly if the user gives
  a grants.gov or agency URL instead of pasting text. If `WebFetch` can't
  reach it (some grants.gov detail pages are JS-rendered or gated), ask the
  user to paste the text or the PDF content instead — don't guess at a NOFO's
  contents from a landing page summary. A grants.gov opportunity **listing**
  page (title, agency, dates) is not the NOFO itself; the actual review
  criteria and eligibility detail live in the attached PDF/announcement
  document. If only the listing page is reachable, say so explicitly and
  extract only what it actually contains — don't infer scoring criteria that
  aren't there.
- **Optional input:** the org's basic profile (nonprofit status, budget
  size), if the user wants a same-pass eligibility gut-check. Not required —
  that fuller comparison is `grant-fit-scorer`'s job.

## Process

1. **Get the text.** If given a URL, `WebFetch` it. If the fetch returns
   only a summary/listing page rather than the full announcement, tell the
   user and ask for the PDF text or a paste instead of proceeding on partial
   information.

2. **Map to the eight canonical sections**, regardless of the source NOFO's
   own headings:
   - Basic Information (agency, opportunity number, opportunity title,
     funding instrument, total program funding, award floor/ceiling,
     expected number of awards, key dates)
   - Eligibility (eligible applicant types verbatim, explicit exclusions,
     cost-share/match requirement and its calculation, subaward or
     pass-through requirements, submission limits per applicant)
   - Program Description (purpose, priorities the application must address,
     required outcomes/performance measures, authorizing statute if given)
   - Application Contents and Format (required forms, narrative page limits,
     formatting rules, required attachments)
   - Submission Requirements and Deadlines (every hard date — pre-application
     if any, full application, intent-to-apply, and the exact time + time
     zone if stated)
   - Application Review Information — the highest-value section. Extract:
     - **Threshold / responsiveness criteria** — the go/no-go screen applied
       *before* scoring. List every condition that disqualifies an
       application outright, verbatim where possible. This is the section
       writers most often skip and most need.
     - **Merit review criteria** — every scored criterion, its point value
       or percentage weight, and its sub-criteria with their own point
       splits if the notice breaks them out. Preserve the notice's own
       point math; don't round or re-normalize it.
     - Review/selection process notes (panel type, program policy factors
       like geographic balance, if stated)
   - Award Notices (what happens after selection, timeline to award)
   - Post-Award Requirements (reporting frequency/type, special compliance
     flags — human subjects, data sharing, indirect cost caps)

3. **Flag what's missing.** If a NOFO doesn't state something the canonical
   structure expects (no cost-share requirement stated, no page limit
   given), write "Not specified in the notice" rather than leaving the field
   blank or inferring a default — a missing requirement is information the
   writer needs, not a gap to paper over.

4. **Build the quick-scan summary** — the five facts a writer needs before
   deciding whether to read further: deadline, award range, total points
   available and what the single highest-weighted criterion is, the
   cost-share requirement (if any), and the single most likely disqualifier
   for a small/new applicant (usually: not an eligible entity type, can't
   meet cost-share, or missing a required registration like SAM.gov). If
   two disqualifiers look equally likely, don't force a false single
   pick — name both in the one sentence rather than arbitrarily dropping
   one.

5. **Produce the brief** in the Output format below.

## Output format

```markdown
# NOFO Decode: {Opportunity Title}

**Opportunity #:** {number} · **Agency:** {agency} · **Decoded:** {YYYY-MM-DD}
**Source:** {URL or "pasted text, no URL given"}

## Quick scan
| | |
|---|---|
| Deadline | {date + time + time zone, or "Not specified"} |
| Award range | {floor}–{ceiling} · {n} awards expected |
| Total review points | {n} (highest-weighted: {criterion name}, {n} pts) |
| Cost share | {requirement, or "None stated"} |
| Most likely disqualifier for a small/new applicant | {one sentence} |

## 1. Basic Information
{fields as extracted}

## 2. Eligibility
**Eligible applicants:** {verbatim list}
**Exclusions:** {verbatim or "None stated"}
**Cost share:** {requirement + calculation}
**Subaward/pass-through requirements:** {if any}
**Submission limits:** {per-applicant caps, if any}

## 3. Program Description
**Purpose:** {1-2 sentences}
**Required priorities (must address ≥1 unless noted):** {list}
**Required outcomes/performance measures:** {list or "Not specified"}

## 4. Application Contents and Format
{required forms, narrative page limit, formatting rules, required attachments — as a list}

## 5. Submission Requirements and Deadlines
{every date, as a table: Milestone | Date | Time (with time zone)}

## 6. Application Review Information

### Threshold / responsiveness criteria (go/no-go — screened before scoring)
{numbered list, verbatim where possible}

### Merit review criteria ({total} points)
| Criterion | Points | What it evaluates |
|---|---|---|
| {name} | {n} | {1-line description, quote where useful} |
| ↳ {sub-criterion, if broken out} | {n} | {description} |
| ... | | |

### Review/selection process
{panel type, program policy factors, if stated}

## 7. Award Notices
{timeline/process}

## 8. Post-Award Requirements
{reporting type/frequency, special compliance flags}

## Fields not specified in the notice
{list any canonical fields the source NOFO didn't address — don't silently drop these}
```

Save as `nofo-decode-{org-or-opportunity-slug}-{YYYY-MM-DD}.md` if the user
wants a file; otherwise deliver in chat. Either way, this is the artifact
`grant-fit-scorer` and `grant-deadline-scout` expect as input — keep the
Quick scan table and the Merit review criteria table intact even if the user
asks for a shorter version, since those two tables are what the other two
skills parse.

## Tips

- **Don't fabricate point values.** If a NOFO describes criteria narratively
  without assigning points ("technical merit will be weighted more heavily
  than budget"), say exactly that — don't invent a percentage to fill the
  table. A missing number is real information.
- **Threshold criteria are not optional to extract**, even when they're
  scattered across multiple sections instead of listed in one place (common
  in older or shorter notices). An application that fails one of these never
  gets scored — this is the highest-leverage section in the whole document
  for a small org deciding whether to bother applying.
- **Watch for point math that doesn't obviously sum** — some notices score
  out of 100, others out of a different total, and sub-criteria don't always
  cleanly add to their parent criterion's stated maximum in the source text.
  Preserve what's written rather than "fixing" the arithmetic.
- **Cost-share and subaward mechanics are frequent disqualifiers** for small
  nonprofits and are easy to skim past — always surface them in the Quick
  scan even if the org's ability to meet them isn't this skill's job to
  judge (that's `grant-fit-scorer`).
- **Older/informal solicitations** (state pass-through grants, foundation
  RFPs written in prose) won't map cleanly to all eight sections. Decode
  what's there, mark the rest "Not specified," and don't force structure the
  source document doesn't have.
- Hands off to `grant-fit-scorer` (score this decoded opportunity against an
  org) and `grant-deadline-scout` (track this deadline alongside others).
