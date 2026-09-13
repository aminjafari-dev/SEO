---
name: google-trends-keyword-validator
description: Validates SEO niche topics and keyword clusters using Google Trends. Normalizes raw niche concepts into search queries, collects interest-over-time, seasonal patterns, regional interest, and related rising queries, saves downloaded reports/CSVs, and scores keyword viability.
---

# Google Trends Keyword & Niche Validator

This skill defines the autonomous protocol for validating keyword clusters and niche concepts against Google Trends. It transforms high-level editorial concepts into verified search queries, analyzes historical trajectory, detects seasonality and geographic demand, captures related rising topics, and saves structured CSV reports and validation scorecards.

---

## When to Use This Skill
- Validating candidate niches before committing content resources.
- Verifying whether search volume is rising, evergreen, seasonal, or dying.
- Discovering untapped "Breakout" long-tail queries directly from Google's database.
- Downloading and archiving Google Trends reports (interest over time, regional breakdown, related queries/topics) for audit and tracking.

---

## Core Rules & Guardrails

1. **NEVER Query Category Labels or Full Sentences**:
   - ❌ WRONG: `Attic Fan Thermostat & Troubleshooting`, `Complete guide on how to fix vintage sewing machines`
   - ✅ CORRECT: `attic fan`, `attic fan thermostat`, `attic fan motor`, `vintage sewing machine`
   - *Rule*: Google Trends measures exact query frequency. Search queries must reflect real human search behavior (1–4 words, no punctuation/ampersands).

2. **Always Analyze in Two Time Windows**:
   - **5-Year Window (`date=today 5-y`)**: Measures long-term trajectory (Rising, Evergreen/Flat, Declining/Fad) and multi-year cyclical stability.
   - **12-Month Window (`date=today 12-m`)**: Measures granular monthly seasonality, exact peak months, and recent breakout query velocity.

3. **Batch Comparisons in Groups of 3–5**:
   - Compare the core entity against related sub-components simultaneously in Google Trends (e.g., `attic fan` vs `attic fan thermostat` vs `whole house fan` vs `solar attic fan`).
   - This normalizes relative interest and reveals which sub-topic commands the highest share of search intent.

4. **Preserve Raw Data Artifacts**:
   - Save every downloaded report (Timeline, GeoMap, Related Queries, Related Topics) into `research/<date>/trends-reports/<slug>/` with predictable file naming.

---

## Step-by-Step Workflow

### Step 1: Query Normalization & Disaggregation
Given any niche concept (from `candidates.md`, `quick-filter.md`, or user prompt), disaggregate it into 4 distinct search-intent tiers:

| Tier | Purpose | Format | Example for `c11-attic-fan` |
|---|---|---|---|
| **Tier 1: Root Entity** | Broadest volume baseline | 1–2 words | `attic fan` |
| **Tier 2: Primary Sub-Topic** | Core focus of the micro-niche | 2–3 words | `attic fan thermostat` |
| **Tier 3: Symptom / Problem** | Troubleshooting & pain point | 3–4 words | `attic fan not working`, `attic fan humming` |
| **Tier 4: Comparative / Choice** | Commercial decision & vs | 3–4 words | `ridge vent vs attic fan`, `solar attic fan` |

---

### Step 2: URL Construction & Parameter Setting

Construct Google Trends exploration URLs using standard parameters:
- **Base URL**: `https://trends.google.com/explore`
- **Target Country**: `geo=US` (or `geo=GB`, `geo=CA`, or omit for worldwide)
- **Timeframes**:
  - 5-Year: `date=today%205-y`
  - 12-Month: `date=today%2012-m`
- **Search Type**: Web Search (default), or `gprop=youtube` for video verification.

#### URL Generation Pattern:
```
# Single term 5-year:
https://trends.google.com/explore?date=today%205-y&geo=US&q=attic%20fan

# Comparison 5-year (up to 5 terms separated by commas):
https://trends.google.com/explore?date=today%205-y&geo=US&q=attic%20fan,attic%20fan%20thermostat,whole%20house%20fan,solar%20attic%20fan
```

---

### Step 3: Report Retrieval & Archiving

For each keyword set, extract and download the 4 standard Google Trends reports and save them to:
`research/<date>/trends-reports/<slug>/`

1. **Interest Over Time (MultiTimeline)**:
   - File: `<slug>-<term>-timeline-5y.csv`
   - Data columns: `Week / Month`, `Interest Index (0-100)`.
