# Project Signal: The Stakeholder Communication Engine

**Five AI-generated stakeholder updates passed every consistency check and still weren't ready to send — because the engine didn't know the CMO had been quietly nervous about this rollout for two months, and "calm" needed a different calibration than the registry specified.**

That's the gap this project documents. Horizon decided what to build. Clarity changed how people work. This one is about the moment a risk surfaces mid-sprint and five different people — a CMO, a CFO, an engineering VP, a vendor, a field lead — all need the same truth delivered five different ways, without any of them catching a version that contradicts what someone else got.

Most PMs write one email in that moment. It's too technical for the CMO, too soft for the CFO, and too alarming for the field team — because one message can't actually serve five audiences with different fears, different vocabularies, and different thresholds for panic.

**[→ See the rest of the judgment calls in PROCESS.md](https://github.com/zinaleeHQ/project-signal/blob/main/PROCESS.md)** — same kind of thinking, more of it, including why the vendor escalation notice was the hardest of the five to get right.

> **One Source of Truth. Five Audiences. Zero Information Overload.**

[![Methodology](https://img.shields.io/badge/Methodology-Stakeholder%20Intelligence%20%7C%20Audience%20Mapping-blueviolet?style=flat-square)]()
[![Domain](https://img.shields.io/badge/Domain-Enterprise%20Communications%20%7C%20Risk%20Management-teal?style=flat-square)]()
[![Status](https://img.shields.io/badge/Status-Portfolio%20Simulation-orange?style=flat-square)]()

---

## ∴︎ Why This Matters Outside of Tech

Every organization eventually hits a moment where one piece of bad news has to reach several audiences at once, and each of them would panic, disengage, or misread the situation if they got someone else's version. A law firm partner explaining a case setback to a client needs a completely different message than the one going to the associates staffed on it, and both need to match what's going to the firm's insurer if it comes to that. A hospital administrator explaining a supply shortage to clinical staff can't send the same note that goes to the board.

The skill underneath this project is audience-aware communication built on a single, unshakeable source of truth — saying the same real thing five different ways without any version drifting from what's actually happening. Get it wrong, and you don't just have a communication problem. You have five people who each think they know what happened, and none of their versions quite match.

---

## The Operational Challenge

Sprint 2 of the Horizon delivery window is closing. The HL7 mapping upgrade is on track. But a risk has surfaced: the RCM platform API integration that Epic 2's billing dashboard depends on is four days behind schedule, thanks to an undocumented parameter change in the platform's v2.4.1 release.

There's no clinical safety impact. But left unresolved before the Sprint 3 cutover, it creates real Days Sales Outstanding (DSO) exposure — and five stakeholders, each with a different stake in the outcome, need to hear about it before rumors beat the facts to their inbox.

| Stakeholder | Primary Concern | Must Not See |
|---|---|---|
| **Chief Medical Officer** | Clinical operations continuity | API parameter details, sprint velocity |
| **Chief Financial Officer** | DSO (Days Sales Outstanding) exposure — tracked alongside Defect Spillover as a leading indicator | Technical root cause, team dynamics |
| **VP of Engineering** | Technical root cause and resolution path | Executive narrative, political framing |
| **RCM Platform Vendor** | SLA accountability and remediation timeline | Internal team capacity issues |
| **Clinical Operations Field Lead** | Will anything change for my team this week? | Everything else |

This project documents an AI-assisted communication engine that takes one source of raw sprint data and generates five audience-appropriate outputs at once — without burying anyone in irrelevant detail, and without ever letting two versions of the same fact drift apart.

---

## ⎔︎ What Feeds the Engine

Three inputs, and the second one is doing most of the actual work.

Sprint status is the unfiltered source of truth — epic status, root cause, resolution path, DSO exposure window, team capacity, clinical impact. Every one of the five outputs has to trace back to this file and agree with it.

The stakeholder registry is what separates this from a simple summarizer: a structured map defining, per audience, a technical-depth dial (0 to 10), a word-count ceiling, a tone register, what to lead with, and — just as important — an explicit list of what to omit entirely. Writing "the CMO doesn't want technical detail" into a prompt as prose gets treated as a soft suggestion. Writing `technical_depth: 0` and `hard_omit: [API details, sprint velocity]` into a structured file gets treated as a rule. That distinction is the whole reason this engine produces five genuinely different documents instead of one document with four watered-down copies.

The risk register adds prioritization context — probability, impact, owner, mitigation — so the engine knows what actually warrants escalation versus what can stay quiet for now.

---

## ⚙︎ How the Engine Actually Works

The prompt (`/prompts/stakeholder-reporting-prompt.md`) runs in three layers, and it's a harder problem than either Horizon's scoring or Clarity's redesign, because it has to hold two things in its head at once: the underlying facts, which never change, and five different audience filters, which change everything about how those facts get presented.

Layer one ingests all three data files and builds an internal model of sprint state, active risks, and audience parameters together. Layer two applies the registry's conditional logic per output — technical depth, word ceiling, tone, lead-with priority, hard omits — so the CMO briefing and the engineering standup are drawing from the same well while reading nothing alike. Layer three is the part that actually matters most: before any output is finalized, the engine checks all five against each other and flags any place where a fact — a timeline, a dollar figure, a clinical impact claim — reads differently across two documents. That's not a style pass. A consistency violation is a blocker, the same way a compliance violation blocks a WSJF score in Horizon.

Here's why that layer earns its own step instead of living inside the drafting step: the real danger in a multi-audience system isn't saying the wrong thing to one person. It's saying two *slightly* different true things to two people who later compare notes. If the CMO reads "resolution by end of sprint" and the CFO reads "resolution within 5 business days," those might describe the same date — but they don't land the same way, and the CFO may walk away thinking the timeline just got longer. That kind of inconsistency erodes trust faster than the original risk does.

---

## The Output: Five Communications, One Story

| Output | Format | Length | Leads With |
|---|---|---|---|
| CMO Briefing | Narrative prose | 150 words | Clinical operations are unaffected |
| CFO Update | Bullets + one number | 100 words | DSO exposure window |
| Engineering Standup | Status table + action items | Full technical detail | Root cause and resolution path |
| Vendor Escalation | Formal notice | Structured | SLA miss and remedy request |
| Ops Field Update | FAQ | 5 questions | "Will anything change for my team?" |

The real test of whether this worked: could the CMO and the VP of Engineering compare notes over lunch and find zero contradictions between their two documents — just very different levels of detail sitting on top of the same underlying truth? That's the bar, and it's a genuinely different bar than "did each document sound appropriate on its own."

---

## Where PM Judgment Actually Had to Show Up

All five outputs passed the consistency check. Technically, the engine did exactly what it was built to do — and that's the floor, not the ceiling, because passing a consistency check only proves the documents agree with each other. It doesn't prove any of them are ready to land in a real inbox.

The registry doesn't know that the CMO has been quietly nervous about this rollout for two months and needs a different calibration of "calm" than the default setting. It doesn't know the CFO has been asking pointed questions about DSO exposure since Q1, so a number that reads as reassuring on paper might land as an escalation given the history. It doesn't know the VP of Engineering is already having a rough sprint with their team, so a resource-confirmation ask needs to read as a conversation, not an assignment. None of that lives in a data file. All of it lives in the PM's head, and none of it shows up until a human reads each output as the *recipient*, not the sender, and asks what that specific person is actually going to feel by the third sentence.

The vendor escalation is the sharpest example of why this matters. It carries real contractual weight, and its tone register is the narrowest of the five — too soft, and the vendor doesn't feel the SLA obligation; too sharp, and a relationship you still depend on takes damage before the technical problem is even fixed. Getting that balance right isn't something a registry parameter can specify in advance. It's a judgment call made fresh, every time, by someone who knows the actual relationship.

---

## ↳︎ Repository Contents

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

Deciding what each audience must *not* see is its own kind of judgment call — one that depends on reading organizational dynamics, trust levels, and political risk well enough that no AI could make the call independently. The registry exists precisely because that decision has to happen before the AI runs, not after.

---

## Try This Yourself

There's a live page with a one-click **Copy Prompt** button — grabs the full prompt plus data, ready to paste into Claude, GPT-4, or Gemini.

›︎ [Open Project Signal Prompt Copy page](https://zinaleeHQ.github.io/project-signal/)

It pauses at a judgment checkpoint before the final phase, same as the others. That pause is the point.

---

## ↳︎ Portfolio Navigation

Project 3 of 4 — the communication layer wrapped around everything Horizon and Clarity built.

| Project | Question Answered | Methodology |
|---|---|---|
| [Project Horizon](https://github.com/zinaleeHQ/project-horizon) | What do we build, and when? | SAFe · WSJF |
| [Project Clarity](https://github.com/zinaleeHQ/project-clarity) | How do we change how people actually work? | Lean · DMAIC |
| **Project Signal** (this repo) | How do we keep every stakeholder aligned? | Stakeholder Intelligence · Audience Mapping |
| [Project Vista](https://github.com/zinaleeHQ/project-vista) | How do we give every stakeholder self-service visibility? | KPI Governance · Data Architecture |

[**← Back to Portfolio Overview**](https://github.com/zinaleeHQ/zinaleeHQ/)

---

*Portfolio case study · Built from publicly available information · No proprietary data used · June 2026*
