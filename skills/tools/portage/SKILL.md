---
name: portage
description: >-
  Runs a pre-migration audit before moving a blog or site to Astro, starting
  with Ghost. Inventories every URL, joins it to traffic and backlink data,
  decides keep / move / merge / drop for each one, drafts the redirect map,
  lists every CMS feature the new build must replace, and records a dated
  baseline to measure recovery against. Use whenever the user is planning to
  migrate, replatform or rebuild a site, mentions moving off Ghost, WordPress,
  Squarespace or Gatsby, asks what to check before a migration, wants a
  redirect map, or is worried about losing traffic when switching CMS, even if
  they don't mention Portage.
---

# Portage Pre-Migration Audit

## Overview

This skill produces the audit you run before any content moves. It covers the
URL inventory, the keep / move / merge / drop call for every URL, a draft
redirect map, a checklist of platform features to rebuild, and a baseline
snapshot.

Most migration traffic loss is decided before launch. Pages get dropped
without redirects. Redirects stack on top of old redirects. The RSS feed moves
and subscribers lose it. The newsletter signup vanishes because it was a
built-in CMS feature nobody listed. The conversion step is the easy part. This
audit is the part people skip.

The skill is written for Ghost to Astro first, which matches Portage's
ghost2astro tool. The process works for other sources too. Step 5 notes what
changes.

Where it sits: this runs first. Its redirect map and structure checklist feed
the Portage conversion (or a manual build). After launch, the LinkCanary
triage skill checks whether the redirects held, and the baseline here is what
recovery gets measured against.

## Prerequisites

- **Required input:** the current site URL. The skill reads the sitemap to
  build the URL inventory.
- **Strongly recommended:** a Google Search Console Performance export by
  page, covering the last 12 to 16 months. Without it, every keep / drop call
  is marked provisional because it's based on page type, not demand.
- **Optional:**
  - The existing redirects file (Ghost `redirects.yaml` or `redirects.json`)
    and `routes.yaml`. These must carry over, so ask for them.
  - A backlinks export (Ahrefs, SE Ranking, or Search Console Links report).
    It protects low-traffic pages that other sites link to.
  - The target URL structure for the new site, if it's already decided.
- **Tools:** WebFetch to read the sitemap and spot-check pages. If WebFetch is
  unavailable, ask the user to paste the sitemap URLs.
- No paid connectors are needed.

## Process

1. **Confirm the scope.** Use `AskUserQuestion` to get:
   - Source platform and target (default: Ghost to Astro).
   - Planned launch date.
   - Whether URLs will change. Ghost uses `/{slug}/` for posts. If the new site
     moves posts under `/blog/{slug}/`, every post needs a redirect. Keeping
     URLs identical is the cheapest migration there is. Say so.
   - Which of the optional inputs above they can provide.

2. **Build the URL inventory.** Fetch `/sitemap.xml` with `WebFetch`. On
   Ghost it's an index. Follow it to `sitemap-posts.xml`, `sitemap-pages.xml`,
   `sitemap-tags.xml` and `sitemap-authors.xml`. Record each URL, its type
   and its lastmod date. Then add the Ghost URLs that sitemaps leave out:
   - Pagination: `/page/2/`, `/tag/{slug}/page/2/`
   - Feeds: `/rss/`, `/tag/{slug}/rss/`
   - AMP: `/{slug}/amp/`, if AMP was ever enabled
   - Images: `/content/images/...`, including sized variants like
     `/content/images/size/w600/...`. Other sites often hotlink these.
   - Newsletter web versions: `/email/{uuid}/`
   Leave out `/ghost/` admin and `/p/{uuid}/` previews.

3. **Join the data.** Match each URL to its clicks, impressions and top query
   from the Search Console export. Match backlinks if provided. Mark a URL as
   **protected** if it's in the top 20% by clicks or has any external
   backlinks. Protected URLs can never be dropped without a redirect.

4. **Decide every URL.** Give each one a single decision:

   | Decision | When | Redirect |
   |---|---|---|
   | **Keep** | Same URL on the new site | None |
   | **Move** | Keeping the content, URL changes | 301 old → new |
   | **Merge** | Thin or overlapping content folded into a stronger page | 301 to the merged page |
   | **Drop** | Off-topic, empty or dead content, not protected | 410, or 301 to the closest real parent |
   | **Keep, noindex** | Useful to visitors, not worth indexing (e.g. tag archives with 1 post) | None |

   Base the call on data. A page with zero clicks in 16 months and no
   backlinks is a drop candidate. A page with backlinks stays or merges, even
   with zero clicks. Flag any call you made without traffic data as
   provisional.

