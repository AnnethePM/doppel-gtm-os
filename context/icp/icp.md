# Doppel ICP

Built only from `context/docs/research/` (checked 2026-11-12). Each line names its research file. INFERRED means the conclusion is drawn from the research, not stated in it. Gaps are listed under Open questions.

Files: `company.md`, `customers.md`, `competitors.md`, `market.md`, `signals.md`, `voice.md` (all in `context/docs/research/`).

## Summary

Organizations whose brand, app, community or executives are already being impersonated. They are usually in North America, in financial services or crypto, and are often unhappy with an incumbent brand protection vendor. Sources: `customers.md`, `signals.md`.

## 1. Firmographic

Segments are tiered by how much proof the research holds, not by what Doppel's site lists. Only Tier 1 should drive list building.

### Segments by proof

| Tier | Segment | Proof in the research | Source |
|---|---|---|---|
| **1. Case study plus named quote** | Investment and holding firms (asset managers, PE, family holding companies) | Advance (25x takedowns, Director of Cybersecurity), ARK Invest (98% takedown success, CTO and Brand Marketing), unnamed financial services firm (500+ employees) | `customers.md` |
| **1. Case study plus named quote** | Crypto and web3 (exchanges, wallets, token foundations, NFT and gaming) | Coinbase (800+ social accounts and 1000+ domains taken down), Dapper Labs, UniSat; quotes from Aptos, Gala Games, CoinList, Backpack, Hashflow | `customers.md` |
| **1. Case study plus named quote** | Consumer platforms with an app | REA Group (more fake apps found in a two-week POC than in the previous year; CISO and Head of Cyber Defence) | `customers.md` |
| **2. Named quote, no case study read** | Tech and software (SaaS, platforms) | Notion (Head of Platform Security), Commerce (Security Analyst), AngelList (Detection and Response), Permiso (Co-CEO). Permiso's case study is listed but was not read | `customers.md` |
| **3. Logos only** | Law firms | About 9 logos (Orrick, Cravath, WilmerHale, Covington and others); Orrick is named in the Series C release. No case study and no quote | `customers.md`, `company.md` |
| **3. Logos only** | Healthcare, retail and consumer, real estate developers, energy and utilities, public sector, sports | Logos only; no case study and no quote | `customers.md` |
| **Not proven** | Manufacturing, education, oil and gas | Listed on Doppel's site; no logo, case study or quote found | `company.md` |

### Qualifiers

| Attribute | Use it as a filter? | Evidence |
|---|---|---|
| **Brand exposure** (the main qualifier) | Yes. The account has at least one of these: a consumer app; a public community (X, Telegram, Discord); a token or NFTs; executives who face retail investors or the public; publicly reported impersonation | REA (fake apps), UniSat (216 impersonations on X), Dapper Labs (fake NFTs), ARK (exec impersonation on LinkedIn, Instagram, WhatsApp and Telegram), Fortune 500 CISO ("highly visible executives"): `customers.md` |
| Geography | Yes. North America first (4 of the 5 case studies), Australia second (REA Group). UK, EMEA and Japan have offices but no case study | `customers.md`, `company.md` |
| Company size | **Tested against 7 named customers (2026-11-13), mostly supported.** Primary: 1,000+ employees: Coinbase (4,951), Ameren (8,913), REA Group (3,418), Advance (~15,600, estimate). Secondary: 201–1,000: BitGo (~565), the unnamed financial services firm (500+); Poshmark (~750 to ~1,100) sits on the line. **Exception: under 200 is not a fit filter when brand exposure is high.** ARK Invest has fewer than 100 employees (~48 in SEC Form ADV data) and is one of the strongest case studies. So size stays a tag, never a filter, and brand exposure (above) decides fit. The bands started as user-provided; the counts are [3P-search] figures from filings and trackers. Also supporting 1,000+: "5X increase in Fortune 500 customers", "dozens of the Fortune 500" | `customers.md` (Employee counts of named customers; user-provided size profile), `company.md` |
| Regulatory pressure | Tiebreaker only. Applies to UK and EU banks that refund victims, and to Australian SPF sectors. That it drives purchases is INFERRED | `market.md` |

## 2. Technographic

| Signal | Why it matters | Evidence |
|---|---|---|
| Uses KnowBe4 | Doppel runs a switching page tied to renewal dates | `signals.md`, `voice.md` |
| Uses an incumbent DRP or brand protection vendor | Most case studies replace an incumbent after a short POC | `customers.md`, `signals.md`. Possible incumbents: ZeroFox, BrandShield, Bolster, Netcraft, Allure, Red Points (`competitors.md`). Which ones Doppel actually displaces: open question |
| Legacy attack surface management or generic threat intel tools | Advance's starting point | `customers.md` |
| Manual takedowns, or cease-and-desist through legal | Advance, ARK ("Whack-A-Mole"), UniSat | `customers.md` |
| Wants API-driven automation | REA wanted an API; Advance onboarded through API integrations | `customers.md` |
| Zoom or Microsoft Teams in use | Doppel sells meeting deepfake simulations on these platforms | `company.md`, `signals.md` |
| Splunk, LinkedIn, WhatsApp, Facebook, Google Ads | Listed integrations | `company.md` |

## 3. Intent signals

Every signal below happened in a real case study. The "where to look" column is INFERRED (it is a method, not a research finding). No signal is ranked, because the research has no conversion data.

### 3a. Visible from outside (use for list building)

