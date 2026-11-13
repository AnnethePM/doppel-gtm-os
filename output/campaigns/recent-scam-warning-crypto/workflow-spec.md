# Workflow Spec: Recent Scam Warning (Crypto and Web3)

**Status:** STRUCTURE-APPROVED 2026-11-12 · copy pending

The user approved the signals table and the 5-cell angle matrix on 2026-11-12. Sections 6 and 7 were written after the angle matrix approval, following the user's gate plan (stop only after those two).

This is a GTME cohort exercise built from public data. It is a dry run: nothing is sent in Doppel's name (`context/docs/gtm-system.md`, Step 8).

**Sources:**
- `context/icp/icp.md`, `context/icp/personas.md`, `context/icp/signal-matrix.md` (S2, workflow W2)
- `context/docs/gtm-system.md`
- `context/docs/research/*`

`context/messaging/facts.md` does not exist yet. Every fact below names its research file, and anything unverified is a `{{placeholder}}`.

---

## 1. Mother Intent (Trigger) [ENGINE]

**A crypto or web3 company has published or updated a scam or impersonation warning on its own website or help center in the last 30 days.**

- Catalog: Website content mentions (`knowledge-base/playbooks/workflow-anatomy.md`).
- The window was changed from the matrix's 90 days to 30 days at the user's request on 2026-11-12. `signal-matrix.md` S2 is updated to match.

## 2. Inclusion / Exclusion [ICP]

### Include

| Box | Rule | Source |
|---|---|---|
| Geography | HQ in the US, Canada or Australia | `icp.md`, user decision 2026-11-12 |
| Segment | B. Crypto and web3: exchanges, wallets, brokers with crypto trading, token foundations, NFT and gaming studios | `signal-matrix.md` Matrix 1, row B |
| Size | Tag only, never a filter: `size_primary` (1,000+ employees), `size_secondary` (201-1,000), `size_other` | `icp.md` (user-provided hypothesis), `gtm-system.md` Step 4 gate 6 |
| Trigger | A page on the company's own domain, dated in the last 30 days, classified as `impersonation_warning` (signals 1 and 2) | `signal-matrix.md` S2 |
| Recipient 1: Champion | Head of Security, Director of Cybersecurity, Information Security Lead, Head of Platform Security, Detection and Response lead | `personas.md` (champion), plus Head of Security at the user's request |
| Recipient 2: Economic buyer | CISO, Head of Information Security, VP of Security, Security Operations leaders (title contains "Security Operations" plus Head, Director or VP) | User-provided titles, 2026-11-12. CISO is in `personas.md`; the rest are not in the research yet |
| Recipient 3: Influencer | Trust & Safety lead, Community Manager, Deputy General Counsel or General Counsel | `personas.md` (influencer) |
| Order | Champion first. If `new_security_leader` = true, the economic buyer goes first | `gtm-system.md` Step 6 |
| Fallback | No champion: the economic buyer becomes recipient 1. No economic buyer either: the Trust & Safety lead | `gtm-system.md` Step 6 |
| Overlap | A title that matches two personas goes to the more senior one. "Head of Security" is champion; "Head of Information Security" is economic buyer | `gtm-system.md` Step 6, user decision |
| Cap | 3 contacts per account, one per persona | `gtm-system.md` Step 6 |

### Exclude

| Who | Why |
|---|---|
| Existing Doppel customers and logos in segment B: Coinbase, BitGo, Galaxy, FalconX, Solana, Aptos, Galxe, M0, Dapper Labs, Gala Games, CoinList, Backpack, Hashflow, UniSat, Magic Eden, LookRare, Mysten Labs / Sui Foundation | Already customers (`customers.md`) |
| Competitors: BrandShield, ZeroFox, Bolster, Netcraft, Allure Security, Red Points, Memcyco | They sell the same thing (`competitors.md`) |
| Pages that aren't warnings (`page_type` other than `impersonation_warning`) | Not an admission of impersonation |
| HQ outside the US, Canada or Australia | Geography gate (`gtm-system.md` Step 4) |
| Contacted in the last 90 days, do-not-contact, or open in the CRM | Suppression (`gtm-system.md` Steps 6 and 10) |
| Role or shared addresses (security@, support@) | Not personal contacts (`gtm-system.md` Step 7) |

