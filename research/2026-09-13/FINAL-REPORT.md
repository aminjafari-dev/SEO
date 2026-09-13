# Niche Research Report — 2026-09-13

**Report Status: PARTIAL (1 Deep Dive Completed per Human Instruction)**  
*Run Parameters*: Target Market: US English (`gl=us&hl=en`), Target Monetization: Google AdSense Display Ads, Target DR: 0 (brand new site), Publishing Capacity: 15–25 articles/month (first 30 in 60 days).

---

## 1. Method and Sources

### 1.1 Discovery & Evaluation Pipeline
This research followed the structured 6-phase pipeline defined in the AdSense Niche Finder execution protocol:
1. **Phase 0 — Workspace Setup & Session Calibration**: Created structured storage (`research/2026-09-13/`), initialized audit logs, and ran session calibration.
2. **Phase 1 — Candidate Generation**: Sourced exactly 20 micro-niches across 5 source types (listed sites, communities, hobby inventories, product-driven, question discovery) and 5 topical categories (equipment hobby, living things, home systems/appliances, crafts/making, outdoor sports). All 20 passed narrowness test T1 (≤8 words) and autocomplete breadth test T2 (6 ≤ U ≤ 45).
3. **Phase 2 — Eight Hard Gates**: Filtered cheapest-first (Policy → Non-YMYL → Producible → Depth → Demand → Trend → SERP Beatability & AIO). 18 candidates passed all gates (KEEP); 2 were rejected (Gate 1 Policy: `c20-compound-bow-tuning`; Gate 5 Depth: `c03-inflatable-kayak`).
4. **Phase 3 — Deep Dive**: Executed full keyword cluster expansion (35 queries across 4 intent buckets), 10 scored SERP inspections via the 12-item difficulty checklist, demand triangulation, AdSense revenue modeling, AI/GEO resistance analysis, and content producibility assessment for the human-selected winner (`c11-attic-fan`).
5. **Phase 4 — Scoring & Sanity Checks**: Applied the weighted formula and ran the 4 sanity checks (High-Score UGC check, Low-Beatability flag, AIO-Vulnerability flag, Seasonal-Risk flag).
6. **Phase 5 — Report Generation**: Synthesized findings, ranking, top 3 profiles, 30-article launch plan, and next steps.

### 1.2 Data Sources & Tools Used
- **Google Autocomplete (GSuggest)**: Queried directly via public HTTP endpoint (`suggestqueries.google.com/complete/search?client=firefox&gl=us&hl=en&q=...`) with `full_network` permissions.
- **Bing Suggest & YouTube Suggest**: Queried via public JSON endpoints to verify cross-platform search breadth.
- **Amazon Completion API**: Queried for commercial buying intent and accessory replacement volume.
- **Wikipedia API**: Measured 12-month trailing monthly pageview averages for primary entity topics.
- **WebSearch / Organic SERP Inspection**: Inspected live Google/Bing organic search result distributions, competitor domain types, forum presence, and content depth.
- **Limitations & Blocked Items**:
  - *Google Direct Browser Scraping*: Calibrated at LOG-001; direct browser navigation redirected to Google `/sorry/` bot detection. Per contract rules, Google AIO and Google Ads fields are recorded as `BLOCKED (unknown-not-rendered)` in the master log, and organic competitiveness was audited via DuckDuckGo, Bing, and native `WebSearch` fallback endpoints.
  - *No Paid SEO APIs*: No Ahrefs, Semrush, or Google Ads accounts were used. All KD, search volume, and CPC figures are explicitly labeled as `estimated` or `proxy-triangulated`.

---

## 2. Ranking

The surviving top-tier micro-niches evaluated across the weighted scoring model:
$$\text{Total Score} = (\text{Beatability} \times 25) + (\text{Ad Value} \times 20) + (\text{Demand} \times 15) + (\text{AIO Resist.} \times 15) + (\text{Producibility} \times 15) + (\text{Longevity} \times 10)$$

