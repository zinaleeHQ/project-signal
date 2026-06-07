# 🔹 Project Signal: The Stakeholder Communication Engine
> **What this project is about, in plain language:**
>
> This project solves the problem of communicating the same sprint reality to five different people who all need to hear something different. An AI tool generated five audience-appropriate communications from one source of truth — and does so whether the sprint is on fire or entirely routine. The PM's job is to read each AI output as the recipient — not the sender — and catch every place where technically correct language would land wrong in the actual relationship.

> **One Source of Truth. Five Audiences. Zero Information Overload.**

[![Methodology](https://img.shields.io/badge/Methodology-Stakeholder%20Intelligence%20%7C%20Audience%20Mapping-blueviolet?style=flat-square)]()
[![Domain](https://img.shields.io/badge/Domain-Enterprise%20Communications%20%7C%20Risk%20Management-teal?style=flat-square)]()
[![Status](https://img.shields.io/badge/Status-Portfolio%20Simulation-orange?style=flat-square)]()

---

## 📋 The Operational Challenge

It is the end of Sprint 2 in the Project Horizon delivery window. Epic 1 (HL7 Mapping Upgrade) is on track. But a risk has materialized: the RCM platform API integration required for Epic 2’s billing reconciliation dashboard is running 4 days behind schedule due to an undocumented parameter change in RCM platform’s v2.4.1 release.

The delay has zero clinical safety impact. But it creates real DSO exposure if unresolved before the Sprint 3 cutover window — and five very different stakeholders need to know about it.

The problem isn’t the risk. **The problem is that every PM’s instinct in this moment is to write one email and send it to everyone.** That email is too technical for the CMO, too vague for the VP of Engineering, too soft for the CFO, too internal for the vendor, and too alarming for the clinical field team.

This project documents an AI-assisted stakeholder communication engine that takes a single source of raw sprint data and generates five audience-appropriate communications simultaneously — without losing consistency, without burying anyone in irrelevant detail, and without accidentally saying different things to different people about the same risk.

---

## 👥 The Five Audiences

| Stakeholder | Primary Concern | What They Must NOT See |
|---|---|---|
| **Chief Medical Officer** | Clinical operations continuity | API parameter details, sprint velocity |
| **Chief Financial Officer** | DSO exposure and revenue timing | Technical root cause, team dynamics |
| **VP of Engineering** | Technical root cause and resolution path | Executive narrative, political framing |
| **RCM Platform Vendor** | SLA accountability and remediation timeline | Internal team capacity issues |
| **Clinical Operations Field Lead** | Will anything change for my clinicians this week? | Everything else |

---

## 📥 The Data Inputs

Three structured inputs feed the communication engine. See the `/data` folder for full source files.

### Sprint Status (Raw)
Unfiltered sprint data: Epic 1 and 2 status, the RCM platform API root cause, technical resolution path, DSO exposure window, team capacity, and clinical impact assessment. This is the single source of truth that all five communications must draw from — consistently.

### Stakeholder Registry
A structured map defining communication parameters for each of the five audiences: format, word count ceiling, technical depth dial (0–10), primary metric they track, and what to omit entirely. The registry is what transforms the prompt from a summarizer into an audience intelligence engine.

### Risk Register
The active risk log providing prioritization context: probability, impact, current status, owner, and mitigation for the RCM platform API risk and two secondary risks. Gives the engine context for what to escalate vs. what to hold.

---

## 🤖 The AI Communication Engine

The prompt in `/prompts/stakeholder-reporting-prompt.md` is the most architecturally sophisticated of the three portfolio projects. It operates in three layers:

**Layer 1 — Context Ingestion**
Processes all three data files simultaneously and builds an internal model of sprint state, active risks, and audience parameters.

**Layer 2 — Audience Variable Logic**
For each of the five outputs, applies a conditional instruction set:
- Technical depth dial (0 = zero jargon / 10 = full technical detail)
- Word count ceiling per format type
- Tone register (executive briefing / peer update / formal vendor notice / field FAQ)
- Lead with: clinical impact / financial impact / technical resolution / accountability / simple answer
- Hard omit list per audience

**Layer 3 — Consistency Enforcement**
Before finalizing any output, the engine validates that no two communications contradict each other on the same fact. The risk status, timeline, and clinical impact must be consistent across all five — even when the framing is completely different.

---

## 📊 The Output: Five Communications, One Story

The same risk — described five completely different ways:

| Output | Format | Length | Leads With |
|---|---|---|---|
| CMO Briefing | Narrative prose | 150 words | Clinical operations are unaffected |
| CFO Update | Bullets + one number | 100 words | DSO exposure window |
| Engineering Standup | Status table + action items | Full technical | Root cause + resolution path |
| Vendor Escalation | Formal notice | Structured | SLA miss + remedy request |
| Ops Field Update | FAQ | 5 questions | “Will anything change for my team?” |

> **The test of a good communication engine:** A CMO and a VP of Engineering could each read their respective outputs, compare notes over lunch, and find no contradictions — just different levels of detail on the same underlying truth.

---

## 📁 Repository Contents

```
project-signal/
├── README.md                              ← This document
├── PROCESS.md                             ← PM decision log and AI methodology
├── /data/
│   ├── sprint-status-raw.md               ← Unfiltered sprint data — the source of truth
│   ├── stakeholder-registry.md            ← Audience map with communication parameters
│   └── risk-register.md                   ← Active risks with probability/impact/owner
├── /prompts/
│   └── stakeholder-reporting-prompt.md    ← The AI communication engine
└── /output/
    ├── cmo-briefing.md                    ← Clinical leadership narrative
    ├── cfo-update.md                      ← Financial impact summary
    ├── engineering-standup.md             ← Technical team status brief
    ├── vendor-escalation.md               ← RCM platform SLA miss notice
    └── ops-field-update.md                ← Clinical operations FAQ
```

---

## ✅ Product Manager Requirements

| Requirement | How This Project Demonstrates It |
|---|---|
| *“Build trusted partnerships with business leaders and key stakeholders”* | Stakeholder registry maps each audience’s concerns, metrics, and communication preferences — the foundation of trusted relationships |
| *“Communicate product progress, outcomes, risks, and opportunities to leadership teams”* | Five outputs deliver the same risk status to five leadership audiences in their own language |
| *“Serve as primary liaison between business stakeholders, technology teams, and external vendors”* | The engine simultaneously manages internal executive communication AND a formal vendor escalation from the same data source |
| *“Manage timelines, priorities, and resources to ensure successful delivery”* | Risk register and sprint status data demonstrate active timeline management with escalation triggers |
| *“Act as product ambassador and subject matter expert for assigned platforms”* | Vendor escalation notice demonstrates platform-level accountability and SLA management fluency |

---

## ✅ Product Manager Methodology Intervention

Deciding what each audience must not see requires knowing organizational dynamics, trust relationships, and political risk well enough to make a judgment call that no AI can make independently. The stakeholder registry exists because those judgment calls must be made by a human before the AI can execute anything.



---


## 🚀 Want to Try This Yourself?

This project has a live HTML page with a one-click **Copy Prompt** button that copies the complete prompt for you, including data. Paste/Ctrl-V into Claude, GPT-4, or Gemini — no setup required.

👉 [Open Project Signal Prompt Copy page](https://zinaleeHQ.github.io/project-signal/)

Each prompt pauses at a PM judgment checkpoint before the final phase. Answer "yes" when you are ready to move forward. (That pause is the point.)


---


## 🔗 Portfolio Navigation

This is **Agent 3 of 3** — the communication and control layer that wraps around everything built in Agents 1 and 2.

| Project | Question Answered | Methodology |
|---|---|---|
| [Project Horizon](https://github.com/zinaleeHQ/project-horizon) | What do we build and when? | SAFe · WSJF |
| [Project Clarity](https://github.com/zinaleeHQ/project-clarity) | How do we change how people work? | Lean · DMAIC |
| **Project Signal** (this repo) | How do we keep every stakeholder aligned? | Stakeholder Intelligence · Audience Mapping |
| [Project Vista](https://github.com/zinaleeHQ/project-vista) | How do we give every stakeholder self-service visibility? | KPI Governance · Data Architecture |

[**← Back to Portfolio Overview**](https://github.com/zinaleeHQ)

---

*Portfolio simulation · All scenario details constructed from publicly available information · No proprietary data from any organization has been used · Built June 2026*
