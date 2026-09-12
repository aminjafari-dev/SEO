# Demand Estimation Checklist (free and first-party sources first)

Search volume numbers from tools are modeled, not measured, and disagree by 3–5x. Always triangulate at least three independent signals and report a range with the method labeled `measured`, `estimated`, or `proxy`.

## 1. How each source produces its number (know the bias)

- **Google Keyword Planner (GKP)**: first-party but a 12-month average, bucketed without ad spend, groups close variants, tuned to commercial queries, lags 1–2 months. Free with a Google Ads account.
- **Ahrefs**: GKP base, de-grouped, calibrated with clickstream. Conservative. Shows Clicks, Clicks-per-search, Traffic Potential, Parent Topic.
- **Semrush**: GKP base with its own model. Reads higher than Ahrefs.
- **Moz, Mangools, Ubersuggest, Keywords Everywhere, SE Ranking**: mostly repackaged GKP.
- **Similarweb**: pure clickstream; good above 10k volume, unreliable for the long tail.
- **Google Search Console**: measured impressions, but only for queries your site appeared for.
- **Google Trends**: real Google data, relative 0–100 index, sampled; needs calibration for absolutes.

## 2. Google Keyword Planner tricks (when an Ads account is available)

- Exact numbers instead of buckets appear once the account has spent a small amount; a $1–2/day campaign for a few days usually unlocks them.
- The Forecast tab ("Get search volume and forecasts") shows projected impressions at a bid, even with no spend. High bid → impressions ≈ monthly searches.
- Download the CSV with monthly columns; the 12-month average hides seasonality.
- Use the three-month change and YoY change columns for trend.
- Always set location and language; default global/US numbers can be 10–50x off for other markets.
- Enter singular and plural separately; identical numbers mean GKP grouped them.
- Top-of-page bid columns double as the CPC proxy for AdSense value.

## 3. The measurement gold standard (optional, low cost)

Run a Google Ads exact-match `[keyword]` campaign for 7–14 days with a bid high enough to show on most searches. Real searches ≈ impressions ÷ search impression share. The Search terms report shows the actual phrases users typed. Repeat in Microsoft Ads for Bing demand (relevant to ChatGPT/Copilot).

## 4. Google Search Console as an instrument (once any site exists)

- Impressions at positions 1–3 ≈ 70–95% of real searches. Positions 4–10 undercount (adjust 2–3x on mobile-heavy queries). Position 11+ is not a demand measure.
- Page → Queries tab: sum impressions across all queries for a page = real cluster demand, usually 3–10x the head term.
- Regex filters: `^(how|what|why|can|does|should)\b` for questions; `^(\S+\s+){6,}\S+$` for conversational 7+ word queries.
- GSC reveals long-tail queries with real impressions that tools report as 0.
- If you do not rank yet, publish a decent page, wait 4–6 weeks, read impressions even at position 20.

## 5. Reverse-engineer from competitor traffic (when Ahrefs/Semrush is available)

Approximate organic CTR by position without SERP features: #1 25–30%, #2 13–16%, #3 9–11%, #4 6–8%, #5 5–6%, #6–10 2–4%. Reduce by 30–60% when an AI Overview is present, 20–40% with 3–4 ads, 10–30% with someone else's featured snippet.

Volume ≈ page traffic for that keyword ÷ CTR at its position. Average across #1–#3.

