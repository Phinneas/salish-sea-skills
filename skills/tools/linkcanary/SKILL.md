---
name: linkcanary
description: >-
  Triages a link-check or crawl report into a prioritized fix list. Ranks every
  broken link, redirect chain and redirect loop by how much it hurts, groups
  duplicates into single fixes, filters out false positives, and names the fix
  for each one. Use whenever the user shares a LinkCanary report, a Screaming
  Frog export, a Search Console 404 list, an Ahrefs broken-links export, or a
  pasted list of bad URLs and asks what to fix first, which broken links
  matter, how to clean up redirects, or "where do I start" with a pile of link
  errors. Also use after a site migration or redesign when the user wants to
  check for broken links, even if they don't mention LinkCanary.
---

# LinkCanary Triage

## Overview

This skill turns a raw link report into a short, ordered fix list.

A crawler finds every problem. It doesn't tell you which ones matter. A broken
link in your main nav costs you on every page view. A dead citation in a 2021
post costs you almost nothing. Most reports list both the same way, so people
either fix nothing or burn a day on the wrong things.

The output is a triage report: P1 to P4 priority tiers, one row per fix (not
per error), a named action for each row, and a separate list of likely false
positives.

It works on any crawler's output. LinkCanary is the fastest way to get the
input because it traces the full redirect path, not just the start and end
status. Screaming Frog, Search Console and Ahrefs exports work too.

Where it sits: run it after any crawl. After a migration, it pairs with the
Portage pre-migration audit. The audit plans the redirects. This skill checks
whether they held.

## Prerequisites

- **Required input:** a link report. Any of these works:
  - LinkCanary CSV or JSON report
  - Screaming Frog export (Response Codes, Redirect Chains, or All Outlinks)
  - Google Search Console Pages report, "Not found (404)" rows
  - Ahrefs or SE Ranking broken-links export
  - A pasted list of URLs with their status codes
- **Recommended:** page traffic data, such as a Search Console Performance
  export by page or a GA4 landing-page report. It sharpens the priority
  scoring. Without it, the skill ranks by page type and link scope alone and
  says so in the report.
- **Optional:** WebFetch, to re-check URLs that returned 5xx, 403, 429 or timed
  out. Without it, those rows are marked "unverified" rather than dropped.
- No paid connectors are needed.

## Process

1. **Read and normalize the input.** Identify the source format from its
   columns. Map every row to the same fields: source page, target URL, status
   code, redirect hops, final URL, link type (internal or external), and link
   location (nav, footer, body) when the report has it. If a field is missing,
   leave it blank. Don't guess it.

2. **Ask for what's missing.** Use `AskUserQuestion` if you don't know these.
   Ask them in one go:
   - The site's money pages: services, pricing, contact, signup, checkout,
     donate. These drive the P1 tier.
   - Whether a traffic export is available.
   If the user skips, infer money pages from URL patterns (`/services`,
   `/pricing`, `/contact`, `/donate`) and mark that inference in the report.

3. **Group into fixes.** Group rows by target URL. One dead URL linked from 40
   pages is one fix, not 40. Flag a target as **sitewide** if it appears on
   more than half the crawled pages or in the nav or footer. Sitewide links
   get fixed once in a template.

4. **Classify each fix.** Assign one issue type:
   - **Broken (4xx):** 404 or 410 on the target.
   - **Server error (5xx) or timeout:** often temporary. Re-check before
     acting.
   - **Redirect loop:** the path never resolves. Always P1.
   - **Redirect chain:** two or more hops before the final URL.
   - **Single redirect:** an internal link pointing at a URL that redirects
     once. It works but leaks crawl budget and adds latency.
   - **Soft 404:** a redirect that lands on the homepage or a generic page
     instead of a real replacement.
   - **Likely bot block:** 403, 429 or 999 from sites known to block crawlers
     (LinkedIn, Amazon, Instagram, Facebook, many news paywalls).
   - **Protocol:** an `http://` link on an `https://` site.

5. **Verify the doubtful ones.** If WebFetch is available, re-request every
   5xx, timeout, 403, 429 and 999 target once. Move the ones that now resolve
   to the false-positives list. If WebFetch isn't available, keep them in
   their tier and mark them "unverified."