5. **List what the platform did for you.** Check each item and mark it
   "rebuild," "replace," "drop on purpose" or "n/a." For Ghost:
   - Tag and author archive pages
   - Pagination
   - RSS feed at the same URL (feed readers and newsletter tools depend on it)
   - XML sitemap
   - Members, newsletter signup and Portal links (`#/portal/...`)
   - Paid tiers or gated content
   - Comments
   - Site search
   - Code injection: analytics, schema markup, verification tags
   - Custom meta titles, descriptions and OG images per post
   - Canonical URLs set by hand
   - Ghost cards: bookmark, gallery, toggle, callout, button, embeds. Each
     needs a component in the new build or the content breaks.
   - Hardcoded absolute internal links (`https://yoursite.com/...`) in post
     bodies
   - Existing redirects in `redirects.yaml`

   For other sources, swap in that platform's equivalents. WordPress adds
   `/?p=ID` URLs, date archives, categories and plugin shortcodes. Squarespace
   adds `/blog?offset=` pagination and `/s/` file URLs. Gatsby adds
   `/page-data/` and whatever the site's `gatsby-node` generated.

6. **Carry over and flatten the old redirects.** Take every existing redirect
   and point it at its final destination on the new site. If an old
   Squarespace URL redirects to a Ghost URL that will itself redirect to an
   Astro URL, write one rule from the Squarespace URL straight to the Astro
   URL. Stacked migrations are the most common source of redirect chains.

7. **Record the baseline.** Date-stamp the current numbers:
   - Clicks and impressions, last 28 days
   - Count of indexed pages (Search Console Pages report)
   - Top 20 pages by clicks, with their average position
   - RSS subscriber and newsletter counts, if the user has them
   Recovery gets judged against this. Without it, nobody can say whether the
   migration worked.

8. **List risks and a go / no-go check.** Name the specific things most
   likely to cost traffic on this site. Then write the checklist the user
   runs on launch day.

9. **Write the audit** in the format below.

## Output format

Save as `migration-audit-{site}-{YYYY-MM-DD}.md` if writing a file. Also
export the redirect map as `redirects-{site}.csv` (columns: `from,to,status`)
so it can be loaded into the new host's redirect config.

```markdown
# Pre-Migration Audit: [site]

**Move:** [Ghost] → [Astro]  |  **Planned launch:** [date]
**URL structure:** [unchanged / changing: describe]
**Data used:** [Search Console export (dates) / backlinks / redirects file / none, decisions provisional]

## Summary

| Decision | URLs | Protected URLs in this group |
|---|---|---|
| Keep | | |
| Move | | |
| Merge | | |
| Drop | | |
| Keep, noindex | | |

## Baseline ([date])

| Metric | Value |
|---|---|
| Clicks, last 28 days | |
| Impressions, last 28 days | |
| Indexed pages | |

**Top 20 pages**
| URL | Clicks | Avg position |
|---|---|---|

## URL decisions

| URL | Type | Clicks (12-16 mo) | Backlinks | Protected | Decision | New URL | Note |
|---|---|---|---|---|---|---|---|

## Redirect map

| From | To | Status | Source |
|---|---|---|---|
| | | 301 / 410 | [new decision / carried from redirects.yaml] |

## Platform features to rebuild

| Feature | Status | Note |
|---|---|---|
| RSS feed at /rss/ | rebuild / replace / drop on purpose / n/a | |

## Risks

1. [Specific risk on this site and what it could cost]

## Launch-day go / no-go

- [ ] Redirect map loaded and spot-checked (10 random rows + all protected URLs)
- [ ] No redirect chains (every rule points at a final URL)
- [ ] RSS feed resolves at the old URL
- [ ] Sitemap live and submitted in Search Console
- [ ] Analytics and verification tags firing
- [ ] Newsletter signup works end to end
- [ ] Top 20 pages load with the correct title, description and canonical
```

## Tips

- **Keep URLs if you can.** Every changed URL is a small bet. Matching Ghost's
  `/{slug}/` pattern in Astro removes most of the risk in one decision.
- **Never bulk-redirect to the homepage.** Search engines treat it as a soft
  404. Send each dropped page to its closest real parent, or return a 410.
- **Don't trust the sitemap alone.** It skips pagination, feeds, images and
  anything noindexed. Step 2's extra list exists for that reason.
- **Low traffic doesn't mean safe to drop.** A page with one strong backlink
  can be worth more than a page with 200 clicks. That's what the protected
  flag is for.
- **Image URLs are easy to forget.** If other sites embed your
  `/content/images/` files, moving them breaks those embeds. Redirect the
  folder or keep the path.
- **Don't skip the baseline.** Traffic often dips for a few weeks after any
  migration. Without a dated baseline, a normal dip looks like a disaster and
  a real loss looks like a normal dip.
- **Hands off to:** the Portage conversion tool (or a manual build) with the
  redirect CSV and the feature checklist. After launch, crawl the new site and
  run the LinkCanary triage skill on the report.
