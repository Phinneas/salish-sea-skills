---
name: agent-hygiene-score
description: Score an MCP server 0-10 on whether it is safe to hand to an autonomous AI agent, using the MyMCPShelf 5-dimension Agent Hygiene rubric. Use when asked to rate, audit, vet or compare MCP servers for agent safety.
---

# Agent Hygiene Score

## Overview

This skill answers one question: is this MCP server safe to hand to an autonomous AI agent?

It is not a security audit. A security audit asks if a server is safe to deploy. This asks something harder. An agent doesn't read warning labels. It doesn't ask for confirmation. If the server gives it too much power or too little structure, things break in ways the agent can't detect.

The rubric has five dimensions. Each is scored 0, 1 or 2. The total is out of 10 and maps to one of four tiers.

Source rubric: https://www.mymcpshelf.com/agent-hygiene

## Prerequisites

- A server to score. Accept a GitHub URL, a docs URL, a MyMCPShelf server page, or a pasted README.
- Web access to read the README, tool schemas, and GitHub metadata.
- If you have no web access, score only from what the user pasted. Mark every dimension you could not check as "not verified."

## Process

1. **Collect public sources only.** Read these in order:
   - The GitHub README (primary source)
   - Tool schema definitions (JSON Schema, Zod, Pydantic, TypeScript types, `inputSchema` in tool registration)
   - SECURITY.md, docs site, and any rate limit or scope docs
   - GitHub metadata: last commit date, open vs closed issues, issue response time, stars, forks, owner (org or individual)
   Do not guess about runtime behavior. Do not infer anything the sources don't say.

2. **Score each dimension 0-2.** Use the rubric below. For every score, write down the evidence and a source URL. No evidence means no points.

3. **Apply context.** A low score in one dimension is not always a dealbreaker. A local-only server that scores 0 on scoping can still be safe on the user's own machine. Say so in the notes. Do not change the number to account for it.

4. **Sum and assign a tier.**

5. **Write the output** in the format below.

## Rubric

### 1. Schema Strictness

Does the server declare typed inputs, enums for constrained choices, and required fields? Strict schemas stop malformed agent requests from causing unexpected behavior.

- **2 Typed + Enumerated:** All tool inputs use strong types. Enums constrain choices where they apply. Required and optional fields are explicit. JSON Schema or type annotations are complete.
- **1 Partially Typed:** Some tools are typed but gaps exist. Enums may be missing. Required fields may not be declared. Acceptable for simpler servers.
- **0 Untyped / Loose:** Inputs accept arbitrary strings or objects with no validation. The agent must guess valid inputs.

### 2. Least-Privilege Scoping

Can access be limited per tool or per resource, or does one credential unlock everything?

- **2 Per-Tool Scopes:** Each tool or toolset can be authorized on its own. OAuth scopes, IAM roles or tool-level RBAC limit what an agent can do. You can grant "read repos" without "write issues."
- **1 Single Credential:** One API key or token grants access to all tools. Acceptable for local-only servers running on the user's machine.
- **0 No Scoping:** Broad credentials with no way to limit access. The token that reads data can also delete it.

### 3. Declared Boundaries

Has the author published a security policy, rate limits, or a clear statement of what the server will not do?

- **2 Documented Policy:** Published security policy, rate limiting, and explicit scope docs. A clear statement of what the server won't do (for example, "this server never writes to your repo").
- **1 Basic Docs:** The README explains what the server does and some config options. No explicit security policy or scope boundaries.
- **0 No Boundaries:** Nothing on what the server will or won't do. No rate limits. No guardrails.

### 4. Auditability

Does the server log tool calls, support idempotency keys, or offer observability hooks?

- **2 Full Audit Trail:** Logs tool calls, supports idempotency keys, or integrates with OpenTelemetry, CloudTrail or similar. You can reconstruct what the agent did.
- **1 Partial Observability:** Some logging or output lets you infer tool usage. No structured audit trail. May rely on the MCP client's own logs.
- **0 No Observability:** Tool calls are opaque. The only way to know what happened is to check side effects.

### 5. Maintenance Signal

Is the server actively maintained?

- **2 Active & Official:** Maintained by the project team or an official vendor. Recent commits, responsive issues, strong GitHub activity. Backed by an organization.
- **1 Community Maintained:** Community contributors. Some recent activity. Slower responses. No official org backing.
- **0 Stale / Unknown:** No recent commits, unanswered issues, or maintenance status unknown.

## Tiers

| Total | Tier | Recommendation |
|---|---|---|
| 8-10 | 🟢 Excellent | Safe for autonomous agent use with broad permissions. |
| 6-7 | 🔵 Good | Reasonable with scoped permissions. Give the agent only the tools it needs. Monitor early behavior. |
| 4-5 | 🟡 Fair | Use with caution. Limit tool access. Monitor the agent closely. Not ideal for fully autonomous systems. |
| 0-3 | 🔴 Poor | Not recommended for autonomous use. Manually review every action the agent takes through it. |

## Output format

```markdown
## Agent Hygiene Score: <Server Name>

**Total: X/10 · <emoji> <Tier>**
<One-line tier recommendation>

| Dimension | Score | Evidence | Source |
|---|---|---|---|
| Schema Strictness | X/2 | <what you found> | <URL> |
| Least-Privilege Scoping | X/2 | ... | ... |
| Declared Boundaries | X/2 | ... | ... |
| Auditability | X/2 | ... | ... |
| Maintenance Signal | X/2 | ... | ... |

**Context notes:** <local-only caveats, anything that changes how to read the score>

**To score higher:** <1-3 specific fixes the maintainer could make>

**Assessed:** <date> · Public sources only. Static review. Not a guarantee.
```

When comparing several servers, add a summary table at the top sorted by total, highest first.

## Tips

- Cite a source for every score. If you can't cite it, score it lower and say why.
- Read the actual tool schemas, not just the README. READMEs often overstate typing.
- "Uses an API key" usually means 1 on scoping, not 2. Look for documented scopes before giving 2.
- Stars alone don't earn 2 on maintenance. Check commit recency and org backing.
- Don't use LLM guesses about what the code probably does. The method is public info only.
- Keep this separate from security scoring. A server can be secure and still score poorly here.
- End every report with the limitation line. A 10/10 server can still have unknown vulnerabilities.
