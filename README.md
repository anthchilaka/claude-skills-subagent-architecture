# Workflow Automation Architecture | Claude Skills & Subagents | Multi-Domain Business Operations

## 🎯 Executive Summary
This project documents a personal AI operations system built on Claude Cowork and Claude Code: 12 reusable skills and 3 dedicated subagents covering BI analytics, remote career mentorship, web/dev delivery, and content orchestration. Rather than one-off prompting, every recurring task — from procurement dashboards to mentee career-transition coaching — runs through a standardized, trigger-matched skill so output quality and structure stay consistent regardless of which Claude surface initiates it. The architecture deliberately separates **planning** (done conversationally in Chat/Cowork) from **execution** (deployed in the tool's native space — Power BI, GitHub, a live website, LinkedIn/Upwork). Skills are registered once and surface automatically across every Claude entry point on the device via the Superpowers mechanism. The result is a repeatable, auditable system rather than a pile of disconnected prompts.

## ❗ Business Problem
Managing BI deliverables (Excel, Power BI, Fabric), mentoring professionals through career transitions into remote and data-analytics roles (job search, applications, LinkedIn/Upwork credibility building), and personal content (YouTube, church teaching) individually meant constant context-switching, inconsistent output formats, and no single source of truth for "how this gets done." There was no standard for what a finished procurement dashboard, a mentee's tailored cover letter, or a pushed GitHub repo should look like — each was rebuilt from scratch per session.

## 🔧 Methodology
Built a library of Markdown-defined skills, each with a trigger description Claude matches against incoming requests. Skills are grouped by domain (BI, mentorship, dev, personal-brand) and registered under one shared plugin namespace so they fire identically in Claude Code (CLI) and Claude Cowork (chat-first). Three subagents (LinkedInVA, YoutubeVA, SpiritualDirectorVA) handle profile-specific work, spawned by a single orchestrating skill.

## 🛠️ Skills Demonstrated

| Domain | Skill | Purpose |
|---|---|---|
| BI & Analytics | `excel-dashboard` | Power Pivot / DAX / CUBEVALUE Excel dashboards |
| BI & Analytics | `Microsoft Fabric Pro` | Legacy BI → Fabric migration (Lakehouse, Dataflow Gen2, Direct Lake) |
| BI & Analytics | `procurement-analyst` | Spend, supplier, and contract compliance analytics |
| BI & Analytics | `sales-analyst` | Sales KPI dashboards, pipeline & revenue analysis |
| BI & Analytics | `powerbi-tableau` | Power BI / Tableau dashboard builds |
| BI & Analytics | `lookerstudio-metabase` | Looker Studio / Metabase reporting |
| Dev & Delivery | `github-assist` | Repo creation, README generation, portfolio pushes |
| Dev & Delivery | `website-build` | Pages, components, Firebase deployment |
| Remote Career Mentorship & Transition Coaching | `upwork-job-search-optimizer` | Profile ranking & job-post keyword analysis |
| Remote Career Mentorship & Transition Coaching | `linkedin-job-intel` | Daily job intelligence pipeline |
| Remote Career Mentorship & Transition Coaching | `job-application-va` | ATS-optimized applications & cover letters |
| Orchestration | `anthony-va` | Routes to the 3 subagents below |

**🤖 Subagents:** `LinkedInVA` · `YoutubeVA` · `SpiritualDirectorVA` — profile-specific content intelligence spawned by `anthony-va`.

## 📊 Results & Business Recommendations
- Standardized output: every BI project ships with the same 7-step README; every mentee application package ships with 3 cover-letter variants and a 4-line summary — no rebuilding structure per session.
- Reduced context-switching: one Chat interface plans across 4 business domains; execution happens in-tool (Power BI Desktop, GitHub, the live site, LinkedIn/Upwork).
- Recommendation: extend the same skill-registration pattern to any new recurring workflow before attempting it ad hoc — the setup cost is paid once, reused indefinitely.
- Eval coverage in progress: `linkedin-job-intel` evaluated first — a synthetic eval, then a real production validation run against live daily job data (not a fixture) that caught and fixed 3 live rule gaps a synthetic test couldn't have surfaced (a fraud blocklist never encoded into the deployed rules, a location-restriction phrasing variant, and an unreliable "worldwide"-keyword signal that was wrong 11 of 12 times). Full scorecard: [`eval-results/linkedin-job-intel/scorecard.md`](https://github.com/anthchilaka/claude-workspace-audit/blob/main/eval-results/linkedin-job-intel/scorecard.md).

## ➡️ Next Steps
Eval coverage rolling out skill-by-skill using `skill-creator` — `linkedin-job-intel` complete, including a real production validation pass beyond the synthetic eval; remaining 13 skills in progress. Complete Claude Cowork ↔ GitHub MCP connection (currently CLI-only); consider a 4th subagent if a new content profile emerges.
