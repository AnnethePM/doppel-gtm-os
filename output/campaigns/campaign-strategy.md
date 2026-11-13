# Campaign Strategy: Doppel

**Status:** v1, 2026-11-13. GTME cohort exercise built from public data only. Nothing is sent in Doppel's name (`context/docs/gtm-system.md`, Step 8).

**Built from:** `CLAUDE.md`, `context/icp/` (icp, personas, signal-matrix), `context/positioning/`, `context/messaging/messaging.md`, `context/docs/case-studies.md`, `context/docs/research/*`, `context/docs/gtm-system.md`, `knowledge-base/playbooks/workflow-anatomy.md` (Mother Intent Catalog). `meetings/` and `knowledge-base/learnings/` are empty.

**Labels:** INFERRED = my judgment, not stated in the research. `{{placeholder}}` = a number with no source yet (CLAUDE.md rule 2).

---

## Summary

**Target audience (given):** Tier 1 and 2 segments from `signal-matrix.md` (A. investment and holding firms, B. crypto and web3, C. consumer platforms with an app, D. tech and SaaS), North America and Australia, Brand and Executive Protection as the lead product.
**Core value proposition:** find impersonation of the brand and its executives across every channel and take it down at the source, fast, without manual reporting (`messaging.md`).
**Key differentiators:** one platform across DRP, HRM and Email Security; takedowns across "registrars, social platforms, ad networks, and telcos"; head-to-head POC wins against incumbents (`positioning.md`, `company.md`).

## How to read the ranking

The ideas are ranked by **signal strength + data ease**, each scored 1 to 5 (total out of 10). Ties are broken by volume, then by time to build.

- **Signal strength:** how strongly the signal shows a need right now. Where `signal-matrix.md` already scored the signal, I reuse its "clear buying reason" score.
- **Data ease:** can the signal be pulled programmatically and reliably. Reuses the matrix's "data you can get" score where it exists.
- **Expected volume per month:** **all INFERRED estimates.** No source gives signal volumes (`signal-matrix.md`: "Volume per signal: Not found"). Bands: Low = under 50 new accounts a month, Medium = 50 to 200, High = over 200. Replace each with `{{verified_monthly_volume}}` from a 50-account Clay test before building.
- **Difficulty:** Easy = native Clay actions only; Medium = one HTTP or scraper step; Hard = several custom sources or heavy AI research.
- **Tier:** build order, per the skill (Tier 1 = build first).
- Every score is INFERRED.

---

## Ranked overview

