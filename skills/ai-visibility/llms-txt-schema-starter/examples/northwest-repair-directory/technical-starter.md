# Example: Northwest Repair Directory technical starter

**Input:** `visibility_audit_output` from `can-ai-find-you`  
**Status:** draft for owner approval  
**Next skill:** `answer-page-rebuilder`

## Proposed `/llms.txt`

```markdown
# Northwest Repair Directory

> A directory of appliance repair providers serving Oregon, with a focus on clear service categories, locations, and listing methodology.

Northwest Repair Directory helps people find and compare appliance repair providers. The directory does not itself perform repairs and does not guarantee provider availability, pricing, licensing, or outcomes.

## Core resources
- [About Northwest Repair Directory](https://example-repair-directory.test/about): entity, scope, and contact information.
- [Portland appliance repair](https://example-repair-directory.test/portland/appliance-repair): providers listed for the Portland area.
- [How listings work](https://example-repair-directory.test/methodology): inclusion, updates, and limitations.
```

## Proposed JSON-LD for `/about`

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://example-repair-directory.test/#organization",
  "name": "Northwest Repair Directory",
  "url": "https://example-repair-directory.test/",
  "description": "A directory of appliance repair providers serving Oregon.",
  "areaServed": {"@type": "State", "name": "Oregon"},
  "contactPoint": {"@type": "ContactPoint", "contactType": "customer service", "url": "https://example-repair-directory.test/contact"}
}
```

## Implementation and validation

| Item | Proposed action | Status |
|---|---|---|
| `/llms.txt` | publish at domain root with stable HTTPS links | owner approval |
| Identity | link Organization `@id` from WebSite and WebPage | draft |
| Methodology | publish visible listing/inclusion method | content handoff |
| Schema | validate JSON-LD syntax and Rich Results Test eligibility where applicable | pending deployment |
| Accuracy | confirm description, region, contact URL, and disclaimer | owner approval |

## Handoff: technical_visibility_output

```yaml
technical_visibility_output:
  status: draft
  canonical_entity_id: https://example-repair-directory.test/#organization
  canonical_urls:
    - https://example-repair-directory.test/about
    - https://example-repair-directory.test/portland/appliance-repair
    - https://example-repair-directory.test/methodology
  approved_facts_needed: [directory scope, contact URL, listing methodology]
  proposed_assets: [root/llms.txt, about/organization-jsonld]
  content_priorities: [direct Portland category answer, comparison limitations, listing freshness]
  next_skill: answer-page-rebuilder
```
