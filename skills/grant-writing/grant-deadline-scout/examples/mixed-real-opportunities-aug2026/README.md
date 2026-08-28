# Example: Mixed real opportunities, compiled 2026-08-28

**Scenario:** Dry-run test of `grant-deadline-scout` against a set of real,
independently verified federal and corporate funding opportunities spanning
closed, upcoming, and rolling deadlines — chosen to exercise every tier the
skill defines, not just the easy cases.

**Input:** Five real opportunities found via web search, each independently
verified (see sources in `deadline-calendar.md`):
- EPA Environmental Education Grant Program (EPA-EE-25-01) — closed
- FEMA Nonprofit Security Grant Program (NSGP) FY2026 — closed
- IMLS Museums for America — upcoming
- IMLS Inspire! Grants for Small Museums — upcoming, same deadline as above
- Walmart Spark Good Local Grants, Cycle 3 — open now, rolling window with a hard close date
- USDA Rural Development Community Facilities — rolling, no fixed deadline

**Output:** [deadline-calendar.md](./deadline-calendar.md)

**Result:** The skill correctly separated two deadlines that were both
already closed relative to the compile date, correctly flagged that the two
IMLS programs share a single deadline (a cluster worth naming even though
it's not a *conflict* in the capacity sense — same funder, same date, an
applicant would likely only pursue one), and correctly used writer-hours/
award-size reasoning rather than raw date order to note that the
Walmart opportunity — despite falling in the Long-lead tier by date — is
actually a fast, low-effort near-term action given its small award size and
already-open status. No fabricated opportunities or invented deadlines were
used — every entry traces to the source cited in the calendar.
