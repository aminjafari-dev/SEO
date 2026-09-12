---
name: adsense-niche-finder
description: >-
  Researches the web to discover, evaluate, score, and rank narrow niches and
  keyword clusters for a brand-new AdSense-monetized content website. Use when
  the user asks to find a niche, find low-competition keywords, evaluate a
  niche or topic for a new site, estimate keyword demand or difficulty, or plan
  a content site for display-ad revenue.
---

# AdSense Niche Finder

Goal context: read `GOAL.md` at the workspace root first. Summary: pick a niche where a DR-0 site can rank, earn AdSense revenue, and survive AI Overviews. No subject preference; decide on data only.

## Operating rules

- Work autonomously. Do not ask the user which niche to pick; produce a ranked shortlist with evidence.
- Save everything under `research/<YYYY-MM-DD>/`. Create it if missing. Write progress as you go so a crashed run can resume.
- Prefer measured data over tool estimates, and estimates over guesses. Label every number as `measured`, `estimated`, or `proxy`.
- Never fabricate volumes, KD scores, CPCs, or RPMs. If a number is unavailable, say so and use the proxy method.
- Prefer sources published within the last 12 months for anything about Google, AdSense, or AI search; these change fast.
- Search engines rate-limit automated queries. Use the `cursor-ide-browser` tools for Google SERP inspection, pace requests, and fall back to Bing or DuckDuckGo if blocked.
- Do not run any application from the command line. `curl` for public JSON endpoints is fine.

## Pipeline

```
Progress:
- [ ] Phase 0: Set up research folder and load references
- [ ] Phase 1: Generate 40+ candidate niches
- [ ] Phase 2: Quick filter (hard gates) → keep 10–15
- [ ] Phase 3: Deep dive each survivor (competition, demand, ad value, AIO exposure)
- [ ] Phase 4: Score, rank, sanity-check
- [ ] Phase 5: Write final report with top 3 niches and content plans
```

### Phase 0: Setup

1. Create `research/<date>/` with `candidates.md`, `quick-filter.md`, `deep-dive/`, `FINAL-REPORT.md`.
2. Read the reference files listed at the bottom as needed. Do not load all at once; load per phase.

### Phase 1: Generate candidates (target 40+)

Use `reference/idea-sources.md`. Mix at least five different source types (marketplace listings of sold sites, Reddit hobby communities, rising Google Trends, Amazon sub-categories, question sites, Wikipedia category trees, AI-engine prompts). For each candidate record in `candidates.md`:

- Niche name and one-line definition (what the site is about, who searches it).
- Source where the idea came from.
- 3–5 seed keywords typed the way a real person would search.
- Initial guess on intent type (informational / commercial / mixed).

Bias toward: hobbies with equipment and technique questions, home and garden sub-topics, pets by species/breed, DIY and repair, niche crafts, specific tools/software how-tos, regional or cultural topics underserved in English, "how to" problems with many variations.
Avoid at generation time: anything medical, financial advice, legal, insurance, crypto, gambling, adult, weapons, drugs, celebrity, news.

### Phase 2: Quick filter (10 minutes per niche)

For each candidate, run the hard gates. A single FAIL removes the niche. Record PASS/FAIL with a one-line reason in `quick-filter.md`.

Hard gates:
1. **Policy-safe**: Not in AdSense prohibited or restricted categories (see `reference/adsense-economics.md`).
2. **Non-YMYL**: Does not require medical, financial, or legal expertise to write safely.
3. **Beatable SERPs**: For 3 seed keywords, the Google top 10 contains at least one forum/UGC result (Reddit, Quora, niche forum) or at least two small/unknown sites. If all three SERPs are big brands only → FAIL.
4. **Real demand**: Google autocomplete returns 5+ suggestions for the head term, and at least one seed keyword shows a Wikipedia article or subreddit with activity. Zero autocomplete + no community → FAIL.
5. **Depth**: You can list 50+ plausible article titles in 5 minutes. If the niche exhausts at 20 articles → FAIL (too thin even for a thin niche).
6. **AI Overview exposure**: Search 3 seed keywords in Google. If all 3 show an AI Overview that fully answers the query with no reason to click → FAIL. One or two is acceptable; note it.
7. **Producible**: Content can be written from research, public knowledge, or cheap first-hand experience. Requires expensive products, lab tests, or credentials → FAIL.
8. **Not dying**: Google Trends 5-year line is flat or rising. Steep decline → FAIL.

Keep the 10–15 strongest passers. Create `deep-dive/<niche-slug>.md` for each.

