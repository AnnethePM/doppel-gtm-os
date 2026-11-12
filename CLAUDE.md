# Doppel GTM Context OS

## Company

Doppel (https://www.doppel.com) sells an AI social engineering defense platform that combines Digital Risk Protection (brand and executive impersonation takedowns), Human Risk Management (simulation and training) and Email Security. Source: https://www.doppel.com/ (checked 2026-11-12), summarized in `context/docs/research/company.md`.

## Key files

- Research (raw, sourced, checked 2026-11-12): `context/docs/research/company.md`, `customers.md`, `competitors.md`, `market.md`, `signals.md`, `voice.md`
- ICP (five layers, plus who is not a fit): `context/icp/icp.md`
- Buyer personas (champion, economic buyer, influencer): `context/icp/personas.md`

## How this folder works

- `.claude/skills/`: reusable Claude skills for repeat GTM tasks. Read when a task matches a skill.
- `context/icp/`: ideal customer profiles and buyer personas. Read before any targeting, prospecting, or copy.
- `context/positioning/`: market category, competitors, differentiators. Read before writing anything that compares or positions Doppel.
- `context/messaging/`: approved value props, messaging pillars, proof points. Read before writing any copy.
- `context/brand-kit/`: voice, tone, visual guidelines, logos. Read before producing anything customer facing.
- `context/docs/research/`: raw research notes and sources on the company and market. Read when you need to verify or cite a fact.
- `knowledge-base/playbooks/`: step-by-step processes that work. Read before running a repeatable motion.
- `knowledge-base/learnings/`: what worked, what failed, and why. Read before planning new campaigns.
- `meetings/`: meeting notes and transcripts, one file per meeting. Read when a task references a past conversation.
- `output/campaigns/`: finished and draft campaign assets. Read to reuse or update past work; write new deliverables here.
- `tools/`: scripts and integrations used by this repo. Read when a task needs automation or external data.
- `weekly-priorities/`: one file per ISO week (e.g. `2026-W46.md`) with that week's goals. Read at the start of every session.
- `work-log/`: one file per ISO week, matching weekly-priorities, with timestamped entries. Write to it after every change.

## Rules

1. Cite a source (URL or file path) for every company fact.
2. Never invent numbers. If a number has no source, leave a placeholder and flag it.
3. No em dashes in any copy.
4. Ask before sending or publishing anything.
5. Log every change in this week's work log (`work-log/YYYY-Www.md`) with a timestamp.

## Skills

From the GTM Starter Kit (bolaji-ships/gtm-starter-kit). Type `/` in a new session to see them.
- Research to copy, in order: `campaign-strategy`, `signal-matrix`, `build-workflow-spec`, `campaign-copy`. Plus `miro-gtm-flowchart` to draw the system.
- Clay builds (use `tools/rex`): `build-clay`, `prompt-builder`, `campaign-contract`, `design-clay-table-json`, `import-clay-table`, `save-clay-schema`, `calculate-costs`, `workspace-cost-audit`, `export-tables`, `campaign-qa`.
- Research and deliverability: `crawl4ai`, `agent-browser`, `inbox-placement-test`.

## Tools

- Clay: enrichment, signals and list building. Claude works in it through `tools/rex/` (unofficial SDK, your browser session; start with `GETTING_STARTED.md`).
- n8n: workflow automation.
- crawl4ai (`tools/crawl4ai/`) and agent-browser (`tools/agent-browser/`): web crawling and browser automation. Installed separately.
- Miro: GTM flow charts via `miro-gtm-flowchart`. Needs the Miro MCP.
- EmailBison and MailReach: inbox placement tests via `inbox-placement-test`.
- To decide later: email sequencer, LinkedIn outreach tool, CRM.