Ahrefs Traffic Potential (total organic traffic of the #1 page) is the best single number for topic demand because it includes the cluster and already reflects click losses.

Inflation check: tool says 5,000 but the #1 page gets 150 visits → inflated or zero-click.

## 6. Google Trends calibration

- **Anchor method**: compare the keyword with a keyword of known volume and similar magnitude. Ratio of average index values ≈ ratio of volumes. Chain anchors for tiny keywords.
- "Search term" = literal string; "Topic" = entity across phrasings and languages. Use Topic for category demand.
- "Not enough data" for 12 months in a big country → probably under a few hundred searches/month there.
- 5-year view for structural trend (growing / flat / dying). 12-month view for seasonality.
- Sub-region breakdown for where demand concentrates (matters for RPM: US/UK/CA/AU pay most).
- Rising and Breakout related queries → demand tools have not caught up with.
- Compare up to 5 phrasings at once to find the wording people actually use.
- Glimpse browser extension adds absolute estimates to Trends.

## 7. Cluster demand, not string demand

- Export all keywords the #1 page ranks for (tool) or collect via autocomplete + PAA + related searches + Reddit titles (free). Sum, then apply clicks-per-search.
- Ahrefs Parent Topic tells you which bigger term you are actually competing for.
- Question mapping: 40 questions × 30 searches = 1,200 real demand invisible on any single line.
- **Autocomplete threshold**: Google only suggests phrases above a minimum frequency. Appearing in autocomplete = real demand even when tools show 0–10. Enumerate with `keyword a`, `keyword b`, … and `keyword ` with trailing space; also prefix words (how/best/why + keyword).
- Bottom-of-SERP "related searches" and "People also search for" = Google telling you the cluster.

## 8. Non-Google demand signals

- **Wikipedia pageviews** (Wikimedia REST API): measured, absolute, public. Best free calibration source for entities and topics.
- **YouTube**: autocomplete (`ds=yt` endpoint), result counts, view counts of top 10 videos and their age (views/month). Large YouTube demand + small Google demand = visual topic, expect video carousels.
- **Amazon**: autocomplete and best-seller rank in the category → product demand and price levels (RPM proxy).
- **Reddit**: subreddit subscribers, posts per week, upvotes on question threads; `site:reddit.com "keyword"` result counts. Use the browser tool (JSON endpoints block scripts).
- **Quora**: question follower and answer counts.
- **Pinterest Trends, TikTok Creative Center** for consumer/visual niches.
- **Bing Webmaster Tools Keyword Research**: free Bing volume. Bing ≈ 3–8% of Google in most markets; also the retrieval layer for ChatGPT/Copilot.
- **Etsy/eBay** listing counts and sold counts for craft and collectible niches.
- **Job boards / course platforms** for skill and B2B topics.
- **Exploding Topics, Glimpse, SparkToro** for emerging demand and audience profile.

## 9. AI-engine demand (GEO)

No official prompt volumes exist. Use proxies:
- `site:perplexity.ai "keyword"` and `site:perplexity.ai/page "keyword"` in Google: indexed Perplexity pages reveal real prompts and their count.
- Residual `site:chatgpt.com/share "keyword"` results.
- AI Overview presence rate across the cluster = share of demand Google now answers generatively.
- Bing volume as a floor for ChatGPT Search / Copilot retrieval demand.
- Ask ChatGPT/Perplexity: "What are the most common questions people ask about X?" for phrasing, not counts.
- Reddit/Quora question frequency doubles as prompt-demand proxy.
- Rule of thumb: informational queries have lost a meaningful share (often 20–50%) of clicks to AI answers; transactional and experience-based queries much less.

## 10. Convert searches to capturable visits

```
Capturable visits ≈ Volume × Clicks-per-search × Organic share × CTR at target position × Intent-match share × Geo-match share
```
Example: 5,000 × 0.6 × 0.8 × 0.12 (position 3 with AIO) × 0.7 × 1.0 ≈ 200 visits/month.

Also account for device split (mobile has more features above the fold), repeat-search rate, branded share of variants, and seasonality timing (a Q4 keyword needs to rank by October).

## 11. Sanity checks

- Tools disagree 3x+ → grouped, ambiguous (multiple meanings), or trending.
- Volume high, #1 traffic tiny → zero-click or inflated.
- Volume 0 but phrase in autocomplete → real long tail; trust autocomplete.
- Tools stable, Trends cliff → tools stale; trust Trends.
- Same number for singular/plural → grouped.
- Odd phrase with big volume → check for a brand, song, show, or product creating unrelated demand.
- Wrong country setting → re-run.

## 12. Triangulation workflow (free-first)

1. Autocomplete breadth on Google, Bing, YouTube for the head term and 5 modifiers.
2. Wikipedia monthly pageviews for the core entity (12 months).
3. Google Trends: 5-year trend, seasonality, regions, anchor calibration against one known-volume keyword.
4. Reddit/Quora/YouTube activity counts.
5. If a tool is available: volume, Clicks, Traffic Potential, Parent Topic for the head term and the #1 page's cluster.
6. If an Ads account is available: GKP exact numbers or forecast impressions; top-of-page bids for RPM proxy.
7. Record low/high range, method, and label. Apply the capture formula.
