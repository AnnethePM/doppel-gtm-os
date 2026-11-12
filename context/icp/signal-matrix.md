# Doppel Signal Matrix

**Status: work in progress (v1, 2026-11-12).** For a GTME cohort exercise, built from public sources only. Validate before building in Clay.

Inputs: `context/icp/icp.md`, `context/icp/personas.md` and `context/docs/research/*`. Method: `knowledge-base/playbooks/signal-matrix-framework.md` and `workflow-anatomy.md`.

Choices confirmed with the user on 2026-11-12:
- **Rows:** ICP Tier 1 and Tier 2 segments
- **Columns:** the three personas
- **Geography:** North America and Australia
- **Lead product:** Brand and Executive Protection in every cell. HRM (simulation and training) and Email Security are upsells.

Labels:
- **INFERRED:** not supported by the research files, or a judgment of mine.
- **[verify]:** a data source I know of but did not check this session.
- **Scores:** my assessment against the evidence cited (all INFERRED).

---

## Matrix 1: Segments x Personas

### Row definitions

| Segment | Target definition (filterable) | Lead / upsell | Priority | Why |
|---|---|---|---|---|
| **A. Investment and holding firms** | US, Canadian and Australian asset managers, wealth managers, investment advisers, PE firms and family holding companies, whose brand or executives face retail investors or the public | Brand and Exec Protection / HRM simulation | **High** | Three case studies (Advance, ARK, the unnamed financial services firm). Regulators publish impersonation alerts that name firms, which gives a niche signal. Rich US and Canadian data |
| **B. Crypto and web3** | US, Canadian and Australian exchanges, wallets, brokers with crypto, token foundations, and NFT and gaming studios with a public community on X, Telegram or Discord | Brand Protection / Exec Protection | **High** | The most proof: Coinbase, Dapper Labs and UniSat, plus five named quotes. Fake support accounts are common and publicly reported |
| **C. Consumer platforms with an app** | US and Australian consumer brands whose app is the main product (marketplaces, property portals, travel, delivery) | Brand Protection (fake apps) / Email Security | **Medium** | One case study (REA Group). Fake apps are detectable, but there are fewer documented cases |
| **D. Tech and SaaS** | US SaaS and platform companies with a branded login page that phishing kits copy | Brand Protection (phishing domains) / Phishing Triage, Email Security | **Medium-Low** | Named quotes only (Notion, Commerce, AngelList, Permiso). No case study read |

Source for the proof column: `customers.md`, `icp.md`.

### Company examples

Each one is a real company with a public impersonation warning or report found on 2026-11-12. That warning is itself the signal. None is on Doppel's customer lists in `customers.md`.

