# Google Trends Technical Reference & Automation Guide

## 1. Google Trends URL Schema Reference

Google Trends URLs encode query terms, dates, and geographic boundaries as follows:

| Parameter | Meaning | Supported Values | Example |
|---|---|---|---|
| `q` | Query or Entity | Comma-separated strings (max 5) | `q=attic%20fan,attic%20fan%20thermostat` |
| `geo` | Target Geography | ISO-3166-1 alpha-2 country code | `geo=US`, `geo=GB`, `geo=CA` |
| `date` | Time Window | Predefined or custom dates | `date=today%205-y`, `date=today%2012-m`, `date=today%203-m`, `date=all` |
| `gprop` | Google Property | Web (default), YouTube, Shopping | `gprop=youtube`, `gprop=froogle` |
| `cat` | Topic Category | Numeric vertical ID (optional) | Omit unless ambiguous (e.g. apple fruit vs tech) |

---

## 2. Query Disaggregation Matrix for Micro-Niches

When evaluating any niche candidate from `quick-filter.md`, use this matrix to generate the exact 5 queries for the comparison batch:

| Candidate Slug | Tier 1: Root Entity | Tier 2: Sub-Topic | Tier 3: Symptom 1 | Tier 3: Symptom 2 | Tier 4: Comparison |
|---|---|---|---|---|---|
| `c11-attic-fan` | `attic fan` | `attic fan thermostat` | `attic fan not working` | `attic fan humming` | `ridge vent vs attic fan` |
| `c17-pellet-stove` | `pellet stove` | `pellet stove igniter` | `pellet stove error code` | `pellet stove auger jam` | `pellet stove vs wood stove` |
| `c02-sump-pump-backup` | `sump pump` | `sump pump battery backup` | `sump pump beeping` | `sump pump not working` | `sump pump battery vs generator` |
| `c18-axolotl-tank` | `axolotl` | `axolotl tank` | `axolotl water temperature` | `axolotl tank filter` | `axolotl tank chilling` |
| `c09-aquascaping-trimming` | `aquascaping` | `planted aquarium` | `aquascaping tools` | `aquarium plant trimming` | `high tech planted tank` |
| `c06-recumbent-trike` | `recumbent trike` | `tadpole trike` | `recumbent bike for seniors` | `recumbent trike adjustment` | `recumbent trike vs bike` |

---

## 3. Data Export Parsing & Normalization

Google Trends exports CSV files with a standard header format:
1. `multiTimeline.csv`:
   - Line 1–2: Title and parameter notes.
   - Line 3: Header (`Week` or `Month`, `<Term 1>: (United States)`, `<Term 2>: (United States)`).
   - Subsequent lines: `YYYY-MM-DD,value1,value2`.
   - Normalization: Values range from 0 to 100. `<1` indicates negligible search volume below the sampling threshold.
2. `relatedQueries.csv`:
   - Contains two distinct sections: **TOP** (indexed 0–100) and **RISING** (percentage increase, e.g., `+250%`, or `Breakout`).
   - "Breakout" indicates that the search term grew by more than 5,000% compared to the prior period.

---

## 4. Automation Fallback Strategies

If direct CSV export download buttons are blocked by browser session constraints or bot detection:
1. **Interactive Browser Extraction (`cursor-ide-browser`)**:
   - Navigate to `https://trends.google.com/explore?...`
   - Use `browser_snapshot` to locate the export buttons (`button[aria-label*="CSV"]` or download icons).
   - Alternatively, evaluate table values via `browser_cdp` using `Runtime.evaluate` to scrape rendered SVG graph data and table rows directly into structured JSON.
2. **Unofficial API / Direct JSON Endpoints**:
   - Trends requests fire background XHR calls to `https://trends.google.com/trends/api/widgetdata/multiline` and `https://trends.google.com/trends/api/widgetdata/relatedsearches`.
   - The token is retrieved from the initial exploration token call (`https://trends.google.com/trends/api/explore`).
