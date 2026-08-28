# Grant Fit Scorer

**What:** Scores a specific grant opportunity against your org's eligibility, capacity, and competitive strength.
**When:** You're deciding whether to spend writer hours on a specific opportunity.
**Output:** A Go / Go with gaps / No-go recommendation, with a ranked, actionable gap list.

## Use Cases

- A NOFO looks mission-aligned but you're not sure the org can actually compete for it
- You have three open opportunities and limited writer time — which is worth pursuing
- A board member is pushing for a grant the org may not be eligible for
- You want to know specifically what to build (a partnership, a track record) before the next funding cycle

## The Skill

Gates on eligibility first — if the org can't legally apply, it says so and
stops, rather than scoring a moot competitive assessment. If eligible, it
scores mission fit, capacity fit (award size vs. budget, cost-share
ability), and — the core of the assessment — competitive strength against
the opportunity's *actual* weighted review criteria, not a generic
checklist. It deliberately does not output a fabricated win-probability
percentage; it outputs a plain recommendation plus a ranked list of the
specific gaps that would need to close.

**Second skill in the grant-writing chain.** Takes `nofo-decoder`'s output
as input; a "Go" result typically heads to `grant-deadline-scout` next.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply: the decoded opportunity (from `nofo-decoder`, or a raw NOFO —
  Claude will decode the relevant sections first) and a basic org profile
  (mission, nonprofit status, budget, relevant track record).

## Getting Started

```
Score our fit for this grant: [paste decoded NOFO or link] — here's our org: [org profile]
```

Claude will:
1. Check eligibility and threshold criteria first — stop with a plain
   No-go if the org doesn't qualify
2. Score mission fit and capacity fit
3. Score competitive strength against each actual weighted review criterion
4. Rank the gaps that would need closing, by how much they're worth
5. Give a bottom-line recommendation

## Time Investment

- **First run:** 15-20 minutes (org profile is usually the slow part — worth writing once and reusing)
- **Iterations:** a few minutes per new opportunity, once the org profile exists

## Next Steps

- A "Go" or "Go with gaps" result → send the deadline to `grant-deadline-scout`
- A gap list → use it to prioritize what to build (partnerships, track record) before the next cycle

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/grant-fit-scorer)

## License

MIT. Use freely. Attribute appreciated.
