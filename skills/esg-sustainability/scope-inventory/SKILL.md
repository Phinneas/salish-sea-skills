---
name: scope-inventory
description: >-
  Builds a starter Scope 1/2/3 greenhouse gas inventory for a small
  organization, grounded in the GHG Protocol Corporate Accounting and
  Reporting Standard and Corporate Value Chain (Scope 3) Standard. Produces
  a screening-level emissions table (by scope and category), states which
  figures are measured vs. estimated, and flags what a formal/assured
  inventory would still need. Use whenever the user asks to "build our
  carbon inventory," "estimate our emissions," "figure out our carbon
  footprint," "what's our Scope 1/2/3," wants a starting point for CDP,
  SBTi, a B Corp assessment, or a client/grant application asking for GHG
  data, or says something like "we've never measured our emissions, where
  do we even start" — even if they never say "Scope 1/2/3" or "GHG
  inventory" by name. Do NOT use this for auditing marketing claims about
  emissions or sustainability (that's `greenwashing-check`) or for a full
  materiality-driven ESG report (that's `materiality-interview` /
  `impact-report-ghostwriter`).
---

# Scope Inventory

## Overview

Small organizations are increasingly asked for a carbon footprint — by a
grant funder, a corporate customer's supply-chain questionnaire, a B Corp
assessment, or their own board — and most have never measured one and don't
have a sustainability staffer to build one. This skill produces a
**starter, screening-level GHG inventory**: Scope 1 (direct emissions),
Scope 2 (purchased electricity/heat), and a materiality-screened slice of
Scope 3 (value chain), using whatever real activity data the org can
supply, with every figure labeled as measured, estimated, or screened out
as immaterial. It does not fabricate precision the underlying data doesn't
support, and it says plainly where it stops short of an assurance-grade
inventory.

This skill shares its regulatory grounding with `greenwashing-check`
(same research session) but is not sequentially chained to it — an org
can run this on its own. If the org later wants to make public claims
based on this inventory ("we're tracking our footprint," "X% renewable"),
route those claims through `greenwashing-check` before they're published.
For a fuller ESG narrative built around this data, the next skill in the
chain is `materiality-interview`.

The GHG Protocol Corporate Standard is explicit that organizations should
set their boundaries and be transparent about method and data quality
rather than chase false precision — a defensible screening-level inventory
with clearly flagged estimates is more useful (and more honest) than a
falsely precise number built on guesses. This skill follows that
philosophy throughout: ask for real data first, use a disclosed estimation
method when data isn't available, and never present an estimate as if it
were measured.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** basic org facts — what the org does, roughly how
  many staff/FTEs, whether it leases or owns its space(s), and whether it
  operates any vehicles. If any of this is missing, ask before proceeding;
  don't guess at organizational boundary or scope.
- **Required input (partial is fine):** whatever activity data the org
  actually has — electricity bills (kWh or $ spent, and utility/provider
  if known), **who controls the heating for their space** (org-controlled
  gas/oil combustion is Scope 1; org-paid electric heat is already in the
  Scope 2 bill; landlord-provided/included heat is Scope 3 Category 8 —
  ask this explicitly, don't infer it from "leases an office"), vehicle
  fuel or mileage, business travel (flights, hotel nights, rental cars,
  and mileage for *any* org-business driving in a personal vehicle — see
  Process step 2 on the Category 6/7 distinction), typical employee
  commute patterns and **how many weeks a year the org is actually
  operating** (account for holidays/PTO — ask, or state the assumption
  explicitly if the org doesn't know), and major purchased goods/services
  categories. The org will rarely have all of this — that's expected.
  Ask for what exists; don't block on what doesn't, but do ask the
  heating-control and work-weeks questions directly rather than silently
  assuming an answer, since both change which scope a number lands in or
  how large it is.
- **Optional tool:** `WebFetch`/`WebSearch`, to look up the org's eGRID
  subregion from its ZIP/utility (for Scope 2 location-based factors) or
  to confirm current EPA emission factor values if the ones on hand seem
  stale. If unavailable, use the most recent EPA GHG Emission Factors Hub
  values you have and say which year's factors were used.

## Process

1. **Confirm organizational and operational boundaries.** For a
   single-entity small org this is usually trivial — the whole
   organization, operational control approach — but ask rather than
   assume if the org has multiple locations, a fiscal sponsor, or a
   parent/affiliate structure. State the boundary and approach chosen
   (equity share / financial control / operational control — operational
   control is the default for a small org with no ownership complexity,
   meaning the org accounts for 100% of emissions from operations it has
   the authority to set policy for, regardless of ownership share) at
   the top of the output. Also confirm the **reporting period** (which
   12 months, or which fiscal year) before finalizing the output — don't
   silently assume "the last 12 months" if the org hasn't said so.

2. **Screen all 15 Scope 3 categories for relevance before calculating
   any of them.** The 15 categories (GHG Protocol Corporate Value Chain
   Standard) are: upstream — (1) purchased goods and services, (2)
   capital goods, (3) fuel- and energy-related activities not already in
   Scope 1/2, (4) upstream transportation and distribution, (5) waste
   generated in operations, (6) business travel, (7) employee commuting,
   (8) upstream leased assets; downstream — (9) downstream transportation
   and distribution, (10) processing of sold products, (11) use of sold
   products, (12) end-of-life treatment of sold products, (13) downstream
   leased assets, (14) franchises, (15) investments. For a typical small
   service-based org (consultancy, nonprofit, small retailer with no
   manufacturing), categories 6 (business travel), 7 (commuting), 1
   (purchased goods/services), and 5 (waste) are usually the only
   material ones — the rest are usually genuinely not applicable (no
   products sold downstream, no franchises, no investment portfolio) and
   should be marked "screened out — not applicable" with a one-line
   reason, not silently dropped. Don't calculate a category with no
   plausible relevance just to look thorough.

   **Category 6 vs. Category 7, specifically:** an employee driving their
   *own* car to a field site or client meeting on org business (even
   informally, even without a company travel policy) is Category 6
   (business travel), not Category 7. Category 7 is only the routine
   home-to-regular-workplace commute. Mileage reimbursed at the IRS
   business rate is a strong signal it's Category 6. Don't lump the two
   together just because both involve a personal vehicle.

   **A category can be material but still unquantifiable** — that's a
   different state from "not applicable" and the output must not
   conflate them (see step 6). A small org very often has *no* data at
   all for Category 1 (purchased goods/services) or Category 5 (waste)
   — that doesn't mean the category is immaterial, and marking it
   "screened out" the same way you'd mark a genuinely inapplicable
   category (e.g. no franchises) would understate the footprint by
   omission. Keep these visibly distinct.

3. **Collect activity data for Scope 1, Scope 2, and the material Scope 3
   categories.** Ask directly for each data point named in Prerequisites.
   When the org has a number, use it. When they don't, say so and move to
   step 4's estimation fallback for that line only — don't stall the
   whole inventory waiting for data that isn't coming.

4. **Apply emission factors, activity-based where data supports it,
   spend-based as the disclosed fallback.**
   - **Scope 1:** EPA GHG Emission Factors Hub combustion factors (by
     fuel type) applied to actual fuel/mileage data. If the org has no
     Scope 1 sources (no owned vehicles, no on-site combustion — common
     for an office-based small org), state Scope 1 as zero/not applicable
     rather than omitting it.
   - **Scope 2:** report *both* methods where possible, per GHG Protocol
     Scope 2 Guidance — **location-based** (grid-average emission factor
     for the org's eGRID subregion, from EPA's eGRID data) and
     **market-based** (utility-specific emission rate or renewable energy
     certificates, if the org has a green power contract or RECs). If
     only one method is feasible, report location-based and say why
     market-based wasn't available (e.g., "no supplier-specific rate or
     REC documentation provided").
   - **Scope 3:** activity-based (actual miles, actual spend by verified
     category, actual waste tonnage) where the org has it; EPA Supply
     Chain GHG Emission Factors (spend-based, by NAICS/sector $-spend) as
     the fallback for purchased goods/services when no activity data
     exists. Always say which method was used per line.

5. **Total and tabulate**, converting all gases to CO2e using EPA's GHG
   Emission Factors Hub global warming potentials, by scope and by
   category, with a grand total. Most Emission Factors Hub tables report
   directly in CO2e; a few (notably some mobile-combustion/mileage
   factors) report CO2-only and require adding CH4/N2O separately via
   their GWPs. If you use a factor and aren't certain it's already CO2e,
   say so in the emission-factor-source cell (e.g. "EPA mobile combustion
   factor, CO2-only — CH4/N2O not added") rather than silently treating
   it as complete.

6. **Label every scope 3 category and every figure's data quality using
   three distinct states — don't collapse them into two:**
   - **Included — Measured/Estimated** (a number is calculated, from a
     bill/receipt/logged activity or a disclosed estimation method).
   - **Included — not quantified (data gap)**: the category is plausibly
     material but the org has no data and no defensible estimation basis
     for it. This is *not* the same as "screened out" and must say so —
     e.g. "Category 1 (purchased goods & services): likely material, not
     quantified — no spend-by-category data available." Never let a data
     gap read as a materiality finding.
   - **Screened out — not applicable** (the category genuinely doesn't
     exist for this org, with a one-line reason, e.g. "no franchises").
   Never present an estimated figure without its label, and never round
   or format an estimate to imply precision it doesn't have (e.g. don't
   report "14,283.6 kg CO2e" from a spend-based estimate — report
   "~14,300 kg CO2e (estimated)"). State the grand total as a **partial**
   total when any material category is in the "not quantified" state —
   don't let a total that excludes a known-material category read as a
   complete footprint.

7. **Write the limitations section.** State plainly: this is a
   screening-level starter inventory, not third-party verified or
   assured, and — if the org's actual use case needs one — not a
   substitute for a full CDP, SBTi, or formal regulatory-grade inventory,
   which requires more rigorous data collection, category coverage, and
   (usually) third-party assurance. Say what would need to change to get
   there (more complete activity data, assurance review, full Scope 3
   category coverage rather than a materiality screen).

## Output format

```markdown
# Starter GHG Inventory — [Org Name]

**Reporting period:** [dates]
**Organizational boundary:** [approach] — [org name/entity covered]
**Operational boundary:** Scope 1, Scope 2, and Scope 3 (screened)
**Prepared:** [date] | **Status:** Screening-level, not third-party assured

## Scope 1 — Direct Emissions

| Source | Activity data | Data quality | Emission factor source | tCO2e |
|---|---|---|---|---|
| ... | ... | Measured/Estimated | ... | ... |

*(If none: "No Scope 1 sources identified — [org] owns no vehicles and has no on-site fuel combustion.")*

## Scope 2 — Purchased Electricity/Heat

| Method | Activity data | Data quality | Emission factor source | tCO2e |
|---|---|---|---|---|
| Location-based | ... | ... | eGRID subregion [X] | ... |
| Market-based | ... | ... | ... | ... |

## Scope 3 — Value Chain (screened)

| Category | Status | Data quality | Method | tCO2e |
|---|---|---|---|---|
| 1. Purchased goods & services | Included — quantified / Included — not quantified (data gap) / Screened out | ... | Activity/Spend-based | ... |
| 5. Waste generated in operations | ... | ... | ... | ... |
| 6. Business travel | ... | ... | ... | ... |
| 7. Employee commuting | ... | ... | ... | ... |
| [others] | Screened out — not applicable | — | [reason] | — |

*If any material category is "Included — not quantified," say so plainly above this table and label the total below as partial.*

## Total

| Scope | tCO2e | % of total |
|---|---|---|
| Scope 1 | ... | ...% |
| Scope 2 (location-based) | ... | ...% |
| Scope 3 (quantified categories only) | ... | ...% |
| **Total (partial if any material category is unquantified — say so)** | **...** | **100%** |

## Data quality summary

- Measured: [list of line items]
- Estimated: [list of line items] — [method used for each]
- Included but not quantified (data gap): [categories that are material
  but have no data — this is distinct from screened out and must stay
  visibly separate]
- Screened out — not applicable: [categories excluded and why]

## Limitations

[Screening-level disclosure per Process step 7 — not assured, not a
substitute for a formal inventory if one is required, what more rigorous
data collection would add.]

## Next steps

- To make public claims based on this inventory, run them through
  `greenwashing-check` first.
- For a materiality-driven narrative around this data, use
  `materiality-interview`.
```

Save the output as `scope-inventory-{org-slug}-{YYYY-MM-DD}.md`.

## Tips

- **No usable data at all.** If the org genuinely has no bills, receipts,
  or logs on hand, you can still produce a rough Scope 2 estimate from
  square footage or headcount using published small-office energy-use
  benchmarks (e.g., EIA CBECS averages) — but label it clearly as a
  benchmark-based rough estimate, not a spend- or activity-based estimate,
  and say the org should replace it with real utility data as soon as
  possible. Don't extend this benchmark approach to Scope 3 categories —
  if there's no spend or activity data for a materially relevant
  category, mark it "included — not quantified (data gap)" per step 6
  rather than guessing at a number with no defensible basis, and rather
  than marking it "screened out" (which means something different — see
  next tip).
- **Don't let "no data" masquerade as "not applicable."** These are the
  two most-confused states in this skill's output — a material category
  with no data is still material and should visibly say so as a data
  gap (step 6), not disappear into the same "screened out" bucket as a
  category that genuinely doesn't exist for this org. Collapsing the two
  understates the footprint by omission, which is exactly the kind of
  false precision this skill exists to avoid.
- **Don't inflate precision.** A screening-level inventory built partly
  on spend-based factors is inherently rough. Round appropriately and say
  so — false precision is itself a substantiation problem if this
  inventory is later quoted publicly (see `greenwashing-check`).
- **Don't let this become a claims document.** This skill's job is to
  produce the number and its provenance, not to draft "we're committed to
  sustainability" language around it. Keep marketing language out of the
  output entirely.
- **Where this skill hands off:** feed public-facing claims built on this
  inventory through `greenwashing-check` before they ship. Feed the
  inventory itself into `materiality-interview` if the org wants a full
  ESG narrative built around it.

## Example

See `examples/green-thread-scope-inventory/scope-inventory.md` for a
screening-level dry run on a fictional small organization.
