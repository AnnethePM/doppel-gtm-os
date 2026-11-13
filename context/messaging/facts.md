# Doppel: Authorized Copy Facts

The ONLY source of names, numbers and claims for prospect-facing copy (`/campaign-copy` FACTS GATE). Anything not listed here renders as `{{placeholder}}` in copy.

This is a GTME cohort exercise built from public data. Nothing is sent in Doppel's name (`context/docs/gtm-system.md`, Step 8). "Approved by" means approved for this exercise by the repo owner, not by Doppel.

**Last updated:** 2026-11-13 by the repo owner (names rule) and Claude (entries from the research)

---

## Sender identity

| Field | Value |
|---|---|
| Sender name(s) | `{{sender_name}}` (dry run: no real sender) |
| Title | `{{sender_title}}` |
| Signature format | `{{sender_name}}` on one line |
| Sender persona notes | First person singular, peer to peer |

## What we do (locked value prop)

The lead-in is verbatim; the tail may adapt per route.

- **Variant A:** "At Doppel, we find fake accounts, sites and apps using your name and get them taken down at the source."
  Source: coverage of "web, social, messaging, ads, app stores, email, and dark web signals" and takedowns across "registrars, social platforms, ad networks, and telcos" (`context/docs/research/company.md`); "takes them down at the source" is the core message in `messaging.md`. Revised 2026-11-13 after the human test (was "Doppel finds ... using a brand's name and takes them down with the social platform, registrar or ad network directly"). Approved when Email 1 is approved.

Product one-liner (context, not copy): "The Agentic Social Engineering Defense Platform" unifying "Digital Risk Protection, Human Risk Management, and Email Security" (`voice.md`).

## Approved claims and numbers (exact phrasings)

All are published by Doppel and not independently verified. Sources: `context/docs/case-studies.md` and `context/docs/research/customers.md`.

| Claim | Approved phrasing | Source | Approved by / date |
|---|---|---|---|
| Coinbase volume | Coinbase's Trust & Safety team credits Doppel with "the takedown of over 800 social media accounts and 1000+ fraudulent domains" | doppel.com/customer-love | Repo owner, 2026-11-13 (name rule) |
| UniSat | UniSat used to report impersonations by hand to each platform, with "weeks-long rounds of communication". 249 impersonations taken down. 216 of 289 social detections were on X | UniSat story, doppel.com blog | Repo owner, 2026-11-13 |
| Advance volume | Takedowns went from about 10 a year to over 150 in the first year and 250 in the second | doppel.com/customers/advance | Repo owner, 2026-11-13 |
| Advance speed | Domain takedowns went from an average of 30 days to under a week | doppel.com/customers/advance | Repo owner, 2026-11-13 |
| Dapper Labs | 1,076 threats detected and 876 taken down, including 133 fake social accounts and 22 counterfeit domain and media channels | Dapper Labs story, doppel.com blog | Repo owner, 2026-11-13 |
| Dapper Labs quote | "Doppel enables us to put brand protection and anti-phishing security on autopilot." (Steve Krause, SVP, Deputy General Counsel) | Same | Repo owner, 2026-11-13 |
| Galxe | 405 threats taken down; 6 minutes triage time | Galxe story, doppel.com/customers | Repo owner, 2026-11-13 |
| M0 | Takedowns "within 24 to 48 hours" | M0 story, doppel.com/customers | Repo owner, 2026-11-13 |
| Aptos Foundation | "In less than three days, takedowns are completed." (Dudley Alan Grant, Security Lead) | Aptos story, doppel.com/customers | Repo owner, 2026-11-13 |
| Gala Games | "In just 6 months with Doppel we've identified and neutralized 900+ instances of phishing threats." (Jason Brink) | doppel.com/customer-love | Repo owner, 2026-11-13 |
| ARK Invest | "98%" takedown success rate; impersonation reports "basically cut in half" | doppel.com/customers/ark-invest | Repo owner, 2026-11-13 |
| REA Group | In a two-week POC, Doppel found more fake apps than the company had found in the previous year | REA Group story | Repo owner, 2026-11-13 |

