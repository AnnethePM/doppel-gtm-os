# Doppel Outbound GTM System

**Status:** design v1, 2026-11-12. This is a GTME cohort exercise built from public data. It is designed as if Doppel's team ran it. Do not send real outreach in Doppel's name: run every step up to the sequence as a dry run (see Step 8).

**Flow chart:** [Doppel GTM System on Miro](https://miro.com/app/board/uXjVEOVTIaw=/) (drawn 2026-11-13 from this file; layout source: `diagrams/doppel-gtm-system.json`). If this file changes, rebuild the chart from the JSON.

**Built from:** `context/icp/icp.md`, `context/icp/personas.md`, `context/icp/signal-matrix.md` and `context/docs/research/*`. Tools are taken from `CLAUDE.md`. Where `CLAUDE.md` says "to decide later", this design names a **proposed default** so every step has a tool:
- Sequencer: **EmailBison**. It is already in the stack for inbox placement tests.
- LinkedIn tool: **HeyReach**.
- CRM: **HubSpot**.

All three are proposals (INFERRED) and still need the user's decision. `CLAUDE.md` is not changed until that decision is made.

**Conventions:**
- **INFERRED:** a design choice that no research file supports.
- **[set after baseline]:** a threshold that needs real data first. No number is invented.
- **Starting value:** a parameter to tune, not a benchmark.

---

## The system at a glance

```
 0 CONTEXT OS (this repo) ─────────────────────────────────────────────┐
   icp.md · personas.md · signal-matrix.md · research · learnings       │
        │ read before every build and every weekly run                  │
        ▼                                                               │
 1 SIGNALS (always on: n8n schedules) ──▶ S1 domains · S2 warnings      │
        │                                 S3 ads · S4 regulator · S5 apps
        ▼                                                               │
 2 FIND COMPANIES (Clay: Companies table) ◀── monitored account universe│
        ▼                                                               │
 3 ENRICH (Clay: Enrich Company, Bloomberry)                            │
        ▼                                                               │
 4 ICP FIT CHECK (Clay formula gates) ──fail──▶ log reason ─────────────┤
        │pass                    └─hold──▶ manual review queue          │
        ▼                                                               │
 5 ROUTE (segment x signal ──▶ angle cell + lead product)               │
        ▼                                                               │
 6 FIND PEOPLE (Find People + Claygent ──▶ shared People table)         │
        ▼                                                               │
 7 FIND + VERIFY EMAIL (Clay native waterfall + 2nd verifier)           │
        │valid                   └─no valid email──▶ LinkedIn-only track│
        ▼                                                               │
 8 SEQUENCE (email: EmailBison · LinkedIn: HeyReach, both proposed)     │
        ▼                                                               │
 9 REPLY HANDLING (EmailBison + HeyReach inboxes ──▶ n8n + Claude)      │
        ▼                                                               │
10 CRM (HubSpot, proposed) ── company · contact · signal · deal         │
        ▼                                                               │
11 WEEKLY FEEDBACK LOOP (n8n + Claude Code) ──▶ writes to Context OS ───┘
        (Step 0 reads the changes before the next build)
```

---

## Step 0: Context OS

**What happens:** every build and every weekly run starts by reading the repo. The repo is the single source for who to target (`icp.md`), who to contact and what they care about (`personas.md`), which signals to run and the angle for each cell (`signal-matrix.md`), and what has already been learned (`knowledge-base/learnings/`). Each week's goals live in `weekly-priorities/`, and every change goes in `work-log/`.

**Tools:** this Git repo, Claude Code skills (`campaign-strategy`, `build-workflow-spec`, `campaign-copy`, `build-clay`), GitHub.

| Decision | Answer | Leads to |
|---|---|---|
| Is there an approved workflow spec for this signal? (`output/campaigns/<slug>/workflow-spec.md` marked STRUCTURE-APPROVED) | Yes | Build in Clay (Steps 1 to 7) |
| | No | Run `build-workflow-spec` first. Nothing is built without a spec |
| Has `icp.md` or `signal-matrix.md` changed since the last build? | Yes | Re-check the gates (Step 4) and routing (Step 5) against the new version before running |
| | No | Run as is |
| Is a fact in the copy sourced in `context/docs/research/`? | Yes | It can be used |
| | No | Remove it, or add a placeholder and flag it (CLAUDE.md rule 2) |
| Did last week's review (Step 11) change any Context OS file? (check `work-log/` and `git log`) | Yes | Apply each change to the step that reads it (see "Feedback map" in Step 11) before this week's run |
| | No | Run last week's configuration |

---

## Step 1: Buying signals (always on)

**What happens:** scheduled jobs check for the five build-first signals from `signal-matrix.md` and push each hit into Clay with its date, its source, and the evidence (domain, ad, alert, app or page URL).

**Tools:**
- n8n: the schedules.
- Data sources: Apify (dnstwist actor), crt.sh, SerpApi (Google Search and Ads Transparency engines), crawl4ai (regulator pages), and app store endpoints [verify].
- Clay webhook: receives every signal.

| Signal | What it detects | Tool | Run frequency (starting value) |
|---|---|---|---|
| S1 Lookalike domain | New TLS certificate on a permutation of a monitored brand's domain | n8n schedule → Apify dnstwist → crt.sh JSON → Clay webhook | Daily |
| S2 Public scam warning | A monitored company's site has a scam or impersonation page updated in the last 90 days | n8n → SerpApi Google Search (`site:` query) → Clay webhook | Weekly |
| S3 Third-party brand ads | Google ads that use the brand's name from an advertiser that isn't the brand | n8n → SerpApi `google_ads_transparency_center` → Clay webhook | Weekly |
| S4 Regulator alert (Segment A) | IOSCO I-SCAN or CIRO alert naming a firm as impersonated | n8n → scrape (crawl4ai or Clay HTTP) → Clay webhook | Weekly |
| S5 Fake app (Segments B, C) | App listing using the brand's name from a different developer | n8n → app store endpoints [verify] → Clay webhook | Weekly |

Secondary signals S6 (brand protection hiring), S7 (new CISO) and S8 (uses KnowBe4) are not triggers. They run as enrichments in Step 3.

| Decision | Answer | Leads to |
|---|---|---|
| Is the hit the brand's own asset? (a domain it owns, its own advertiser ID, its own developer account) | Yes | Discard. Store it as a known asset so it is skipped next time |
| | No | Keep it |
| Has this company had a signal in the suppression window? (starting value: 90 days) | Yes, same signal | Attach the new evidence to the existing record. No new outreach |
| | Yes, different signal | Attach it and flag as "stacked signal" (it may change the route in Step 5) |
| | No | New signal record. Go to Step 2 |
| Did a scheduled job fail or return zero for 2 runs in a row? | Yes | Alert in the weekly review (Step 11). The endpoint may have changed (crt.sh is informal) |
| | No | Continue |

---

## Step 2: Finding companies

**What happens:** signals S1, S2, S3 and S5 search by brand, so they need a list of companies to monitor. S4 names companies directly. There are therefore two ways in, and both write to one Clay **Companies** table (the `build-clay` structure).

1. **Monitored universe (ICP first):** Clay Find Companies with the Tier 1 and 2 segment filters from `icp.md`, in the US, Canada and Australia. It is refreshed monthly (starting value). This list is what S1, S2, S3 and S5 check.
2. **Signal-native discovery:** S4 alerts, plus S2 searches without a `site:` filter (for example "fake {segment} support" warnings), surface companies that aren't in the universe yet.

**Tools:** Clay (Find Companies, Companies table), n8n (refresh schedule).

| Decision | Answer | Leads to |
|---|---|---|
| Is the company already in the Companies table? (match on domain) | Yes | Attach the signal to the existing row |
| | No | Create the row, then go to Step 3 |
| Does the company have a usable domain? | Yes | Continue |
| | No (for example, an S4 alert with only a firm name) | Resolve the domain with Clay Enrich Company by name. If that fails, park it in a manual list |
| Is the company in Doppel's customer list? (`customers.md` logos and named customers) | Yes | Exclude, and tag `existing_customer` |
| | No | Continue |

---

## Step 3: Enrichment

**Tools:**
- Clay Enrich Company, Find Jobs at Company, Find People, formulas, and Use AI or Claygent as fallbacks only.
- Bloomberry or TheirStack, for KnowBe4 use.
- `calculate-costs` skill for spend checks.

**What happens:** cheap facts first, then the secondary signals that route the message. Following the `build-clay` rules, Use AI and Claygent are proven on 1 or 2 rows before any scale run, and a scale run needs the operator's OK with a cost estimate.

| Field | Tool | Used in |
|---|---|---|
| Headcount, industry, HQ country, LinkedIn URL | Clay Enrich Company | Step 4 gates |
| Segment (A, B, C, D or none) | Clay formula on industry keywords, with a Use AI fallback (proven on 2 rows) | Step 4 and Step 5 |
| Brand exposure flags: consumer app, public community, token or NFT, public-facing executives | Clay formulas and HTTP checks (app store, X or Telegram link on the site). Use AI only as a fallback | Step 4 qualifier |
| S6 Hiring brand protection roles | Clay Find Jobs at Company | Step 5 route |
| S7 New CISO in the last 90 days | Clay Find People (title and start date) | Step 5 route, Step 6 |
| S8 Uses KnowBe4 | Bloomberry or TheirStack (CSV or HTTP) | Step 5 upsell route |
| Known incumbent DRP vendor (ZeroFox, BrandShield, Bolster, Netcraft, Allure, Red Points) | Job posts mentioning the vendor (Clay Find Jobs). INFERRED as a method | Step 5 angle |

| Decision | Answer | Leads to |
|---|---|---|
| Did Enrich Company return headcount and country? | Yes | Go to Step 4 |
| | No | Try a second provider (a Claygent fallback, proven on 2 rows). If it still fails, Hold in Step 4 |
| Is the Use AI segment classification confident? | Yes | Use it |
| | No | Set segment to "unclassified" and Hold in Step 4 |
| Will the projected credit spend for this run exceed the budget? (`calculate-costs`) | Yes | Stop, and ask the operator |
| | No | Run |

---

## Step 4: ICP fit check

**What happens:** deterministic gates in Clay, cheapest first. Each gate either passes, fails with a logged reason, or holds the row for a human. The gates come straight from `icp.md`.

**Tools:** Clay formula columns (one per gate, with run conditions so later gates spend nothing on failed rows), and a filtered Clay view for the Hold queue.

| Order | Gate | Pass | Fail | Hold |
|---|---|---|---|---|
| 1 | Geography: HQ in the US, Canada or Australia | Next gate | Fail: `geo_out` | Country unknown |
| 2 | Not an existing Doppel customer | Next gate | Fail: `existing_customer` | n/a |
| 3 | Segment is A, B, C or D | Next gate | Fail: `segment_out` (for example manufacturing, which `icp.md` lists as not proven) | Unclassified |
| 4 | Not-a-fit checks: counterfeit or piracy is the only need; ATO-only need; nothing public to impersonate | Next gate | Fail with the not-a-fit reason from `icp.md` | Unclear |
| 5 | Brand exposure: at least one flag from Step 3 | Next gate | Fail: `no_exposure` | n/a |
| 6 | Company size (user-provided hypothesis: 1,000+ primary, 201-1,000 secondary) | **Tag only, never fail.** Tag `size_primary`, `size_secondary` or `size_other` | n/a | n/a |

Gate 6 is a tag, not a filter, because `icp.md` marks the size bands as unproven. Step 11 tests them by comparing results by tag.

| Decision | Answer | Leads to |
|---|---|---|
| Did the row pass gates 1 to 5? | Yes | Go to Step 5 |
| | No | Log the fail reason (fail reasons feed Step 11), no further spend |
| | Hold | Manual review queue in Clay (a filtered view). Reviewer marks it pass or fail within the week |
| Is the row a stacked signal (2 or more signals)? | Yes | Priority flag, so it is worked first |
| | No | Normal priority |

---

## Step 5: Routing by segment

**What happens:** each qualified row gets one route made of segment, signal, persona order, lead product and angle. The angle comes from the Matrix 1 cell, and the signal sets the opening line. Routing is a Clay formula, so the logic stays visible and testable.

**Tools:**
- A Clay formula column for the route.
- `campaign-copy` skill (Claude Code) for the copy for each route.
- `prompt-builder` skill for any per-row AI personalization line, proven on 2 rows first.

| Segment | Lead product (all rows) | First persona | Angle source |
|---|---|---|---|
| A. Investment and holding | Brand and Exec Protection | Champion. Economic buyer first if the trigger is S4 | `signal-matrix.md` Matrix 1, row A |
| B. Crypto and web3 | Brand Protection | Champion | Row B |
| C. Consumer apps | Brand Protection (fake apps) | Champion | Row C |
| D. Tech and SaaS | Brand Protection (phishing domains) | Champion | Row D |

| Decision | Answer | Leads to |
|---|---|---|
| Which signal triggered? | S1 | Opener built on the lookalike domain (shown as evidence, not as an accusation) |
| | S2 | Opener referencing the company's own scam warning |
| | S3 | Opener built on the third-party ads |
| | S4 | Opener referencing the regulator alert. Economic buyer first |
| | S5 | Opener built on the fake app listing |
| Stacked signals? | Yes | Use the higher-scoring signal from Matrix 2 as the opener and the other as supporting proof |
| | No | Single-signal opener only |
| S7 New CISO? | Yes | Add the economic buyer as a contact, with the "new leader" variant |
| | No | Standard persona order for the segment (table above) |
| S8 Uses KnowBe4? | Yes | Tag for the HRM upsell after the first meeting. It doesn't change the first message, because lead product stays Brand Protection (user decision, 2026-11-12) |
| | No | No upsell tag. The deal is Brand Protection only for now |
| Known incumbent vendor? | Yes | Use the "replace the incumbent" angle (a two-week POC proof point, REA) |
| | No | Use the "first program" angle (manual takedowns, as at ARK and UniSat) |

Copy rules: `campaign-copy` skill, `knowledge-base/playbooks/copy-iron-laws.md`, `copy-bans.yaml`, and no em dashes. The guardrail from `signal-matrix-framework.md` applies: describe their situation, never diagnose their gaps.

---

## Step 6: Finding people

**What happens:** two sourcing paths feed one shared **People** table, following the `build-clay` structure.

1. **Find People** (Clay, MixRank data), scoped to the qualified Companies view, using the persona titles from `personas.md`:
   - Champion: Director of Cybersecurity, Head of Cyber Defence, Head of Platform Security, Information Security Lead, Detection and Response lead.
   - Economic buyer: CISO, plus CTO where there is no CISO.
   - Influencer: Deputy General Counsel or General Counsel, Brand Marketing Manager, Trust & Safety, fraud lead.
2. **Claygent people search** for companies where Find People returns nobody (proven on 2 rows first).

**Tools:**
- Clay Find People (a staging table for each segment).
- Clay Claygent (people search), then "Send table data" into the shared People table.
- `build-clay` skill and `tools/rex` to build and audit the tables.

| Decision | Answer | Leads to |
|---|---|---|
| Was a champion found? | Yes | Contact 1 |
| | No | Make the economic buyer contact 1 |
| Was an economic buyer found? | Yes | Contact 2 (contact 1 if the trigger is S4 or S7) |
| | No | Run Claygent search. If still none, go champion-only |
| Was an influencer found? | Yes | Contact 3, but only for Segments A and B, where the research shows legal and brand involvement |
| | No | Skip |
| Has anyone been found at all? | Yes | Go to Step 7. Cap at 3 contacts per account (starting value), one per persona |
| | No | Park the account. Retry at the next monthly refresh |
| Was the person contacted in the last 90 days, or are they in the CRM as open, customer or do-not-contact? | Yes | Suppress |
| | No | Continue |
| Does the title match more than one persona? | Yes | Take the higher persona (economic buyer over champion) |
| | No | Continue |

---

## Step 7: Finding and verifying emails

**What happens:** one native Clay waterfall group, built from `tools/rex/templates/waterfall-work-email.json` (Prospeo → LeadMagic → Icypeas → Findymail, 4 steps by default, with LeadMagic validation on each step). A second verifier then runs on the results. It is conservative: no catch-all addresses, and it runs as a button only after the operator's go-ahead (`build-clay` rules).

**Tools:**
- Clay native waterfall: Prospeo, LeadMagic, Icypeas and Findymail, with LeadMagic validation on each step.
- Second verifier: a different provider from the step that found the email, so the check is independent (INFERRED). The provider is to be chosen from the operator's Clay connections (`clay.list_auth_accounts()`).

| Decision | Answer | Leads to |
|---|---|---|
| Did the waterfall return an email? | Yes | Second verifier |
| | No | LinkedIn-only track (Step 8) |
| What does the second verifier say? | Valid | Email track |
| | Catch-all or risky | Excluded from email (no catch-all rule). LinkedIn-only track |
| | Invalid | Drop the email. LinkedIn-only track |
| Is it a role or shared address (security@, info@)? | Yes | Drop. These are not personal contacts |
| | No | Continue |
| Is there a LinkedIn profile URL? | Yes | Eligible for the LinkedIn steps |
| | No | Email only. If there's no email either, drop the contact |

---

## Step 8: The sequence (email and LinkedIn)

**What happens:** each contact gets the routed sequence. Email goes through EmailBison and LinkedIn through HeyReach (both proposed). The steps below are a starting cadence (INFERRED) to tune in Step 11.

**Tools:**
- **Email sequencer: EmailBison** (proposed). It is already used for placement tests. If it is replaced, `campaign-qa` also supports Instantly and PlusVibe.
- **LinkedIn tool: HeyReach** (proposed).
- **Clay to sequencer:** Clay HTTP push or n8n.
- **Pre-launch checks:** `inbox-placement-test` (EmailBison and MailReach), `campaign-qa`, and the `campaign-copy` rules.

| Day (starting value) | Channel | Content |
|---|---|---|
| 1 | Email 1 | Signal opener plus the cell angle plus one proof point (a case study from `customers.md`) |
| 2 | LinkedIn | Profile view, then a connection request with no note (INFERRED) |
| 4 | Email 2 | A second proof point from the same segment |
| 6 | LinkedIn | If connected: a short message referencing the signal |
| 9 | Email 3 | A low-effort offer, for example "want the list of what we found?" (INFERRED; it has to be real data from the signal) |
| 14 | Email 4 | Break-up email |

**LinkedIn-only track:** connection request, then 2 messages if accepted.

| Decision | Answer | Leads to |
|---|---|---|
| Did the copy pass `campaign-qa` against the workflow spec? | Yes | Next check |
| | No | Fix and re-run QA |
| Did the inbox placement test pass? [threshold: set after baseline] | Yes | Next check |
| | No | Fix domains or warm-up, then re-test. Nothing launches until it passes |
| Did a human approve the launch? (CLAUDE.md rule 4) | Yes | Launch |
| | No | Hold |
| **Is this a cohort dry run?** | **Yes (current state)** | Stop here. Export the final sequence and contacts for review. No sending, because sending would present this outreach as coming from Doppel |
| | No (operated by Doppel's team) | Send |
| Did they reply at any step? | Yes | Stop the sequence and go to Step 9 |
| | No | Continue |
| Did the connection request get accepted? | Yes | LinkedIn messages run |
| | No | Email steps only |
| Did the email bounce? | Yes | Stop email, switch to LinkedIn-only, and log the provider that found it (Step 11) |
| | No | Continue |

---

## Step 9: Reply handling

**What happens:** every reply is classified, then routed. An LLM classifier drafts the label (Claude through n8n, INFERRED) and a human confirms it before anything is sent back.

**Tools:**
- EmailBison inbox and HeyReach inbox (both proposed), where replies arrive.
- n8n webhook: sends each reply to Claude for a label.
- Claude: drafts the label.
- HubSpot (proposed): logs the reply and runs the action.

| Reply class | Action |
|---|---|
| Positive or meeting request | Book the meeting and create a deal in the CRM. The first meeting offers the two-week POC (REA and a16z proof points) |
| Referral ("talk to X") | Add X as a new contact with the referrer named, send them a short email, and pause the original contact |
| Objection: price or minimums | Reply with the value proof (takedown speed and volume). Pricing is custom: sales or a partner (`company.md`) |
| Objection: "our current tool is good enough" | Offer the side-by-side POC. The unnamed financial services firm's quote: "widely considered one of the best... basically the same platform" (`personas.md`) |
| Objection: "too much work for my team" | Point to onboarding: "It was a single email" (Advance) |
| Not now, or timing | Snooze until the date they give, or 90 days if none (starting value). Re-enter with a new signal |
| Wrong person | Ask who the right person is. Update the persona mapping |
| Unsubscribe or negative | Do-not-contact in the CRM and in all sequences, right away |
| Out of office | Pause until their return date, then resume |
| Bounce or auto-reply error | Mark the email invalid and switch to LinkedIn-only |

| Decision | Answer | Leads to |
|---|---|---|
| Is the classifier confident, and has a human confirmed it? | Yes | Run the action |
| | No | Human labels it |
| Is the objection new? (not in `personas.md`) | Yes | Log it verbatim for Step 11. It goes into `personas.md` |
| | No | Count it |

---

## Step 10: The CRM

**What happens:** the CRM holds the record of every account and contact touched, and why.

**Tools:**
- **HubSpot** (proposed). It has a free tier, so a cohort project can use it without cost.
- Clay to HubSpot sync through Clay's HubSpot integration [verify].
- n8n for EmailBison and HeyReach events into HubSpot.

| Object | Key fields |
|---|---|
| Company | Domain, segment (A-D), ICP tier, size tag, gate results, existing-customer flag, suppression date |
| Contact | Persona, title, email status, LinkedIn URL, sequence status, reply class, do-not-contact |
| Signal (custom object or table) | Signal ID (S1-S8), date, evidence URL, workflow ID (W1-W7), stacked signal flag |
| Deal | Source workflow, segment, angle cell, lead product, upsell tags (HRM via S8, Email Security), stage |

| Decision | Answer | Leads to |
|---|---|---|
| Does the company or contact already exist? | Yes | Update it. Never create a duplicate (match on domain and email) |
| | No | Create it |
| Was a meeting booked? | Yes | Create a deal at the first stage, attributed to the workflow and the signal |
| | No | Activity only |
| Was there an unsubscribe or a negative reply? | Yes | Do-not-contact, synced back to Clay suppression and the sequencer |
| | No | Continue |

---

## Step 11: Weekly feedback loop

**What happens:** every week, results flow back into the Context OS, so the next week's build starts smarter. The review uses this week's `weekly-priorities/` file and is logged in `work-log/`.

**Tools:**
- n8n: weekly export from the sequencer and the CRM
- `calculate-costs` and `workspace-cost-audit`: Clay spend
- `campaign-qa`: checks the copy and table against the spec
- this repo: where the results get written back

**Metrics, tracked by workflow, segment, signal, angle cell, persona and size tag:**
- Signal hits, gate pass rate and fail reasons
- Contacts found, valid email rate, bounce rate
- Reply rate, positive rate, meetings
- Credits and dollars per meeting

| Decision | Answer | Leads to |
|---|---|---|
| Is a workflow's positive rate below the kill threshold after enough sends? [both: set after baseline] | Yes | Pause it. Write why in `knowledge-base/learnings/`, and mark the signal status in `signal-matrix.md` |
| | No | Keep it |
| Is one angle cell clearly ahead of the others in its segment? | Yes | Make it the default angle. Update Matrix 1 |
| | No | Test a new angle variant (one change per iteration) |
| Is a gate failing more rows than expected? | Yes | Check whether the gate or the signal is wrong. Update `icp.md` or the signal query |
| | No | No change |
| Did a size tag (`size_primary` and so on) show a clear difference? | Yes | Move the size bands from hypothesis to evidence in `icp.md`, citing the data |
| | No | Keep it as a tag |
| Did a new objection or pain appear in replies? | Yes | Add it verbatim to `personas.md`, with the source "reply, [date], [workflow]" |
| | No | No change |
| Is bounce rate or placement getting worse? | Yes | Pause sending, re-run `inbox-placement-test`, and check which waterfall step supplied the bounced addresses |
| | No | Continue |
| Is a scheduled signal job silent or erroring? | Yes | Fix the endpoint, and log it in `work-log/` |
| | No | Continue |
| Did Tier 3 segments (law firms, healthcare) show positive replies through stacked signals? | Yes | Propose promoting the segment in `icp.md` |
| | No | No change |

**Tools for writing back:** Claude Code edits the files, `git commit` records the change, and `work-log/` logs it with a timestamp.

### Feedback map: back into the Context OS

Every result has a home in the repo and a step that reads it the following week. Step 0 checks for changes before each run, which closes the loop.

| Result from this week | Written to (Context OS) | Read next week by | What changes |
|---|---|---|---|
| Signal hit counts, silent or failing jobs | `context/icp/signal-matrix.md`: Matrix 2 status and the "Enough volume" score; Matrix 3 tracker | Step 1 | Which signals run and how often; killed signals stop |
| Gate pass and fail reasons; Hold outcomes | `context/icp/icp.md`: firmographic tiers and Not a fit table | Step 4 | Gate rules and order |
| Results by size tag | `context/icp/icp.md`: company size row (hypothesis becomes evidence, with the data cited) | Step 4 | Whether size becomes a filter |
| Tier 3 positives | `context/icp/icp.md`: segment tiers | Steps 2 and 4 | Segments added to the monitored universe |
| Reply and positive rate by angle cell | `context/icp/signal-matrix.md`: Matrix 1 angles | Step 5 | The default angle per cell |
| New objections and pains, verbatim | `context/icp/personas.md` | Steps 5 and 9 | Copy angles and objection replies |
| Wrong-person replies, referrals | `context/icp/personas.md`: job titles | Step 6 | Find People title filters |
| Bounce rate by waterfall step | `knowledge-base/learnings/YYYY-Www.md` | Step 7 | Waterfall order or verifier |
| Placement test results, cadence results | `knowledge-base/learnings/YYYY-Www.md` | Step 8 | Cadence and sending setup |
| Credits and dollars per meeting | `knowledge-base/learnings/YYYY-Www.md` | Step 3 | Which enrichments are worth their cost |
| What worked, what failed, and why | `knowledge-base/learnings/YYYY-Www.md` | Step 0 (before any new campaign) | The next `campaign-strategy` and `build-workflow-spec` run |
| Next week's goals | `weekly-priorities/YYYY-Www.md` | Step 0 | What gets built or tested |
| Every change above | `work-log/YYYY-Www.md` and a git commit | Step 0 (the "did last week change anything?" check) | Triggers the update |

---

## Four-pillar check

| Pillar | Where the design meets it | Gaps and risks |
|---|---|---|
| **Clean data** | One Companies table and one People table (no duplicates); domain and email are the match keys at every step; known own-assets are stored so signals don't re-fire (Step 1); gates log a fail reason on every rejected row (Step 4); the waterfall has two verifiers and no catch-all addresses (Step 7); the CRM is update-not-create (Step 10); do-not-contact syncs back to Clay | HubSpot is only proposed, so sync rules can't be finalized yet. Segment classification uses AI as a fallback and can drift, so check it weekly. Customer exclusion relies on a public logo list that will go stale |
| **Always-on signals** | S1 to S5 run on n8n schedules, daily or weekly (Step 1); signal-first, not list-first (the framework guardrail); suppression and stacking are handled at the source; failed jobs get an alert | S4 and S5 rely on endpoints not yet verified ([verify] in `signal-matrix.md`). crt.sh is an informal endpoint. No signal volumes are known yet, so test each on 50 accounts first |
| **Composable workflows** | 6 of 9 signals are universal: one Clay build, reused across all four segments (`signal-matrix.md`); routing is one visible formula keyed on segment and signal (Step 5); each workflow is spec-first (`build-workflow-spec`), so the proposed tools (EmailBison, HeyReach, HubSpot) can be swapped without a redesign | EmailBison, HeyReach and HubSpot are proposals, not decisions, so the connections from Step 8 onward can't be finalized until they are confirmed. Angle copy has to be written per cell (12 cells) |
| **Tight feedback loops** | Weekly review with fixed decisions (Step 11); the feedback map gives every result a file in the Context OS and a step that reads it; Step 0 checks for those changes before each run, so the loop closes; objections are captured verbatim from replies; size bands and Tier 3 segments get tested by tags instead of guesses | Thresholds can't be set until there's a baseline [set after baseline]. In the cohort dry run nothing is sent, so the loop can only test the steps up to sending (signal hits, gate rates, email find rates), not replies |

## Open decisions
1. Confirm or replace the proposed tools: EmailBison (sequencer), HeyReach (LinkedIn), HubSpot (CRM). Then update `CLAUDE.md` Tools
2. Sending domains and warm-up plan (needed before any inbox placement test)
3. Kill, iterate and scale thresholds (after baseline)
4. Weekly owner for the manual review queue (Step 4 Hold) and for reply confirmation (Step 9)
5. Whether to draw this on Miro with `miro-gtm-flowchart` (needs the Miro MCP)