6. **Score priority.** Use three factors:
   - **Severity:** loops and 4xx are worst. Then chains. Then single
     redirects and protocol issues.
   - **Page value:** money pages and the top 20% of pages by clicks count as
     high. Everything else counts as normal.
   - **Scope:** sitewide or 10+ source pages counts as wide.

   Assign tiers:

   | Tier | Rule |
   |---|---|
   | **P1: fix today** | Any redirect loop. Any broken internal link that is sitewide, on a money page, or on a high-value page. |
   | **P2: fix this week** | Other broken internal links. Internal redirect chains of 3+ hops. Broken external links on money or high-value pages. |
   | **P3: fix this month** | Internal links pointing at a single redirect or a 2-hop chain. Soft 404s. Broken external links on normal pages. Protocol issues. |
   | **P4: batch later** | Broken external links on low-traffic or old posts. Unverified bot-block codes. |

7. **Name the fix.** Pick one action per row:
   - **Update link:** point the link straight at the final URL. This is the
     default for redirects and chains.
   - **Fix at destination:** add a 301 from the dead URL to its real
     replacement. Choose this over editing sources when the dead URL has many
     inbound links, backlinks from other sites, or search traffic. One
     redirect beats 40 edits.
   - **Collapse chain:** change the first redirect rule so it points at the
     final URL. This fixes every link through that chain at once.
   - **Replace source:** for dead external citations, find the moved page, an
     equivalent source, or an archived copy. Say which one.
   - **Remove link:** only when nothing replaces it and the sentence still
     reads fine without it.
   - **Template edit:** for sitewide nav or footer links.

8. **Find bulk fixes.** List any pattern that one change can clear. For
   example, every `/blog/2019/...` URL now 404s, or every link to an old domain.
   Suggest the single redirect rule or find-and-replace that clears it.

9. **Write the report** in the format below.

## Output format

Save as `link-triage-{site}-{YYYY-MM-DD}.md` if writing a file. Otherwise
return it in chat.

```markdown
# Link Triage: [site] ([date of crawl])

**Input:** [source tool], [N] rows → [N] unique fixes
**Traffic data:** [used / not provided, ranked by page type and scope only]
**Money pages:** [list, or "inferred from URL patterns"]

## Summary

| Tier | Fixes | Rows cleared |
|---|---|---|
| P1: fix today | | |
| P2: fix this week | | |
| P3: fix this month | | |
| P4: batch later | | |
| False positives | | |

## Bulk fixes (do these first)

| Pattern | Rows cleared | One change |
|---|---|---|
| | | |

## P1: fix today

| Target URL | Issue | Found on | Fix | Detail |
|---|---|---|---|---|
| | | [N pages / sitewide / page URL] | [action] | [new URL, redirect rule, or replacement source] |

## P2: fix this week
[same table]

## P3: fix this month
[same table]

## P4: batch later
[same table, may be summarized by count if long]

## False positives and unverified

| Target URL | Code | Why it's likely fine | Verified? |
|---|---|---|---|
| | | | |

## Notes
- [Any assumptions: inferred money pages, missing columns, partial crawl]
```

## Tips

- **403 and 429 from big platforms are usually fine.** LinkedIn, Amazon and
  most social sites block crawlers. A human clicking the link gets through.
  Don't tell anyone to remove those links without checking in a browser.
- **Don't redirect dead pages to the homepage.** Search engines treat that as
  a soft 404, and users land somewhere useless. Redirect to the closest real
  match. If there's no match, a 410 is more honest.
- **Citations matter more on some sites.** On ESG, grant and research content,
  a dead source weakens a claim. Prefer "replace source" over "remove link."
- **Chains usually come from stacked migrations.** A site that moved from
  Squarespace to Ghost to Astro can have old URLs that hop twice. Collapse the
  rules at the server. Don't edit every link.
- **Partial crawls skew the numbers.** If the report says the crawl stopped
  early, say so at the top. Sitewide counts will be low.
- **Hands off to:** the Portage pre-migration audit when the chains point at
  a messy redirect file that needs rebuilding.
