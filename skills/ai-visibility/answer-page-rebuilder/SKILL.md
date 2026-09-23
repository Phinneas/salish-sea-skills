---
name: answer-page-rebuilder
description: Restructure existing web pages so AI search systems and human readers can extract accurate, citable answers. Use after an AI visibility audit and technical starter pack, when pages are vague, thin, poorly structured, stale, or not aligned to the questions customers ask.
---

# Answer Page Rebuilder

Improve the **content layer**, not by writing for a mythical universal AI algorithm, but by making evidence, answers, entities, and boundaries clear to readers and retrieval systems. A page can be technically crawlable and still fail because it does not answer the query, identify the source, define terms, or support claims.

## Prerequisites

No connectors required — runs on Claude alone. You supply the existing page content and the audit/technical handoffs. WebFetch is optional for pulling live page content from a URL instead of pasting it.

## Inputs

Accept `visibility_audit_output` from **can-ai-find-you**, `technical_visibility_output` from **llms-txt-schema-starter**, existing page URLs/content, target queries, audience, jurisdiction, source documents, SME notes, and approval constraints. Preserve the original URL where possible and record redirects when not.

## Workflow

1. **Select pages by query gap.** Prioritize pages with high-value queries where the property is absent, mentioned without citation, or beaten by a competitor. Confirm search intent, audience, geography, freshness, and the page’s legitimate scope.
2. **Extract source truth.** Inventory claims, definitions, evidence, dates, authorship, methodology, limitations, and calls to action. Separate first-party facts, attributed third-party facts, expert opinion, and unsupported marketing language.
3. **Rebuild the answer spine.** Lead with a direct answer or definition; add scope and “as of” date; explain method/evidence; use descriptive H2/H3 questions; present comparisons and steps in tables or lists; include examples, caveats, and a concise conclusion. Do not bury the answer under brand copy.
4. **Strengthen provenance.** Add author/reviewer, organization identity, last-updated date, source links, methodology, contact/correction path, and relevant policy or evidence pages. Use the approved canonical entity facts and JSON-LD map; never add claims solely to fill schema fields.
5. **Optimize extractability without manipulation.** Use one clear concept per paragraph, explicit terminology, stable anchors, meaningful link text, accessible headings, and HTML text rather than image-only answers. Do not hide text, stuff queries, generate fake FAQs, or copy competitor wording.
6. **Preserve accuracy and legal safety.** Mark uncertainty, jurisdiction, eligibility, pricing, availability, and time-sensitive claims. For regulated topics, require qualified review. Do not imply that a rewritten page will be cited.
7. **Validate and package.** Compare old/new coverage, answer completeness, evidence traceability, reading accessibility, internal links, canonical URL, structured-data parity, and deployment status. Emit `content_visibility_output` with changed URLs, query coverage, unresolved facts, and the retest plan for **can-ai-find-you**.

## Required output

Provide a page-by-page change plan or revised draft, query-to-answer map, before/after claim inventory, source and provenance map, structured-data compatibility notes, approval questions, and a machine-readable handoff containing `canonical_url`, `target_queries`, `answer_blocks`, `source_refs`, `last_reviewed`, `open_risks`, and `retest_queries`.

## Quality rubric

A rebuilt page should answer the target question in the opening section, define who/what/where/when, support material claims, disclose limitations, identify the responsible source, provide useful next actions, and remain readable without JavaScript-dependent interaction. Prefer a narrow, excellent page over a broad page that makes unsupported claims.

## Next Steps: can-ai-find-you

Pass `content_visibility_output` to **can-ai-find-you** and rerun the same benchmark prompts, date-stamped and separated by model/platform. Compare mention, citation, cited-URL support, freshness, and competitor outcomes against the original baseline. Treat changes as observed outcomes, not proof of a universal ranking effect.

## References

[1]: https://schema.org/ "Schema.org vocabulary"
[2]: https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data "Google Search Central: structured data"
[3]: https://github.com/answerdotai/llms-txt "The /llms.txt proposal, v2"

## Example

See `examples/northwest-repair-directory/answer-page-rebuild.md`.