## 3. Sources [ENGINE]

| What | Source | Tool |
|---|---|---|
| Monitored universe | Clay Find Companies: crypto, blockchain and fintech industries, US, Canada and Australia. Refreshed monthly | Clay, with n8n for the refresh |
| Trigger: warning pages | `site:{domain} (impersonation OR scam OR "fake support" OR phishing)`, past month | SerpApi Google Search via Clay HTTP [verify the date-filter parameter] |
| Page text and date | The URL the trigger returns | Clay HTTP fetch, with crawl4ai as the fallback for JavaScript pages |
| Page classification | The page text | Clay Use AI column with fixed outputs, proven on 2 rows before scaling |
| Company facts | Headcount, HQ country, LinkedIn | Clay Enrich Company |
| Hiring | Job posts | Clay Find Jobs at Company |
| New security leader | People with a start date | Clay Find People |
| Contacts | Persona titles above | Clay Find People, with Claygent people search as the fallback, into the shared People table (`build-clay`) |
| Emails | Clay native waterfall (Prospeo, LeadMagic, Icypeas, Findymail) plus a second verifier | Clay (`gtm-system.md` Step 7) |

KnowBe4 use (S8) is not read in this workflow. It stays a CRM tag for a later training upsell (`gtm-system.md` Step 5).

## 4. Signals table [ENGINE] (APPROVED 2026-11-12)

| # | Signal | Role | How it's read | Output |
|---|---|---|---|---|
| 1 | Warning page found in the last 30 days | **trigger** | Boolean: SerpApi returns at least 1 result on the company's own domain, dated 30 days old or newer | `has_recent_warning` = true / false |
| 2 | The page is an impersonation warning | **trigger** (gate inside the trigger) | Use AI classification with fixed outputs: `impersonation_warning` / `general_security_tips` / `news_or_blog` / `other`. Only `impersonation_warning` passes | `page_type` |
| 3 | Impersonation channels named on the page | **router** | Keyword matching on the page text in 3 categories, then a count of the categories matched. **Social and messaging:** X, Twitter, Telegram, Discord, WhatsApp, Instagram, TikTok, Facebook, LinkedIn, "DM". **Fake support:** phone number, call, "support agent", "customer support", live chat, email from us. **Fake sites and apps:** website, domain, URL, link, app, extension, "search ad", "Google ad" | `channel_cluster` |
| 4 | Hiring Trust & Safety, brand protection or takedown roles | **router** | Boolean: at least 1 open job in the last 60 days with a title containing "trust and safety", "trust & safety", "brand protection", "takedown", "fraud investigations" or "digital risk" | `hiring_tns` = true / false |
| 5 | New security leader | **context-clause** (never routes) | Boolean: a Find People result with title CISO, Head of Information Security, VP of Security, or Head/Director/VP of Security Operations, and a start date 90 days old or newer | `new_security_leader` = true / false |

**Groups for signal 3:**

| `channel_cluster` | Rule |
|---|---|
| `social_messaging` | Only the social and messaging category matched |
| `fake_support` | Only the fake support category matched |
| `web_assets` | Only the fake sites and apps category matched |
| `multi_channel` | 2 or 3 categories matched. Also store which ones: `multi_includes_social` = true / false |
| `unspecified` | No category matched |

## 5. Routing matrix with angles [ENGINE] (APPROVED 2026-11-12)

**The axes:** `channel_cluster` (5 values) x `hiring_tns` (2 values) = 10 combinations. These fold into **5 cells**, keeping only the cells with verifiable customer evidence.