**First-person copy phrasings** (same facts, sender's voice; revised 2026-11-13 after the human test):
- Coinbase: "With us, Coinbase's Trust & Safety team has taken down over 800 social media accounts and 1000+ fraudulent domains."
- UniSat: "UniSat went from weeks of back and forth with each platform to 249 impersonations taken down." ("weeks of back and forth" paraphrases "weeks-long rounds of communication".)
- Advance: always introduced as "Advance, a family-owned holding company" (from its case study description), so crypto readers know who it is.
- Dapper Labs: "For Dapper Labs, we've found 1,076 threats and taken down 876, from fake social accounts to counterfeit domains."

**Formatting rules for proof:**
- Write company names as plain names ("Coinbase", never "coinbase.com").
- Keep each number exactly as above. No rounding up, no "up to".
- Counts that come from our own scraped data are prefixed "at least".

## Numbers to keep fuzzy

- Doppel's customer count, funding and ARR growth: never in copy.
- Any median takedown time beyond the customer phrasings above (for example the homepage "<10h", or "under one hour", which is for phishing domains only).

## Authorized social-proof names

**Rule (repo owner, 2026-11-13):** customers listed on Doppel's website may appear in copy. Listed means named on doppel.com: the homepage and /customers logo walls, customer stories, /customer-love and press releases (`customers.md`).

**With an approved result** (usable as proof, with the phrasing above): Coinbase, UniSat, Advance, Dapper Labs, Galxe, M0, Aptos Foundation, Gala Games, ARK Invest, REA Group.

**Logo-drop only** (named on the site, no approved result here; name only, never imply an outcome): every other company on the logo walls in `customers.md`, plus CoinList, Backpack, Hashflow, Notion, AngelList, Permiso, Commerce and Sugar23.

| Name | What it proves | Matches | Caveat |
|---|---|---|---|
| Coinbase | Volume of social and domain takedowns | Crypto exchange | Best industry match for segment B |
| UniSat | Manual reporting replaced; impersonation on X | Crypto wallet | Named in a doppel.com blog story, not on the logo wall |
| Advance | Domain takedown speed and volume | Holding company and PE firm | Channel match (domains), not an industry match for crypto |
| Dapper Labs | Detection and takedown across channels | Web3 gaming | Web3, not an exchange |
| Galxe, M0, Aptos Foundation, Gala Games | Crypto takedown results | Crypto and web3 | Not used by the approved angles yet. Using one needs an angle change in the spec |

## Proof caveats

- Every result is Doppel's own published claim, not independently verified.
- Advance proves domain takedowns for a holding company. Do not present it as a crypto customer.
- UniSat's 216 of 289 figure is detections, not takedowns.
- Andreessen Horowitz is an investor as well as a logo. Do not use it as customer proof.

## Banned

### Banned angles
- "Fastest takedowns" or any speed race with competitors (competitors publish faster medians, `positioning/competitors.md`)
- "Under one hour" without its scope (phishing domains only)
- ROI or cost-saving claims (none confirmed)
- Naming or criticizing a competitor
- Any line implying the prospect's warning page means their team failed (iron law 14 and the insult test)

### Never in copy
- **Let's F***ing Joe**: the name contains profanity and reads badly in a cold email, even masked.
- Anonymous customers (the unnamed financial services firm, law firm, productivity platform, LA real estate firm, Fortune 500 CISO): they cannot be named.
- LooksRare, Magic Eden, Mysten Labs / Sui Foundation: no longer listed on the website.

## Voice notes

- Register: direct, plain, peer to peer. Doppel's own copy uses active verbs (find, take down), not "monitor" (`brand-kit/brand.md`).
- Hedges about the prospect: "my guess is", "could be off", "not 100% sure", "probably".
- Subjects: lowercase, 3 to 5 words, no variables, same subject across the thread.

## CTA ladder

- **Primary:** a question about who handles takedowns today.
- **Secondary (final email):** referral ("who owns this on your side?").
- Never: "book a call", calendar links, "free".

## Internal only (never in prospect copy)

- Pricing (custom, not public), signal volumes, reply rates, anything in `knowledge-base/learnings/`.
