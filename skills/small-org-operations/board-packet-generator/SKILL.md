---
name: board-packet-generator
description: Assemble a decision-ready nonprofit or small-organization board packet from source documents, reports, agendas, and action logs. Use when preparing board meeting materials, consent agendas, committee reports, executive summaries, or pre-read packets from scattered files.
---

# Board Packet Generator

Build a packet that lets directors prepare before the meeting and decide during it. Do not simply concatenate files. The packet must expose the decision, context, recommendation, financial or operational implication, risk, and requested action for every substantive item.

## Prerequisites

No connectors required — runs on Claude alone. You supply the meeting frame and source documents; DOCX, PDF, spreadsheets, Markdown, or pasted text are all accepted.

## Inputs

Accept the meeting date, agenda or draft agenda, prior minutes, action register, executive/committee reports, financial statements or dashboard, proposals, policies, correspondence, and packet deadline. Accept DOCX, PDF, spreadsheets, Markdown, or pasted text after inspecting the structure.

## Workflow

1. **Freeze the meeting frame.** Confirm board/committee, date, time zone, attendees expected, packet owner, approval deadline, and whether items are for decision, discussion, information, or consent.
2. **Inventory sources.** Record filename, owner, period, version/date, confidentiality, and whether the source is final. Do not silently use an outdated draft when a conflict exists.
3. **Design the agenda spine.** Put consent items together; separate strategic decisions from routine reports; assign realistic time boxes; and place the highest-consequence decision early enough to receive full discussion.
4. **Create a one-page cover memo.** Summarize the meeting purpose, decisions requested, major changes since last meeting, financial/runway signal, risks requiring board attention, and items deferred. Link each statement to a source.
5. **Build decision briefs.** For every decision, include the exact motion or approval language, recommendation, alternatives considered, evidence, budget/authority impact, risks, implementation owner, and what happens if the board takes no action. Mark unresolved questions.
6. **Compress reports.** Convert long reports into a short executive summary plus a clearly labeled appendix. Preserve material exceptions, adverse trends, and dissent; do not bury bad news.
7. **Reconcile governance records.** Carry forward unresolved prior actions, identify the proposed owner and due date, and flag minutes or approvals that are missing rather than fabricating them.
8. **Run a release check.** Check agenda numbering, cross-references, page labels, dates, financial periods, confidentiality, accessibility, and whether every decision has a clear ask. Produce a packet index and open-items list.

## Output

Return a packet index, cover memo, time-boxed agenda, decision briefs, consent agenda, executive summaries, appendices/source register, action follow-up, and release checklist. Use fields `item_id`, `type`, `purpose`, `decision_or_ask`, `owner`, `source_refs`, `financial_impact`, `risk`, `time_box`, and `status`.

## Guardrails

Do not invent motions, votes, quorum, attendees, approvals, financial figures, or legal conclusions. Label proposed language as `DRAFT MOTION`. Open-meeting, notice, retention, and public-record rules vary by jurisdiction; identify the applicable state/local policy for verification rather than asserting a universal rule. Redact sensitive personal data from circulation copies.

## Example

See `examples/harbor-light-food-network/board-packet.md`.
