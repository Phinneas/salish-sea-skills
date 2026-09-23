# Portage Pre-Migration Audit

**What:** The audit you run before moving a site to Astro, so the move doesn't cost you traffic.
**When:** You're planning to leave Ghost (or WordPress, Squarespace, Gatsby) and haven't moved any content yet.
**Output:** A URL-by-URL decision table, a draft redirect map (plus CSV), a checklist of platform features to rebuild, and a dated traffic baseline.

## Use Cases

- You're moving a Ghost blog to Astro and want to keep your rankings.
- You're consolidating an old blog and need to decide what to keep, merge or drop.
- Your site has been migrated before and the old redirects need carrying forward.
- A client is replatforming and needs a documented plan before the build starts.

## The Skill

1. Builds a full URL inventory from the sitemap, plus the URLs sitemaps miss (pagination, feeds, images).
2. Joins each URL to its traffic and backlinks, and protects the ones that matter.
3. Decides keep, move, merge, drop or noindex for every URL.
4. Drafts the redirect map and flattens any old redirects so nothing chains.
5. Lists every feature the old CMS handled for you (RSS, newsletter signup, cards, code injection) so none of it silently disappears.
6. Records a dated baseline so you can measure recovery after launch.

Written for Ghost to Astro first, matching Portage's ghost2astro tool. It covers other platforms too.

**Chain:** Pre-migration audit → Portage conversion (or manual build) → LinkCanary triage after launch.

## Prerequisites

- Runs on Claude alone. No paid tools needed.
- Your site URL.
- Strongly recommended: a Search Console Performance export by page, covering 12 to 16 months. Without it, keep and drop decisions are marked provisional.
- Optional: your existing `redirects.yaml`, a backlinks export, and the planned URL structure for the new site.

## Getting Started

```
Use the portage pre-migration audit on [yoursite.com]. We're moving from Ghost to Astro.
```

Claude will:
1. Confirm the launch date and whether URLs will change
2. Pull every URL and join it to your traffic data
3. Make a call on each URL and draft the redirects
4. Check every platform feature you'll need to rebuild
5. Snapshot your current numbers as the baseline

## Time Investment

- **First run:** 30 to 60 minutes, depending on site size
- **Iterations:** 10 minutes to revise decisions

## Next Steps

After running this:
- Load `redirects-{site}.csv` into your new host's redirect config.
- Build the features marked "rebuild" before launch.
- Run the launch-day checklist.
- Crawl the new site after launch and run the LinkCanary triage skill on the report.

## Technical Docs

- **Full SKILL.md:** See [SKILL.md](./SKILL.md) for the complete technical specification.
- **On SSC site:** [Read the full methodology and examples](https://salishseaconsulting.com/skills/tools/portage)

## License

MIT. Use freely. Attribute appreciated.
