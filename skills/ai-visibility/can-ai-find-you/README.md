# Can AI Find You?

**What:** Audits whether AI search products discover, mention, and cite your property for target queries — and which competitors or sources win instead.
**When:** You suspect you're invisible in ChatGPT/Claude/Perplexity/Gemini/Grok answers and want evidence, not vibes.
**Output:** A model-by-model results table, gap diagnosis, prioritized fix list, and a machine-readable `visibility_audit_output` handoff.

## Use Cases

- Customers say they "asked ChatGPT" and your organization never came up
- A competitor keeps getting cited for queries you should own
- You want a date-stamped baseline before investing in content or schema work
- Post-redesign or post-migration check that AI search still finds you

## The Skill

Builds a benchmark of 20-50 representative prompts (discovery, comparison, recommendation, local, branded), runs them across the major AI search products, and classifies every outcome — cited, mentioned-not-cited, competitor-wins, not retrieved, wrong entity, stale. Gaps are diagnosed as technical discoverability, entity clarity, content extractability, authority, freshness, or query-fit — with no claims of a universal ranking algorithm. Every run is date-stamped and model-separated.

**First skill in the AI visibility chain.** Its `visibility_audit_output` feeds `llms-txt-schema-starter` (technical fixes) and `answer-page-rebuilder` (content fixes), and you return here for the retest after deployment.

## Prerequisites

- No connectors required — runs on Claude alone with manually captured benchmark runs.
- Optional: the SE Ranking/DataForSEO AI Search visibility data layer (or its CSV/JSON export) supplies benchmark data at scale; without it, you run the prompt set manually and paste results.

## Getting Started

```
Use the can-ai-find-you methodology to audit https://example.com for these queries: [list]
```

Claude will:
1. Build a benchmark prompt set with locale, date, and model recorded
2. Load or capture results per model, classifying each outcome
3. Diagnose which gap type explains each loss
4. Rank the highest-leverage fixes
5. Hand back the audit plus a `visibility_audit_output` block

## Time Investment

- **First run:** 2-4 hours (mostly running and capturing the benchmark prompts)
- **Iterations:** about an hour for a same-query retest

## Next Steps

- Pass `visibility_audit_output` to `llms-txt-schema-starter` for the technical layer
- After technical and content fixes deploy, rerun the same benchmark here for a controlled retest

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/ai-visibility/can-ai-find-you)

## License

MIT. Use freely. Attribute appreciated.
