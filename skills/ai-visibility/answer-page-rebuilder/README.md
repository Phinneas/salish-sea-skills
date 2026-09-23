# Answer Page Rebuilder

**What:** Restructures existing pages so AI search systems and human readers can extract accurate, citable answers.
**When:** Your pages are technically crawlable but still lose — they're vague, thin, stale, or don't actually answer the questions people ask.
**Output:** A page-by-page rebuild (or change plan) with a query-to-answer map, provenance map, and a `content_visibility_output` retest handoff.

## Use Cases

- The audit shows competitors winning queries your pages should answer
- A key page buries the answer under brand copy and marketing language
- Content is stale, unsourced, or makes claims the evidence doesn't support
- You need pages that work for AI extraction without keyword stuffing or fake FAQs

## The Skill

Rebuilds pages around an answer spine: direct answer first, scope and "as of" date, method and evidence, descriptive question headings, comparisons in tables, explicit limitations. Provenance gets strengthened — author, organization identity, last-reviewed date, source links, correction path — using the canonical entity facts and JSON-LD map from the technical layer. Accuracy is non-negotiable: uncertainty, jurisdiction, pricing, and time-sensitive claims are marked, and nothing is added just to fill a schema field.

**Third skill in the AI visibility chain.** It consumes `visibility_audit_output` from `can-ai-find-you` and `technical_visibility_output` from `llms-txt-schema-starter`, then hands `content_visibility_output` back to `can-ai-find-you` for the retest.

## Prerequisites

- No connectors required — runs on Claude alone. You supply the existing page content (pasted) and the audit/technical handoffs.
- Optional: WebFetch to pull live page content from a URL instead of pasting it.

## Getting Started

```
Use the answer-page-rebuilder methodology on this page: [URL or pasted content + handoffs]
```

Claude will:
1. Prioritize pages by query gap and confirm intent and scope
2. Extract the source truth: claims, evidence, dates, authorship
3. Rebuild the answer spine — direct answer first, then support
4. Strengthen provenance and align with the structured-data map
5. Package the rebuild with a query-to-answer map and retest plan

## Time Investment

- **First run:** 2-4 hours per priority page
- **Iterations:** 30-60 minutes per additional page once the pattern is set

## Next Steps

- Deploy after editorial/business approval, then rerun the benchmark in `can-ai-find-you`
- Treat retest changes as observed outcomes, not proof of a ranking formula

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/ai-visibility/answer-page-rebuilder)

## License

MIT. Use freely. Attribute appreciated.
