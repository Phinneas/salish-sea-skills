# Board Packet Generator

**What:** Assembles a decision-ready board packet from scattered source documents — not a file dump, but cover memo, decision briefs, and a time-boxed agenda.
**When:** Board meeting is approaching and the materials live in six different inboxes, and directors need to actually prepare.
**Output:** Packet index, one-page cover memo, agenda, decision briefs, consent agenda, executive summaries, action follow-up, and a release checklist.

## Use Cases

- Monthly or quarterly board packets for a small nonprofit without a governance staffer
- Turning committee reports and financials into something directors will read
- A big decision (new site, budget, hire) needs a proper decision brief, not a verbal ask
- Prior actions keep getting lost between meetings

## The Skill

Designs the packet around decisions: every substantive item gets the exact motion language, recommendation, alternatives, evidence, budget impact, risk, owner, and what happens if the board does nothing. Long reports are compressed to an executive summary plus appendix without burying adverse trends. Proposed language is labeled `DRAFT MOTION`, and missing minutes or approvals are flagged, never fabricated.

**Part of the small-org operations set** alongside `meeting-minutes-compliance` — this skill builds the packet going into the meeting; that one produces the record coming out of it.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: meeting frame, agenda, prior minutes, action log, reports, financials, and proposals. DOCX, PDF, spreadsheets, Markdown, or pasted text are all accepted.

## Getting Started

```
Use the board-packet-generator methodology to build the packet for our [date] board meeting: [source documents]
```

Claude will:
1. Freeze the meeting frame and inventory your sources
2. Design a time-boxed agenda spine with consent items grouped
3. Write the one-page cover memo with source-linked signals
4. Build a decision brief per substantive item
5. Run the release check and hand back the packet with an open-items list

## Time Investment

- **First run:** 2-4 hours (mostly gathering and confirming sources)
- **Iterations:** about an hour per meeting once the structure exists

## Next Steps

- After the meeting, run `meeting-minutes-compliance` on the raw notes
- Carry the open-items list into the next packet's action follow-up

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/small-org-operations/board-packet-generator)

## License

MIT. Use freely. Attribute appreciated.
