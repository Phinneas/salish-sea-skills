# Example: Illustrative small nonprofit × EPA EE Region 10 (2020 cycle)

**Scenario:** Demonstrates `grant-fit-scorer` scoring a realistic small
nonprofit against the real decoded NOFO from `nofo-decoder`'s dry run
(`../../nofo-decoder/examples/epa-ee-region10-2020/decode.md`).

**Org used:** "Cascade Watershed Alliance" is an illustrative example
organization, not a real Salish Sea Consulting client — built to be a
realistic small-nonprofit test case (small budget, real strengths, real
capacity gaps) since no real client data was available for this dry run. Per
`CONTRIBUTING.md`'s example guidance, real client scenarios used in future
examples should be anonymized; this one is synthetic from the start.

**Input:** The decoded EPA EE Region 10 NOFO + the org profile below.

```
Org: Cascade Watershed Alliance
Type: 501(c)(3), incorporated in Oregon (within EPA Region 10)
Annual budget: $220,000
Staff: 2 part-time program staff + a volunteer coordinator
Programs: Youth stream water-quality monitoring (3 local schools);
  small-scale riparian stewardship/restoration days
Prior grants: One completed 2-year Oregon state watershed council grant
  ($40,000, no subaward component) — no prior federal (EPA or otherwise)
  assistance agreements
Partnerships: Informal working relationship with one local school district
  and a regional land trust; no signed partnership letters yet
Available match funds: ~$15,000 cash reserves earmarked for program growth,
  plus an estimated $10,000 in-kind (staff time, volunteer hours) if a
  project were awarded
Experience with subawards: None — has never distributed or managed
  subgrants to third parties
```

**Output:** [fit-assessment.md](./fit-assessment.md)

**Result:** The skill correctly gated on eligibility (org passes: eligible
entity type, located in-region) before scoring competitive fit, then
produced a "Go with gaps" rather than a rosy "Go" or a blanket "No-go" — it
named the mismatch between the org's available match ($25,000 total against
a $100,000 award's required $25,000 minimum, which only works at the lower
end of the award range) and, more sharply, flagged that the org has zero
experience with the mandatory subaward mechanism, which is both a threshold
requirement and worth real review points. No numeric win probability was
invented anywhere in the output.
