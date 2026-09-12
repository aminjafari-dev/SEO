# Competition (Difficulty) Checklist for a DR-0 Site

The site has no authority, no links, no brand. Difficulty is judged relative to that. Every keyword judgment must be based on an actual SERP inspection with the query and date recorded.

## 1. Tool difficulty scores (if any are available)

- Ahrefs KD counts referring domains to the top 10 only. Semrush KD% blends authority, links, and SERP features and reads higher. Moz leans on domain authority. Google Keyword Planner "competition" is ads competition, not organic.
- For this project: target Ahrefs KD under 15 (or Semrush under 30) as a first filter, then always confirm manually. A low KD with a brand-only SERP is still unbeatable.
- If two tools disagree by 3x or more, the SERP is probably dominated by high-authority domains with few page-level links; treat it as harder than the lower number.

## 2. Manual SERP inspection (incognito, target country set)

Record for each keyword: date, top 10 domains, page types, SERP features.

Who is ranking:
- Giants (Wikipedia, Amazon, Forbes, Healthline, government, universities, major retailers, major publishers): 5+ in top 10 → unbeatable for a new site. 2–4 → hard. 0–1 → good.
- Forums and UGC (Reddit, Quora, Stack Exchange, niche forums, Facebook groups, YouTube comments): 1 → good, 2+ → excellent. Google shows them when no dedicated page answers well.
- Small or unknown sites, personal blogs, Medium, Substack, LinkedIn, PDFs, Slideshare: weak pages, beatable.
- Same domain twice → strong topical authority; harder.
- Google properties (YouTube, Maps, Shopping, Play Store) dominating → skip.

How well pages match:
- Titles not containing the keyword or a close variant → pages rank by accident; beatable.
- Homepages or category pages instead of dedicated articles → beatable with a focused article.
- Content older than 2 years with no updates → beatable in most niches.
- Thin content (under 600 words), poor formatting, no images → beatable.
- Mixed intent SERP (blogs + products + videos) → Google unsure; easier than a locked SERP.

## 3. Search operators for competition counts

- `allintitle:"keyword"` → number of pages targeting the keyword in the title. Under ~1,000 low, over ~50,000 high, but always compare to demand.
- `intitle:"keyword" inurl:keyword` → fully optimized pages. Under ~100 is promising.
- `keyword -site:wikipedia.org -site:amazon.com -site:reddit.com` → what the SERP looks like without giants; shows the tier you actually compete against.
- `site:reddit.com "keyword"` → community demand and the questions people ask.
- `site:.gov "keyword"` and `site:.edu "keyword"` → whether authoritative institutions cover it (bad sign if they dominate).

Keyword Golden Ratio (for volume under 250): `KGR = allintitle count ÷ monthly volume`. Under 0.25 → often rankable within weeks with no links. 0.25–1.0 → possible. Over 1.0 → skip for a new site.

## 4. Page-level analysis of the top 3 URLs

- Referring domains to the URL (Ahrefs free backlink checker via browser, Moz Link Explorer free tier). Under 5 → beatable with content and internal links. 5–20 → needs a few links. 20+ → long-term or skip.
- Link quality: 50 directory links matter less than 5 editorial links.
- Content depth: headings, subtopics covered, images, tables, FAQs, schema.
- Freshness: last-modified date, current-year references.
- Page experience: PageSpeed Insights score; ad-heavy slow pages are easier to outrank on a tie.
- On-page: keyword in title, H1, URL, intro. Missing → they win on authority only.
- Internal links to the page: `site:competitor.com "keyword"` count.
- Estimated page traffic vs. keyword volume: big gap → inflated volume or zero-click.

## 5. Domain-level analysis of ranking sites

- DR/DA compared to 0. Rule of thumb: at least 2–3 of the top 10 should be DR under 20 for a new site to have a path in.
- Topical authority: `site:competitor.com topic` page count. 100+ pages on the topic → hard to displace even with fewer links.
- Whole-site niche relevance: dedicated niche sites are harder than general publications touching the topic once.
- Brand search volume: brands with thousands of monthly branded searches carry trust that content alone will not beat.
- Traffic trend: falling competitor traffic → Google already demoting them; opening.
- Knowledge panel / Wikipedia page → recognized entity; hard.

## 6. Intent and SERP features

Intent:
- Informational (how, what, why, guide, tips, ideas, examples) → easiest for a new site and best for display ads.
- Commercial investigation (best, review, vs, top) → affiliates dominate; medium-hard.
- Transactional (buy, price, near me, discount) → e-commerce and brands; skip.
- Navigational (brand names) → never.

Features that steal clicks (affects revenue more than rank): ads above the fold (count them), AI Overview, featured snippet owned by someone else, shopping carousel, local pack, video carousel, image pack, PAA pushing results down, knowledge panel, top stories.

Zero-click check: if the SERP answers the query on the page (snippet, AIO, calculator, date), rankability is irrelevant; revenue will be near zero.

SERP volatility: re-check important SERPs after 1–2 weeks. Frequent reshuffling means Google has not settled; new content can break in. A SERP unchanged for years is locked.

## 7. Red flags → skip regardless of KD

- Top 10 entirely brands or large publishers.
- Every result is a homepage of a company (brand-dominated intent).
- Google's own properties dominate.
- AIO or snippet fully answers, clicks-per-search under 0.3.
- YMYL topic.
- Peak season already passed or 70%+ of volume in one quarter.
- Trademark or product name of another company.
- Volume high but the #1 page gets negligible traffic.

## 8. Green flags → prioritize

- Reddit, Quora, or forums in the top 5.
- Titles in top 10 mostly do not match the keyword.
- Several top 10 URLs with under 5 referring domains.
- 2–3+ results from DR-under-20 domains.
- Content older than 2 years or under 800 words.
- Mixed-intent SERP.
- Low allintitle count relative to demand (KGR under 0.25 for small terms).
- AIO/Perplexity cite mid-tier sites or Reddit rather than official sources.
- Rising Google Trends line.

## 9. Per-keyword score (0 hard → 2 easy, sum of 12 items; under 10 hard, 10–18 medium, over 18 target)

1. Tool KD average: 0 if >50, 1 if 25–50, 2 if <25 (skip if unavailable and rescale)
2. Giants in top 10: 0 if 5+, 1 if 2–4, 2 if 0–1
3. Forums/UGC in top 10: 0 none, 1 one, 2 two+
4. Median referring domains to top 3 URLs: 0 if >30, 1 if 5–30, 2 if <5
5. Count of DR<20 domains in top 10: 0 if none, 1 if 1–2, 2 if 3+
6. Exact-title matches in top 10: 0 if 8+, 1 if 4–7, 2 if <4
7. Top 3 content quality/freshness: 0 strong & fresh, 1 mixed, 2 weak or old
8. Click-stealing SERP features: 0 heavy, 1 some, 2 mostly clean
9. Intent: 0 transactional/navigational, 1 commercial, 2 informational or mixed
10. Query resistance to AI answers: 0 single fact, 1 moderate, 2 experience/visual/process
11. AIO/AI citation sources: 0 official only, 1 mixed, 2 mid-tier and UGC
12. Cluster depth around the keyword: 0 isolated, 1 some variants, 2 rich cluster

Niche beatability score (0–10 for the weighted scorecard) = average per-keyword score across the 10 inspected keywords ÷ 2.4.
