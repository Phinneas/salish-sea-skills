# NOFO Decoder

**What:** Extracts eligibility, review/scoring criteria, and deadlines from a federal grant notice into one structured brief.
**When:** You have a NOFO/RFA/solicitation (pasted, or a link) and need to know fast whether it's worth applying to and how it's actually scored.
**Output:** A decode brief — quick-scan summary, full eligibility, and a review-criteria table with point values.

## Use Cases

- A funder sends a NOFO and you need a go/no-go read before committing writer time
- You're screening several open opportunities and need to compare eligibility and scoring quickly
- You're starting a proposal and want the review criteria in front of you before drafting, not after
- A board member asks "can we even apply for this" and you need a fast, defensible answer

## The Skill

This skill maps any federal-style funding notice into the eight sections
required by 2 CFR Part 200, Appendix I — Basic Information, Eligibility,
Program Description, Application Contents and Format, Submission
Requirements and Deadlines, Application Review Information, Award Notices,
and Post-Award Requirements — regardless of how the specific agency labels
or orders them. The highest-value output is the Application Review
Information section: every threshold (go/no-go) disqualifier, and every
scored criterion with its actual point value.

**First skill in the grant-writing chain.** Its output feeds directly into
`grant-fit-scorer` (scores an org against the decoded opportunity) and
`grant-deadline-scout` (tracks the decoded deadline alongside others).

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply the NOFO text (paste it) or a URL. If you give a URL, Claude
  uses `WebFetch`; if that only reaches a grants.gov listing page rather
  than the full announcement PDF, it'll tell you rather than guess at
  criteria that aren't actually visible.

## Getting Started

```
Decode this NOFO: [paste text or link]
```

Claude will:
1. Pull the full text if given a link
2. Map it into the eight canonical sections
3. Pull out every threshold/disqualifying criterion and every scored
   criterion with its point value
4. Flag anything the notice doesn't specify, rather than guessing
5. Hand back a quick-scan summary plus the full decode

## Time Investment

- **First run:** 15-30 minutes (mostly the time to paste/locate the full notice text)
- **Iterations:** a few minutes to re-run against a new notice

## Next Steps

- Feed the decode into `grant-fit-scorer` to check whether your org is
  actually competitive for it
- Feed the deadline into `grant-deadline-scout` to track it against
  everything else on your calendar

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/nofo-decoder)

## License

MIT. Use freely. Attribute appreciated.
