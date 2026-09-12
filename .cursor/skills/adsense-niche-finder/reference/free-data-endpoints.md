# Free Data Endpoints and Operators

Verified working with `curl` from this environment unless noted. Pace requests (1–2 seconds apart). URL-encode the query. Use `curl -s -m 15` and a browser-like `-A` User-Agent where indicated.

## Autocomplete (demand breadth, phrasing, long tail)

Google web search:
```
https://suggestqueries.google.com/complete/search?client=firefox&hl=en&gl=us&q=QUERY
```
Returns `[query, [suggestions...]]`. Change `gl` for country, `hl` for language.

Google YouTube:
```
https://suggestqueries.google.com/complete/search?client=firefox&ds=yt&q=QUERY
```

Bing:
```
https://api.bing.com/osjson.aspx?query=QUERY
```

Amazon (US marketplace):
```
https://completion.amazon.com/api/2017/suggestions?mid=ATVPDKIKX0DER&alias=aps&prefix=QUERY
```
Requires `-A 'Mozilla/5.0'`. JSON with `suggestions[].value`.

Enumeration trick: request `QUERY a`, `QUERY b`, … `QUERY z`, plus `how to QUERY`, `best QUERY`, `QUERY for beginners`, `QUERY vs`, `QUERY problems`, `why QUERY`. Deduplicate. Each unique suggestion is a phrase with real search frequency.

## Wikipedia pageviews (measured absolute demand for entities)

```
https://wikimedia.org/api/rest_v1/metrics/pageviews/per-article/en.wikipedia/all-access/user/ARTICLE_TITLE/monthly/YYYYMM0100/YYYYMM0100
```
Requires a descriptive `-A` header (e.g., `-A 'niche-research/1.0'`). `ARTICLE_TITLE` uses underscores. Returns monthly `views`. Use for trend (12–24 months) and as a Trends calibration anchor. Also useful: the interactive UI at `https://pageviews.wmcloud.org/`.

Top articles in a category → candidate leaves:
```
https://en.wikipedia.org/w/api.php?action=query&list=categorymembers&cmtitle=Category:CATEGORY&cmlimit=500&format=json
```

## Google Trends

No stable public API. Use the browser tool on `https://trends.google.com/trends/explore?date=today%205-y&geo=US&q=QUERY` and read the chart; compare up to 5 terms with commas. For related "Rising" queries scroll to the bottom cards. Screenshot for the report when useful.

## Reddit

Scripted JSON (`/r/SUB/about.json`, `/search.json`) is blocked from this environment. Use the browser tool:
- Subreddit size and activity: `https://www.reddit.com/r/SUB/` (members, online, posts per day).
- Question demand: Google `site:reddit.com "QUERY"`; Reddit search `https://www.reddit.com/search/?q=QUERY&sort=new` and read post dates for frequency.

## Google search operators (run in the browser tool; pace queries, fall back to Bing/DDG if blocked)

- `allintitle:"QUERY"` → title-competition count.
- `intitle:"QUERY" inurl:QUERY` → fully optimized pages.
- `QUERY -site:wikipedia.org -site:amazon.com -site:reddit.com -site:youtube.com` → SERP without giants.
- `site:reddit.com "QUERY"`, `site:quora.com "QUERY"` → community demand.
- `site:.gov "QUERY"`, `site:.edu "QUERY"` → institutional coverage.
- `site:perplexity.ai "QUERY"`, `site:perplexity.ai/page "QUERY"` → indexed AI prompts/answers.
- `site:chatgpt.com/share "QUERY"` → residual shared ChatGPT conversations.
- `site:COMPETITOR.com QUERY` → competitor topical depth.
- `"QUERY" "2026"` or current year → freshness of coverage.
- Use `&gl=us&hl=en&pws=0` in the Google URL to reduce personalization.

## Free SEO tools usable via browser (may show captchas; retry slowly)

- Ahrefs free tools: Keyword Generator, Keyword Difficulty Checker, Backlink Checker, Website Authority Checker (`https://ahrefs.com/free-seo-tools`).
- Moz Link Explorer free tier (requires account).
- Semrush free tier (10 queries/day with account).
- Ubersuggest free daily searches.
- Google PageSpeed Insights (`https://pagespeed.web.dev/`) for competitor page experience.
- Bing Webmaster Tools Keyword Research (requires account) for Bing volume.
- Google Keyword Planner (requires Google Ads account; forecast tab works with no spend).

## YouTube (demand and visual-topic signal)

Search results page in the browser: result count, top-10 view counts and upload dates → views per month. Channels dedicated to the topic with 50k+ subs indicate durable interest.

## Wayback Machine (competitor age and update history)

```
https://archive.org/wayback/available?url=DOMAIN&timestamp=20150101
```
Returns the closest archived snapshot; earliest snapshot approximates domain age. Or browse `https://web.archive.org/web/*/DOMAIN`.

## Output handling

Save raw JSON responses under `research/<date>/raw/` when they inform a decision, so numbers in the report can be audited.
