---
name: llms-txt-schema-starter
description: Create or repair an LLM-friendly `/llms.txt` starter pack and high-quality Schema.org JSON-LD for an organization or directory property. Use after an AI visibility audit, when improving machine-readable entity context, or when preparing technical inputs for answer-page restructuring.
---

# llms.txt + Schema Starter

Build a small, maintainable technical layer that makes important pages easier to understand and validate. `/llms.txt` is a proposed Markdown convention: it provides concise background, guidance, and links to detailed pages; it is not a guaranteed instruction channel or a substitute for crawlability, authoritative content, or search indexing.[1] Schema.org JSON-LD clarifies entities and relationships for consuming systems, but no schema type guarantees AI citation.

## Prerequisites

No connectors required — runs on Claude alone. You supply the audit handoff and canonical entity facts. WebFetch is optional for inspecting the live property (HTTPS, robots, sitemap, canonicals) instead of pasting what you observe; the deliverable ships either way.

## Inputs

Accept `visibility_audit_output` from **can-ai-find-you**, canonical organization/entity facts, domain and URL inventory, page types, contact/identity links, products/services, locations, authors, and current sitemap/robots/crawl notes. Preserve canonical URLs. Ask for confirmation before publishing anything.

## Workflow

1. **Inspect the property.** Check HTTPS, status codes, canonical tags, robots directives, sitemap, redirects, rendered text, and duplicate/near-duplicate URLs. Never use `/llms.txt` to mask an inaccessible or misleading page.
2. **Select canonical resources.** Choose a short set of durable, high-value pages: about/entity, products or services, methodology, policies, contact, locations, and answer pages. Exclude login pages, thin tag pages, tracking URLs, and unsupported claims.
3. **Draft `/llms.txt`.** Use a clear H1 title, a short blockquote summary, a brief description, and Markdown sections with linked resources. Keep descriptions factual and useful. Use absolute HTTPS links, stable titles, and no fabricated markdown extensions. If a site section is covered, place the file at the appropriate root/path and state its scope.
4. **Create JSON-LD.** Select only supported types that match the page: `Organization` or a more specific subtype for identity, `WebSite`, `WebPage`, `Article`/`TechArticle`, `FAQPage` only for genuine visible FAQs, `BreadcrumbList`, `Product`, `Service`, `LocalBusiness`, `Person`, and `ItemList` for appropriate directory/list pages. Link entities with `@id`, use canonical URLs, and ensure every material property is visible and accurate on-page.
5. **Cross-link identity.** Use `sameAs` only for verified profiles. Keep organization name, logo, URL, contact, locations, author, and service names consistent across pages. Do not add `FAQPage` or review markup merely to seek rich results or AI citations.
6. **Validate.** Check JSON syntax, schema vocabulary, required/recommended fields, visible-content parity, canonical URLs, and deployment paths. Record validator results and known limitations. Schema validation is not evidence of citation eligibility.
7. **Hand off.** Emit `technical_visibility_output` with file contents, proposed insertion points, URL map, facts requiring approval, and deployment checklist for **answer-page-rebuilder**.

## Required output

Provide `/llms.txt`, JSON-LD blocks per page type, an implementation map, validation checklist/results, unsupported-claim warnings, and a machine-readable handoff. Include `status: draft|approved|deployed`, `source_fact`, `canonical_url`, and `owner_approval` for each material fact.

## Guardrails

Do not claim that llms.txt is an adopted universal standard, that Schema.org directly controls AI ranking, or that a markup deployment will cause citation. Do not expose personal data, hidden text, keyword stuffing, fake reviews, or claims absent from visible pages. Use current official documentation and verify schema types against Schema.org and search-engine guidelines.[2][3]

## Next Steps: answer-page-rebuilder

Pass `technical_visibility_output` to **answer-page-rebuilder**. It should use the canonical facts, URL map, entity model, and audit query gaps to restructure existing pages for direct, extractable answers. Once those pages are deployed, return to **can-ai-find-you** for the same-query retest.

## References

[1]: https://github.com/answerdotai/llms-txt "The /llms.txt proposal, v2"
[2]: https://schema.org/ "Schema.org vocabulary"
[3]: https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data "Google Search Central: structured data"

## Example

See `examples/northwest-repair-directory/technical-starter.md`.