| Rank | Campaign | Mother intent | Segment | Persona | Signal | Data | Score | Volume / mo (est.) | Difficulty | Tier |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Recent public scam warning | Website content mentions | A, B, C, D (B first) | Champion, Econ. buyer, Influencer | 4 | 4 | **8** | Medium | Medium | 1 |
| 2 | New lookalike domain | Niche-specific play | A, B, C, D | Champion | 4 | 4 | **8** | Medium | Medium | 1 |
| 3 | Someone else is buying ads on your name | Niche-specific play | A, B, C, D | Champion | 4 | 4 | **8** | Medium | Medium | 1 |
| 4 | Law firms warning about impostors **(Creative non-ICP)** | Website content mentions | Law firms (outside rows A to D) | Econ. buyer (CISO) | 4 | 4 | **8** | Low | Easy | 2 |
| 5 | Hiring a brand protection analyst | Hiring specific roles | A, B, C, D | Champion | 3 | 5 | **8** | Low | Easy | 2 |
| 6 | Regulator named your firm | Regulatory changes | A | Econ. buyer | 5 | 3 | **8** | Low | Medium | 2 |
| 7 | Fake app in the stores | Niche-specific play | B, C | Champion | 5 | 3 | **8** | Low | Medium | 2 |
| 8 | Customers like Advance, Coinbase and REA **(Lookalike)** | Lookalike of customers | A, B, C | Champion | 3 | 4 | **7** | High | Easy | 1 |
| 9 | New CISO, first 90 days **(New Hire)** | New leadership (past 90/180 days) | A, B, C, D | Econ. buyer | 2 | 5 | **7** | Medium | Easy | 2 |
| 10 | New CISO at a KnowBe4 shop | New leadership + Companies using specific software | A, B, C, D | Econ. buyer | 3 | 4 | **7** | Medium | Medium | 2 |
| 11 | Live impersonation count (Golden ICP) | Niche-specific play | B (then A) | Champion | 5 | 2 | **7** | Low | Hard | 2 |
| 12 | Pro sports teams and ticket scams **(Creative non-ICP)** | Niche-specific play | Sports teams and leagues | Econ. buyer, Influencer | 2 | 5 | **7** | Low | Easy | 2 |
| 13 | New Trust & Safety or fraud lead **(New Hire)** | New hires in target dept | B, C | Influencer | 2 | 5 | **7** | Low | Easy | 3 |
| 14 | Security resellers not yet in the directory **(Creative non-ICP)** | Niche-specific play (channel) | VARs and MSSPs | Partner lead | 2 | 5 | **7** | Low | Easy | 3 |
| 15 | Creative Ideas: where you'd be impersonated | Niche-specific play | A, B | Champion | 1 | 5 | **6** | High | Medium | 2 |
| 16 | Executives in the spotlight | Niche-specific play | A | Econ. buyer | 3 | 3 | **6** | Medium | Medium | 2 |
| 17 | Incumbent named in job posts | Competitor customers | A, B, C, D | Champion | 3 | 3 | **6** | Low | Medium | 2 |
| 18 | Australia SPF designated sectors | Regulatory changes | C (AU) | Econ. buyer | 3 | 3 | **6** | Low | Medium | 3 |
| 19 | Token or app launch | New product launches | B, C | Champion | 2 | 3 | **5** | Low | Medium | 3 |
| 20 | A peer was breached by social engineering | Niche-specific play (news) | A, B, D | Econ. buyer | 3 | 2 | **5** | Low | Hard | 3 |

Required types: Creative (non-ICP) = 4, 12, 14. New Hire = 9, 13. Lookalike = 8. Creative Ideas = 15. Golden ICP = 11. No-AI campaigns are below the cards.

**Why the Lookalike is Tier 1 despite ranking 8th:** its signal is weaker, but the volume is the highest of any idea, it builds with native Clay actions only, and it carries the strongest proof. It is the safest list to test copy on while the signal workflows are validated.

---

## Customer discovery analysis

Full table: `context/docs/case-studies.md`. Patterns (INFERRED from that file):

