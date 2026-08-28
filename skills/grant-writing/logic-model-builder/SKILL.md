---
name: logic-model-builder
description: >-
  Build a funder-ready logic model — resources/inputs, activities, outputs,
  outcomes, and impact, connected by explicit if-then reasoning — for a
  program or project. Use whenever the user asks to "build a logic model",
  "map our theory of change", "show the impact chain", needs the required
  Logic Model attachment for a grant application (many federal NOFOs, EPA's
  Environmental Education program among them, require one by name), or
  describes a program's activities and asks what outcomes it should claim —
  even if they don't use the term "logic model" themselves ("show how this
  program actually works" or "what are we really trying to change" both
  belong here). Fourth skill in the grant-writing chain — typically follows
  grant-fit-scorer's "Go" call and feeds budget-narrative-writer (a budget
  should fund exactly what the logic model claims it funds).
---

# Logic Model Builder

## Overview

A logic model is the single-page argument for why a program should work,
built as a causal chain: given these resources, we run these activities,
which produce these outputs, which lead to these outcomes, which add up to
this impact. Reviewers use it to sense-check the whole proposal in about 30
seconds — a program whose budget, activities, and claimed outcomes don't
visibly connect on one page reads as unfocused even if each piece is
individually well-written. This skill builds that model using the W.K.
Kellogg Foundation framework, the reference most federal NOFOs either name
directly or implicitly expect.

The discipline this skill enforces is the **if-then chain**: each column
must follow causally from the one before it, not just sit adjacent to it in
a table. "We ran 12 workshops" (an output) does not by itself justify "50%
increase in community water-quality literacy" (an outcome) — the model has
to make the mechanism explicit, and if it can't, that's a sign the claimed
outcome is aspirational rather than earned.

## Prerequisites

Runs on Claude alone. No connector required.

- **Required input:** a description of the program — what it does, who it
  serves, and what change it's trying to make. This can be informal (a
  paragraph, a decoded NOFO's Program Description section, notes from a
  planning conversation).
- **Helpful input:** the opportunity's stated required outcomes or
  performance measures, if this logic model is being built for a specific
  NOFO (from `nofo-decoder`'s output) — outcomes claimed should speak
  directly to what the funder said it wants to see, not just what sounds
  good in general.
- **Helpful input:** any existing data the org has (prior program
  participation numbers, past outcome measurements) to ground outputs and
  outcomes in real figures rather than placeholder estimates.

## Process

1. **Establish the impact statement first, then work backward.** Ask (or
   infer from the program description): what is the long-term, 7-10 year
   change this program ultimately serves, at the community/systems level?
   This anchors everything else — Kellogg's framework works best when
   impact is fixed before the intermediate steps are filled in, so
   activities don't drift into justifying themselves rather than the
   impact. If there's no live back-and-forth available to ask (a one-pass
   request rather than an ongoing conversation), infer the impact
   statement from the program description and say plainly that it's
   inferred rather than confirmed — don't silently present a guess as
   something the user stated.

2. **List Resources/Inputs.** The human, financial, organizational, and
   community resources actually available or being requested — staff time,
   partner contributions, the grant funds themselves, existing
   infrastructure or relationships. Be concrete (named roles and hours, not
   "staff"; named partners, not "community support").

3. **List Activities.** What the program actually does with those
   resources — the processes, events, tools, and actions. Each activity
   should trace to a resource that enables it; an activity with no
   corresponding input is a budget gap waiting to be discovered later.

4. **Derive Outputs from Activities.** The direct, countable products of
   each activity — units of service delivered, participants reached,
   materials produced. Outputs answer "did the program actually happen at
   the scale claimed," not "did it work." Use real or realistic numbers,
   not "increased" or "improved" language — that belongs one column over.

5. **Derive Outcomes from Outputs, split by timeframe.** Specific changes in
   participants' behavior, knowledge, skills, or status:
   - **Short-term outcomes** (achievable in 1-3 years, typically the life of
     a single grant): usually knowledge or skill change, or early behavior
     change.
   - **Longer-term outcomes** (4-6 years): usually sustained behavior
     change or condition change, past what one grant cycle alone can prove
     but plausible as a trajectory from the short-term outcomes.
   For each outcome, state the mechanism connecting it to an output —
   *why* would this output plausibly produce this outcome — not just list
   both and let the reader assume a connection.

