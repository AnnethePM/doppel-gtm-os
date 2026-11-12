# Doppel ICP

Built only from `context/docs/research/` (checked 2026-11-12). Each line names its research file. INFERRED means the conclusion is drawn from the research, not stated in it. Gaps are listed under Open questions.

Files: `company.md`, `customers.md`, `competitors.md`, `market.md`, `signals.md`, `voice.md` (all in `context/docs/research/`).

## Summary

Organizations with a well-known brand or executives that attackers can impersonate across domains, social media, ads, apps and email. The strongest evidence is in financial services, crypto and fintech, law firms, and fast-growing tech. These companies are often unhappy with an incumbent brand protection or awareness vendor. Sources: `customers.md`, `signals.md`.

## 1. Firmographic

| Attribute | Fit | Evidence |
|---|---|---|
| Industry (strongest evidence) | Financial services (asset managers, PE/VC, banks, credit unions); crypto and fintech; law firms; technology and software | Logo wall groups and case studies (Advance, ARK Invest, REA Group, Coinbase, Dapper Labs, UniSat): `customers.md` |
| Industry (on site; fewer proof points) | Healthcare, retail and consumer, real estate, energy and utilities, sports and media, manufacturing, education, public sector | Site industry list: `company.md`. Logo wall: `customers.md` |
| Size | Mid-market to Fortune 500. The site also lists small business. | "Small business, Mid-market, Enterprise", "protects dozens of the Fortune 500", 5X growth in Fortune 500 customers: `company.md`. Only stated case-study size is 500+ employees: `customers.md` |
| Geography | North America first. Also UK and EMEA, Japan, Australia (APAC) | Offices in SF, NY, Austin, Toronto, London and Tokyo; Email Security GA in AMER and APAC: `company.md`. Case studies are North American, plus REA Group in Australia: `customers.md` |
| Brand exposure | A consumer-facing brand, app, community or token; or highly visible executives | REA (fake apps), ARK (exec impersonation), UniSat and Dapper Labs (community scams), Fortune 500 agriscience CISO ("highly visible executives"): `customers.md` |
| Regulatory pressure | Banks and payment firms that refund victims (UK, EU); designated SPF sectors in Australia (banks, telcos, digital platforms) | `market.md`. That this drives purchases is INFERRED |

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

| Signal | Strength | Evidence |
|---|---|---|
| KnowBe4 renewal approaching | Strong (Doppel targets it directly) | `signals.md` |
| Unhappy with current DRP vendor (slow or failed takedowns, missed threats) | Strong (the pattern in most case studies) | `customers.md`, `signals.md` |
| Active impersonation: fake domains, apps, social accounts, ads, or scam warnings posted by the company | Strong | `signals.md`. How to detect these is INFERRED |
| Deepfake, vishing or helpdesk social engineering incident at the company or a peer | Medium | `signals.md` (INFERRED trigger). Gartner survey figures: `market.md` |
| Regulatory deadline in the account's sector and region (UK APP consultation Dec 2026; Australia SPF; EU PSR) | Medium | `market.md`, `signals.md` |
| New CISO or Head of Security or Trust & Safety; security hiring; funding round; app or token launch; new market; M&A or rebrand; big sponsorship or event | Hypothesis | All INFERRED in `signals.md`; not yet tested |

## 4. Persona (detail in `personas.md`)

| Role | Who | Evidence |
|---|---|---|
| Champion | Security operator who owns takedowns or detection (Director of Cybersecurity, Head of Cyber Defence, Head of Platform Security) | Smedberg (Advance), Dalton (REA), Pyykonen (Notion): `customers.md` |
| Economic buyer | CISO (sometimes the CTO) | Bown (REA), anonymous Fortune 500 CISO, LA real estate firm's CISO, Keller (ARK CTO): `customers.md` |
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
- Whether the smaller industries on the site (healthcare, energy, education, manufacturing) have real traction
