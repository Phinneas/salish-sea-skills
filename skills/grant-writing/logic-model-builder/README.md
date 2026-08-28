# Logic Model Builder

**What:** Builds a funder-ready logic model — resources, activities, outputs, outcomes, and impact, connected by explicit if-then reasoning.
**When:** You need the required Logic Model attachment for a grant application, or you just want to sense-check whether a program's activities actually add up to its claimed outcomes.
**Output:** A one-page logic model table plus a plainly stated if-then chain, with weak links named rather than hidden.

## Use Cases

- A NOFO requires a Logic Model or Theory of Change attachment (common in federal environmental, education, and health grants — EPA's Environmental Education program names it explicitly)
- You've decoded a NOFO and scored a fit, and need to show reviewers how your program actually produces the outcomes it claims
- A board or funder asks "what are we really trying to change" and you want an honest answer, not a mission-statement restatement
- You're revising an existing program description and want to check whether the outcomes you're claiming are actually earned by the activities you're running

## The Skill

This skill builds a logic model using the W.K. Kellogg Foundation framework
— the reference most federal funders name directly or expect implicitly:
Resources/Inputs → Activities → Outputs → Outcomes (short-term and
longer-term) → Impact. The discipline it enforces is the if-then chain:
each column has to follow causally from the one before it, with the
mechanism stated, not just sit next to it in a table. A logic model that
can't state *why* an output would plausibly produce a claimed outcome gets
that gap flagged explicitly rather than smoothed over.

**Fourth skill in the grant-writing chain.** Typically follows
`grant-fit-scorer`'s "Go" call, and feeds `budget-narrative-writer` — the
budget should visibly fund exactly what this model claims it funds.

## Prerequisites

- No connectors required — runs on Claude alone.
- You supply a description of the program: what it does, who it serves,
  what change it's trying to make. Informal is fine — a paragraph, a
  decoded NOFO's Program Description section, or notes from a planning
  conversation all work.
- Helpful but optional: the opportunity's stated required outcomes (from
  `nofo-decoder`), and any real participation or outcome data the org
  already has, so the model uses actual numbers instead of estimates.

## Getting Started

```
Build a logic model for [program name/description]
```

Claude will:
1. Establish the long-term impact statement first and work backward from it
2. List concrete resources/inputs and the activities they enable
3. Derive countable outputs from those activities
4. Derive short- and longer-term outcomes, stating the mechanism connecting
   each outcome to the output that produces it
5. Check that the outcomes actually ladder up to the impact statement
6. Walk the full if-then chain out loud, end to end, and flag any link that
   doesn't hold

## Time Investment

- **First run:** 20-40 minutes, more if the org's outcomes aren't yet well-defined
- **Iterations:** 10-15 minutes to revise once the underlying program details change

## Next Steps

- Feed the model into `budget-narrative-writer` so the budget visibly funds
  the same activities this model claims
- If the NOFO requires a visual/graphic format rather than a table, ask
  Claude (or a design tool) to render the same content as a flow diagram

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/grant-writing/logic-model-builder)

## License

MIT. Use freely. Attribute appreciated.
