# Dry run: Northwest Repair Directory technical starter

Second stage of the chain. Consumes the `visibility_audit_output` from
`../../../can-ai-find-you/examples/northwest-repair-directory/` and drafts the
technical layer for the fictional directory: a root `/llms.txt`, Organization
JSON-LD with a stable `@id`, and an implementation/validation checklist —
explicitly without claiming that llms.txt or schema guarantee citation. Emits
`technical_visibility_output` for
`../../../answer-page-rebuilder/examples/northwest-repair-directory/`.

**Input given to the skill:** the audit handoff — priority URLs, entity
ambiguities, and canonical facts needing owner approval.

See [technical-starter.md](./technical-starter.md) for the output.