- **Industries:** crypto and web3 is the deepest (Coinbase, Dapper Labs, UniSat, Galxe, M0, Aptos, Let's F***ing Joe, Gala Games). Then financial services (Advance, ARK, an unnamed firm), and one each in consumer platforms (REA), productivity software, identity security (Permiso), legal (an unnamed global law firm), entertainment (Sugar23) and real estate.
- **Sizes:** only one story states headcount (500+ employees). Size bands stay a tag, not a filter (`icp.md`).
- **Roles quoted:** security leads (Director of Cybersecurity, Security Lead, Head of Cyber Defence), CISOs, plus legal (Deputy GC, COO and GC), marketing (Brand Marketing Manager, Senior Marketing Manager) and Trust & Safety.
- **Common problems:** manual reporting and slow takedowns (Advance, UniSat, M0, the law firm); finding out only from user reports (Galxe, Let's F***ing Joe); impersonation ads (the productivity platform, Let's F***ing Joe, the unnamed financial services firm).

**Targeting challenge:**
- **Law firms.** The case studies read on 2026-11-13 add a law firm story: takedowns in seven days against a 30 to 45 day industry average, by the CISO's own figures. Law firms are Tier 3 ("logos only") in `icp.md`. This is the first proof for them, so ideas 4 and 20 test them before `icp.md` is changed.
- **Malvertising.** Paid ads are a stronger theme than the matrix assumed: three stories now cover them. That supports idea 3 as Tier 1.
- **HRM.** Permiso is the first HRM (simulation) case study. It gives idea 10 a proof point.

**Best customers for the Lookalike (idea 8):** Advance and ARK (segment A), Coinbase and Galxe (segment B), REA Group (segment C).

---

## Campaign cards

Proof points cite `context/docs/case-studies.md` unless noted. **Customer names cannot appear in copy until they are listed in `context/messaging/facts.md`, which does not exist yet.** Until then, each name in an angle is a `{{social_proof}}` placeholder in copy.

### 1. Recent public scam warning · Tier 1
- **Mother intent:** Website content mentions (`signal-matrix.md` S2, workflow W2)
- **Segment and persona:** A, B, C, D, starting with B (spec already approved: `output/campaigns/recent-scam-warning-crypto/workflow-spec.md`). Champion first; economic buyer first if a new CISO is detected.
- **Signal and source:** the company published or updated a scam or impersonation warning on its own domain in the last 30 days. SerpApi Google Search via Clay HTTP (`site:{domain} (impersonation OR scam OR "fake support")`), with page date and type checked by Clay HTTP fetch.
- **Angle:** "You've already told customers about it, so the question is how fast the fakes come down." Galxe relied on user reports and was "constantly reacting after the damage had already occurred"; with Doppel it has a 6-minute triage time and 405 threats taken down. Mitigate risk, save time.
- **AI strategy:** summarize the warning page in one line (which channel, which scam), and quote the company's own wording back.
- **Volume:** Medium (est.) · **Difficulty:** Medium (one SerpApi step; the date filter still needs a [verify]).
- **Overview:** Opener names the warning page and its date. Body: one proof point matched to the segment (Galxe for B, Advance for A). CTA: a question about who files the takedowns today. Already specced, so it is the fastest to launch.

### 2. New lookalike domain · Tier 1
- **Mother intent:** Niche-specific play (S1, W1)
- **Segment and persona:** A, B, C, D · Champion
- **Signal and source:** a new TLS certificate on a permutation of the brand's domain, issued in the last 14 days. Apify dnstwist for permutations, then crt.sh JSON via Clay HTTP. Exclude domains the brand owns.
- **Angle:** the domain exists today; how long until it is gone? Advance's domain takedowns went from 30 days to under a week; Coinbase took down "1000+ fraudulent domains". Mitigate risk.
- **AI strategy:** none needed. The domain and its issue date are the personalization.
- **Volume:** Medium (est.) · **Difficulty:** Medium (crt.sh is an informal endpoint and may change).
- **Overview:** "{{lookalike_domain}} got a certificate on {{cert_date}}." Describe, don't diagnose; the guardrail in `signal-matrix.md` warns against alarming openers. CTA: offer the list of other variants found.

### 3. Someone else is buying ads on your name · Tier 1
- **Mother intent:** Niche-specific play (S3, W3)
- **Segment and persona:** A, B, C, D · Champion
- **Signal and source:** Google ads using the brand's name from an advertiser that is not the brand, shown in the last 30 days. SerpApi `google_ads_transparency_center`, region US or AU, via Clay HTTP. Filter out resellers and affiliates.
- **Angle:** malicious ads. The unnamed productivity platform had a "persistent 'malvertising' attack"; Doppel "took down almost all of the active malicious ads within the first day", and the platform reports "2,000+" takedowns. Let's F***ing Joe was blacklisted by ISPs after a surge in fraudulent Google Ads. Mitigate risk, save money.
- **AI strategy:** classify the ad text (fake support, fake download, fake investment) to pick the route.
- **Volume:** Medium (est.) · **Difficulty:** Medium
- **Overview:** Opener describes the advertiser and the claim in the ad. Route by ad type. CTA: "Is anyone on your side filing these with Google today?" The Meta version is killed for the US and AU (`signal-matrix.md`).

### 4. Law firms warning about impostors · Tier 2 · Creative (non-ICP)
- **Mother intent:** Website content mentions
- **Segment and persona:** large law firms in the US (outside rows A to D; Tier 3 in `icp.md`) · CISO, then General Counsel or the Managing Partner's office
- **Signal and source:** the firm's site has a "fraud alert" or "beware of impostors" page. Base list: the AmLaw 200 (public list), with Clay HTTP `site:` search for the warning page. Exclude the roughly 9 law firm logos already on Doppel's wall (`customers.md`).
- **Angle:** a firm's name is the asset that gets copied. The unnamed global law firm's CISO reports takedowns "in seven days" against an industry average of "30 and 45 days" (the CISO's figures), and PII removal that now takes minutes. Mitigate risk, save time for lawyers.
- **AI strategy:** pull the impersonation type from the warning page (fake lawyer emails, fake recovery services).
- **Volume:** Low (est.; one-off list, then monthly refresh) · **Difficulty:** Easy
- **Overview:** a test of whether law firms are a real segment, as `icp.md` asks. Keep it small; if replies come, propose promoting law firms in `icp.md`.

### 5. Hiring a brand protection analyst · Tier 2
- **Mother intent:** Hiring specific roles (S6, W6)
- **Segment and persona:** A, B, C, D · Champion (the hiring manager)
- **Signal and source:** open roles titled "brand protection", "takedown analyst", "digital risk protection" or "trust and safety". Clay Find Jobs at Company.
- **Angle:** the role is being built by hand. REA Group says Doppel "has removed a huge amount of manual work for us"; the law firm's CISO compared multi-channel coverage to "a 12- or 18-person team". Save time, save money.
- **AI strategy:** extract the job post's listed duties (manual reporting, monitoring) and mirror them.
- **Volume:** Low (est.) · **Difficulty:** Easy
- **Overview:** Opener quotes one duty from the post. Position Doppel as what the new hire would run, not a replacement. As a buying signal this is INFERRED (`signal-matrix.md`).

### 6. Regulator named your firm · Tier 2
- **Mother intent:** Regulatory changes (S4, W4)
- **Segment and persona:** A (investment and holding firms) · Economic buyer first
- **Signal and source:** an IOSCO I-SCAN or CIRO alert names the firm as impersonated, in the last 30 days. Clay HTTP scrape, matched to company names. ASIC equivalent [verify].
- **Angle:** executives impersonated in front of investors. ARK's impersonation reports were "basically cut in half"; ARK reports "98%" takedown success. Mitigate risk.
- **AI strategy:** none needed. The alert is the hook.
- **Volume:** Low (est.) · **Difficulty:** Medium (page structure not yet tested)
- **Overview:** the clearest buying reason of any signal (5/5 in the matrix), but low volume. Reference the alert factually; never imply blame.

### 7. Fake app in the stores · Tier 2
- **Mother intent:** Niche-specific play (S5, W5)
- **Segment and persona:** B, C · Champion
- **Signal and source:** an app using the brand's name or icon from a different developer, released in the last 90 days. iTunes Search API and SerpApi Google Play via Clay HTTP [verify both].
- **Angle:** REA's two-week POC found more fake apps than its incumbent had in the previous year. Mitigate risk.
- **AI strategy:** compare developer name and icon text to confirm it is not the brand's own app.
- **Volume:** Low (est.) · **Difficulty:** Medium
- **Overview:** Opener names the app and developer. CTA: offer to share the full list.

### 8. Customers like Advance, Coinbase and REA · Tier 1 · Lookalike
- **Mother intent:** Lookalike of customers
- **Segment and persona:** A, B, C · Champion
- **Signal and source:** companies matching the best case studies on industry, region and brand exposure (retail-facing asset managers like Advance and ARK; exchanges and web3 platforms like Coinbase and Galxe; property and marketplace apps like REA). Clay Find Companies plus a Clay lookalike enrichment, then the brand exposure gate (`gtm-system.md` Step 4).
- **Angle:** what happened at the closest peer. Advance: "75%+" faster takedowns and "25x" more takedowns. Coinbase: "over 800 social media accounts and 1000+ fraudulent domains". REA: more fake apps found in two weeks than in the previous year. Mitigate risk, save time.
- **AI strategy:** pick the closest case study per account and write one line on why it's similar (same channel, same customer base).
- **Volume:** High (est.) · **Difficulty:** Easy
- **Overview:** Opener: "{{peer}} had the same problem: {{peer_problem}}." One result, one CTA offering a two-week POC (`positioning.md`). Blocked on `facts.md` for the names.

### 9. New CISO, first 90 days · Tier 2 · New Hire
- **Mother intent:** New leadership (past 90/180 days) (S7, W7)
- **Segment and persona:** A, B, C, D · Economic buyer
- **Signal and source:** a CISO, Head of Security or Head of Cyber Defence who started in the last 90 days. Clay Find People with title and start date.
- **Angle:** a quick win the board will see. "The effort involved in creating something that looks real has gone to basically zero." (REA's CISO). The Fortune 500 CISO's team cut exposed executive PII by 93%. Mitigate risk.
- **AI strategy:** previous company plus a check of whether the new company has a public scam warning (stacks with idea 1).
- **Volume:** Medium (est.) · **Difficulty:** Easy
- **Overview:** Acknowledge the new role. Offer an impersonation baseline for the first 90 days. As a buying signal this is INFERRED (`signals.md`); a stacked public warning raises priority.

### 10. New CISO at a KnowBe4 shop · Tier 2
- **Mother intent:** New leadership + Companies using specific software (S7 + S8)
- **Segment and persona:** A, B, C, D · Economic buyer
- **Signal and source:** a new CISO (idea 9) at a company that uses KnowBe4. Bloomberry (job-post based; it lists 40,069 KnowBe4 companies, `signal-matrix.md`) or TheirStack. Never run S8 alone.
- **Angle:** HRM upsell. Doppel's own line: "KnowBe4 was built for yesterday's attacks." Permiso: "Doppel fundamentally changed how we think about human risk." Offer "a plus-one alongside your current platform" (`signals.md`). Mitigate risk.
- **AI strategy:** none beyond the stack.
- **Volume:** Medium (est.) · **Difficulty:** Medium
- **Overview:** Lead with simulation across email, Teams and voice, not training. Don't knock KnowBe4; Doppel's page says "KnowBe4 isn't going out of business".

### 11. Live impersonation count · Tier 2 · Golden ICP
- **Mother intent:** Niche-specific play
- **Segment and persona:** B first, then A · Champion
- **Signal and source:** what a rep would find in 10 minutes: count accounts on X and Telegram using the brand's name or logo that are not the official handle. Claygent research, proven on 2 rows first (`build-clay` rules).
- **Angle:** "I found {{count}} accounts using your name on X." UniSat had 216 impersonations on X out of 289 social detections; Aptos's security lead said other vendors were "great for domains, but not for Telegram, not for X." Mitigate risk.
- **AI strategy:** Claygent search plus a confidence check; only send if count ≥ {{min_count}}.
- **Volume:** Low (est.) · **Difficulty:** Hard (X search access and cost; heavy AI)
- **Overview:** The highest-intent message in this list, but the most expensive. Run `calculate-costs` before scaling.

### 12. Pro sports teams and ticket scams · Tier 2 · Creative (non-ICP)
- **Mother intent:** Niche-specific play
- **Segment and persona:** NFL, NBA, MLB, NHL and MLS teams (outside rows A to D) · CISO or IT security lead, then marketing or ticketing
- **Signal and source:** base list from public league sites; enrich with a ticket-scam warning page on the team's site (Clay HTTP `site:` search). Exclude the 49ers and Knicks, which are Doppel partners (`company.md`).
- **Angle:** fake tickets and fake merch sell on your name. Doppel is the "Official Social Engineering Defense Partner" of the 49ers (`company.md`). Entertainment proof: Sugar23 took down over 600 impersonations. Mitigate risk.
- **AI strategy:** note the next big home date or event from the team's schedule.
- **Volume:** Low (est.; under 200 teams in total) · **Difficulty:** Easy
- **Overview:** Partner credibility, not a case study. Whether partnership terms allow naming the 49ers in copy is unknown: placeholder until `facts.md` exists.

### 13. New Trust & Safety or fraud lead · Tier 3 · New Hire
- **Mother intent:** New hires in target dept
- **Segment and persona:** B, C · Influencer
- **Signal and source:** Head of Trust & Safety, fraud lead or community lead who started in the last 90 days. Clay Find People.
- **Angle:** "put brand protection and anti-phishing security on autopilot" (Dapper Labs). Save time.
- **AI strategy:** previous company and its scale.
- **Volume:** Low (est.) · **Difficulty:** Easy
- **Overview:** Secondary to idea 9. The influencer rarely holds budget (`personas.md` open question), so ask for the right security contact.

### 14. Security resellers not yet in the directory · Tier 3 · Creative (non-ICP)
- **Mother intent:** Niche-specific play (channel). Not in the catalog; flagged as a new intent.
- **Segment and persona:** US and Canadian value-added resellers and MSSPs selling security, not in Doppel's partner directory · Partner or alliance lead
- **Signal and source:** reseller lists (vendor partner pages, for example other security vendors' directories), minus the 82 partners on https://doppel.com/partners/directory (`company.md`).
- **Angle:** Doppel already works through 75 value-added resellers including Optiv, GuidePoint and CDW (`company.md`). Make money: a product their clients are asking about.
- **AI strategy:** pull which DRP or HRM vendors the reseller already lists, to show the gap.
- **Volume:** Low (est.) · **Difficulty:** Easy
- **Overview:** Not a sales campaign. Value depends on Doppel's partner program terms, which are not in the research.

### 15. Creative Ideas: where you'd be impersonated · Tier 2
- **Mother intent:** Niche-specific play
- **Segment and persona:** A, B · Champion
- **Signal and source:** no trigger. Base list from the ICP; Clay HTTP fetch of the homepage, support page and executive page.
- **Angle:** "I had an idea for {{company}}." Three specific places an attacker would copy them, taken from their site (a support handle, a named executive, an app or a token). Mitigate risk.
- **AI strategy:** a Use AI prompt that reads the site and writes three bullets (build with `prompt-builder`, prove on 2 rows).
- **Volume:** High (est.) · **Difficulty:** Medium
- **Overview:** Broadest list, so personalization does the work. Proof line: Doppel covers "web, social, messaging, ads, app stores, email, and dark web signals" (`company.md`).

### 16. Executives in the spotlight · Tier 2
- **Mother intent:** Niche-specific play
- **Segment and persona:** A · Economic buyer
- **Signal and source:** a CEO or CIO who appears in financial media or has a large public following. Clay Claygent for press and podcast mentions, LinkedIn follower count.
- **Angle:** "As a global brand with highly visible executives, protecting our leadership team is paramount." (Fortune 500 CISO). ARK's case is about impersonation of "high-profile figures". Mitigate risk.
- **AI strategy:** cite the executive's latest public appearance.
- **Volume:** Medium (est.) · **Difficulty:** Medium
- **Overview:** Exec Protection as the lead product. "Highly visible executives" as a signal is INFERRED (`signals.md`).

### 17. Incumbent named in job posts · Tier 2
- **Mother intent:** Competitor customers
- **Segment and persona:** A, B, C, D · Champion
- **Signal and source:** a job post that names ZeroFox, BrandShield, Bolster, Netcraft, Allure or Red Points as a tool used. Clay Find Jobs at Company with keyword match.
- **Angle:** a two-week POC side by side. "In just a two-week proof-of-concept, Doppel took down about half of what our incumbent solution did in an entire year." (Zane Lackey). Mitigate risk, save money.
- **AI strategy:** extract the vendor name and context.
- **Volume:** Low (est.) · **Difficulty:** Medium
- **Overview:** Which incumbents Doppel replaces most is an open question (`icp.md`). Never criticize the rival by name in copy (`competitors.md` response table).

### 18. Australia SPF designated sectors · Tier 3
- **Mother intent:** Regulatory changes (S9)
- **Segment and persona:** C in Australia (digital platforms), plus telcos · Economic buyer
- **Signal and source:** the sector designation effective 2026-05-23 (`market.md`, secondary source). Static list, Clay industry filter.
- **Angle:** the SPF asks firms to "detect, disrupt" scams; REA Group is an Australian reference. Mitigate risk.
- **AI strategy:** none.
- **Volume:** Low (est.) · **Difficulty:** Medium
- **Overview:** Use only as a secondary enrichment until the dates are confirmed from a government source.

### 19. Token or app launch · Tier 3
- **Mother intent:** New product launches
- **Segment and persona:** B, C · Champion
- **Signal and source:** a new token, NFT drop or app launch in the last 60 days. Press releases and app store release dates.
- **Angle:** launches attract copies. Dapper Labs: "1,076 threats detected", including "over 100,000 NFTs". Mitigate risk.
- **AI strategy:** name the launch.
- **Volume:** Low (est.) · **Difficulty:** Medium
- **Overview:** As a buying signal this is INFERRED (`signals.md`). Test only after Tier 1.

### 20. A peer was breached by social engineering · Tier 3
- **Mother intent:** Niche-specific play (news)
- **Segment and persona:** A, B, D · Economic buyer
- **Signal and source:** news of a helpdesk vishing or deepfake breach at a peer in the same sector. News search via Claygent.
- **Angle:** Mandiant ranks vishing the second most common initial access vector (`market.md`, secondary source: verify before copy). Mitigate risk.
- **AI strategy:** match the peer to the prospect.
- **Volume:** Low (est.) · **Difficulty:** Hard
- **Overview:** Risky tone; never sound like ambulance chasing. INFERRED signal.

---

## No-AI campaigns

**"Who files your takedowns?"** (on the idea 8 Lookalike list)
- Why it works without AI: the list is tight (segment plus brand exposure), and the question names the pain every case study shares.
- Core message: one line question, one result (Advance's domain takedowns went from 30 days to under a week), one CTA asking for a two-week POC.

**"Two weeks against your incumbent"** (on the idea 17 list)
- Why it works without AI: the list already uses a rival, so the offer speaks for itself.
- Core message: the Zane Lackey POC quote, then "Worth a side-by-side?"

## Front-end offers

1. **Free impersonation snapshot.** A list of lookalike domains, ad copies and fake accounts using the brand, from the same checks as ideas 2, 3 and 11. The prospect sees the problem before any pitch. Delivered as a dry-run artifact only in this exercise.
2. **Two-week head-to-head POC.** Doppel's own sales motion (REA, Zane Lackey quote). It lets the prospect compare results against the incumbent.
3. **Deepfake simulation demo for the exec team.** For idea 10: Doppel's simulation reports a "9 min" average conversation with a deepfake (`company.md`, sample size not found). Use the figure only with its caveat.

---

## What to do next

1. **Validate volumes:** run a 50-account Clay test on ideas 1, 2, 3 and 8 and replace every Volume band with `{{verified_monthly_volume}}`.
2. **Create `context/messaging/facts.md`** from `knowledge-base/playbooks/templates/facts-template.md` so customer names can be used in copy.
3. **Finish idea 1:** its structure is already approved; run `/campaign-copy` on `output/campaigns/recent-scam-warning-crypto/workflow-spec.md`.
4. **Spec the next workflow:** run `/build-workflow-spec` on idea 2 or idea 8.
