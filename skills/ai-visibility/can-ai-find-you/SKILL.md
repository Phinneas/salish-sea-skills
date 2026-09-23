---
name: can-ai-find-you
description: Audit whether AI search experiences discover, mention, and cite an organization or directory property for target queries, which sources win instead, and what technical or content gaps explain the result. Use for AI visibility audits across ChatGPT, Claude, Perplexity, Gemini, and Grok, especially when SE Ranking/DataForSEO AI Search visibility data is available.
---

# Can AI Find You?

Run an evidence-based AI visibility audit. Measure **retrieval and citation outcomes**, not vague “AI readiness.” AI search products can use different indexes, retrieval systems, browsing tools, freshness windows, and citation policies; there is no universal ranking rule. Treat model behavior as observational and time-stamped.

## Prerequisites

No connectors required — runs on Claude alone with manually captured benchmark runs. Optional: the SE Ranking/DataForSEO AI Search visibility data layer (the `seranking-dataforseo` connector, or its CSV/JSON export) supplies benchmark data at scale; without it, you run the prompt set manually and paste results.

## Inputs

Accept the property/domain, target audience and geography, query set, competitors, reporting period, crawl/indexability notes, and exported or connected SE Ranking/DataForSEO AI Search visibility data. Reuse the existing `seranking-dataforseo` data layer when available; do not invent a parallel endpoint, metric, or connector. If the connector is unavailable, accept its CSV/JSON export and clearly label the data source and timestamp.

## Workflow

1. **Define the benchmark.** Create 20–50 representative prompts across discovery, comparison, recommendation, local, problem-solving, and branded intent. Record locale, device/context, date, model/product, and expected entity names.
2. **Load visibility data.** Prefer SE Ranking/DataForSEO fields for prompt, platform/model, mention, cited URL, citation position, competitor, visibility/share, and timestamp. Preserve raw IDs and query text.
3. **Validate with controlled runs.** Where access is available, run the same prompt family across ChatGPT Search, Claude web search, Perplexity, Gemini with Google grounding, and Grok web search. Capture the exact response, cited URLs, whether the property is mentioned, and whether the cited page actually supports the claim. Never treat one run as a stable ranking.
4. **Classify the outcome.** Use `cited`, `mentioned_not_cited`, `competitor_wins`, `not_retrieved`, `wrong_entity`, `stale_or_inaccurate`, and `insufficient_evidence`. Distinguish first-party citation from third-party citation.
5. **Diagnose the gap.** Separate technical discoverability, entity clarity, content extractability, authority/provenance, freshness, and query-fit hypotheses. Do not claim causality from correlation alone.
6. **Produce the handoff.** Rank the highest-leverage fixes and pass a structured `visibility_audit_output` to `llms-txt-schema-starter`, including domains/pages, query gaps, technical findings, entity facts, and citations to preserve.

## Required output

Return an audit frame, data provenance, model-by-model results table, competitor-winner table, gap diagnosis, prioritized recommendations, query backlog, and a machine-readable handoff. At minimum include `query`, `platform`, `run_at`, `mentioned`, `cited`, `cited_url`, `winner`, `support_check`, `source`, and `confidence`.

## Model-specific guardrails

Do not present ChatGPT, Claude, Perplexity, Gemini, or Grok as sharing one crawler or citation algorithm. Public documentation confirms that ChatGPT Search may expose citations, Anthropic web search returns citations, Gemini can ground responses in Google Search, Perplexity emphasizes citations, and Grok’s web-search tools return source URLs; these are product/tool behaviors, not guarantees that any page will be selected.[1][2][3][4][5] Report the observed retrieval path rather than asserting hidden ranking factors.

## Next Steps: llms-txt-schema-starter

Pass `visibility_audit_output` to **llms-txt-schema-starter**. It should use the audit’s canonical facts, prioritized URLs, entity ambiguities, and technical findings to create or repair `/llms.txt`, JSON-LD, and validation notes. After the technical and content fixes are deployed, return to **can-ai-find-you** for a retest.

## References

[1]: https://help.openai.com/articles/9237897-chatgpt-search "Searching the web with ChatGPT"
[2]: https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/web-search-tool "Anthropic web search tool"
[3]: https://ai.google.dev/gemini-api/docs/google-search "Grounding with Google Search"
[4]: https://www.perplexity.ai/hub/products/search "Perplexity Search"
[5]: https://docs.x.ai/developers/tools/web-search "Grok Web Search"
[6]: https://github.com/answerdotai/llms-txt "llms.txt proposal and current status"

## Example

See `examples/northwest-repair-directory/visibility-audit.md`.