2. **Subregion / Metro Breakdown (GeoMap)**:
   - File: `<slug>-<term>-subregion.csv`
   - Data columns: `State / Metro`, `Relative Interest Index`.
3. **Related Topics (Top & Rising)**:
   - File: `<slug>-<term>-related-topics.csv`
   - Data columns: `Topic`, `Top Score (0-100)` or `Rising (% growth / Breakout)`.
4. **Related Queries (Top & Rising)**:
   - File: `<slug>-<term>-related-queries.csv`
   - Data columns: `Query`, `Top Score (0-100)` or `Rising (% growth / Breakout)`.

*Execution Note*: Use browser automation (`cursor-ide-browser` or `browser-use`) or Trends API/endpoints to navigate to each URL and capture the report data or triggered CSV downloads. If browser downloads are blocked or headless, parse the rendered table widgets directly or leverage curl endpoints.

---

### Step 4: Metric Calculation & Scoring

Evaluate the captured data against 5 quantitative validation benchmarks:

#### 1. Long-Term Trajectory (5-Year Slope):
- **Rising (+10% to +100%+ over 5y)**: Score = 10/10. High growth opportunity.
- **Evergreen / Flat (±10% variance across 5y)**: Score = 8.5/10. Highly durable, reliable AdSense income.
- **Declining (-15% to -40%)**: Score = 4/10. Proceed only with low-effort production.
- **Dying / Fad (> -50% decline)**: Score = 0/10. **REJECT (Fail Gate 8)**.

#### 2. Seasonality Ratio (Peak-to-Trough):
- Calculate: $\text{Seasonality Ratio} = \frac{\text{Highest Month Average Index}}{\text{Lowest Month Average Index}}$
- **Non-Seasonal (< 1.8x)**: Steady year-round revenue.
- **Moderate Seasonal (1.8x – 3.5x)**: Predictable peak (e.g., summer or winter); requires off-season buffer content.
- **Hyper-Seasonal (> 3.5x)**: Extreme revenue drought for 6–8 months. Must be flagged with `Seasonal-Risk`.

#### 3. Regional Concentration:
- Inspect top 5 US states. If >60% of search interest comes from only 1 or 2 states, it is a regional sub-niche. If distributed across 20+ states, it is national.

#### 4. Breakout Velocity:
- Inspect the **Related Queries (Rising)** list.
- Count queries marked **"Breakout"** (>5,000% surge) or with >+100% growth.
- These queries form immediate priority articles for the 30-article launch plan.

---

### Step 5: Deliverable Template (`<slug>-trends.md`)

Save the synthesized report to `research/<date>/deep-dive/<slug>-trends.md`:

```markdown
# Google Trends Validation Report: <Niche Name> (`<slug>`) — <date>

## 1. Disaggregated Queries Evaluated
- Tier 1 (Entity): `<query>`
- Tier 2 (Sub-topic): `<query>`
- Tier 3 (Symptoms): `<query 1>`, `<query 2>`
- Tier 4 (Comparisons): `<query 1>`, `<query 2>`

## 2. 5-Year Trajectory & Longevity
- 5-Year Trend Status: Rising / Evergreen / Declining
- Historical 5-Year Average Index: <number>
- Trajectory Summary: <one paragraph>

## 3. Seasonality Profile (12-Month Analysis)
- Peak Months: <e.g., June–August>
- Trough Months: <e.g., December–February>
- Peak-to-Trough Ratio: <e.g., 2.8x (Moderate Seasonal)>
- Off-Season Mitigation Strategy: <how to generate off-season traffic>

## 4. Geographic Distribution
- Top 5 States / Regions: 1. <State> (<Index>), 2. <State> (<Index>), ...
- Geographic Reach: National / Regional / Climate-Zoned

## 5. High-Velocity & Breakout Queries
| Query | Growth Rate | Actionable Article Idea |
|---|---|---|
| `<query>` | Breakout / +X% | `<title>` |

## 6. Archival File Manifest
- Timeline Data: `trends-reports/<slug>/<file>.csv`
- Subregion Data: `trends-reports/<slug>/<file>.csv`
- Related Queries: `trends-reports/<slug>/<file>.csv`

## 7. Validation Verdict
- Final Status: **VERIFIED-PASS** / **MARGINAL** / **FAIL**
- Recommendation: <proceed to cluster build / adjust focus>
```
