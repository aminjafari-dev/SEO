# Report Templates

Copy these into the research folder. Keep the field names so runs are comparable.

## candidates.md (Phase 1)

```markdown
# Candidate niches — <date>

| # | Niche | Definition (who searches, what for) | Source URL | Seed keywords (3–5) | Intent guess |
|---|-------|--------------------------------------|------------|----------------------|--------------|
| 1 | | | | | |
```

## quick-filter.md (Phase 2)

```markdown
# Quick filter — <date>

| # | Niche | Policy | YMYL | Beatable SERPs | Demand | Depth (50+ titles) | AIO exposure | Producible | Trend | Result | Notes |
|---|-------|--------|------|----------------|--------|--------------------|--------------|------------|-------|--------|-------|
| 1 | | PASS | PASS | PASS (2 forums in top10 for "…") | PASS (14 suggestions, r/… 45k) | PASS | 1/3 AIO | PASS | flat | KEEP | |
```

## deep-dive/<niche-slug>.md (Phase 3)

```markdown
# Deep dive: <Niche name> — <date>

## Definition
One paragraph: what the site covers, who the reader is, what problem brings them to search.

## Keyword cluster
| Keyword | Intent | Question? | Volume bucket (label) | AIO? | Notes |
|---------|--------|-----------|------------------------|------|-------|

Cluster demand estimate: LOW–HIGH searches/month (method: …; label: estimated/proxy).

## Competition snapshot (10 keywords, checked <date>, gl=us)
| Keyword | Giants | Forums | DR<20 sites | Title matches | Top-3 RDs | allintitle | KGR | Features | Score /24 |
|---------|--------|--------|-------------|---------------|-----------|------------|-----|----------|-----------|

Average per-keyword score: …  → Beatability (0–10): …
Notable competitors: domain, estimated size, weakness.

## Demand signals
- Google autocomplete: N unique suggestions across enumeration.
- Wikipedia pageviews (<article>): … /month, 12-month trend …
- Reddit: r/… members, ~… posts/week. Quora: …
- YouTube: top-10 videos … total views, newest …
- Google Trends (5y): rising/flat/declining; seasonality: …; top regions: …
- Tool data (if any): …
- Demand (0–10): …

## AdSense value
- Ads on commercial-adjacent queries: … of 5 queries showed 3+ ads.
- Typical product/service price level: …
- GKP top-of-page bids (if available): …
- RPM tier: A/B/C/D → assumed RPM range $…–$…
- Revenue projection (low–high): 10k pv: $…; 30k pv: $…; 100k pv: $…
- Ad value (0–10): …

## AI / GEO exposure
- AIO present on …/10 keywords.
- `site:perplexity.ai` results: …
- Citation sources: official / mixed / mid-tier.
- AI-resistant query types present: …
- AIO resistance (0–10): …

## Producibility and depth
- Expertise needed: none / hobbyist / professional.
- First-hand experience possible cheaply? …
- Article inventory: … plausible titles; expansion sub-niches: …
- Producibility (0–10): …

## Longevity
- 5-year trend: …; dependency on a single product/platform: …
- Longevity (0–10): …

## Risks
- …

## Weighted score
Beatability ×25 + Ad value ×20 + Demand ×15 + AIO resistance ×15 + Producibility ×15 + Longevity ×10 = … / 1000
```

## FINAL-REPORT.md (Phase 5)

```markdown
# Niche research report — <date>

## 1. Method and sources
Sources used, tools available/unavailable, dates of SERP checks, limitations.

## 2. Ranking
| Rank | Niche | Beatability | Ad value | Demand | AIO resist. | Producibility | Longevity | Total |
|------|-------|-------------|----------|--------|-------------|---------------|-----------|-------|

## 3. Top 3 niches
### 3.1 <Niche>
- Definition and target reader
- Keyword cluster summary (link to deep dive)
- Competition snapshot summary
- Demand range and method
- RPM tier and revenue projection at 10k / 30k / 100k pageviews
- AIO exposure and AI-resistant angles
- Risks
- First 30 articles (ordered easiest-to-rank first; include target keyword and intent per article)

### 3.2 …
### 3.3 …

## 4. Recommended pick
One paragraph with the decisive reasons and the main risk to monitor.

## 5. Next steps
- Domain naming direction (brandable, not exact-match)
- Site structure: pillar pages and clusters
- Publishing cadence and the first 90 days
- Required pages before AdSense application (About, Contact, Privacy, Editorial policy, author bio)
- When to apply for AdSense and when to re-run this research (e.g., 6 months)
```
