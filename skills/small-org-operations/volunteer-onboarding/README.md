# Volunteer Onboarding

**What:** Designs a practical volunteer journey — intake, screening, orientation, demonstrated training, placement, and first-30-day support.
**When:** Volunteers are starting soon and the current process is a welcome email and good intentions.
**Output:** Role card, intake fields, screening decision tree, orientation agenda, training checklist, first-shift brief, follow-up plan, status tracker, and message templates.

## Use Cases

- Standing up a volunteer program for the first time at a small nonprofit
- A new role (event, distribution, transport) needs a real role card and screening path
- Volunteers churn after the first shift and you don't know why
- Screening requirements vary by role and you need proportionate, consistent checks

## The Skill

Treats onboarding as a risk-managed relationship, not an information dump: a role card with explicit boundaries, proportionate role-based screening, orientation that requires acknowledgment, training to demonstration before any system or client access, and structured check-ins at first shift, week two, and day 30. Screening, safeguarding, and mandatory-reporting rules vary by jurisdiction and role — those are flagged for verification, never invented.

**Part of the small-org operations set** — standalone, but pairs naturally with `board-packet-generator` when the board needs to approve a new volunteer program or policy.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: mission, role tasks and boundaries, schedule, audience served, supervisor, policies, and start date. Pasted notes are fine.

## Getting Started

```
Use the volunteer-onboarding methodology to design onboarding for [role]: [mission + policies]
```

Claude will:
1. Write the role card with boundaries and prerequisites
2. Define intake fields — only what's needed to place and support
3. Map the proportionate screening path by role risk
4. Build the orientation agenda and demonstration-based training checklist
5. Deliver the first-shift brief, 30-day plan, and status tracker

## Time Investment

- **First run:** 2-3 hours for the first role
- **Iterations:** under an hour per additional role once the skeleton exists

## Next Steps

- Pilot with the first cohort and capture day-30 feedback
- Bring policy changes (screening, safeguarding) to the board via `board-packet-generator`

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/small-org-operations/volunteer-onboarding)

## License

MIT. Use freely. Attribute appreciated.
