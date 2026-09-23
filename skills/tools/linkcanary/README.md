# LinkCanary Triage

**What:** Turns a raw link report into a short, prioritized fix list.
**When:** You've run a crawl and have hundreds of link errors but no idea which ones matter.
**Output:** A triage report with P1 to P4 tiers, one row per fix, a named action for each, and a false-positives list.

## Use Cases

- A crawl turned up 300 broken links and you have one afternoon to fix what matters.
- You just migrated or redesigned the site and want to know what broke.
- Search Console is showing a growing list of 404s.
- Redirect chains from old migrations are stacking up and you want to flatten them.
- A client wants a link-health report they can act on, not a raw export.

## The Skill

1. Reads the report from any crawler and normalizes it.
2. Groups duplicate errors into single fixes. One dead URL on 40 pages is one fix.
3. Classifies each fix: broken, redirect loop, redirect chain, soft 404, likely bot block.
4. Re-checks doubtful codes (5xx, 403, 429) so you don't chase false alarms.
5. Ranks everything P1 to P4 by severity, page value and how many pages it touches.
6. Names the fix: update the link, add a redirect at the destination, collapse a chain, replace a dead source, or remove the link.

LinkCanary is the fastest way to get the input because it traces the full redirect path. The skill works on other crawlers' exports too.

## Prerequisites

- Runs on Claude alone. No paid tools needed.
- A link report from LinkCanary, Screaming Frog, Search Console, Ahrefs or SE Ranking. A pasted list of URLs and status codes works too.
- Recommended: a Search Console or GA4 traffic export by page. It sharpens the ranking.
- Optional: web access, so Claude can re-check doubtful URLs.

## Getting Started

```
Use the linkcanary triage methodology on this crawl report [attach or paste]
```

Claude will:
1. Ask which pages are your money pages (services, contact, donate)
2. Group and classify every error
3. Re-check the doubtful ones
4. Return a ranked fix list, bulk fixes first

## Time Investment

- **First run:** 10 to 20 minutes, depending on report size
- **Iterations:** 5 minutes per re-crawl

## Next Steps

After running this:
- Do the bulk fixes first. They clear the most rows per change.
- Work P1 today and P2 this week.
- If most problems trace back to a messy redirect file, run the Portage pre-migration audit to rebuild it.

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/tools/linkcanary)

## License

MIT. Use freely. Attribute appreciated.
