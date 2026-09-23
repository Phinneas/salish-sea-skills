---
name: meeting-minutes-compliance
description: Convert raw board, committee, or nonprofit meeting notes into accurate, review-ready governance minutes. Use when cleaning notes, separating discussion from decisions, recording motions and votes, tracking conflicts and actions, or preparing minutes for approval and retention.
---

# Meeting Minutes Compliance

Create a neutral record of what the body was authorized to do and what it actually did. Minutes are not a transcript and not a polished narrative. They should allow a later reader to establish date, participants, quorum or authority as documented, agenda actions, motions, vote results, recusals, follow-up, and approval status.

## Prerequisites

No connectors required — runs on Claude alone. You supply the raw notes, agenda, and any vote or attendance evidence; pasted text or common document formats are fine.

## Inputs

Accept raw notes, agenda, attendance/roll, prior minutes, motions, vote counts, committee reports, action log, meeting type, jurisdiction/policy references, and recorder questions. Preserve the original notes as a source; never overwrite them.

## Workflow

1. **Set the record frame.** Identify organization/body, meeting type, date, time, location or remote format, chair, recorder, expected attendees, and applicable bylaws/policy. If quorum or notice is not documented, mark it `NOT RECORDED`.
2. **Separate fact from reconstruction.** Tag each note as opening/attendance, report, discussion, motion, vote, conflict/recusal, action, adjournment, or uncertainty. Do not convert a discussion comment into a decision.
3. **Reconstruct the agenda order.** Use the approved agenda when available. Keep out-of-order business labeled. For every substantive item, record the issue, material discussion summary, motion text if any, mover/seconder only when known, vote result, abstentions/recusals, and outcome.
4. **Use neutral compression.** Summarize viewpoints without attributing motives or editorial judgment. Preserve dissent, recusals, failed motions, tabled items, and declared conflicts when documented.
5. **Extract the action register.** Convert commitments into `action_id`, owner, due date, dependency, source note, and status. Ask for owner/date when absent; never assign them silently.
6. **Run a record-integrity review.** Compare minutes against agenda, attendance, motions, vote evidence, and prior action log. Flag contradictions, missing approvals, unclear authority, confidential content, and any statement that requires recorder confirmation.
7. **Prepare approval copy.** Output draft minutes with a prominent draft status, a recorder-query list, proposed approval motion only if requested, and a retention/file-naming recommendation based on the organization’s policy.

## Output

Return draft minutes, decisions/motions table, attendance and quorum record, conflicts/recusals, action register, recorder queries, and source register. Use explicit statuses: `documented`, `not recorded`, `needs confirmation`, and `not applicable—reason supplied`.

## Governance boundary

This skill follows basic governance-record conventions; it is not a legal compliance determination. Open-meeting, notice, accessibility, public-record, retention, quorum, and minute-content requirements vary by state, locality, entity type, and governing documents. Identify the relevant rule or bylaw for qualified review rather than applying a fifty-state rule.

## Guardrails

Do not invent attendees, quorum, motions, seconds, vote counts, approvals, legal citations, or exact quotations. Do not make minutes more favorable by deleting adverse discussion, dissent, conflicts, or failed actions. Keep personal and sensitive information out of circulation copies unless necessary and authorized.

## Example

See `examples/harbor-light-food-network/board-minutes.md`.