### Phase 3: Deep dive (per surviving niche)

Follow `reference/difficulty-checklist.md` and `reference/demand-checklist.md`. Produce per niche:

**A. Keyword cluster (30–60 keywords)**
- Expand seeds via Google, Bing, YouTube autocomplete (endpoints in `reference/free-data-endpoints.md`), People Also Ask, related searches, Reddit thread titles, AlsoAsked-style question trees.
- Tag each keyword: intent, question/non-question, estimated volume bucket, AIO present yes/no.

**B. Competition snapshot (for the 10 most important keywords)**
- Top 10 domains, count of giants vs small sites vs forums.
- Title match count, content age, content depth of the top 3.
- Referring domains to the top 3 URLs (Ahrefs free backlink checker via browser, or note as unavailable).
- `allintitle:"keyword"` count. Compute KGR when volume is under 250.
- SERP features present: ads, AIO, featured snippet, PAA, video, shopping, local.

**C. Demand estimate**
- Autocomplete breadth, Wikipedia monthly pageviews for the core entity, subreddit size and posts/week, YouTube result counts and view counts of top videos, Google Trends relative level vs an anchor keyword, Bing volume if Bing Webmaster Tools is available.
- Estimate cluster volume as a range (low/high) and state the method.

**D. AdSense value**
- Advertiser presence: count ads on commercial-adjacent queries in the cluster. Zero ads across the cluster is a warning sign.
- Related product/service prices (expensive products → higher CPC → higher RPM).
- Map to an RPM tier using `reference/adsense-economics.md`.

**E. AI / GEO exposure**
- AIO presence rate across the 10 keywords.
- Perplexity indexed pages: `site:perplexity.ai "<niche term>"` count.
- Are AIO/Perplexity citations mid-tier sites (winnable) or official/Wikipedia only (hard)?
- Does the niche have queries AI cannot answer well: personal experience, local specifics, tools/calculators, comparisons with tables, images/diagrams needed, frequently updated data? Note them.

**F. Expansion and monetization ceiling**
- Adjacent sub-niches the site could grow into.
- Affiliate potential as secondary revenue (yes/no, what).

### Phase 4: Score and rank

Score each niche 0–10 on the six dimensions, multiply by weight, sum.

- Beatability for a DR-0 site: weight 25
- AdSense value (RPM tier, advertiser density): weight 20
- Demand size (cluster volume range): weight 15
- AI Overview / zero-click resistance: weight 15
- Content producibility and depth (50–200 articles possible, no credentials): weight 15
- Longevity (5-year trend, evergreen): weight 10

Sanity checks before finalizing:
- Does the estimated revenue (see formula in `reference/adsense-economics.md`) at 30,000 pageviews/month exceed $300? If not, the niche needs a very cheap content cost to make sense; flag it.
- Would a reasonable person believe this site can exist for 5 years? If the whole niche depends on one product or platform that could vanish, cap longevity at 4.
- Are the top 3 niches genuinely different from each other? If two overlap, replace one with the next candidate.

### Phase 5: Final report

Write `research/<date>/FINAL-REPORT.md` using the template in `reference/report-templates.md`. It must contain:

1. Method summary and data sources used, with limitations.
2. Full ranked table of all deep-dived niches with scores.
3. For each of the top 3: definition, target reader, keyword cluster, competition snapshot, demand range, RPM tier and revenue projection at 10k/30k/100k pageviews, AIO exposure, risks, and a first 30-article content plan ordered by easiest-to-rank first.
4. Recommended pick with a one-paragraph justification.
5. Next steps: domain naming direction, site structure, publishing cadence, when to apply for AdSense (typically after 20–30 quality articles and required pages).

## Quality bar

- Every claim about a SERP includes the query and the date it was checked.
- Every volume figure includes its source and label (measured / estimated / proxy).
- No niche is recommended without at least 10 SERPs manually inspected.
- The report must be usable by someone who has never seen this chat.

## Reference files

- `reference/adsense-economics.md`: RPM tiers, revenue formula, policy gates, AIO impact on ad revenue.
- `reference/difficulty-checklist.md`: competition analysis for a new site, red and green flags, scoring.
- `reference/demand-checklist.md`: demand estimation with free and first-party sources, triangulation.
- `reference/idea-sources.md`: where to find niche ideas on the web.
- `reference/free-data-endpoints.md`: public JSON endpoints and search operators verified to work.
- `reference/report-templates.md`: candidate, deep-dive, and final report templates.
