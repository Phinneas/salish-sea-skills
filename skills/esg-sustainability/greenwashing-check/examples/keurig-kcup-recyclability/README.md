# Example: Keurig K-Cup "recyclable" claims (2019–2024)

**Scenario:** Dry-run test of `greenwashing-check` against a real,
publicly documented set of environmental marketing claims — required
before this skill is considered publishable (see
`../../../../testing`, Layer 2).

**Input:** Two real, independently verifiable claims made by Keurig Dr
Pepper about its K-Cup single-use coffee pods, both drawn from public
record rather than constructed for this test:

1. The unqualified claim ("100% recyclable," asterisked, live on
   Keurig's site since the end of 2020 and still there as of September
   2024) and the underlying representation Keurig made to investors in
   its 2019 and 2020 Form 10-K filings — that internal testing
   "validate[d] that [K-Cup pods] can be effectively recycled" — which
   the SEC found omitted that two of the largest U.S. recycling
   companies, operating more than a third of the country's recycling
   facilities, had given "significant negative feedback" on the pods and
   did not intend to accept them. The SEC charged Keurig with violating
   Section 13(a) of the Securities Exchange Act over this omission and
   Keurig paid a $1.5 million civil penalty (Sept. 10, 2024), without
   admitting or denying the findings.
   Source: [SEC press release 2024-122](https://www.sec.gov/newsroom/press-releases/2024-122);
   [NPR, Sept. 12, 2024](https://www.npr.org/2024/09/12/nx-s1-5109902/keurig-kcup-pods-recycle-sec-fine).

2. Keurig's own post-settlement public statement, given to NPR the same
   week: "Our K-Cup pods are made from recyclable polypropylene plastic
   (also known as #5 plastic), which is widely accepted in curbside
   recycling systems across North America. We continue to encourage
   consumers to check with their local recycling program to verify
   acceptance of pods, as they are not recycled in many communities."

**Output:** [audit.md](./audit.md)

**Result:** The skill correctly separated the two claims rather than
treating "Keurig's recyclability claims" as one item, rated the
unqualified pre-2024 claim High risk under § 260.12(d) (component —
pod size/shape — significantly limits actual recyclability regardless of
the material's technical recyclability) with a direct citation to the
same reasoning the SEC and later commentators (e.g. the Colgate toothpaste
tube litigation, which turns on an identical fact pattern) applied, and
rated the post-settlement qualified statement Low-Medium — genuinely
improved by disclosing that most communities don't recycle the pods, but
still flagged "widely accepted" as needing a real substantiation figure
(a percentage or source) rather than an unquantified adjective. No risk
rating or fix was invented without tying it to the specific Green Guides
provision or the real enforcement history above.