| Cell | Deterministic read | What it tells us (situation) | The angle it earns | Verifiable evidence |
|---|---|---|---|---|
| **A** | (`social_messaging`, or `multi_channel` with `multi_includes_social` = true) + `hiring_tns` = true | They are being impersonated through fake accounts and DMs, told customers this month, and are adding Trust & Safety or takedown headcount right now | The new role inherits a queue of fake accounts to report platform by platform. Doppel makes that role the one who approves takedowns, not the one who files them | **Coinbase:** "leading to the takedown of over 800 social media accounts and 1000+ fraudulent domains." (Brett Farmer, Trust & Safety Operations), [doppel.com/customer-love](https://www.doppel.com/customer-love) |
| **B** | (`social_messaging`, or `multi_channel` with `multi_includes_social` = true) + `hiring_tns` = false | Same fake-account problem, handled by the existing team with no takedown headcount being added | Fake accounts removed at the volume they appear, without adding a role or reporting platform by platform | **UniSat:** 249 impersonations taken down after manual reporting with "weeks-long rounds of communication". 216 of 289 social detections were on X. [UniSat story](https://www.doppel.com/blog/no-viable-alternative-doppel-social-media-brand-protection-unisat-says) |
| **C** | (`web_assets`, or `multi_channel` with `multi_includes_social` = false) + `hiring_tns` = true | Lookalike sites, links, apps or ads are being used against them, and they are hiring into the function | The new role works from verified lookalike domains with takedowns already filed, not from a manual search | **Advance:** takedowns went from about 10 a year to "over 150 in their first year and 250 in their second". Domain takedowns fell "from an average of 30 days down to under a week". [doppel.com/customers/advance](https://www.doppel.com/customers/advance) |
| **D** | (`web_assets`, or `multi_channel` with `multi_includes_social` = false) + `hiring_tns` = false | Same lookalike-asset problem, handled by the current team | Lookalike domains come down in days, not after weeks with registrars | **Advance:** "Simple domain takedowns would drag on for 30 days or fail entirely", then "under a week". **Coinbase:** "1000+ fraudulent domains". [Advance](https://www.doppel.com/customers/advance), [customer-love](https://www.doppel.com/customer-love) |
| **E** | `unspecified` (hiring or not), or `fake_support` with no other category | They warn about impersonation, but either name no channel or name only fake support, which has no case study | Find where the impersonation actually is, across channels, and remove it, without building a team for it | **Dapper Labs:** 1,076 threats detected and 876 taken down, including 133 fake social accounts and 22 counterfeit domain and media channels. "Doppel enables us to put brand protection and anti-phishing security on autopilot." (Steve Krause, SVP, Deputy GC). [Dapper Labs story](https://www.doppel.com/blog/dapper-labs-leverages-doppel-safeguard-brand-integrity) |

All evidence is published by Doppel and not independently verified (`customers.md`).

**How the other combinations fold in:**

| Read | Goes to | Rule |
|---|---|---|
| `multi_channel` with social | A or B (by hiring) | Social has the most crypto proof, so it takes precedence |
| `multi_channel` without social | C or D (by hiring) | Sites and apps is the matched category with evidence |
| `fake_support` only | E | No fake-support case study. It uses the general angle until `{{fake_support_proof}}` exists |
| `unspecified` + hiring, or + not hiring | E | No channel to reference. The hiring signal is not used in copy |

**Branch coverage:**
- `{{channels_named}}` exists in A to D only. E never references a channel.
- `{{tns_role_title}}` exists in A and C only. B, D and E never mention hiring.

**What the persona changes (copy emphasis, not cells):**
- Champion: operational (queue, speed, volume).
- Economic buyer: the customers the warning protects. That link is INFERRED.
- Influencer: less manual reporting and legal work (Advance: "manual legal cease-and-desist processes").

## 6. Variables contract [ENGINE]

| Variable | Source field | Exists in branches |
|---|---|---|
| `{{first_name}}` | People table: First Name (Find People or Claygent) | A, B, C, D, E |
| `{{company_name}}` | Companies table: Name (Clay Enrich Company) | A, B, C, D, E |
| `{{persona}}` | People table: persona (formula on title, overlap rule in section 2). Used for copy emphasis only, never printed | A, B, C, D, E |
| `{{route_cell}}` | Companies table: routing formula output (A to E). Picks the template, never printed | A, B, C, D, E |
| `{{warning_page_url}}` | SerpApi: `organic_results[0].link` (Clay HTTP column) | A, B, C, D, E |
| `{{warning_page_title}}` | SerpApi: `organic_results[0].title` | A, B, C, D, E |
| `{{warning_page_date}}` | Page date: the SerpApi `date` field, or the page's own "last updated" text | A, B, C, D, E |
| `{{channels_named}}` | Signal 3 keyword output, written as plain words (for example "X and Telegram", "fake websites and apps") | A, B, C, D only |
| `{{tns_role_title}}` | Clay Find Jobs at Company: the title of the newest matching job | A, C only |
| `{{leader_title}}` | Clay Find People: title of the new security leader | Any cell, only when `new_security_leader` = true |
| `{{proof_point}}` | A fixed lookup by `{{route_cell}}`, using the evidence column in section 5. It moves into `context/messaging/facts.md` when `/campaign-copy` creates that file | A, B, C, D, E |
| `{{fake_support_proof}}` | Not available. No case study in the research | None until sourced |
| `{{sender_name}}`, `{{sender_title}}` | Sequencer sender profile | A, B, C, D, E (dry run: placeholder) |

Copy may use only these variables. Variables use the `{{snake_case}}` format and are matched to the sequencer's syntax at export.

## 7. Cadence and channel [ENGINE]

| Item | Setting | Source |
|---|---|---|
| Periodicity | **Always-on.** The trigger check runs weekly on the monitored universe. With a 30-day window, each warning is eligible for up to 4 weekly runs, and dedupe stops repeats | `gtm-system.md` Step 1 (S2 weekly) |
| Dedupe and suppression | One entry per company per warning URL. No re-entry for 90 days unless a new warning URL appears | `gtm-system.md` Steps 1 and 6 |
| Channel | **Both: email and LinkedIn.** Contacts without a verified email go to the LinkedIn-only track | `gtm-system.md` Steps 7 and 8 |
| Tools | EmailBison (email) and HeyReach (LinkedIn), both proposed and pending the user's decision | `gtm-system.md` Step 8 |
| Sequence shape | **3 emails and 2 LinkedIn DMs** (changed 2026-11-13 at the user's request, from 4 emails and 1 DM). Starting cadence (INFERRED, tune after baseline): Email 1 on day 1, empty LinkedIn connection request on day 2, Email 2 on day 4, DM 1 on day 6 if connected, Email 3 on day 9, DM 2 on day 11 if connected | User, 2026-11-13; `gtm-system.md` Step 8 |
| Pre-launch | `campaign-qa` against this spec, then `inbox-placement-test`, then human approval (CLAUDE.md rule 4) | `gtm-system.md` Step 8 |
| Send status | **Dry run.** Export the final sequence and contacts for review. Do not send | `gtm-system.md` Step 8 |
| Feedback | Results by cell (A to E), persona and size tag go to the weekly loop (`gtm-system.md` Step 11). Angle changes are made in this spec and re-approved, never patched in the copy | `gtm-system.md` Step 11, `build-workflow-spec` rules |

---

## Definition of done

- [x] Mother intent: one sentence, signal-led, matched to the catalog
- [x] Inclusion: ICP box, trigger definition and recipient, tagged [ICP]
- [x] Exclusion: who's out and why
- [x] Sources: trigger and every enrichment
- [x] Signals table: every read deterministic, every role declared
- [x] Count groups declared for the count that routes (signal 3)
- [x] Routing matrix with the angle column complete (5 cells, with the fold-in rules)
- [x] Branch coverage: every cell's angle uses only data that exists in that cell
- [x] Variables contract: every `{{variable}}` mapped to its source field
- [x] ENGINE and ICP markers on every section
- [x] Cadence and channel declared

**Next:** `/campaign-copy` reads this file (its GATE 1 checks the status and this checklist) and turns the angles for cells A to E into copy.
