---
name: letter-of-support-kit
description: >-
  Produce a set of partner letters for a grant application — letters of
  support, letters of commitment, and letters of collaboration — each
  matched to the right document type and drafted with the specificity
  reviewers expect instead of interchangeable boilerplate. Use whenever the
  user asks to "write a letter of support", "get partner letters for this
  grant", "draft a commitment letter", "we need letters from our
  partners", or has a list of partner organizations and needs
  funder-appropriate letters that name what each partner is actually
  contributing — even if they just say "letters for the grant" without
  specifying which type (this skill's first job is sorting that out). Sixth
  skill in the grant-writing chain — typically runs alongside or after
  logic-model-builder, since a partner's role should trace to a specific
  activity in that model.
---

# Letter of Support Kit

## Overview

Funders read partner letters looking for one thing: proof that the
relationship named in the application is real, not a courtesy signature
collected the week before the deadline. A stack of near-identical letters
that all say "we fully support this important initiative" reads as
exactly what it is, and experienced reviewers discount it accordingly.
This skill produces letters that name specific facts — what the partner is
actually contributing, at what level, tied to a specific activity in the
program — because specificity is what makes a letter evidence rather than
decoration.

The skill's first job is sorting the request into the right document type,
because funders and reviewers read these differently and a mismatched
type undermines the letter before its content even matters:

- **Letter of Support** — confirms a fact the application relies on (the
  partner endorses the project, will refer participants, agrees the need
  is real). No resource commitment implied.
- **Letter of Commitment** — proves a specific, checkable pledge at a
  claimed level: most often a *named individual's* availability (a co-PI's
  time commitment, a subrecipient's staff assignment), but the same logic
  applies to an *organizational* forward pledge with a concrete, checkable
  claim (a for-profit partner committing to interview every graduate, a
  vendor committing to a specific service level) — the common thread is a
  specific future action a reviewer could verify, not just who happens to
  be named. This is the type reviewers scrutinize hardest, because an
  unfunded or unverifiable commitment here is a real proposal weakness.
- **Letter of Collaboration** — NSF's specific term for a partner
  contributing unfunded resources or effort (equipment access, unpaid
  advisory time, data sharing). By NSF's own policy, these must avoid
  evaluative language about the proposal's merit — the letter states the
  contribution, not an opinion of the project's quality.

Getting the type wrong is a common and avoidable mistake: asking a
collaborator for a "letter of support" when the application actually needs
a letter of commitment leaves the exact claim reviewers will check —
availability at a stated level — unstated.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** a list of partners and, for each, what they're
  actually contributing (referral pathway, staff time, in-kind resources,
  data, endorsement only). If the user doesn't know which letter type a
  partner needs, work it out together using the Process step 1 test
  rather than defaulting to "letter of support" for everything.
- **Required input:** the applicant organization's name, the program name,
  and the grant period's dates — every letter's header, salutation, and
  duration language needs these even though they're about the applicant,
  not the partner. Ask if not given rather than leaving the whole kit full
  of placeholders for information the user could have supplied up front.
- **Required input:** enough program detail to name what the partnership
  supports — ideally `logic-model-builder`'s output, since a partner's
  contribution should trace to a specific activity or resource in that
  model, not a vague mission-alignment statement.
- **Helpful input:** the funder's own letter requirements if stated in the
  NOFO (some funders specify required content, page limits, or explicitly
  restrict evaluative language — check `nofo-decoder`'s Application
  Contents section).

## Process

1. **Determine the letter type for each partner**, using this test: does
   the application depend on a *specific, checkable forward pledge at a
   claimed level* — a named individual's availability, or an
   organization's commitment to a concrete future action? → Letter of
   Commitment. Is the partner contributing *unfunded* resources, access,
   or effort, under a funder (like NSF) that uses the collaboration-letter
   convention? → Letter of Collaboration. Otherwise, is the partner simply
   *confirming a fact* the application relies on with no resource
   commitment? → Letter of Support. When genuinely ambiguous, ask rather
   than guess — the wrong type undermines the letter's evidentiary value;
   if there's no live back-and-forth available (a one-pass drafting
   request), pick the type matching the partner's strongest forward-looking
   claim and note the judgment call in the Flags section rather than
   blocking on it.

   A partner's material sometimes spans two types — a backward-looking
   fact (a historical hire rate, a past collaboration) alongside a
   forward-looking pledge (a new commitment for this program). Don't split
   this into two letters or force a single clean bucket; draft one letter
   in whichever type matches the forward-looking pledge (since that's what
   the application is actually relying on going forward), and use the
   backward-looking fact as supporting context within that same letter.

