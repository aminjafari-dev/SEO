# Project Goal: AdSense Niche Site

## The goal in one sentence

Find a narrow, thin niche where a brand-new website with zero authority can rank on Google (and be cited by AI engines), attract steady informational traffic, and earn money from Google AdSense display ads. Then build a content website around it.

## What "success" means

- A niche where a new site can realistically reach 20,000–50,000+ monthly pageviews within 12–18 months from organic search.
- Content that a solo publisher (or a small team using AI-assisted writing plus human editing) can produce without professional credentials, lab equipment, or expensive products.
- An AdSense page RPM (revenue per 1,000 pageviews) high enough that the traffic converts into meaningful income, ideally RPM above $10, with a path to premium ad networks (Mediavine, Raptive) later.
- A niche that is evergreen or growing, not a dying trend or a 3-month seasonal spike.
- A niche where AI Overviews and zero-click answers do not swallow most of the clicks.

## Constraints and starting position

- No prior subject or preference. The subject is chosen purely on data.
- New domain: Domain Rating 0, no backlinks, no brand, no audience.
- Monetization: Google AdSense first. Affiliate links are a possible secondary layer but are not the goal.
- Must comply with Google AdSense content policies and Google Search quality guidelines (helpful, original, people-first content; clear author identity).
- Language and market default to English / United States (highest AdSense RPMs and largest inventory). Other markets are acceptable if the data shows a clear advantage.
- Budget assumption: near zero for paid tools. Research must work with free tools, public endpoints, and manual SERP inspection. Paid data (Ahrefs, Semrush) is a bonus when available, never a requirement.

## What we are NOT doing

- Not chasing YMYL topics (medical, financial advice, legal) where Google demands credentials.
- Not building on trademarks, celebrity gossip, news, or trending-only topics.
- Not targeting transactional keywords dominated by e-commerce and brands.
- Not building thin, AI-spun content farms. Narrow niche, deep coverage, real value.

## How the research is done

The methodology is captured in the project skill `.cursor/skills/adsense-niche-finder/SKILL.md`. Invoke it with `/adsense-niche-finder` or by asking the agent to find niches for this project. The skill contains:

1. The niche-discovery pipeline (generate candidates, quick-filter, deep-dive, score, report).
2. The competition (difficulty) checklist tuned for a DR-0 site.
3. The demand-estimation checklist using free and first-party sources.
4. AdSense economics: what makes a keyword valuable for display ads.
5. AI Overview / GEO exposure checks.
6. Public data endpoints the agent can query directly.
7. Output templates so every research run produces comparable results.

All research output is saved under `research/` in this workspace so runs can be compared over time.

## Decision rule

A niche is accepted only when it passes every hard gate (policy-safe, non-YMYL, beatable SERPs, real demand, acceptable AI-Overview exposure, producible content) and scores in the top tier on the weighted scorecard defined in the skill. The final deliverable is a ranked shortlist of 3 niches, each with a seed keyword list, a competition snapshot, a demand estimate, a revenue projection, and a first 30-article content plan.
