# Dry run: Northwest Repair Directory AI visibility audit

First stage of the AI visibility chain. Northwest Repair Directory is a
fictional Oregon appliance-repair directory (`example-repair-directory.test`),
clearly labeled as a test fixture — no live connector was available, so the
benchmark values are illustrative, not live measurements. Its
`visibility_audit_output` handoff is consumed by
`../../../llms-txt-schema-starter/examples/northwest-repair-directory/`.

**Input given to the skill:** the fictional property profile, a five-query
benchmark spanning ChatGPT Search, Perplexity, Gemini, Grok, and Claude, and
an SE Ranking/DataForSEO-style export fixture with documented provenance.

See [visibility-audit.md](./visibility-audit.md) for the output.