2. **Gather the specific facts for each letter**, not just the partner's
   name and role: what exactly are they contributing (a number, a
   service, a resource, a role), at what level or duration, and which
   activity in the program this supports. A letter with no specific
   number or duration is functionally boilerplate no matter how it's
   worded.

3. **Draft in the partner's voice, not the applicant's.** These letters go
   out on the partner organization's letterhead over their signature —
   write as that organization speaking, in first person plural ("we will
   provide..."), not as the applicant describing the partner in third
   person.

4. **Match tone and content to the letter type:**
   - Letter of Support: confirms the need/project, states organizational
     endorsement, names any factual basis for that endorsement (years of
     relationship, prior collaboration, direct knowledge of the need).
   - Letter of Commitment: states the named individual, their role, the
     specific time/resource commitment, and the duration — this is the
     one type where vagueness is a real defect, not just weak writing.
   - Letter of Collaboration: states the specific unfunded contribution
     factually, with **no evaluative or endorsement language** about the
     proposal's quality or importance — that distinction matters
     specifically for NSF submissions and should be preserved rather than
     smoothed into generic supportive language.

5. **Flag any letter that can't be made specific** with the information
   given — don't paper over a missing fact with enthusiasm. Ask for the
   missing detail (a number, a name, a duration) rather than writing
   around the gap.

6. **Render the kit** using the Output format below — one drafted letter
   per partner, each ready for the partner to review and put on their own
   letterhead.

## Output format

```markdown
# Letter of Support Kit: {Program Name}

**Prepared:** {YYYY-MM-DD} · **For opportunity:** {opportunity name, if applicable}

## Letter log
| Partner | Letter type | Contribution | Tied to activity |
|---|---|---|---|
| {org} | Support / Commitment / Collaboration | {one-line summary} | {logic model activity, if applicable} |

---

## {Partner Organization Name} — {Letter Type}

> [Partner Organization Letterhead]
>
> {Date}
>
> {Recipient — funder name/program office, or "To Whom It May Concern" if
> not specified}
>
> Dear {Reviewer / Program Officer / To Whom It May Concern},
>
> {Letter body — specific, in the partner's voice, matched to the type per
> Process step 4. 2-4 paragraphs.}
>
> Sincerely,
>
> {Name, Title}
> {Partner Organization}

---
{Repeat for each partner.}

## Flags
{Any letter where a specific fact (a number, name, or duration) was missing
and had to be left as a placeholder — list what's needed before this letter
is send-ready.}
```

Save as `letters-of-support-{program-slug}-{YYYY-MM-DD}.md` if the user
wants a file; otherwise deliver in chat. These are drafts for the partner
to review, edit, and place on their own letterhead — never submit a
partner letter the partner organization hasn't actually reviewed and
approved.

## Tips

- **Specificity is the entire value of this document.** "We fully support
  this important project" is worth less to a reviewer than "we will
  provide classroom space for 12 workshop sessions between March and
  June, as we did for [applicant]'s 2024 program." Push for the second
  kind even when the user's first draft of the ask is the first kind.
- **Never draft a Letter of Commitment with a vague time commitment.**
  "Available as needed" is not a commitment a reviewer can verify — get a
  real percentage, hours, or duration, or flag it as missing.
- **NSF's no-evaluative-language rule for Letters of Collaboration is a
  real compliance point**, not a style preference — a collaboration
  letter that praises the project's merit can actually work against the
  applicant under NSF's own review guidance. Don't default to warm,
  supportive language here.
- **These are drafts, not final documents.** Always say so plainly when
  delivering the kit — every letter needs the partner's own review,
  editing in their voice if needed, and their actual signature on their
  own letterhead before submission.
- **Cost warning:** none — this is Claude-only.
- Hands off from `logic-model-builder` (which activities partners support)
  and pairs with `budget-narrative-writer` when a partner's contribution
  is also a contractual or subaward budget line.