| Signal | Where to look (INFERRED) | Proof it matters | Source |
|---|---|---|---|
| Fake social accounts impersonating the brand or its executives | Search X, LinkedIn, Instagram, Telegram and WhatsApp for the brand and executive names | UniSat: 216 impersonations on X. ARK: scams on LinkedIn, Instagram, WhatsApp and Telegram. Coinbase: "over 800 social media accounts" taken down | `customers.md` |
| Fake apps in app stores | Search the App Store and Google Play for the brand name | REA: a two-week POC found more fake apps than the previous year | `customers.md` |
| Others buying ads with the brand's name | Meta Ad Library and Google Ads Transparency Center | Unnamed financial services firm: bad actors were buying Facebook and Google ads with its branding | `customers.md` |
| Lookalike or malicious domains | Domain search for the brand name plus common variants | Advance: domain takedowns "would drag on for 30 days or fail entirely". Coinbase: "1000+ fraudulent domains" | `customers.md` |
| The company publicly warns customers about scams | Its website, help center and social posts | INFERRED: a public warning means the problem is already visible to customers. No case study mentions one | `signals.md` |
| Uses KnowBe4 | Technographic data or job posts that mention it | Doppel runs a KnowBe4 switching page: "Planning your move from KnowBe4? Start here" | `signals.md`, `voice.md` |
| Regulated sector and region with a set date | UK and EU banks and payment firms; Australian banks, telcos and digital platforms | UK APP consultation planned for December 2026; Australian SPF designation effective 2026-05-23 | `market.md` |

### 3b. Confirm on the first call (not visible from outside)

| Signal | Question to ask | Proof it matters | Source |
|---|---|---|---|
| Slow or failed takedowns with the current vendor | "How long does a domain takedown take today?" | Advance: 30 days, then under a week after switching. LA real estate firm: six to 20 weeks before | `customers.md` |
| The incumbent misses threats | "Who usually spots impersonations first, you or your vendor?" | LA real estate firm often found impersonations before its vendor did. REA's incumbent was "becoming less effective at active takedowns" | `customers.md` |
| Takedowns are manual | "Who files takedowns today, and how?" | ARK: a "Whack-A-Mole" process. Advance: "manual legal cease-and-desist processes" | `customers.md` |
| A KnowBe4 or DRP renewal is coming up | "When does your current contract renew?" | Doppel's KnowBe4 webinar is about "how to use your renewal date to plan your rollout" | `signals.md` |

### Kept out of the table (untested)
A new CISO, security hiring, a funding round, an app or token launch, entry into a new market, M&A, a rebrand, or a big sponsorship. All are INFERRED in `signals.md`, and no case study shows one of them leading to a purchase. Don't use them for scoring until tested.

## 4. Persona (detail in `personas.md`)

| Role | Who | Evidence |
|---|---|---|
| Champion | Security operator who owns takedowns or detection (Director of Cybersecurity, Head of Cyber Defence, Head of Platform Security) | Smedberg (Advance), Dalton (REA), Pyykonen (Notion): `customers.md` |
| Economic buyer | CISO (sometimes the CTO). User-provided, not yet in the research: Head of Information Security, VP of Security, Security Operations leaders | Bown (REA), anonymous Fortune 500 CISO, LA real estate firm's CISO, Keller (ARK CTO): `customers.md` |
| Influencer | Legal, brand and marketing, corporate affairs, Trust & Safety, fraud | Krause (Deputy GC), Sils (COO and GC), Staudt (Brand Marketing), Farmer (Trust & Safety), REA fraud team: `customers.md` |

## 5. Engagement readiness

| Ready now | Not ready yet |
|---|---|
| Will run a short head-to-head POC against the incumbent (REA's two weeks; the a16z quote about a two-week POC) | No incumbent and no active impersonation: no pain to compare against (INFERRED) |
| A renewal date for KnowBe4 or a DRP vendor is close | Just renewed with an incumbent (INFERRED from renewal-date messaging) |
| Can share a baseline asset list (domains, brands, executives), since onboarding is "minutes" and "a single email" | |
| Visible, ongoing impersonation | |

Sources: `customers.md`, `signals.md`.

## Not a fit

| Profile | Why | Evidence |
|---|---|---|
| Buyers who need the lowest price or small contracts | A rival says Doppel is premium, with "higher minimums". Pricing is custom, through sales or a partner | `competitors.md` (BrandShield, a rival's claim), `company.md` |
| Teams with no time to give input on enforcement | A rival says "Enforcement scope is narrow and requires input from the customer" | `competitors.md` (BrandShield, a rival's claim) |
| Buyers whose main need is marketplace counterfeits or piracy | Red Points and BrandShield lead with counterfeits. Doppel's proof is impersonation and phishing | `competitors.md`, `customers.md`. INFERRED |
| Buyers who need real-time account-takeover (ATO) protection on their own site | That is Memcyco's category. Doppel makes no ATO claim | `competitors.md`. INFERRED |
| Organizations with no public brand, app or visible executives to impersonate | No case study or logo fits this profile | `customers.md`. INFERRED |

## Open questions (not in the research)
- Deal size, minimums and pricing units: is mid-market actually served profitably?
- Which incumbents Doppel replaces most often, and its win and loss reasons
- Sales cycle length and buying committee size
- ICP for Email Security and HRM buyers (no case studies for those products)
- Whether the hypothesis triggers (new CISO, funding, launches) actually convert
- Whether Tier 3 segments (law firms, healthcare, retail) are real buying segments or just logos. Next step: find a law firm or healthcare case study or quote
- Size bands: tested on 2026-11-13 against 7 named customers (see the Company size row and `customers.md`). Still open: headcounts from the filings themselves (all counts so far come from search summaries), and whether small high-exposure firms like ARK are common or an exception
- Which regulations drive email security and training demand (the regulation-to-demand chain in `market.md` names none)
- Whether UK, EMEA and Japan have paying customers beyond offices and partners
