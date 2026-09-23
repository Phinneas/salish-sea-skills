# Example: Green Thread Studio materiality interview

## Assessment frame

Green Thread Studio is a fictional 11-person apparel-repair cooperative in Portland, Oregon. The period is calendar year 2025. The boundary covers the studio, employees, contractors, repair customers, and primary material suppliers. This is an internal, GRI-informed prioritization; no assurance or certification conclusion is made.

## Impact universe

| impact_id | activity_or_relationship | topic | polarity | status | stakeholders | evidence | confidence |
|---|---|---|---|---|---|---|---|
| I-01 | Repair and reuse services | Product life extension | positive | actual | customers, environment | 1,240 repairs logged; repair tickets | high |
| I-02 | Solvent and dye handling | Chemicals and waste | negative | potential | workers, environment | purchasing log; no waste-weight baseline | medium |
| I-03 | Work scheduling and pay | Fair work and worker voice | positive/negative | actual | workers | wage sheet; two worker interviews | medium |
| I-04 | Garment intake and data capture | Customer privacy and inclusion | negative | potential | customers | intake form; no retention rule | medium |
| I-05 | Imported notions and packaging | Supply chain and materials | negative | potential | suppliers, environment | supplier list; no screening process | low |

## Materiality register

| topic | impact_ids | severity | likelihood | priority | rationale | owner | data_gaps | reporting_action |
|---|---|---:|---:|---|---|---|---|---|
| Fair work and worker voice | I-03 | 5 | 4 | high | Pay and scheduling directly affect a small workforce; worker voice is currently informal. | Operations lead | turnover, wage progression, grievance log | report current practice and next-year baseline |
| Product life extension | I-01 | 4 | 5 | high | Core service creates a documented reuse benefit, but avoided-impact methodology is not established. | Repair lead | method for avoided purchases/materials | report repair count without claiming avoided emissions |
| Chemicals and waste | I-02 | 4 | 3 | medium | Potential harm is significant for workers and environment; controls exist unevenly. | Studio manager | waste mass, incident log, SDS review | disclose controls and measurement plan |
| Supply chain and materials | I-05 | 4 | 3 | medium | Imported inputs have limited supplier visibility. | Purchasing lead | supplier geography and screening | include gap and 2026 action |
| Customer privacy and inclusion | I-04 | 3 | 3 | provisional | Data collection is limited but retention and accessibility are undocumented. | Customer lead | retention period, accessibility review | validate before public prioritization |

## Stakeholder voice

Workers asked for a predictable scheduling rule and a documented way to raise safety concerns. Customers valued repair over replacement but requested clearer accessibility information. Management initially ranked marketing reach above waste controls; the interview calibration moved chemicals and waste higher because the potential harm is more significant than brand visibility.

## Blind spots and next questions

Validate supplier labor and environmental practices, quantify waste by material type, document customer-data retention, and invite a non-management worker representative to review the ranking.

## Handoff: materiality_output

```yaml
materiality_output:
  organization: Green Thread Studio
  period: 2025
  boundary: studio, employees, contractors, customers, primary material suppliers
  framework_lens: GRI-informed impact materiality
  topics:
    - topic_id: MT-01
      name: Fair work and worker voice
      priority: high
      impact_ids: [I-03]
      source_refs: [wage-sheet-2025, worker-int-01, worker-int-02]
      confidence: medium
    - topic_id: MT-02
      name: Product life extension
      priority: high
      impact_ids: [I-01]
      source_refs: [repair-log-2025]
      confidence: high
    - topic_id: MT-03
      name: Chemicals and waste
      priority: medium
      impact_ids: [I-02]
      source_refs: [purchasing-log-2025]
      confidence: medium
    - topic_id: MT-04
      name: Supply chain and materials
      priority: medium
      impact_ids: [I-05]
      source_refs: [supplier-list-2025]
      confidence: low
    - topic_id: MT-05
      name: Customer privacy and inclusion
      priority: provisional
      impact_ids: [I-04]
      source_refs: [intake-form-v2]
      confidence: medium
  open_questions: [waste mass, supplier screening, privacy retention, accessibility]
```
