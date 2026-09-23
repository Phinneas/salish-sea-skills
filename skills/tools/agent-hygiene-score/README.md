# agent-hygiene-score

A Claude skill that scores an MCP server 0-10 on one question: is it safe to hand to an autonomous AI agent?

It uses the same 5-dimension rubric published on MyMCPShelf: https://www.mymcpshelf.com/agent-hygiene

## What it checks

| Dimension | What it asks |
|---|---|
| Schema Strictness | Are tool inputs typed, enumerated and marked required? |
| Least-Privilege Scoping | Can access be limited per tool, or does one key unlock everything? |
| Declared Boundaries | Is there a security policy, rate limits, a "won't do" list? |
| Auditability | Are tool calls logged or traceable? |
| Maintenance Signal | Is it actively maintained and backed by an org? |

Each dimension scores 0-2. The total maps to a tier: Excellent (8-10), Good (6-7), Fair (4-5), Poor (0-3).

## How to use it

Ask Claude something like:

- "Run an agent hygiene score on https://github.com/firecrawl/firecrawl-mcp-server"
- "Compare the GitHub and Playwright MCP servers for agent safety"
- "Is this MCP server safe to give my agent?" (then paste the README)

## What you get

A scorecard with a total, a tier, per-dimension evidence with source links, context notes, and fixes the maintainer could make to score higher.

## Limits

Public sources only: README, schemas, docs and GitHub metadata. No runtime testing and no code scanning. A high score is a starting point, not a guarantee.

## Install

- **Claude.ai / Cowork:** add it from Settings > Skills, or save it from the proposal card.
- **Claude Code:** copy this folder to `~/.claude/skills/agent-hygiene-score/`.

## Author

Buzz · Salish Sea Consulting · MyMCPShelf
