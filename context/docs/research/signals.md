# Doppel: Buying Signals

Raw research, not conclusions. All sources checked 2026-11-12.
Each signal lists the public evidence for it. Signals with no direct evidence are marked INFERRED. This file is the input for the `signal-matrix` skill. It is not a finished matrix.

## A. Signals Doppel itself points to

### 1. Renewal of an incumbent security awareness vendor (KnowBe4)
- Evidence: Doppel runs https://www.doppel.com/farewell-to-knowbe4 [P]. The headline is "KnowBe4 was built for yesterday's attacks." The page says "For the record, KnowBe4 isn't going out of business. This is about your security program moving on."
- A webinar on the page covers "how to use your renewal date to plan your rollout without a coverage gap". It offers "a full farewell or adding a plus-one alongside your current platform". [P]
- The homepage banner says: "Planning your move from KnowBe4? Start here". Source: https://www.doppel.com/ [P]
- Signal: the company uses KnowBe4 (detectable through technographic data), and its renewal date is approaching. Renewal dates themselves: Not found publicly.

### 2. Unhappy with the current brand protection or DRP vendor
- Evidence: most case studies describe replacing an incumbent. Advance's domain takedowns "would drag on for 30 days or fail entirely". REA Group's incumbent was "becoming less effective at active takedowns". The unnamed financial services firm's previous provider was "very slow to respond, if they responded at all". Sources: https://www.doppel.com/customers/advance, https://www.doppel.com/customers/rea-group-protects-its-brands-and-reputation-social-engineering-defense, https://www.doppel.com/customers/onboarding-doppel-broader-detection-faster-takedowns-less-manual-work [P]
- Sales motion: a short proof of concept against the incumbent. REA Group ran "a two-week POC", and Zane Lackey quotes "a two-week proof-of-concept". [P] (see customers.md)
- Signal: the company uses a known DRP vendor (ZeroFox, BrandShield, Bolster, Netcraft and others). Contract renewal dates: Not found publicly.

### 3. Highly visible executives
- Evidence: an anonymous Fortune 500 agriscience CISO says "As a global brand with highly visible executives, protecting our leadership team is paramount." Source: https://www.doppel.com/customer-love [P]. ARK Invest's case is about impersonation of "high-profile figures". Source: https://www.doppel.com/customers/ark-invest [P]
- Signal: a well-known CEO or founder, a large social following, or executives in the press. INFERRED, based on the product's focus.

### 4. Active impersonation of the brand
- Evidence: ARK Invest had scams on LinkedIn, Instagram, WhatsApp and Telegram. UniSat had 216 impersonations on X. Sources: https://www.doppel.com/customers/ark-invest, https://www.doppel.com/blog/no-viable-alternative-doppel-social-media-brand-protection-unisat-says [P]
- Signal: public scam warnings on the company's own site or social accounts ("we will never DM you"), fake support accounts, lookalike domains, or fake apps in app stores. INFERRED as detectable signals. Doppel's own detection would find these. A manual check is also possible.

### 5. Deepfake or vishing incident, or helpdesk attacks
- Evidence: the KnowBe4 page cites vishing against helpdesks and AI agents, and multi-channel attacks over text, voice and Teams. Source: https://www.doppel.com/farewell-to-knowbe4 [P]. Doppel launched Zoom and Microsoft Teams meeting simulations. Source: https://www.doppel.com/company/press-releases/doppel-enters-japan-marking-next-phase-global-expansion [P]
- Signal: a public breach disclosure that mentions social engineering or a helpdesk, or press coverage of a deepfake CEO scam at the company or a peer. INFERRED.

## B. Regulatory deadlines (see market.md for sources)

| Signal | Who it hits | Date | Source quality |
|---|---|---|---|
| UK APP reimbursement consultation; regime moves to the FCA | UK banks and payment firms | Formal consultation planned for December 2026 | [3P-search] |
| Australia SPF: banks, telcos and digital platforms designated | AU banks, telcos, platforms | Effective 2026-05-23; consumer complaints to AFCA from 2027-03-31 (vendor-reported) | [3P-search] |
| EU PSR: spoofing refund liability and platform liability | EU banks and payment firms, online platforms | Application date Not found | [3P-search] |
| FTC public comment on platforms' role in impersonation | US platforms and ad networks | Notice dated 2026-10-01 | [P] https://www.ftc.gov/node/338570 |

INFERRED: An account in a regulated sector inside one of these jurisdictions, with a deadline coming up, is a timing signal.

## C. Company events (INFERRED from the pattern of customers and the product scope)

These have no direct public evidence linking them to Doppel purchases. They are hypotheses to test.

- **New CISO, Head of Security, or Head of Trust & Safety hired** in the last 90 days. INFERRED: a new leader often reviews existing vendors. Detect through LinkedIn job changes.
- **Hiring for brand protection, threat intel, fraud or "trust and safety" roles.** INFERRED. Detect through job posts.
- **Funding round, IPO or rapid growth.** INFERRED: a more visible brand attracts more impersonation. Many crypto and fintech customers on the logo wall (Ramp, Plaid, Cursor, Notion) are fast-growing, venture-backed companies. Source: https://www.doppel.com/customers [P]
- **Launch of a consumer app or crypto token**, or entry into new countries. INFERRED: REA Group's problem was fake apps, and Dapper Labs' was fake NFTs. Sources: customers.md [P]
- **Sports or media sponsorships, or a large event**, which create ticket and merchandise scams. INFERRED from the 49ers and Knicks partnerships, which Doppel frames as defense.
- **M&A or rebrand**, which creates new domains to impersonate. INFERRED.
- **A peer was publicly breached through social engineering** (for example, a helpdesk vishing attack at a company in the same sector). INFERRED.

## D. Doppel's own growth signals (useful context for outreach timing)

- New offices: Toronto (2026-09-03), Austin BDR hub, and Tokyo, plus London. Source: https://www.doppel.com/company/press-releases/doppel-opens-first-canadian-office-meet-demand-social-engineering-defense [P]
- New products in 2026: Phishing Triage (May 4), Email Security (announced May 27, GA July 30), and AI Managed Service for HRM (July 30). Sources: company.md [P]
- Hiring: Revelio shows about 20 open roles and about 9 new roles per month in 2026. Source: https://www.reveliolabs.com/companies/doppel/employees [3P-search]

## Not found
- Data that ties any specific signal to Doppel's conversion or win rates
- Public renewal dates for KnowBe4 or DRP vendor contracts
- Intent data or review-site category activity for Doppel
