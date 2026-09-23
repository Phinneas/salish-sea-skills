# Example: Northwest Repair Directory AI visibility audit

**Property:** `https://example-repair-directory.test` (fictional test fixture)  
**Benchmark date:** 2026-08-29  
**Data source:** SE Ranking/DataForSEO-style AI Search export fixture; no live connector was available in the workspace, so values below are illustrative and explicitly not live measurements.

## Benchmark results

| Query | Platform | Mentioned | Cited | Cited URL | Winner | Diagnosis |
|---|---|---:|---:|---|---|---|
| best appliance repair directory in Oregon | ChatGPT Search | No | No | — | Yelp | directory entity not clear; no answer page |
| appliance repair companies Portland | Perplexity | Yes | No | — | Google Maps | brand mentioned in prompt context only |
| compare repair directories Portland | Gemini Search grounding | No | No | — | Angi | weak comparison content |
| repair directory Portland Oregon | Grok Web Search | No | No | — | Yelp | no concise category/location page |
| Northwest Repair Directory reviews | Claude web search | Yes | Yes | `/about` | Northwest Repair Directory | citation supports identity only |

## Gap diagnosis

The property has a crawlable-looking homepage and an about page, but the entity is not described consistently as a directory, its category/location pages lack direct answers, and no canonical methodology page explains listings or inclusion. The technical layer should expose stable canonical resources and structured identity. The content layer should build a Portland appliance-repair answer page with methodology and limitations.

## Handoff: visibility_audit_output

```yaml
visibility_audit_output:
  property: https://example-repair-directory.test
  benchmark_at: 2026-08-29
  data_source: SE Ranking/DataForSEO-style fixture
  priority_urls:
    - https://example-repair-directory.test/about
    - https://example-repair-directory.test/portland/appliance-repair
    - https://example-repair-directory.test/methodology
  canonical_entity:
    name: Northwest Repair Directory
    type: directory property
    region: Oregon
  query_gaps:
    - best appliance repair directory in Oregon
    - appliance repair companies Portland
    - compare repair directories Portland
  technical_findings:
    - no llms.txt observed in fixture
    - Organization/WebSite identity not consistently linked
    - category/location URL lacks direct answer block
  next_skill: llms-txt-schema-starter
```