6. **Derive Impact from Outcomes.** Return to the impact statement from
   step 1 and confirm the outcomes actually ladder up to it. If they don't
   — if the impact statement is broader than anything the outcomes could
   plausibly cause — either narrow the impact statement or flag the gap
   explicitly rather than papering over it with vague language.

7. **Pressure-test the chain.** Walk the if-then logic once, end to end,
   out loud in the output: "If [resources], then [activities]. If
   [activities], then [outputs]. If [outputs are achieved], then
   [outcomes]. If [outcomes are achieved], then [impact]." Any link that
   doesn't hold when stated this plainly needs to be fixed before the model
   ships, not left for a reviewer to notice.

## Output format

```markdown
# Logic Model: {Program Name}

**Built:** {YYYY-MM-DD} · **For opportunity:** {opportunity name, if applicable}

## Impact statement (7-10 years)
{One or two sentences — the fundamental, long-term change this program serves.}

## The model

| Resources/Inputs | Activities | Outputs | Short-term Outcomes (1-3 yrs) | Longer-term Outcomes (4-6 yrs) |
|---|---|---|---|---|
| {resource} | {activity it enables} | {countable product, with a real number} | {specific participant-level change} | {sustained change this builds toward} |
| ... | ... | ... | ... | ... |

## The if-then chain (stated explicitly)
1. If we have {key resources}, then we can {key activities}.
2. If we {key activities}, then we produce {key outputs}.
3. If {key outputs} are achieved, then participants experience {key short-term outcomes} — because {the actual mechanism, not just adjacency}.
4. If {short-term outcomes} hold, then over time {longer-term outcomes} follow — because {mechanism}.
5. If {longer-term outcomes} are sustained, they contribute to {impact statement}.

## Weak links flagged
{Any point in the chain where the causal claim is thin, unproven, or
depends on an assumption worth naming — e.g. "Outcome X assumes
participants apply the skill outside the workshop setting; the model has no
mechanism for reinforcing that." Naming these isn't a flaw in the model —
it's what makes it credible instead of aspirational.}
```

Save as `logic-model-{program-slug}-{YYYY-MM-DD}.md` if the user wants a
file; otherwise deliver in chat. Many NOFOs (EPA's Environmental Education
program is a named example) score the logic model as a distinct, separately
weighted attachment, often specifically for whether it visually displays
both process and outcome elements connecting to the funder's own stated
priorities — check the decoded NOFO's Application Contents section for any
required format (e.g. "graphic" or "visual") before assuming a table
satisfies the requirement; if a true visual/graphic is required, produce
the same content as a simple flow diagram description the user can render,
and say so.

## Tips

- **Don't let outputs masquerade as outcomes.** "200 people attended" is an
  output. "200 people demonstrated increased knowledge on a post-workshop
  assessment" is an outcome. This mistake is the single most common way
  logic models fail — watch for activity/output language creeping into the
  outcome columns.
- **Numbers should be real when the org has them, and honestly labeled as
  estimates when it doesn't.** Never present an estimate as a firm
  historical figure — a reviewer who catches one fabricated number
  discounts the whole document.
- **A logic model with no weak links flagged is a red flag, not a
  strength.** Every real program has at least one place where the causal
  chain depends on an assumption. Naming it plainly is what separates an
  honest model from a marketing document.
- **Multiple programs/audience segments need separate models**, not one
  blended chart — don't average a youth education arm and an adult
  workforce arm into one row set that fits neither cleanly.
- **Cost warning:** none — this is Claude-only. If the user wants a
  polished graphic rather than a markdown table, mention that a design
  tool or a diagramming skill can render the same content visually; this
  skill's job is getting the logic right, not the layout.
- Hands off from `grant-fit-scorer` (typically built after a Go call) and
  into `budget-narrative-writer` — the budget should visibly fund the
  activities this model claims, not a different set of costs.
