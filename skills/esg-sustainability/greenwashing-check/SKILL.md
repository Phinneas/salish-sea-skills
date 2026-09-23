---
name: greenwashing-check
description: >-
  Audits environmental/sustainability marketing claims — on a website,
  in a report, on packaging copy, in a pitch deck — against the FTC Green
  Guides (16 CFR Part 260) substantiation standard, and flags each claim's
  legal risk with a specific fix. Use whenever the user asks to "check our
  sustainability claims," "is this greenwashing," "can we say X on our
  website," "review our green marketing copy," "are we exposed here,"
  pastes marketing/website copy with environmental language and asks if
  it's okay, or is drafting language like "eco-friendly," "sustainable,"
  "carbon neutral," "recyclable," "made with renewable energy," or
  "non-toxic" and wants it checked before it ships — even if they don't
  say "greenwashing" or "Green Guides" by name. This is a substantiation
  and legal-risk screen, not a rewrite-for-tone pass — use `ux-copy` or a
  general drafting skill for voice/tone work. Not legal advice.
---

# Greenwashing Check

## Overview

Environmental marketing claims carry real legal exposure that most
"does this sound authentic" content reviews miss entirely: the FTC's
Green Guides (16 CFR Part 260) set a substantiation standard for exactly
this kind of language, and unsubstantiated claims have produced SEC
penalties (Keurig, $1.5M, 2024, over "100% recyclable" K-Cup pod claims),
FTC settlements (Kohl's $2.5M and Walmart $3M over "bamboo" textile
claims), and a fast-growing wave of consumer class actions (150+ tracked
as of 2025) against claims like "recyclable," "carbon neutral," and
unqualified "eco-friendly"/"sustainable" language. This skill runs a
specific, per-claim audit against that standard: it finds every
environmental claim in the supplied text, classifies it, checks it
against the applicable Green Guides provision, rates its substantiation
risk, and gives a concrete fix — not a general "sounds greenwashy" gut
check.

This skill shares its regulatory grounding with `scope-inventory` (same
build session — the FTC Green Guides and GHG Protocol are the two
reference standards a small org's climate/sustainability claims actually
rest on) but runs independently; it doesn't require a GHG inventory to
run, though a scope-inventory output is exactly the kind of substantiation
a "we're tracking our footprint" or "X% reduction" claim would need.

**This is a substantiation and risk screen, not legal advice.** It tells
you what the Green Guides require and where a claim looks unsubstantiated
or overqualified against real enforcement patterns — it does not replace
review by an attorney before anything materially risky ships.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** the text to audit — pasted website copy, a report
  excerpt, packaging language, ad copy, or a URL.
- **Optional tool:** `WebFetch`, to pull a live page instead of requiring
  a paste. If the page is JS-rendered and `WebFetch` can't get the actual
  claim text, say so and ask for a paste instead of guessing at content
  that wasn't actually retrieved.
- **Optional input:** any substantiation the org already has for a claim
  (a certification, a lab test, a GHG inventory, a supplier disclosure).
  If supplied, weigh it in the risk rating; if not supplied, don't assume
  it exists — treat the claim as unsubstantiated until shown otherwise.

## Process

1. **Get the text.** Paste, or `WebFetch` if given a URL. If only a
   partial page loads (common with JS-heavy sites), say so explicitly
   before auditing only what was actually retrieved.

2. **Extract every discrete environmental/sustainability claim**,
   quoting each verbatim. Split compound statements into separate claims
   if they'd be independently deceptive — this covers two different
   patterns: (a) two unrelated attributes stated together, like
   "sustainably sourced, recyclable packaging" (sourcing and
   recyclability are independently checkable), and (b) a broad claim
   paired with its own supporting clause, like "carbon neutral,
   offsetting 100% of our emissions" — split this too, because each half
   can independently mislead (an org could be inaccurately "carbon
   neutral" via bad accounting even while genuinely offsetting 100%, or
   vice versa) and each needs its own substantiation check. Don't skip
   claims buried in headers, footnotes, or image alt text if they're in
   the supplied text.