| Rank | Slug | Niche Description | Beatability (/10) | Ad Value (/10) | Demand (/10) | AIO Resist. (/10) | Producibility (/10) | Longevity (/10) | Total (/1000) | Flags |
|:----:|------|-------------------|:-----------------:|:--------------:|:------------:|:-----------------:|:-------------------:|:---------------:|:-------------:|:-----:|
| **1** | **`c11-attic-fan`** | **Attic Fan Thermostat & Troubleshooting** | **8.58** | **8.50** | **7.50** | **8.00** | **9.00** | **8.50** | **837.0** | **Seasonal** |
| 2 | `c17-pellet-stove` | Pellet Stove Error Codes & Mechanical Repair | 8.30 | 8.50 | 7.50 | 8.00 | 8.50 | 8.50 | 822.5 | Seasonal |
| 3 | `c02-sump-pump-backup` | Sump Pump Battery Backup & Alarm Troubleshooting | 8.10 | 8.50 | 7.50 | 8.00 | 8.50 | 8.50 | 817.5 | Clean |
| 4 | `c18-axolotl-tank` | Axolotl Aquarium Care & Chilling | 8.20 | 6.50 | 9.50 | 7.00 | 8.50 | 8.00 | 790.0 | Clean |
| 5 | `c09-aquascaping-trimming` | High-Tech Aquascaping Plant Trimming | 8.00 | 6.50 | 8.00 | 7.50 | 8.50 | 8.50 | 775.0 | Clean |
| 6 | `c06-recumbent-trike` | Recumbent Trike Adjustment & Senior Transport | 8.00 | 7.50 | 6.50 | 8.00 | 8.00 | 8.00 | 767.5 | Clean |

*Sanity Check Summary*: All top 6 candidates passed Sanity Check 1 (forums or small blogs ranking in positions 1–3). None fell below the Beatability threshold (<120) or AIO threshold (<60). `c11-attic-fan` and `c17-pellet-stove` received the "Seasonal" flag due to summer and winter weather peaks respectively.

---

## 3. Top 3 Niches

### 3.1 `c11-attic-fan`: Attic Fan Thermostat & Mechanical Troubleshooting (Evaluated Winner)
- **Definition & Target Reader**: Covers residential powered attic ventilators (PAVs), bimetallic and digital thermostat calibration, motor capacitor diagnosis, noise reduction, and building-science roof ventilation. The reader is a homeowner or DIYer with an active attic fan failure (humming, vibrating, running non-stop, or not turning on during summer heat) seeking step-by-step diagnostic procedures without paying $300+ for an electrician or HVAC contractor.
- **Keyword Cluster Summary**: 35-keyword cluster developed across 4 intent buckets (Informational How-To, Troubleshooting Symptom, Comparison Choice, Cost Planning). Full cluster detailed in [Deep Dive Report](deep-dive/c11-attic-fan.md).
- **Competition Snapshot**: Average per-keyword difficulty across 10 inspected queries is **20.6 / 24** (Beatability: **8.58 / 10**). Small DIY blogs (`RapidRepair.blog`, `FixUpFirst.com`, `ToolsAdvisers.com`, `HouseFixMaster.com`) and forums (`Reddit r/HomeImprovement`, `DIY StackExchange`) dominate positions 1–5. Giant media publishers are virtually absent on symptom-specific queries.
- **Demand Range & Method**: 20,000–35,000 searches/month total cluster demand (proxy-triangulated via 26 initial autocomplete seeds, 100+ long-tail variants, 1,008 Wikipedia views/month for `Attic_fan`, and 150k–350k views on top YouTube diagnostic videos).
- **RPM Tier & Revenue Projections**: Solid **Tier B ($15–$25 RPM)** driven by HVAC contractor ad bidding and replacement electrical components.
  - *10,000 pageviews/mo*: $150 – $250 / month
  - *30,000 pageviews/mo*: $450 – $750 / month
  - *100,000 pageviews/mo*: $1,500 – $2,500 / month
