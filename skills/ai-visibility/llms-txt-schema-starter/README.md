# llms.txt + Schema Starter Pack

**What:** Creates or repairs an LLM-friendly `/llms.txt` and accurate Schema.org JSON-LD for the pages and entities an AI visibility audit flagged.
**When:** The audit says machines can't tell who you are — inconsistent entity, no canonical URLs, no structured data — and you need the technical layer fixed first.
**Output:** A draft `/llms.txt`, per-page JSON-LD blocks, an implementation map, validation results, and a `technical_visibility_output` handoff.

## Use Cases

- An AI visibility audit found entity ambiguity or missing machine-readable context
- You're launching a site and want `/llms.txt` and JSON-LD right from day one
- Existing schema markup is stale, inaccurate, or doesn't match visible content
- You need a canonical URL map before restructuring content

## The Skill

Builds a small, maintainable technical layer: a `/llms.txt` with a factual summary and stable links to your canonical resources, plus JSON-LD using only schema types that match what's actually visible on each page (`Organization`, `WebSite`, `WebPage`, `Article`, `BreadcrumbList`, `LocalBusiness`, and friends), linked by `@id`. Honest about limits: `/llms.txt` is a proposed convention, and no schema type guarantees AI citation — this layer makes you legible, not ranked.

**Second skill in the AI visibility chain.** It consumes `visibility_audit_output` from `can-ai-find-you` and emits `technical_visibility_output` for `answer-page-rebuilder`.

## Prerequisites

- No connectors required — runs on Claude alone. You supply the audit handoff and canonical entity facts (name, URLs, contact, locations, services).
- Optional: WebFetch to inspect the live property (HTTPS, robots, sitemap, canonicals) instead of pasting what you observe.

## Getting Started

```
Use the llms-txt-schema-starter methodology on our site: [audit output + entity facts]
```

Claude will:
1. Inspect the property's crawlability and canonical setup
2. Select the short list of durable, high-value canonical pages
3. Draft `/llms.txt` with factual descriptions and absolute links
4. Create JSON-LD per page type with consistent `@id` identity
5. Deliver an implementation map, validation checklist, and deployment handoff

## Time Investment

- **First run:** 1-3 hours
- **Iterations:** under an hour when facts or pages change

## Next Steps

- Deploy with owner approval, then pass `technical_visibility_output` to `answer-page-rebuilder`
- After content ships, return to `can-ai-find-you` for the same-query retest

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/ai-visibility/llms-txt-schema-starter)

## License

MIT. Use freely. Attribute appreciated.
