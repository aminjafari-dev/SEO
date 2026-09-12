# Research Activity & Query Log — 2026-09-13

## Run parameters
market: gl=us hl=en (note UK/CA/AU) | deep dives per run: 2 | paid data: none | capacity: 15–25 articles/month

## Phase status (tick only when the Definition of Done in section 12 of the plan is fully met)
- [x] Phase 0 done — 2026-09-13 00:40
- [ ] Phase 1 done — 
- [ ] Phase 2 done — 
- [ ] Checkpoint 1 — human chose: 
- [ ] Phase 3 done for: 
- [ ] Checkpoint 2 — human decision: 
- [ ] Phase 4 done — 
- [ ] Phase 5 done — 

## Blocked / unresolved items (hand to human at next checkpoint)
| Row # | Item | Reason | What the human can do |
|-------|------|--------|-----------------------|
| 1 | Google SERP direct browser inspection | Redirected by Google to /sorry/ (unusual traffic / bot block) | Human can manually inspect specific queries in personal browser if needed |

## Chronological Action Log
| # | Timestamp | Niche / Candidate | Action / Tool | Exact Query / Target URL / Endpoint | Key Results & Observations | Decision / Next Action |
|---|-----------|-------------------|---------------|-------------------------------------|----------------------------|------------------------|
| 1 | 2026-09-13 00:37 | - | CALIBRATION | `https://www.google.com/search?q=what+is+photosynthesis&gl=us&hl=en&pws=0&num=10` | Redirected to https://www.google.com/sorry/index (bot block). 0 organic results rendered. | Calibration result: AIO and Google ads cannot render in browser; record as unknown-not-rendered. Google SERPs fallback to Bing/DDG for rank checks. |

## Detailed Investigation Entries

### [LOG-001] Session Calibration
- **Objective / Hypothesis Tested**: Verify whether Google SERP AI Overview and Ads render in browser session.
- **Tool & Exact Command / URL**: `browser_navigate` to `https://www.google.com/search?q=what+is+photosynthesis&gl=us&hl=en&pws=0&num=10`
- **Output / Findings (numbers, domains, suggestions)**: Redirected to Google `/sorry/` page ("Why did this happen?").
- **Interpretation & Verdict**: Direct Google search queries from browser environment are blocked by Google automated traffic detection. Per contract rules, log BLOCKED, mark AIO/ads as unknown-not-rendered, and use Bing/DDG as fallback for domain ranking checks.
