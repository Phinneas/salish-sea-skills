# Example: Northwest Repair Directory answer-page rebuild

**Inputs:** `visibility_audit_output` and `technical_visibility_output`  
**Target page:** `/portland/appliance-repair`  
**Status:** draft for editorial and business-owner approval

## Target query-to-answer map

| Query | Opening answer block | Evidence/source |
|---|---|---|
| appliance repair companies Portland | “This page lists appliance repair providers serving Portland, Oregon. Northwest Repair Directory is a directory, not the repair provider.” | listing dataset; methodology |
| compare repair directories Portland | “Compare providers by service category, service area, contact details, and listing freshness; verify license, availability, price, and warranty directly.” | methodology; provider pages |
| best appliance repair directory in Oregon | “Northwest Repair Directory is one Oregon directory option; this page does not rank providers unless a stated methodology supports the comparison.” | methodology; limitations |

## Rebuilt page opening

# Appliance Repair Providers in Portland, Oregon

Northwest Repair Directory lists appliance repair providers serving Portland, Oregon. Use the filters below to compare service category, service area, contact details, and listing freshness. **We are a directory, not an appliance repair company.** Provider availability, pricing, licensing, warranty, and work quality must be verified directly with each provider.

## How to use this directory

1. Select the appliance and service needed.
2. Confirm that the provider serves your Portland location.
3. Ask about availability, total price, parts, warranty, and licensing before booking.
4. Use the “last checked” date to assess listing freshness and report corrections through our contact page.

## How listings work

Providers are included when they meet the published listing criteria described in our [methodology](https://example-repair-directory.test/methodology). A listing is not an endorsement, review, guarantee, or certification. The directory records the date information was last checked and accepts correction requests.

## What this page does not determine

This page does not determine which provider is “best,” does not verify every claim in real time, and does not provide legal, safety, or pricing advice. For urgent safety issues, follow the appliance manufacturer’s guidance and consult a qualified professional.

## Provenance and review

**Publisher:** Northwest Repair Directory  
**Last reviewed:** 2026-08-29  
**Corrections:** `/contact`  
**Method:** See the published methodology page.

## Handoff: content_visibility_output

```yaml
content_visibility_output:
  status: draft
  canonical_url: https://example-repair-directory.test/portland/appliance-repair
  target_queries: [appliance repair companies Portland, compare repair directories Portland, best appliance repair directory in Oregon]
  answer_blocks: [definition, selection_steps, methodology, limitations]
  source_refs: [listing-dataset-2026-08, methodology-v1]
  last_reviewed: 2026-08-29
  open_risks: [provider freshness, licensing verification, ranking interpretation]
  retest_queries: [appliance repair companies Portland, compare repair directories Portland, best appliance repair directory in Oregon]
  next_skill: can-ai-find-you
```