- **AIO Exposure & AI-Resistant Angles**: AIO risk is **Low (<25%)**. AI overviews cannot replicate physical multimeter continuity testing, hearing the difference between bad sleeve bearings and blown run capacitors, or troubleshooting model-specific 2-wire vs 3-wire junction boxes.
- **Top Risks**: Pronounced summer seasonality (May–August peak). Mitigated by creating year-round content covering winter condensation control, cold-weather draft dampers, and insulation air-sealing.

#### First 30 Articles for `c11-attic-fan` (Ordered Easiest-to-Rank First)

| # | Article Title | Target Keyword | Intent Bucket | Est. Difficulty | Priority |
|---|---------------|----------------|---------------|-----------------|:--------:|
| 1 | Why Does My Attic Fan Keep Shutting Off? (Thermal Overload Guide) | `why does my attic fan keep shutting off` | Troubleshooting | Very Low | P1 |
| 2 | How to Test an Attic Fan Thermostat with a Multimeter (Step-by-Step) | `how to test attic fan thermostat` | How-to | Very Low | P1 |
| 3 | Attic Fan Humming But Not Spinning: 4 Quick Fixes | `attic fan humming but not spinning` | Troubleshooting | Very Low | P1 |
| 4 | Attic Fan Running Constantly in Winter: Causes & Proper Settings | `attic fan constantly running in winter` | Troubleshooting | Very Low | P1 |
| 5 | Why Is My Attic Fan Making a Buzzing Noise? (Vibration & Motor Fix) | `why is my attic fan making a buzzing noise` | Troubleshooting | Very Low | P2 |
| 6 | How to Safely Bypass an Attic Fan Thermostat for Diagnostic Testing | `how to bypass attic fan thermostat` | How-to | Low | P1 |
| 7 | Do Attic Fan Thermostats Go Bad? (5 Warning Signs of Failure) | `do attic fan thermostats go bad` | Informational | Low | P2 |
| 8 | How to Lubricate Attic Fan Motor Bearings (Sleeve vs Ball Bearings) | `how to lubricate attic fan motor` | How-to | Low | P2 |
| 9 | Attic Fan Hums But Won't Start Without a Push: Bad Capacitor Symptoms | `attic fan hums but won't start` | Troubleshooting | Low | P1 |
| 10 | How to Tell If an Attic Fan Motor Is Burned Out (Resistance Check) | `how to test attic fan motor` | Troubleshooting | Low | P1 |
| 11 | How to Wire a Master Flow Attic Fan Thermostat (Diagram Included) | `how to wire a master flow attic fan thermostat` | How-to | Low | P2 |
| 12 | Step-by-Step Broan 355BK Attic Fan Thermostat Replacement Guide | `how to replace attic fan thermostat` | How-to | Low | P2 |
| 13 | How to Replace an Attic Fan Motor on a Belly Band Mount | `how to replace attic fan motor` | How-to | Low | P2 |
| 14 | How to Wire an Attic Fan with Thermostat and Humidistat Controls | `how to wire attic fan with thermostat and humidistat` | How-to | Low | P2 |
| 15 | What Temperature Should an Attic Fan Thermostat Be Set At in Summer? | `what temperature should attic fan be set at in summer` | How-to | Low-Medium | P1 |
| 16 | Attic Fan Vibration Damper Installation: Stopping Ceiling Rattles | `attic fan vibration` | How-to | Low-Medium | P2 |
| 17 | How to Calculate Attic Fan CFM: Sizing Formula for Any Roof Pitch | `how to size an attic fan` | How-to | Low-Medium | P2 |
| 18 | Gable Mount Attic Fan Shutter Sticking: Cleaning & Lube Guide | `gable mount attic fan shutter` | Troubleshooting | Low-Medium | P2 |
| 19 | Best Replacement Thermostat Switch for Attic Exhaust Fans | `best attic fan thermostat replacement` | Commercial | Low-Medium | P2 |
| 20 | Attic Fan Replacement Motor Sizing: 1/5 HP vs 1/4 HP Specifications | `attic fan replacement motor` | Commercial | Low-Medium | P3 |
| 21 | How Much Electricity Does an Attic Fan Use? (Monthly Cost Calculator) | `how much electricity does an attic fan use` | Cost / Planning | Medium | P3 |
| 22 | Ridge Vent vs Attic Fan: Why Running Both Can Harm Your Roof | `ridge vent vs attic fan` | Comparison | Medium | P2 |
| 23 | Solar Attic Fan vs Electric Attic Fan: 10-Year ROI & Performance | `solar attic fan vs electric attic fan` | Comparison | Medium | P2 |
| 24 | Gable Mount vs Roof Mount Attic Ventilators: Which Is Better? | `gable mount vs roof mount attic fan` | Comparison | Medium | P2 |
| 25 | Whole House Fan vs Attic Fan: Key Differences in Cooling Physics | `whole house fan vs attic fan` | Comparison | Medium | P2 |
| 26 | Does an Attic Fan Depressurize Your House? Air Leaks & Backdrafting | `does an attic fan reduce electric bill` | Building Science | Medium | P3 |
| 27 | How Many Soffit Vents Do I Need for a Powered Attic Fan? | `how many cfm attic fan do i need` | How-to | Medium | P3 |
| 28 | Quietest Roof-Mounted Attic Fans for Noise-Sensitive Bedrooms | `quietest attic fan` | Commercial | Medium | P3 |
| 29 | Attic Fan Installation Cost: DIY Breakdown vs Hiring an Electrician | `attic fan installation cost` | Cost / Planning | Medium | P3 |
| 30 | Is an Attic Fan Worth It? (Building Science Energy Audit Analysis) | `is an attic fan worth it` | Informational | Medium | P3 |

---

### 3.2 `c17-pellet-stove`: Pellet Stove Error Codes & Mechanical Troubleshooting (Rank #2 Shortlist)
- **Definition & Target Reader**: Covers residential biomass pellet heating stoves (Harman, Quadra-Fire, Breckwell, Castle), focusing on auger jams, vacuum switch error codes, igniter burnout, and exhaust blower cleaning. Target readers are rural and suburban homeowners relying on pellet heat during winter cold snaps facing stove shutdowns.
- **Competition & SERP Summary**: Beatability score is **8.30 / 10**. Forums (`Hearth.com`, `Reddit r/fixit`, `DoItYourself.com`) and small hearth blogs (`CookUpExperts.com`, `FireplaceUniverse.com`) routinely rank in positions 1–4 for specific error codes (e.g., "3 blinks on Harman status light").
- **Demand & RPM**: 25,000–40,000 searches/month cluster demand during winter. **Tier B ($15–$25 RPM)** with high-ticket affiliate potential on replacement auger motors ($80–$160), control boards ($150–$300), and seasonal pellet orders.
- **Top Risk**: Strong winter seasonality (October–February represents ~65% of annual searches).

---

### 3.3 `c02-sump-pump-backup`: Sump Pump Battery Backup & Alarm Troubleshooting (Rank #3 Shortlist)
- **Definition & Target Reader**: Covers emergency basement flood prevention, battery backup float switches, lead-acid vs AGM deep cycle batteries, dual check valve plumbing, and alarm silencing. Searchers are panicked or proactive homeowners dealing with beeping basement alarms or impending heavy rain storms.
- **Competition & SERP Summary**: Beatability score is **8.10 / 10**. Independent plumbing sites (`WaterCommander.com`) and `Reddit r/HomeImprovement` rank in positions 2–4. Manufacturer PDF manuals hold position 1 on branded error codes.
- **Demand & RPM**: 30,000–45,000 searches/month cluster demand. **Tier B ($18–$30 RPM)** driven by high-cost water damage remediation and professional plumbing leads ($500–$2,500 job values).
- **Top Risk**: Brand authority of Basement Watchdog and Zoeller on branded query strings.

---

## 4. Recommended Pick

### Decisive Recommendation: `c11-attic-fan` (Attic Fan Thermostat & Troubleshooting)
- **Why It Wins**: `c11-attic-fan` scored the highest overall weighted total (**837 / 1000**) and demonstrated the cleanest competitive landscape of all 20 tested candidates. Small independent niche blogs (`RapidRepair.blog`, `FixUpFirst.com`, `HouseFixMaster.com`) hold position #1 on core seed terms, while forum discussions (`Reddit`, `DIY StackExchange`) occupy top-3 positions across primary troubleshooting queries.
- **Economic Viability**: Operates in the high-value Home Improvement / HVAC vertical (**Tier B RPM: $15–$25**), with strong affiliate monetization on replacement thermostats ($20–$40), replacement motors ($70–$140), and solar ventilation units ($300–$650).
- **Zero-Authority Path**: A DR-0 site can achieve immediate organic visibility on symptom-based queries (e.g. *attic fan humming but not spinning*, *why does my attic fan keep shutting off*) where searchers need a diagnostic troubleshooting tree rather than a commercial product pitch.
- **Primary Risk to Monitor**: The summer seasonality curve. To insulate against winter traffic declines, the site must publish balanced content addressing winter attic moisture, cold-climate air-sealing, and whole-house fan shoulder seasons.

---

## 5. Next Steps & Implementation Roadmap

### 5.1 Domain Naming Direction
- **Approach**: Brandable, multi-word authority domain within home ventilation and roofing physics. Avoid exact-match keyword domains (EMDs) like `buyatticfanthermostat.com`.
- **Naming Ideas**:
  - `AtticAirflow.com` / `AirflowAttic.com`
  - `VentilationFix.com` / `VentLogic.com`
  - `AtticDraft.com` / `RoofAirGuide.com`

### 5.2 Site Architecture & Silos
Organize into 4 clean URL directories:
- `/thermostats/` — Wiring diagrams, calibration, multimeter tests, dual-control units.
- `/troubleshooting/` — Humming, vibration, shutoffs, seized bearings, burning smells.
- `/sizing-science/` — CFM calculations, soffit intake formulas, ridge vent short-circuiting.
- `/systems/` — Solar vs electric, roof vs gable, whole-house fan crossovers.

### 5.3 Publishing Cadence (First 90 Days)
- **Capacity**: 15–20 articles/month.
- **Days 1–30**: Publish Articles 1–10 (Tier 1 Ultra-Low Competition Troubleshooting). Index immediately via Google Search Console.
- **Days 31–60**: Publish Articles 11–20 (Tier 2 Hardware & Wiring Guides). Begin interlinking troubleshooting guides to specific wiring/hardware pages.
- **Days 61–90**: Publish Articles 21–30 (Tier 3 Building Science & Comparison Pillars). Establish internal link hubs connecting comparison articles down into specific diagnostic tutorials.

### 5.4 Prerequisites for Google AdSense Approval
Before submitting the site to Google AdSense (around Month 2–3 when 20+ articles are live and organic impressions begin):
1. **Essential Legal & Trust Pages**:
   - `About Us`: Detailed editorial mission, testing methodology, safety disclosure.
   - `Contact`: Real contact form and direct email address.
   - `Privacy Policy`: Standard CCPA/GDPR/AdSense compliant privacy policy.
   - `Terms of Service & Electrical Safety Disclaimer`: Explicit notice that 120V electrical work carries shock risks and users should hire licensed professionals if uncertain.
2. **Design Standards**: Clean responsive mobile layout, zero broken links, zero placeholder text, fast load times (Core Web Vitals green).

### 5.5 Scheduled Review
- **Next Re-Run Date**: March 2027 (prior to the beginning of the summer HVAC surge) to audit keyword rankings, review search console query impressions, and map out the next 30 expansion articles.