3. **Classify each claim** against the Green Guides' claim types (16 CFR
   260.4–260.17). The two general provisions apply to *every* claim
   regardless of type: **§ 260.2** sets the evidence standard
   ("competent and reliable scientific evidence" — tests, analyses, or
   data evaluated objectively by qualified persons, generally accepted
   in the field), and **§ 260.3** sets general principles for how
   qualifications/disclosures must be presented (clear, prominent,
   plain language, close to the claim) and how comparative claims must
   disclose their basis. Every specific claim type below is layered on
   top of those two — cite the specific section AND note substantiation
   traces back to § 260.2. The specific claim types, with their section
   and the one-line rule that matters most for a small org's copy:
   - **General environmental benefit** ("green," "eco-friendly,"
     "sustainable," or a mission/identity statement implying
     environmental performance even with no single attribute named) —
     § 260.4. See step 4 for detail.
   - **Carbon offsets** — § 260.5. See step 4.
   - **Certifications and seals of approval** — § 260.6: a seal or logo
     implying third-party endorsement needs an actual, currently valid
     certification behind it; an org's own badge/seal design implying
     independent review when there isn't one is itself deceptive.
   - **Compostable** — § 260.7: needs substantiation that all materials
     will break down into usable compost, safely and in about the same
     time as other compostable materials, in the composting method
     reasonably available to consumers (home vs. municipal/industrial
     matters — a product compostable only in industrial facilities most
     consumers can't access needs that qualification stated).
   - **Degradable** — § 260.8: needs substantiation the item will fully
     decompose within a reasonably short time (about one year) after
     customary disposal — an item destined for a landfill, where
     decomposition is typically very slow, usually cannot support an
     unqualified degradable claim.
   - **Free-of** ("chemical-free," "BPA-free," etc.) — § 260.9: deceptive
     if the product contains more than trace amounts of the named
     substance, or if the named substance was never a concern for that
     product category in the first place (implies a false comparison to
     alternatives that do contain it) and any comparable substance
     raising the same environmental concern is present.
   - **Non-toxic** — § 260.10: needs substantiation for both human and
     environmental (e.g. aquatic) safety if the claim implies both, and
     for the specific use/disposal context claimed.
   - **Ozone-safe / ozone-friendly** — § 260.11: deceptive if the product
     releases any ozone-depleting substance, and unqualified claims about
     other emissions the product releases that damage the ozone layer
     through a different mechanism are also covered.
   - **Recyclable** — § 260.12. See step 4.
   - **Recycled content** — § 260.13: pre-consumer (manufacturing
     scrap normally reused anyway) content should not be counted the
     same as post-consumer content without qualification, since a
     reasonable consumer's understanding of "recycled" skews toward
     post-consumer; substantiate the actual percentage claimed.
   - **Refillable** — § 260.14: the marketer must actually provide a
     means to refill the package (a system, a refill product, or a
     collection/return program) — offering a container merely capable of
     being refilled by some hypothetical third party isn't sufficient.
   - **Renewable energy** — § 260.15. See step 4.
   - **Renewable materials** — § 260.16: needs substantiation for what
     specifically is renewable (a rapidly-replenishable input) and
     should specify the material if the claim could otherwise be read as
     broader than it is (parallel to § 260.15's renewable-energy
     specificity requirement).
   - **Source reduction** — § 260.17: comparative by nature ("less
     packaging than before") — needs the basis of comparison
     substantiated and disclosed the same way any § 260.3 comparative
     claim does.
   If a claim doesn't fit any of these (e.g. "organic," which the Green
   Guides don't cover but the USDA National Organic Program and FTC
   substantiation law still reach — see the Truly Organic $1.76M
   settlement), say so explicitly and apply § 260.2's evidence standard
   and § 260.3's general principles directly rather than forcing it into
   the wrong specific bucket.

4. **Check each claim against its specific provision**, not just the
   general substantiation standard. The two patterns that account for
   most real enforcement:
   - **Unqualified general claims** ("green," "eco-friendly,"
     "sustainable," "good for the planet," or a broader mission/identity
     statement implying environmental performance even without naming a
     specific attribute — e.g. "sustainability is who we are") —
     § 260.4(b): the FTC considers these inherently hard to substantiate
     because they imply far-reaching, unspecified benefits. Flag *every*
     unqualified general claim as high risk by default, regardless of
     how the org feels about its own practices or how the claim is
     phrased — the risk is in the claim's breadth, not its sincerity or
     grammatical form. Don't exempt mission-statement-style language just
     because it isn't phrased as a specific attribute claim.
   - **Recyclable claims** — § 260.12: unqualified claims require the
     item to be recyclable where recycling facilities are available to
     substantial majority (≥60%) of consumers/communities where it's
     sold, AND no component (shape, size, material mix) may
     "significantly limit" actual recyclability. This is exactly the
     Keurig pattern — a technically-recyclable material (polypropylene)
     in a form (small pod) that most facilities can't actually sort or
     chose not to accept made the unqualified "recyclable" claim
     deceptive even though the plastic itself was real #5 polypropylene.
     The same reasoning was later applied to a "Recyclable" claim on a
     toothpaste tube: the tube's material was technically recyclable,
     but its shape and unremovable product residue meant real recycling
     programs didn't actually process it, so the unqualified claim was
     still deceptive. A claim can be materially true about the
     *material* and still be deceptive about the *product* — check both.
   - **Carbon offset/neutral claims** — § 260.5: flag if the claim
     implies reductions have already happened when they're 2+ years out
     without disclosure, if the underlying reduction was legally required
     anyway (so it isn't actually additional), or if there's no
     scientific/accounting method behind the offset quantification. Note
     the Green Guides don't fully define "carbon neutral"/"net zero" —
     that gap is exactly why private litigation (Apple, Evian, and others)
     has filled it; don't treat "the Green Guides don't explicitly
     prohibit this" as "this is safe."
   - **Renewable energy claims** — § 260.15: unqualified claims require
     matching non-renewable manufacturing/service energy with Renewable
     Energy Certificates (RECs — tradeable certificates representing
     proof that one megawatt-hour of electricity was generated from a
     renewable source), or qualifying the claim to the specific part of
     the product/process that's actually renewable-powered.
   - **Comparative claims** ("20% more X") — § 260.3: must disclose the
     basis of comparison (vs. prior product? vs. competitor?) and have
     substantiation for whichever interpretation a reasonable consumer
     would draw.

5. **Rate substantiation status and risk** for each claim:
   - **Substantiated** — the org supplied competent and reliable evidence
     (§ 260.2: tests, analyses, or data evaluated objectively by
     qualified persons) that covers the claim as reasonably interpreted.
   - **Unsubstantiated** — no evidence supplied, or the evidence doesn't
     cover the claim's likely interpretation (e.g. "recyclable material"
     evidence doesn't substantiate a "recyclable product" claim).
   - **Unclear/needs review** — plausible but the supplied text doesn't
     give enough to judge; say exactly what additional information would
     resolve it.
   Risk level (High/Medium/Low) combines claim breadth, enforcement
   pattern match, and substantiation status. Use this default rubric
   rather than weighing the three factors freehand:
   - **High** — unqualified general benefit claim (any substantiation
     status — these start High per § 260.4(b) regardless), OR any claim
     type that is Unsubstantiated AND matches a known enforcement
     pattern closely (recyclable-but-not-really, carbon
     neutral/offset with no disclosed method, etc.).
   - **Medium** — a specific/narrow (non-general) claim that is
     Unsubstantiated or Unclear but does *not* closely match a known
     enforcement pattern, OR any claim where partial substantiation was
     supplied but doesn't fully cover the claim as reasonably
     interpreted.
   - **Low** — Substantiated (real, adequate evidence supplied), or a
     narrow/specific claim that is fully and clearly qualified per
     § 260.3 with the qualification's own substantiation intact.
   One factor alone can be sufficient to set High (an unqualified general
   claim is High even with no enforcement-pattern match); don't require
   all three factors to point the same way before rating something High.

6. **Write a specific fix for every High or Medium risk claim** — not
   "add a disclaimer," but the actual qualifying language or the
   narrower claim that would be defensible (e.g. rewrite unqualified
   "recyclable" to "made from recyclable #5 plastic — check local
   programs, most do not currently accept this size/shape" if that's the
   real state of facts, per § 260.12(d)'s own guidance on exactly this
   pattern).

## Output format

```markdown
# Greenwashing Check — [Source: page/report name or URL, or a short
descriptive label like "About page copy (pasted, no URL given)" if the
user supplied neither — never leave this blank]

**Audited:** [date] | **Claims found:** [n] | **High risk:** [n] | **Medium risk:** [n] | **Low risk:** [n]

## Claim-by-claim audit

### Claim 1: "[verbatim quoted claim]"

- **Type:** [Green Guides category, e.g. "Recyclable claim, § 260.12"]
- **Substantiation status:** Substantiated / Unsubstantiated / Unclear
- **Risk:** High / Medium / Low
- **Why:** [specific reasoning tied to the provision, and to a real
  enforcement pattern where relevant]
- **Fix:** [specific rewrite or additional disclosure — not a generic
  "add a disclaimer"]

[repeat per claim]

## Summary table

| Claim | Type | Status | Risk | Fix |
|---|---|---|---|---|
| ... | ... | ... | ... | ... |

## Highest-priority fixes

[The 1-3 claims that create the most exposure, in plain language, for
someone who only reads this section.]

## Not legal advice

This is a substantiation and Green Guides compliance screen based on
publicly available FTC guidance and enforcement patterns. It is not legal
advice. Route anything rated High risk, or anything with real revenue or
reputational exposure behind it, to an attorney before it ships or before
you act on this review.
```

Save the output as `greenwashing-check-{source-slug}-{YYYY-MM-DD}.md`. If
no URL, page title, or brand name was supplied, build the slug from a
short description of what was pasted (e.g. "about-page-copy",
"packaging-draft") rather than leaving it blank or guessing a brand name
that wasn't given.

## Tips

- **Default unqualified general claims to High risk.** "Sustainable,"
  "eco-friendly," and "green" with no qualification are the single
  riskiest, most litigated claim pattern precisely because the FTC
  couldn't devise adequate qualifying language for them (§ 260.4(b)) —
  don't soften this because the specific claim "feels" earnest or small.
- **A true fact about a material isn't automatically a true claim about
  a product.** The Keurig K-Cup case and a parallel toothpaste-tube
  "Recyclable" case (see step 3's Recyclable-claims bullet) both turn on
  this: the underlying material (polypropylene, recyclable tube plastic)
  was real, but the finished product's shape/size/mixed materials meant
  it wasn't actually recycled in practice. Always ask "is this claim
  true about what the customer actually holds and does," not just "is
  this claim true about the raw material."
- **Don't manufacture substantiation.** If the org says "well, we
  believe it's sustainable because—" without actual evidence, that's an
  Unsubstantiated rating, not a Low-risk one just because their reasoning
  sounds plausible to you. Ask for the actual evidence before upgrading
  a rating.
- **State claims ("we track our emissions," "carbon neutral by 2030")
  need real substantiation too** — a `scope-inventory` output is
  reasonable substantiation for a footprint-tracking claim; a bare
  intention is not substantiation for a completed-fact claim. Flag any
  present-tense claim about a future commitment as a likely § 260.4/260.5
  problem regardless of sincerity.
- **Where this skill hands off:** if a claim needs real backing the org
  doesn't have yet (e.g. an actual emissions baseline), point to
  `scope-inventory`. If the whole page needs a broader messaging pass
  after the risky claims are fixed, that's a copy/voice job outside this
  skill's scope.

## Example

See `examples/keurig-kcup-recyclability/audit.md` for a dry run against
real, publicly documented claims — the Keurig K-Cup recyclability case
that produced a $1.5M SEC penalty.
