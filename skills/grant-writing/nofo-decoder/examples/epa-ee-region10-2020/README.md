# Example: EPA Environmental Education Local Grants — Region 10 (2020 cycle)

**Scenario:** Dry-run test of `nofo-decoder` against a real, publicly posted
federal NOFO — required before this skill is considered publishable (see
`../../../../TESTING.md`, Layer 2).

**Input:** The full text of EPA's Environmental Education Local Grants RFA,
Region 10 (Alaska/Idaho/Oregon/Washington), 2020 cycle — publicly archived
at
https://www.epa.gov/sites/default/files/2019-10/documents/2020_ee_local_grants_rfa_region_10_pdf_final.pdf.
This is the most recent cycle of this document with full public review-criteria
text available to Claude for testing (the current national cycle,
EPA-EE-25-01, closed March 2026 with the same structure — same 25%
cost-share, same subaward mechanic, same priority categories — confirmed via
grants.gov opportunity #361098 and EPA's program page, but its full
announcement PDF wasn't independently fetchable during this dry run). Note
this vintage clearly if reusing this example to sanity-check future runs.

**Output:** [decode.md](./decode.md)

**Result:** The skill correctly separated threshold (go/no-go) criteria from
scored merit criteria, preserved the source document's exact point math (100
points across 6 categories with sub-criteria) without re-normalizing
anything, and explicitly flagged the two fields the source RFA doesn't
directly restate elsewhere (assistance listing number, and whether a
pre-application/letter of intent is required — this Region 10 RFA doesn't
use one). No point values or eligibility terms were invented — everything in
the Merit Review table below traces to a quoted or closely paraphrased line
in the source document.
