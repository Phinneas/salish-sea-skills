# Greenwashing Check

**What:** Audits environmental/sustainability marketing claims against the FTC Green Guides (16 CFR Part 260) and rates each claim's substantiation status and legal risk.
**When:** Before any "sustainable," "eco-friendly," "recyclable," "carbon neutral," or similar claim ships — on a website, in a report, or on packaging.
**Output:** A claim-by-claim audit — quote, claim type, substantiation status, risk level, and a specific fix.

## Use Cases

- You're about to publish a sustainability page or annual report and want a substantiation check before it goes live
- A board member or client asks "can we actually say this" about a specific line of copy
- You inherited marketing copy with environmental language and don't know what's actually defensible
- You want to know which of your claims look like the patterns that have drawn real FTC/SEC action or class-action suits (Keurig, Kohl's, Colgate, and others)

## The Skill

This skill runs each environmental claim in your text through the FTC
Green Guides (16 CFR 260.4 through 260.17) — the actual federal standard
courts and the FTC use to evaluate this language — rather than giving a
vibes-based "sounds greenwashy" read. It pays particular attention to two
patterns behind most real enforcement: unqualified general claims
("sustainable," "eco-friendly," "green") that the FTC has flagged as
inherently hard to substantiate, and claims that are technically true
about a raw material but not true about the finished product as the
customer actually experiences it (the exact pattern behind Keurig's 2024
SEC penalty over "100% recyclable" K-Cup pods).

Shares its research grounding with `scope-inventory` (same build session)
but runs independently — you don't need a GHG inventory to use this. If a
claim needs real substantiation you don't have yet (a footprint baseline,
a reduction number), it'll point you to `scope-inventory`.

**This is a substantiation and risk screen, not legal advice** — anything
it rates High risk should go to an attorney before it ships.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply the text (paste it) or a URL. If you give a URL, Claude uses
  `WebFetch`; if the page is JS-rendered and only partially loads, it'll
  say so rather than audit content it didn't actually retrieve.

## Getting Started

```
Run a greenwashing check on this: [paste text or link]
```

Claude will:
1. Pull the full text if given a link
2. Extract every discrete environmental claim, quoted verbatim
3. Classify each against the specific Green Guides provision that applies
4. Rate substantiation status (Substantiated / Unsubstantiated / Unclear) and risk (High/Medium/Low)
5. Give a specific rewrite or fix for anything rated Medium or High risk

## Time Investment

- **First run:** 15-30 minutes for a typical page or report section
- **Iterations:** a few minutes to re-check after edits

## Next Steps

- Send anything rated High risk to an attorney before it ships
- If a claim needs real backing you don't have, run `scope-inventory` to build it

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/esg-sustainability/greenwashing-check)

## License

MIT. Use freely. Attribute appreciated.
