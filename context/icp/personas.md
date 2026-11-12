# Doppel Buyer Personas

Built only from `context/docs/research/` (checked 2026-11-12). Quotes are exact and come from real customers, with the speaker named. The research has no direct data on how these roles are measured, so the "Measured on" rows are INFERRED from the proof points Doppel shows each role. Objections come from a rival's marketing or from customer comments about vendors in general, and each one is labeled.

## 1. Champion: the security operator who owns takedowns

| | |
|---|---|
| **Job titles** | Director of Cybersecurity (Christopher Smedberg, Advance); Head of Cyber Defence (Joanna Dalton, REA Group); Head of Platform Security (Daniel Pyykonen, Notion); Information Security Lead (Gerardo Di Giacomo, Aptos); Security Analyst (Cayden Larkin, Commerce); Lead Detection and Response Security Engineer (Giuseppe Petracca, AngelList). Source: `customers.md` |
| **Measured on (INFERRED)** | Takedown speed, takedown volume and success rate, detections found, manual work removed. Doppel's proof points for this role: "75%+" faster takedowns and a "25x" increase (Advance); "98%" success and a "5.5-Hours" median (ARK); more fake apps found in a two-week POC than in the previous year (REA). Source: `customers.md` |

**Top three pains, in their own words**
1. Slow or failed takedowns: "Simple domain takedowns would drag on for 30 days or fail entirely." (Advance case study, describing Smedberg's situation). Source: `customers.md`
2. Manual, never-ending work: "Prior to Doppel, it would take us days to weeks to identify and remove a lot of these scams" (Matthew Staudt, ARK). Dalton describes what Doppel took away: "has removed a huge amount of manual work for us". Source: `customers.md`
3. Constant threat stress: "I used to be stressed about all of the looming threats to our platform" (Pyykonen, Notion). Source: `customers.md`

**What makes them start looking**
- The incumbent tool stops performing: "becoming less effective at active takedowns" (REA). Source: `customers.md`
- A vendor that never improves: "after two or three years, it was basically the same platform." (unnamed security lead, financial services). Source: `customers.md`
- Platforms ignore manual reports: Meta reports "resulted in little to no action" (Advance). Source: `customers.md`

**Objections**
- The current tool is good enough: "We were using a platform that was widely considered one of the best out there," (unnamed security lead, said of the previous vendor). Source: `customers.md`
- Healthy skepticism: "There is no perfect platform in this space," (same security lead). Source: `customers.md`
- Effort to run it: a rival claims Doppel's "Enforcement scope is narrow and requires input from the customer". Source: `competitors.md` (BrandShield, a rival's claim). Counter-evidence: Advance onboarded in "minutes" with "a single email". Source: `customers.md`

## 2. Economic buyer: the CISO

| | |
|---|---|
| **Job titles** | Chief Information Security Officer (Marc Bown, REA Group; anonymous Fortune 500 agriscience CISO; the LA real estate firm's CISO); CTO where security sits under them (Mark Keller, ARK Invest); CISO and VP of Engineering (Michael Coates, CoinList). Source: `customers.md` |
| **Measured on (INFERRED)** | Protecting brand and executives, reducing risk, coverage of threats the team cannot see. Proof points shown to this role: "a 93% reduction in exposed executive PII" (Fortune 500 CISO); impersonation volume "basically cut in half" (ARK). Source: `customers.md` |

**Top three pains, in their own words**
1. The brand is the asset under attack: "Our brand is our biggest asset. People come to our site because of that brand, and we need to protect it." (Bown, REA). Source: `customers.md`
2. AI has made attacks cheap: "The effort involved in creating something that looks real has gone to basically zero." (Bown, REA). Source: `customers.md`
3. Executives are targets: "As a global brand with highly visible executives, protecting our leadership team is paramount." (anonymous Fortune 500 CISO). Source: `customers.md`

**What makes them start looking**
- Attackers scaling with AI: "[Attackers] can scale much more readily with AI tooling." (Bown). Source: `customers.md`. Gartner: 41% of CISOs reported a deepfake incident on an audio call. Source: `market.md`
- Blind spots appear: "You guys have found things that we've forgotten about." (LA real estate firm's CISO, after the switch). Source: `customers.md`
- Regulation that shifts fraud losses onto the company (UK, EU, Australia). Source: `market.md`. That it triggers a purchase is INFERRED

**Objections**
- Price: a rival claims "Doppel positions itself at a premium price point, with higher minimums". Source: `competitors.md` (BrandShield, a rival's claim). Pricing is custom: `company.md`
- Breadth versus focus: a rival claims "Doppel's detection strength lies primarily in phishing." Source: `competitors.md` (BrandShield, a rival's claim)
- Security standards for a vendor: "We are very security conscious," (Keller, ARK). Source: `customers.md`. Doppel holds three ISO certifications, including ISO 42001: `company.md`

## 3. Influencer: legal, brand and Trust & Safety

| | |
|---|---|
| **Job titles** | SVP, Deputy General Counsel (Steve Krause, Dapper Labs); COO and General Counsel (Evan Sils, Sugar23); Legal and Operations (Claire, Backpack); Brand Marketing Manager (Matthew Staudt, ARK); Trust & Safety Operations (Brett Farmer, Coinbase); Corporate Affairs executive (LA real estate firm); fraud team (REA sends tickets). Source: `customers.md` |
| **Measured on (INFERRED)** | Brand and community integrity, less manual enforcement work (Advance relied on "manual legal cease-and-desist processes"), and the number of takedowns (Coinbase: "over 800 social media accounts and 1000+ fraudulent domains"). Source: `customers.md` |

**Top three pains, in their own words**
1. Enforcement on autopilot is the goal: "Doppel enables us to put brand protection and anti-phishing security on autopilot." (Krause, Dapper Labs). Source: `customers.md`
2. Poor service from vendors: "On top of the technology issue was service." (Corporate Affairs executive). Source: `customers.md`
3. Brand integrity at risk: "Doppel's proactive approach and rapid response have been integral in maintaining the integrity and security of our brand" (Sils, Sugar23, excerpt). Source: `customers.md`

**What makes them start looking**
- Scam volume across channels (LinkedIn, Instagram, WhatsApp, Telegram at ARK; 216 impersonations on X at UniSat). Source: `customers.md`
- The legal team is overloaded with manual cease-and-desist work (Advance). Source: `customers.md`

**Objections**
- None found in the research. Open question.

## Open questions
- What each role is actually measured on (no KPI data in the research)
- Who signs the contract, and whose budget it comes from (security, legal or marketing)
- Personas for the HRM and Email Security buyers (no case studies). Likely the same CISO, but unconfirmed
- Objections heard in real deals (the only objections in the research are a rival's claims or general vendor skepticism)
