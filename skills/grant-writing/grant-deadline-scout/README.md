# Grant Deadline Scout

**What:** Turns a scattered list of grant opportunities into one prioritized deadline calendar.
**When:** You have (or want to find) multiple open opportunities and need to know what to work on first.
**Output:** A calendar sorted by real urgency, with capacity conflicts called out explicitly.

## Use Cases

- Multiple grants are open at once and you need to know which one needs attention this week
- You want a monthly gut-check on what's closing soon before a team meeting
- Two deadlines quietly landed in the same week and you need to catch that before it's too late
- You've decoded and scored several opportunities and need them synthesized into one view

## The Skill

Sorts opportunities into urgency tiers (Urgent / Near-term / Upcoming /
Long-lead / Rolling / Closed) based on the actual current date — not just
chronological deadline order — and explicitly flags when two urgent
deadlines cluster close enough together to overload writer capacity. This is
a point-in-time compilation, run when you want a current read; it doesn't
watch grants.gov on its own between runs.

**Third skill in the grant-writing chain** — the synthesis point. Consumes
deadlines from `nofo-decoder` and, where available, Go/No-go calls from
`grant-fit-scorer`.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply a list of opportunities (name + deadline at minimum). Claude
  can search the web to help find open opportunities if asked, but that's a
  snapshot of what search surfaces, not a comprehensive scan of every
  federal/state/foundation funder.

## Getting Started

```
Build a deadline calendar from these opportunities: [list, or paste decoded NOFOs]
```

Claude will:
1. Normalize every opportunity's name, deadline, and fit status
2. Sort into urgency tiers based on today's date
3. Flag any deadlines that cluster badly enough to strain writer capacity
4. Render one dated calendar

## Time Investment

- **First run:** 10-15 minutes
- **Iterations:** a few minutes — re-run whenever the opportunity list changes or on a regular cadence (weekly/monthly)

## Next Steps

- Use the Urgent tier to decide this week's writer allocation
- Re-run periodically — this is a snapshot, not a live monitor. Set up a
  recurring check if you want standing coverage.

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/grant-deadline-scout)

## License

MIT. Use freely. Attribute appreciated.
