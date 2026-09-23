# Dry run: Northwest Repair Directory answer-page rebuild

Final stage of the chain. Rebuilds the fictional directory's
`/portland/appliance-repair` page from the `visibility_audit_output` and
`technical_visibility_output` handoffs: direct answer first, listing
methodology, explicit limitations, and a provenance block — with no invented
rankings or unsupported claims. Emits `content_visibility_output` with retest
queries for `../../../can-ai-find-you/examples/northwest-repair-directory/`.

**Input given to the skill:** both handoffs plus the target page's existing
content and the three priority queries from the audit.

See [answer-page-rebuild.md](./answer-page-rebuild.md) for the output.
