# ð¹ Project Signal: The Stakeholder Communication Engine

> **One Source of Truth. Five Audiences. Zero Information Overload.**

[![Methodology](https://img.shields.io/badge/Methodology-Stakeholder%20Intelligence%20%7C%20Audience%20Mapping-blueviolet?style=flat-square)]()
[![Domain](https://img.shields.io/badge/Domain-Enterprise%20Communications%20%7C%20Risk%20Management-teal?style=flat-square)]()
[![Status](https://img.shields.io/badge/Status-Portfolio%20Simulation-orange?style=flat-square)]()

---

## ð The Operational Challenge

It is the end of Sprint 2 in the Project Horizon delivery window. Epic 1 (HL7 Mapping Upgrade) is on track. But a risk has materialized: the RCM platform API integration required for Epic 2âs billing reconciliation dashboard is running 4 days behind schedule due to an undocumented parameter change in RCM platformâs v2.4.1 release.

The delay has zero clinical safety impact. But it creates real DSO exposure if unresolved before the Sprint 3 cutover window â and five very different stakeholders need to know about it.

The problem isnât the risk. **The problem is that every PMâs instinct in this moment is to write one email and send it to everyone.** That email is too technical for the CMO, too vague for the VP of Engineering, too soft for the CFO, too internal for the vendor, and too alarming for the clinical field team.

This project documents an AI-assisted stakeholder communication engine that takes a single source of raw sprint data and generates five audience-appropriate communications simultaneously â without losing consistency, without burying anyone in irrelevant detail, and without accidentally saying different things to different people about the same risk.

---

## ð¥ The Five Audiences

| Stakeholder | Primary Concern | What They Must NOT See |
|---|---|---|
| **Chief Medical Officer** | Clinical operations continuity | API parameter details, sprint velocity |
| **Chief Financial Officer** | DSO exposure and revenue timing | Technical root cause, team dynamics |
| **VP of Engineering** | Technical root cause and resolution path | Executive narrative, political framing |
| **RCM Platform Vendor** | SLA accountability and remediation timeline | Internal team capacity issues |
| **Clinical Operations Field Lead** | Will anything change for my clinicians this week? | Everything else |

---

## ð¥ The Data Inputs

Three structured inputs feed the communication engine. See the `/data` folder for full source files.

### Sprint Status (Raw)
Unfiltered sprint data: Epic 1 and 2 status, the RCM platform API root cause, technical resolution path, DSO exposure window, team capacity, and clinical impact assessment. This is the single source of truth that all five communications must draw from â consistently.

### Stakeholder Registry
A structured map defining communication parameters for each of the five audiences: format, word count ceiling, technical depth dial (0â10), primary metric they track, and what to omit entirely. The registry is what transforms the prompt from a summarizer into an audience intelligence engine.

### Risk Register
The active risk log providing prioritization context: probability, impact, current status, owner, and mitigation for the RCM platform API risk and two secondary risks. Gives the engine context for what to escalate vs. what to hold.

---

## ð¤ The AI Communication Engine

The prompt in `/prompts/stakeholder-reporting-prompt.md` is the most architecturally sophisticated of the three portfolio projects. It operates in three layers:

**Layer 1 â Context Ingestion**
Processes all three data files simultaneously and builds an internal model of sprint state, active risks, and audience parameters.

**Layer 2 â Audience Variable Logic**
For each of the five outputs, applies a conditional instruction set:
- Technical depth dial (0 = zero jargon / 10 = full technical detail)
- Word count ceiling per format type
- Tone register (executive briefing / peer update / formal vendor notice / field FAQ)
- Lead with: clinical impact / financial impact / technical resolution / accountability / simple answer
- Hard omit list per audience

**Layer 3 â Consistency Enforcement**
Before finalizing any output, the engine validates that no two communications contradict each other on the same fact. The risk status, timeline, and clinical impact must be consistent across all five â even when the framing is completely different.

---

## ð The Output: Five Communications, One Story

The same risk â described five completely different ways:

| Output | Format | Length | Leads With |
|---|---|---|---|
| CMO Briefing | Narrative prose | 150 words | Clinical operations are unaffected |
| CFO Update | Bullets + one number | 100 words | DSO exposure window |
| Engineering Standup | Status table + action items | Full technical | Root cause + resolution path |
| Vendor Escalation | Formal notice | Structured | SLA miss + remedy request |
| Ops Field Update | FAQ | 5 questions | âWill anything change for my team?â |

> **The test of a good communication engine:** A CMO and a VP of Engineering could each read their respective outputs, compare notes over lunch, and find no contradictions â just different levels of detail on the same underlying truth.

---

## ð Repository Contents

```
project-signal/
âââ README.md                              â This document
âââ PROCESS.md                             â PM decision log and AI methodology
âââ /data/
â   âââ sprint-status-raw.md               â Unfiltered sprint data â the source of truth
â   âââ stakeholder-registry.md            â Audience map with communication parameters
â   âââ risk-register.md                   â Active risks with probability/impact/owner
âââ /prompts/
â   âââ stakeholder-reporting-prompt.md    â The AI communication engine
âââ /output/
    âââ cmo-briefing.md                    â Clinical leadership narrative
    âââ cfo-update.md                      â Financial impact summary
    âââ engineering-standup.md             â Technical team status brief
    âââ vendor-escalation.md               â RCM platform SLA miss notice
    âââ ops-field-update.md                â Clinical operations FAQ
```

---

## â Product Manager Requirements

| Requirement | How This Project Demonstrates It |
|---|---|
| *âBuild trusted partnerships with business leaders and key stakeholdersâ* | Stakeholder registry maps each audienceâs concerns, metrics, and communication preferences â the foundation of trusted relationships |
| *âCommunicate product progress, outcomes, risks, and opportunities to leadership teamsâ* | Five outputs deliver the same risk status to five leadership audiences in their own language |
| *âServe as primary liaison between business stakeholders, technology teams, and external vendorsâ* | The engine simultaneously manages internal executive communication AND a formal vendor escalation from the same data source |
| *âManage timelines, priorities, and resources to ensure successful deliveryâ* | Risk register and sprint status data demonstrate active timeline management with escalation triggers |
| *âAct as product ambassador and subject matter expert for assigned platformsâ* | Vendor escalation notice demonstrates platform-level accountability and SLA management fluency |

---

## â Product Manager Methodology Intervention

Deciding what each audience must not see requires knowing organizational dynamics, trust relationships, and political risk well enough to make a judgment call that no AI can make independently. The stakeholder registry exists because those judgment calls must be made by a human before the AI can execute anything.

---

## ð Portfolio Navigation

This is **Agent 3 of 3** â the communication and control layer that wraps around everything built in Agents 1 and 2.

| Project | Question Answered | Methodology |
|---|---|---|
| [Project Horizon](https://github.com/zinaleeHQ/project-horizon) | What do we build and when? | SAFe Â· WSJF |
| [Project Clarity](https://github.com/zinaleeHQ/project-clarity) | How do we change how people work? | Lean Â· DMAIC |
| **Project Signal** (this repo) | How do we keep every stakeholder aligned? | Stakeholder Intelligence Â· Audience Mapping |

[**â Back to Portfolio Overview**](https://github.com/zinaleeHQ)

---

*Portfolio simulation Â· All scenario details constructed from publicly available information Â· No proprietary data from any organization has been used Â· Built June 2026*