| Segment | Examples (source) |
|---|---|
| A | Topaz Capital, Canada ([newswire, Apr 2026](https://www.newswire.ca/news-releases/topaz-capital-ltd-warns-of-impersonation-scheme-862211854.html)); Wealthsimple, Canada ([advisor.ca, Jun 2026](https://www.advisor.ca/industry-news/regulation/ciro-wealthsimple-warn-about-social-media-scams/)); IG Wealth Management, Canada ([CIRO alert](https://www.ciro.ca/node/30286), likely 2025); Fisher Investments, US ([scams page](https://www.fisherinvestments.com/en-us/scams)); CI Financial, Canada ([fraud page](https://www.cifinancial.com/ci-is/ca/en/fraud-awareness.html)); Savant Wealth, US ([article](https://savantwealth.com/savant-views-news/article/investors-beware-investment-group-imposter-scams-on-the-rise/)); Invesco ([report](https://www.international-adviser.com/fraudsters-target-invesco-clients/), date unclear). More: requires Clay research. Filters: SEC or Canadian registered advisers, retail-facing, with a scams or fraud page on their site |
| B | Kraken, US ([support article, updated 2026-10-13](https://support.kraken.com/gb/articles/impersonation-scams)); Robinhood, US ([scam guide](https://robinhood.com/ca/en/support/articles/how-to-identify-and-report-scams/), [Jul 2026 campaign](https://blog.rankiteo.com/rob1783672001-robinhood-cyber-attack-july-2026/)); Binance Australia ([NASC joint release](https://www.nasc.gov.au/node/132)). More: requires Clay research. Filters: crypto or fintech, NA or AU, with a "fake support" or "impersonation" help article |
| C | Qantas, Australia ([ACCC warning, Feb 2026](https://australianaviation.com.au/2026/02/accc-warns-of-surge-in-qantas-impersonation-scams/)); DoorDash, US ([report, Jul 2026](https://malwaretips.com/blogs/?p=413094)). More: requires Clay research. Filters: consumer app as the main product, NA or AU, more than 1M app downloads [verify the filter source] |
| D | LastPass, US ([alert, Jul 2026](https://blog.lastpass.com/posts/july-2026-phishing-campaign-compliance)); Okta, US ([SecurityWeek](https://www.securityweek.com/organizations-warned-of-rise-in-okta-support-phishing-attacks/amp/)); Cloudbeds, US ([advisory, Feb 2026](https://myfrontdesk.cloudbeds.com/hc/en-us/articles/46491424007579-Security-Advisory-Phishing-Campaign-Targeting-Hospitality-Providers)). More: requires Clay research. Filters: SaaS, has published a phishing or security advisory |

Worth noting (INFERRED): Australian banks (CommBank, Westpac, Heritage Bank, Qudos Bank) publish frequent impersonation alerts and fall under the SPF, but banks have no Doppel case study. They are a candidate segment for v2, not a row here. Sources: [CommBank](https://www.commbank.com.au/articles/newsroom/2026/03/warning-as-impersonation-scams-become-more-sophisticated.html), [Heritage](https://www.heritage.com.au/about/news/2024-2025-scam-alerts/2026-08-06-fake-website-scam), `market.md`.

### The grid: angle per cell

Each angle describes the buyer's situation using proof from the research. It doesn't diagnose a gap.

| Segment | Champion (security lead who owns takedowns) | Economic buyer (CISO or CTO) | Influencer (legal, brand, Trust & Safety, fraud) |
|---|---|---|---|
| **A. Investment and holding** | **Speed of takedowns.** Advance's domain takedowns went from 30 days to under a week, with 25x more takedowns. Source: `customers.md` | **Executives impersonated in front of investors.** ARK cut impersonation reports roughly in half year over year. The Fortune 500 CISO quote: "protecting our leadership team is paramount". Source: `customers.md` | **Brand and marketing:** ARK went from "days to weeks" to removal "within minutes" (Staudt). **Legal:** Advance moved off "manual legal cease-and-desist processes". Source: `customers.md` |
| **B. Crypto and web3** | **Volume across X and Telegram.** UniSat had 216 impersonations on X. Coinbase took down "over 800 social media accounts and 1000+ fraudulent domains". Source: `customers.md` | **Fake support drains customers.** INFERRED link: the Kraken and Robinhood warnings show the pattern. Proof: Coinbase's Trust & Safety numbers. Source: `customers.md`, Matrix 1 examples | **Community and legal:** "put brand protection and anti-phishing security on autopilot" (Dapper Labs, Deputy GC). "we have not identified any viable alternatives to Doppel" (UniSat). Source: `customers.md` |
| **C. Consumer platforms with an app** | **Fake apps found faster.** REA's two-week POC found more fake apps than the previous year. Source: `customers.md` | **The brand is the asset.** "Our brand is our biggest asset" and "The effort involved in creating something that looks real has gone to basically zero." (Bown, REA). Source: `customers.md` | **Fraud team:** REA automates takedowns "based on the tickets we're receiving from the fraud team". Source: `customers.md` |
| **D. Tech and SaaS** | **Less time spent on threats.** "I used to be stressed about all of the looming threats to our platform" (Pyykonen, Notion). Source: `customers.md` | **Takedowns as a core layer.** "Doppel is a core layer of our security program" (Larkin, Commerce, a Security Analyst, not a CISO). CISO-level proof in this segment: INFERRED, none found. Source: `company.md` | **Detection and response:** "Security teams are expected to make high-confidence decisions in minutes" (Petracca, AngelList). Source: `customers.md` |

### Prioritization

| Segment | Signal density | Product fit | Reachability (data) | Rank |
|---|---|---|---|---|
| B. Crypto and web3 | High (public fake-support warnings, community channels) | High (3 case studies, 5 quotes) | High (US and AU, digital-native) | 1 |
| A. Investment and holding | High (regulator alerts name firms) | High (3 case studies) | High (US and Canadian registries) | 2 |
| C. Consumer platforms with an app | Medium (app stores) | Medium (1 case study) | High | 3 |
| D. Tech and SaaS | Medium (phishing advisories) | Low-Medium (quotes only) | High | 4 |

All ratings are INFERRED judgments based on the evidence counts in `customers.md`.

---

## Matrix 2: Signals

### Signal details (Iron Law check)

| # | Type | Signal (observable event) | Mother intent (catalog) | Data source | Detection tool / Clay action | Key filters | Status |
|---|---|---|---|---|---|---|---|
| S1 | Universal | **New lookalike domain with a TLS certificate**, issued in the last 14 days | Niche-specific play | Certificate Transparency logs ([crt.sh](https://crt.sh), JSON output). Permutations from dnstwist | Apify dnstwist actor ([apify.com/ntriqpro/dnstwist-osint](https://apify.com/ntriqpro/dnstwist-osint)) to generate variants, then Clay HTTP to crt.sh `?q=<variant>&output=json` | Cert `not_before` within the last 14 days. Exclude domains the company owns | VERIFIED (crt.sh is an informal endpoint and may change) |
| S2 | Universal | **The company published or updated a scam or impersonation warning** in the last 90 days | Website content mentions | Company website and help center, through Google search | SerpApi Google Search via Clay HTTP: `site:{domain} (impersonation OR scam OR "fake support")`, past 3 months [verify the SerpApi date filter] | Last 90 days. Pages titled scam, fraud, impersonation or security advisory | VERIFIED (examples: Kraken, updated 2026-10-13; LastPass, Jul 2026) |
| S3 | Universal | **Third parties running Google ads that use the brand's name** | Niche-specific play | Google Ads Transparency Center | SerpApi `google_ads_transparency_center` engine, with `text={brand}` and region US or AU ([docs](https://serpapi.com/google-ads-transparency-center-api)), via Clay HTTP | Advertiser is not the brand's own advertiser ID. Shown in the last 30 days | VERIFIED. Needs a filter for legitimate resellers and affiliates |
| S3-Meta | Universal | Same signal, on Facebook and Instagram | Niche-specific play | Meta Ad Library API | Graph API `ads_archive` | n/a | **KILLED for US and AU.** The API returns only political and issue ads outside the EU and UK ([Graph API reference](https://developers.facebook.com/docs/graph-api/reference/ads_archive/)) |
| S4 | Niche (A) | **A regulator publishes an alert that names the firm** as impersonated | Regulatory changes | IOSCO I-SCAN ([iosco.org/i-scan](https://www.iosco.org/i-scan/)); CIRO investor alerts ([ciro.ca](https://www.ciro.ca/node/30286)) | Clay HTTP scrape of the alert lists, matched to company names | Alert in the last 30 days, with "impersonat" in the text | VERIFIED (PARTIAL). Page structure not yet tested. ASIC (Australia) equivalent [verify] |
| S5 | Niche (B, C) | **Fake app found in the app stores** (similar name or icon, different developer) | Niche-specific play | Apple App Store; Google Play | iTunes Search API via Clay HTTP [verify]; SerpApi Google Play engine [verify] | Developer name is not the brand's. Released in the last 90 days | VERIFIED (PARTIAL). Both endpoints need checking |
| S6 | Universal | **Hiring for brand protection or takedown roles** | Hiring specific roles | Job posts | Clay "Find Jobs at Company" | Titles: "brand protection", "brand and exposure management", "takedown analyst", "digital risk protection", "trust and safety" | VERIFIED. Such posts exist ([example](https://www.mediabistro.com/jobs/2198812840-brand-and-exposure-management-analyst)). As a buying signal: INFERRED |
| S7 | Universal | **New CISO or Head of Security** in the last 90 days | New leadership | LinkedIn job changes | Clay "Find People", filtered on title and start date | Titles: CISO, Head of Security, Head of Cyber Defence. Started within 90 days | VERIFIED. As a buying signal: INFERRED (`signals.md` hypothesis) |
| S8 | Universal, compound only | **Uses KnowBe4** (for the HRM upsell) | Companies using specific software | Bloomberry (job-post based, [40,069 companies](https://bloomberry.com/data/knowbe4/)); TheirStack; BuiltWith | Bloomberry or TheirStack via Clay HTTP or CSV import | Pair with S7 or S2. Never run alone | VERIFIED (COMPOUND) |
| S9 | Niche (C, AU) | **Account is in an Australian SPF designated sector** (digital platforms, banks, telcos) | Regulatory changes | Treasury designation instrument, effective 2026-05-23 (`market.md`, secondary source) | Static list. Clay industry filter | AU, digital platforms | VERIFIED (PARTIAL). Secondary source only, and it's a static attribute (no timing), so use only as a secondary enrichment |
| S10 | Universal | Funding round in the last 90 days | Companies fundraising | Crunchbase | Clay "Find Organization" | B and D only (VC-backed) | **KILLED as a mother intent.** The research has no evidence that funding triggers a brand protection purchase. Keep it as a secondary enrichment at most |
| K1 | n/a | Unhappy with the current vendor | n/a | n/a | n/a | n/a | **KILLED.** Not observable. It moves to a discovery question (`icp.md`, section 3b) |
| K2 | n/a | KnowBe4 or DRP renewal date | n/a | n/a | n/a | n/a | **KILLED.** Not public (`signals.md`) |

Volume per signal: **Not found.** No source gives counts. To estimate it, run each signal on 50 accounts in Clay and record the hit rate.

### Four-test scores (1 to 5, all INFERRED)

The tests come from `workflow-anatomy.md`: clear buying reason, enough volume, data you can get, a natural story.

| # | Signal | Clear buying reason | Enough volume | Data you can get | Natural story | Total /20 | Evidence for the buying reason |
|---|---|---|---|---|---|---|---|
| S1 | New lookalike domain | 4 | 4 | 4 | 5 | **17** | Advance (30-day domain takedowns), Coinbase (1000+ domains): `customers.md` |
| S2 | Public scam warning in the last 90 days | 4 | 4 | 4 | 5 | **17** | The company has publicly admitted the problem. Example warnings: Kraken, LastPass, Topaz |
| S3 | Third-party Google ads on the brand | 4 | 3 | 4 | 4 | **15** | Unnamed financial services firm (ads using its branding): `customers.md`. Kraken says fake numbers appear "in search ads" |
| S4 | Regulator names the firm | 5 | 2 | 3 | 5 | **15** | Regulator alerts about Topaz and IG Wealth (Matrix 1 examples) |
| S5 | Fake app in the stores | 5 | 2 | 3 | 5 | **15** | REA (more fake apps found in two weeks than in the previous year): `customers.md` |
| S8 | Uses KnowBe4 (compound) | 3 | 5 | 4 | 3 | **15** | Doppel's KnowBe4 switching page: `signals.md` |
| S6 | Brand protection hiring | 3 | 2 | 5 | 4 | **14** | INFERRED: they are building the function |
| S7 | New CISO | 2 | 4 | 5 | 3 | **14** | INFERRED only |
| S9 | AU SPF sector | 3 | 2 | 3 | 3 | **11** | `market.md`. Effect on purchases INFERRED |
| S10 | Funding | 1 | 3 | 5 | 2 | **11** | None |

### Signal x segment (Play and Product)

| Type | Signal | A. Investment and holding | B. Crypto and web3 | C. Consumer apps | D. Tech and SaaS |
|---|---|---|---|---|---|
| Universal | S1 Lookalike domain | Fake domains spoofing the firm or fund. **Brand Protection** | Fake exchange or wallet login domains. **Brand Protection** | Fake checkout or login domains. **Brand Protection** | Phishing copies of the login page. **Brand Protection** |
| Universal | S2 Public scam warning | "We will never contact you on WhatsApp" pages. **Brand and Exec Protection** | Fake support articles (Kraken pattern). **Brand Protection** | Customer scam alerts (Qantas pattern). **Brand Protection** | Phishing advisories (LastPass pattern). **Brand Protection** |
| Universal | S3 Brand-name ads | Fake investment ads. **Brand Protection** | Fake support numbers in search ads. **Brand Protection** | Fake promotions. **Brand Protection** | Fake download or login ads. **Brand Protection** |
| Universal | S6 Brand protection hiring | Keyword swap: "brand protection". **Brand Protection** | Keywords: "trust and safety", "takedown". **Brand Protection** | Keyword: "fraud". **Brand Protection** | Keyword: "detection and response". **Phishing Triage** |
| Universal | S7 New CISO | **Exec Protection** | **Brand Protection** | **Brand Protection** | **Email Security** (INFERRED) |
| Universal (compound) | S8 Uses KnowBe4 | Stack with S7. **HRM simulation** | Same | Same | Same |
| Niche | S4 Regulator alert | IOSCO I-SCAN, CIRO. **Brand and Exec Protection** | Possible: I-SCAN also lists crypto firms [verify] | n/a | n/a |
| Niche | S5 Fake app | n/a | Fake wallet apps. **Brand Protection** | Fake apps (REA pattern). **Brand Protection** | n/a |
| Niche | S9 AU SPF sector | n/a | n/a | AU digital platforms. Secondary enrichment only | n/a |

**What this shows:** 6 of the 9 signals still in play (S1, S2, S3, S6, S7, S8) are universal. Each is one Clay build, reused across all four segments by changing keywords and the angle. Only S4, S5 and S9 need their own builds.

---

## Build first

| Rank | Signal | Why first |
|---|---|---|
| 1 | **S1 New lookalike domain** | Top score (17). Universal across all four segments. The data source is free (crt.sh). It is Doppel's most-proven pain: Advance's takedowns went from 30 days to under a week, and Coinbase took down 1000+ domains. |
| 2 | **S2 Public scam warning in the last 90 days** | Top score (17). Universal. The company has already said publicly that it's being impersonated, so the opener writes itself. Verified examples exist in every segment. |
| 3 | **S3 Third-party Google ads on the brand** | Score 15 and universal. Backed by a case study (ads using a firm's branding). The SerpApi engine is documented. The Meta version is killed for the US and AU, so this is the only ads signal left. |
| 4 | **S4 Regulator names the firm** (Segment A) | The clearest buying reason of any signal (5/5): a regulator has publicly confirmed the firm is being impersonated. Low volume, but it lands on Tier 1 segment A. |
| 5 | **S5 Fake app in the stores** (Segments B, C) | Backed by REA's strongest result. Build it after the two app store endpoints are checked. |

S6 to S8 come after these, as secondary enrichments that route the narrative, not as mother intents. S8 (KnowBe4) is the HRM upsell route.

---

## Matrix 3: Workflow tracker

| W # | Status | Workflow name | Mother intent | Segments | Persona | Channel | Clay URL | Total leads |
|---|---|---|---|---|---|---|---|---|
| W1 | Planned | New lookalike domains | Niche-specific play (S1) | A, B, C, D | Champion | | | |
| W2 | Planned | Recent public scam warning | Website content mentions (S2) | A, B, C, D | Champion, Influencer | | | |
| W3 | Planned | Third-party brand ads (Google) | Niche-specific play (S3) | A, B, C, D | Champion | | | |
| W4 | Planned | Regulator impersonation alert | Regulatory changes (S4) | A | Economic buyer | | | |
| W5 | Planned | Fake apps in the stores | Niche-specific play (S5) | B, C | Champion | | | |
| W6 | Planned | Brand protection hiring | Hiring specific roles (S6) | A, B, C, D | Champion | | | |
| W7 | Planned | New CISO, plus KnowBe4 for HRM | New leadership (S7 + S8) | A, B, C, D | Economic buyer | | | |

The other tracker columns (campaigns, iterations, copy URL, bounce rate) get filled in when the workflows launch.

## Open questions
- Signal volumes. No source has them. Run a 50-account test per signal
- Whether the S2 and S1 openers come across as helpful or alarming. Copy needs to follow the guardrail of describing the situation, not diagnosing a gap
- Whether to add banks (especially Australian banks under the SPF) as a v2 segment
- Whether CISO-level proof exists for segment D
