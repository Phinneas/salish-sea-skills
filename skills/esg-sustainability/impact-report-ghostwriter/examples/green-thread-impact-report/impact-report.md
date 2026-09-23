# Green Thread Studio Impact Report Draft

**Reporting period:** 1 January–31 December 2025  
**Status:** Working draft for owner review  
**Framework language:** GRI-informed; not a report in accordance with GRI and not assured

## About this report

This report describes Green Thread Studio’s 2025 activities, impacts, management practices, and next priorities. The boundary covers the Portland studio, employees, contractors, repair customers, and primary material suppliers. The report was drafted from the 2025 repair log, wage sheet, worker interviews, purchasing log, supplier list, and customer intake form. Several data gaps remain open and are listed at the end.

## Our organization and impact context

Green Thread Studio is an 11-person apparel-repair cooperative. Its principal impact opportunity is extending garment life through repair and reuse. Its principal management challenges are maintaining fair work and worker voice, controlling chemical and waste risks, and improving visibility into suppliers and customer-data practices.

## How we determined material topics

The material-topic shortlist was developed through an interview-informed review of actual and potential impacts, affected stakeholders, evidence strength, and significance. The process was GRI-informed and retained a distinction between impacts and organizational responses. Topics were not selected solely because they affect reputation or financial performance.

## Material topics at a glance

| Topic | Why it matters | 2025 evidence | Confidence |
|---|---|---|---|
| Fair work and worker voice | Direct effect on a small workforce | wage sheet and two worker interviews | Medium |
| Product life extension | Core service benefit for customers and resource use | 1,240 repair tickets | High |
| Chemicals and waste | Potential worker and environmental harm | purchasing log; no waste baseline | Medium |
| Supply chain and materials | Limited visibility into imported inputs | supplier list | Low |
| Customer privacy and inclusion | Intake data practices and accessibility are not documented | intake form | Medium |

## Material topic: Product life extension

Green Thread recorded **1,240 repairs** in 2025. The repair log is a count of completed jobs; it does not establish the number of purchases avoided, material or emissions savings, or a causal environmental benefit. The studio will define a conservative method in 2026, document assumptions, and report the method before making avoided-impact claims.

## Material topic: Fair work and worker voice

Workers identified predictable scheduling and a documented safety-concern process as priorities. The wage sheet provides a current-period view of pay, but the studio does not yet have a consistent turnover, wage-progression, or grievance dataset. The operations lead will propose a scheduling rule and worker feedback mechanism for approval in Q1 2026.

## Material topic: Chemicals and waste

The studio’s purchasing records indicate solvent and dye use, but waste mass, disposal route, and incident data are not yet measured consistently. The studio will create a chemical inventory, review safety data sheets, weigh relevant waste streams quarterly, and assign a studio-manager owner. Until that baseline exists, the studio will not claim waste reduction.

## Material topic: Supply chain and materials

The supplier list identifies primary material suppliers but does not yet capture geography, labor safeguards, or environmental screening. In 2026, the purchasing lead will add supplier location, screening questions, and evidence fields to the purchasing register.

## Material topic: Customer privacy and inclusion

The intake form collects limited customer information, but retention and accessibility practices are undocumented. The customer lead will define a retention period, limit access, and conduct an accessibility review before the topic is finalized as a public priority.

## Progress, setbacks, and next-period priorities

The strongest result is a complete repair count for the reporting period. The largest limitation is that the studio has more evidence of activity than of outcomes. In 2026, priorities are to establish waste and worker indicators, improve supplier evidence, document customer-data practices, and publish a method before making avoided-impact claims.

## Limitations and data notes

The report uses a small-organizational boundary and a single reporting period. No external assurance was performed. Repair counts are activity data, not avoided-impact estimates. Worker evidence is based on two interviews and may not represent every worker. Supplier and waste data are incomplete.

## Open items for approval

| Item | Owner | Required evidence |
|---|---|---|
| Approve scheduling and worker-voice action | Operations lead | adopted rule and feedback process |
| Confirm chemical and waste baseline plan | Studio manager | inventory, SDS review, weighing method |
| Confirm supplier screening fields | Purchasing lead | revised supplier register |
| Approve privacy retention and accessibility review | Customer lead | policy and review record |

## Source traceability

| Claim | Source |
|---|---|
| 1,240 repairs | repair-log-2025 |
| 11-person organization | organization-profile-2025 |
| worker priorities | worker-int-01; worker-int-02 |
| chemical/dye exposure area | purchasing-log-2025 |
| supplier visibility gap | supplier-list-2025 |
| intake-data gap | intake-form-v2 |

## Handoff: report_output

```yaml
report_output:
  organization: Green Thread Studio
  period: 2025
  framework_language: GRI-informed
  material_topic_ids: [MT-01, MT-02, MT-03, MT-04, MT-05]
  metrics:
    - name: completed repairs
      value: 1240
      source_ref: repair-log-2025
      caveat: activity count; not an avoided-impact estimate
  unresolved_items: [waste baseline, worker indicators, supplier screening, privacy retention, accessibility]
```
