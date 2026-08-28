# Letter of Support Kit

**What:** Drafts a set of partner letters for a grant application — matched to the right type (support, commitment, or collaboration) and written with real specifics instead of boilerplate.
**When:** Your application needs partner letters and you want them to read as evidence, not courtesy signatures.
**Output:** One drafted letter per partner, in the partner's voice, ready for their review and signature — plus a log showing which type each letter is and what it's tied to.

## Use Cases

- A NOFO requires letters of support, commitment, or collaboration from named partners
- You have a list of partner organizations and rough notes on what each contributes, and need real letters
- You're not sure whether a partner needs a letter of support or a letter of commitment, and want that sorted out correctly before drafting
- A collaborator's letter needs to avoid evaluative language because the funder (NSF, for example) treats that as a compliance issue

## The Skill

This skill first sorts each partner letter into the right type — Letter of
Support (confirms a fact), Letter of Commitment (proves a named
individual's availability at a claimed level), or Letter of Collaboration
(NSF's term for unfunded contributions, with no evaluative language about
the project) — because funders and reviewers read these differently, and
picking the wrong type undermines the letter regardless of how well it's
written. It then drafts each letter in the partner's own voice, with
specific facts (numbers, durations, named contributions) tied to a
specific program activity, rather than generic supportive language.

**Sixth skill in the grant-writing chain.** Typically runs alongside or
after `logic-model-builder`, since a partner's contribution should trace
to a specific activity in that model.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply a list of partners and what each contributes. If you're not
  sure which letter type a partner needs, Claude will work through it with
  you rather than defaulting to "letter of support" for everyone.
- Helpful: `logic-model-builder`'s output, so each letter can name the
  specific activity it supports.

## Getting Started

```
Draft letters of support for [program] — partners: [list with what each contributes]
```

Claude will:
1. Determine the right letter type for each partner
2. Gather or ask for the specific facts each letter needs (a number, a
   name, a duration — not just "partner support")
3. Draft each letter in the partner's own voice, matched to its type
4. Flag any letter where a needed specific is still missing

## Time Investment

- **First run:** 20-45 minutes depending on how many partners and how much
  detail is already gathered
- **Iterations:** 5-10 minutes per letter once revised

## Next Steps

- Send each draft to its partner organization for review, editing in their
  voice as needed, and signature on their own letterhead — never submit a
  letter the partner hasn't approved
- Pair with `budget-narrative-writer` if a partner's contribution is also
  a contractual or subaward budget line

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/letter-of-support-kit)

## License

MIT. Use freely. Attribute appreciated.
