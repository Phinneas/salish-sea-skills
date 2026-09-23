# Meeting Minutes to Compliance

**What:** Converts raw board or committee notes into neutral, review-ready governance minutes with explicit decisions, votes, conflicts, and actions.
**When:** The meeting happened, the notes are a mess, and you need a record a later reader — or funder, or auditor — can rely on.
**Output:** Draft minutes, decisions/motions table, attendance and quorum record, recusals, action register, recorder queries, and source register.

## Use Cases

- Cleaning raw notes into approval-ready board minutes
- Separating what was actually decided from what was merely discussed
- Rebuilding an action register with owners and due dates
- Preparing minutes for retention or funder/audit review

## The Skill

Treats minutes as a governance record, not a narrative: date, participants, quorum as documented, motions, vote results, recusals, and follow-up — with explicit statuses (`documented`, `not recorded`, `needs confirmation`) instead of inferences. Dissent, failed motions, and conflicts are preserved, not polished away. This is a record-keeping workflow, not a legal compliance opinion; open-meeting, quorum, and retention rules vary by jurisdiction and are flagged for verification rather than asserted.

**Part of the small-org operations set** alongside `board-packet-generator` — that skill builds the packet going into the meeting; this one produces the record coming out of it.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: raw notes, agenda, attendance/roll, motions and vote evidence, and relevant bylaws or policy. Pasted text or common document formats are fine.

## Getting Started

```
Use the meeting-minutes-compliance methodology on these board notes: [paste notes + agenda]
```

Claude will:
1. Set the record frame and mark anything not documented as `NOT RECORDED`
2. Tag each note as discussion, motion, vote, action, or uncertainty
3. Reconstruct the agenda order with motions and vote results
4. Extract the action register with owners and due dates
5. Deliver draft minutes with a recorder-query list for confirmation

## Time Investment

- **First run:** 1-2 hours per meeting
- **Iterations:** under an hour once your board's format is established

## Next Steps

- Route the recorder queries, then present the minutes for approval
- Feed confirmed actions into the next `board-packet-generator` packet

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/small-org-operations/meeting-minutes-compliance)

## License

MIT. Use freely. Attribute appreciated.
