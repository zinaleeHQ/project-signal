# Run This Prompt — Project Signal

**Project:** Stakeholder Communication Engine (AI-Assisted Multi-Audience Communication)
**Framework:** Audience Intelligence · Multi-Output Communication Design · Consistency Enforcement
**What you'll produce:** Five audience-appropriate communications from one source of truth — CMO, CFO, VP Engineering, RCM vendor, and Clinical Field Lead

---

## How to Use This File

This file is self-contained. Copy everything in the **PROMPT** section below and paste it directly into any capable AI assistant (Claude, ChatGPT, Gemini). All data is embedded — no additional files needed.

The AI will work through three sequential layers:
1. Context Ingestion — build the Shared Fact Baseline from all three inputs
2. Audience Variable Logic — generate five outputs, each adapted for its recipient
3. Consistency Enforcement — validate all outputs before finalizing

**After Layer 2 is complete, the AI will pause and ask your permission before proceeding to Layer 3.** That pause is intentional — it's where your PM judgment matters most.

### What to Do After Copying
1. Paste into your AI of choice
2. Let it run through **Layer 1** (Shared Fact Baseline) — review it; if any fact is wrong, stop and correct it in INPUT_A before continuing
3. Let it run through **Layer 2** (all five draft outputs) — this is the **evaluation checkpoint**
4. Read each output **as the recipient** — not as the PM who knows the full context
5. When satisfied, tell the AI to proceed to **Layer 3** (consistency validation)

---

## PROMPT (copy everything from here to the end of this file)

---

# Prompt: AI-Assisted Stakeholder Communication Engine

**Version:** 1.0
**Framework:** Audience Intelligence · Multi-Output Communication Design
**Author:** Zina Lee, Product Manager

---

## Prompt Architecture Overview

This prompt executes in three sequential layers:

1. **Layer 1 — Context Ingestion:** Parse and model all input data
2. **Layer 2 — Audience Variable Logic:** Generate five outputs with audience-specific parameters
3. **Layer 3 — Consistency Enforcement:** Validate all outputs against a shared fact baseline before finalizing

**Layer 3 is not optional.** A multi-audience communication engine that produces inconsistent outputs is worse than no engine at all. Treat a consistency violation as a blocker.

---

## 🟡 SYSTEM CONTEXT

You are an enterprise stakeholder communication assistant supporting a Product Manager at a multi-site healthcare operations organization. You have been given:

- Raw sprint status data (single source of truth)
- A stakeholder registry defining audience parameters for five recipients
- An active risk register with escalation context

Your role is to generate five audience-appropriate communications from a single source of truth —"maintaining factual consistency across all outputs while adapting format, depth, tone, and emphasis for each audience.

**Critical behavioral rules:**
- Every fact in every output must be traceable to INPUT_A (sprint status)
- No output may introduce a fact not present in INPUT_A
- No two outputs may contradict each other on any shared fact
- Audience parameters in INPUT_B are rules, not preferences — treat hard omits as absolute
- A word count ceiling is a ceiling, not a target — stop when the message is complete
- The goal of each output is not to inform — it is to produce a specific reaction in a specific reader. Design for the reaction, not the information transfer.

---

## 📥 INPUT DATA SOURCES

**INPUT_A: Sprint Status (Raw)**
```
# Data: Sprint Status — Raw

**Sprint:** 2 of 3 · Day 10 of 10
**Status as of:** End-of-sprint review
**Source:** PM synthesis from engineering standup, RCM platform vendor communication, and billing system report

> This is the unfiltered source of truth. All five stakeholder communications must draw from this document consistently. No communication may introduce a fact not present here, and no communication may contradict another on any fact present here.

---

## Epic Status Summary

| Epic | Title | Sprint 2 Status | Story Points Complete | Notes |
|---|---|---|---|---|
| Epic 1 | HL7 Data Mapping Upgrade | ✅ On Track | 34 / 38 SP | Final regression testing in progress. On schedule for Sprint 2 close. Partner Health System A cure notice response delivered Day 7. |
| Epic 2 | Billing Reconciliation Dashboard | ⚠️ At Risk | 14 / 34 SP | Blocked Day 8. See risk detail below. |
| Item 05C | SOC 2 Re-Certification | ✅ Complete | 5 / 5 SP | Closed Day 6. |
| Item 13 | HIPAA Audit Log Gap | ✅ Complete | 5 / 5 SP | Closed Day 5. |

---

## Active Risk: RCM platform API Parameter Change

| Field | Detail |
|---|---|
| **Risk ID** | RISK-002 |
| **Identified** | Sprint 2, Day 8 |
| **Root Cause** | platform v2.4.1 release introduced an undocumented breaking change to the modifier mapping parameter schema. The `dx_modifier_map` field was renamed to `dx_code_modifier` without release note documentation. Our integration layer was calling the deprecated field name, causing silent data validation failures. |
| **Clinical Impact** | **Zero.** Epic 1 (HL7) is fully isolated from the RCM platform billing pipeline. No clinical workflow, patient data, or charge submission for autonomous cases is affected. |
| **Financial Impact** | If unresolved before Sprint 3 Friday cutover: estimated 4–6 business day delay in claims processing for new manual intervention cases. Estimated DSO exposure: $85,000–$120,000 depending on case volume. Existing claims pipeline is unaffected. |
| **Technical Resolution** | EMIS team has identified the fix: update integration layer field mapping from deprecated to current parameter name. Estimated effort: 1 engineer · 1.5 days. Patch ready for QA Thursday. |
| **Timeline** | Patch complete by Thursday EOD · QA Thursday–Friday · Deployment Friday maintenance window · On track for Sprint 3 start. |
| **Vendor Status** | RCM platform has been notified. No response received yet. SLA terms require acknowledgment within 24 hours and root cause documentation within 72 hours. |
| **Probability of Friday Resolution** | High (85%) — contingent on QA finding no secondary issues in the integration layer. |

---

## Secondary Risks (Monitoring Only)

| Risk | Status | Action |
|---|---|---|
| HL7 schema drift at St. Francis (RISK-003) | Low probability · Monitoring | Root cause identified Sprint 2 Day 9. No active failure. Scheduled for Sprint 3 investigation. |
| QA capacity constraint (RISK-004) | Medium probability · Watching | QA team at 95% capacity through Friday. Sprint buffer allocated. No escalation needed unless secondary issues found in RCM platform patch. |

---

## Team Capacity

| Role | Sprint 2 Utilization | Sprint 3 Availability |
|---|---|---|
| Data Engineers (x2) | 100% — Epic 1 + RCM platform patch | Full capacity at Sprint 3 start |
| Full-Stack Devs (x2) | 72% — Epic 2 blocked Day 8 | Full capacity at Sprint 3 start |
| QA Engineers (x2) | 95% — Epic 1 regression + patch QA | Full capacity at Sprint 3 start |
| Tech Lead | 90% | Full capacity at Sprint 3 start |

---

*This document is the single source of truth for all Sprint 2 stakeholder communications. See [stakeholder-registry.md](./stakeholder-registry.md) for audience parameters.*
```

**INPUT_B: Stakeholder Registry**
```
# Data: Stakeholder Registry

**Purpose:** Defines communication parameters for each stakeholder audience. Loaded into the prompt engine as structured input — these are rules, not preferences.

---

## Registry

### 1. Chief Medical Officer

| Parameter | Value |
|---|---|
| **Format** | Narrative prose brief |
| **Word Count Ceiling** | 150 words maximum |
| **Technical Depth** | 0 — zero jargon. No API references, sprint terminology, or system names. |
| **Lead With** | Clinical operations status — are patients or clinicians affected? |
| **Primary Metric** | Clinical continuity (affected / not affected) |
| **Hard Omit** | API parameter details · Sprint velocity · Story points · Vendor SLA terms · Team capacity |
| **Single Ask** | Awareness only — no action required unless resolution fails |
| **Tone** | Calm, confident, brief. CMO should finish reading and feel informed, not alarmed. |

---

### 2. Chief Financial Officer

| Parameter | Value |
|---|---|
| **Format** | Bullet summary + one financial figure |
| **Word Count Ceiling** | 100 words maximum |
| **Technical Depth** | 1 — may reference “billing integration” but not APIs, parameters, or code |
| **Lead With** | DSO exposure window and dollar range |
| **Primary Metric** | Days Sales Outstanding (DSO) impact in dollars |
| **Hard Omit** | Root cause technical detail · Sprint terminology · Team capacity · Vendor relationship dynamics |
| **Single Ask** | Awareness. No CFO action required unless Friday resolution fails — state this explicitly. |
| **Tone** | Direct, quantified, no hedging on the number. |

---

### 3. VP of Engineering

| Parameter | Value |
|---|---|
| **Format** | Status table + technical detail + action items with owners |
| **Word Count Ceiling** | No limit — completeness over brevity |
| **Technical Depth** | 9 — full technical detail including field names, parameter schema, root cause chain |
| **Lead With** | Epic status table — what is on track, what is at risk, what is blocked |
| **Primary Metric** | Story points complete · Blocker resolution ETA · QA risk |
| **Hard Omit** | Executive narrative framing · Clinical impact language · Financial impact language |
| **Single Ask** | Confirm QA resource allocation for Thursday–Friday patch validation |
| **Tone** | Peer-to-peer. Factual, specific, no softening language. |

---

### 4. RCM Platform Vendor

| Parameter | Value |
|---|---|
| **Format** | Formal escalation notice |
| **Word Count Ceiling** | 250 words maximum |
| **Technical Depth** | 5 — sufficient technical specificity to establish the incident clearly, without internal system detail |
| **Lead With** | The undocumented breaking change as the triggering event |
| **Primary Metric** | SLA compliance: 24-hour acknowledgment · 72-hour root cause documentation |
| **Hard Omit** | Internal team capacity · Financial impact dollar figures · Internal escalation status |
| **Single Ask** | Written acknowledgment · Root cause confirmation · SLA credit review |
| **Tone** | Professional and firm. Establishes accountability without being adversarial. Relationship must survive this. |

---

### 5. Clinical Operations Field Lead

| Parameter | Value |
|---|---|
| **Format** | Plain-language FAQ |
| **Word Count Ceiling** | 5 questions maximum · 1–2 sentences per answer |
| **Technical Depth** | 0 — zero jargon. No system names, no financial figures, no sprint references. |
| **Lead With** | “Will anything change for my clinicians?” — answer is No. |
| **Primary Metric** | Workflow impact (yes / no) |
| **Hard Omit** | Everything except clinical workflow impact and timeline |
| **Single Ask** | No action required. Permission to stop reading and return to clinical operations. |
| **Tone** | Reassuring, plain, brief. Every answer should make the reader feel less concerned, not more. |

---

*Loaded as structured logic rules in the stakeholder reporting prompt · See [stakeholder-reporting-prompt.md](../prompts/stakeholder-reporting-prompt.md)*
```

**INPUT_C: Risk Register**
```
# Data: Risk Register

**Sprint:** 2 of 3 · Active as of Day 10
**Owner:** PM · Updated at sprint close

---

## Active Risks

| Risk ID | Description | Probability | Impact | Status | Owner | Mitigation |
|---|---|---|---|---|---|---|
| **RISK-002** | platform v2.4.1 undocumented API parameter change blocking Epic 2 billing dashboard integration | Medium | High | 🔴 Active — In Mitigation | Data Engineer + PM | Integration layer field mapping patch · ETA Thursday EOD · QA Friday · Deploy Friday maintenance window |
| RISK-003 | HL7 schema drift identified at St. Francis Health System — intermittent batch transfer mismatches | Low | Medium | 🟡 Monitoring | Data Engineer | Root cause identified Sprint 2 Day 9. No active failure. Scheduled Sprint 3 investigation. |
| RISK-004 | QA team capacity at 95% through Friday — limited buffer for secondary issues in RCM platform patch | Medium | Medium | 🟡 Watching | QA Lead + Scrum Master | Sprint buffer allocated. Escalation trigger: if secondary integration issues found during patch QA, VP Engineering notified immediately for resource decision. |

---

## Closed Risks This Sprint

| Risk ID | Description | Resolution | Closed |
|---|---|---|---|
| RISK-001 | Partner Health System A cure notice — HL7 data drops | Translation layer patch deployed · Zero data drops confirmed over 72-hour monitoring window · Cure notice response delivered | Sprint 2 Day 7 |

---

## Risk Escalation Triggers

The following conditions automatically escalate the RISK-002 status to **Critical** and trigger a revised stakeholder communication cycle:

- QA identifies secondary integration issues during RCM platform patch validation
- RCM platform fails to acknowledge the escalation notice within 24 hours
- Friday deployment is missed for any reason
- DSO exposure duration extends beyond 6 business days

---

*Risk register is a structured input to the stakeholder reporting prompt · Provides context for what to escalate vs. what to monitor*
```

---

## 🔴 LAYER 1: CONTEXT INGESTION

### Ingestion Instructions

1. Parse INPUT_A and extract: Epic status for each item · Root cause of active risk · Clinical impact (explicit) · Financial impact (explicit) · Resolution timeline · Probability of on-time resolution · Team capacity status

2. Parse INPUT_B and build an audience model for each of the five stakeholders: format · depth dial · word count ceiling · lead topic · hard omit list · desired reaction

3. Parse INPUT_C and identify: which risks require active communication vs. monitoring only · escalation triggers that would change the communication content

4. Build a **Shared Fact Baseline** — a minimal set of facts that all five outputs must agree on:
   - Is clinical operations affected? (Y/N + detail)
   - What is the financial exposure? (range)
   - What is the resolution timeline? (specific dates)
   - What is the probability of on-time resolution? (stated clearly)
   - Is any stakeholder action required? (Y/N per audience)

### Layer 1 Output
Output the Shared Fact Baseline before generating any communications. This becomes the consistency reference for Layer 3.

---

## 🟠 LAYER 2: AUDIENCE VARIABLE LOGIC

Generate all five communications in sequence. For each output:

1. Load the audience parameters from INPUT_B for that stakeholder
2. Apply the technical depth dial to every sentence — if a sentence contains terminology above the dial setting, rewrite it
3. Apply the hard omit list — if a sentence contains an omitted topic, remove it entirely (do not replace with vague language)
4. Lead with the specified topic — the first sentence must address the lead topic
5. End with the single ask — every output must close with exactly one clear request or action item
6. Respect the word count ceiling — stop when complete

### Output 1: Chief Medical Officer Briefing

**Target reaction:** CMO reads this, understands clinical operations are unaffected, and does not need to ask a follow-up question.

```
## Sprint Update — CMO Briefing
[Date]

[Narrative prose · 150 words max · Technical depth: 0]
```

### Output 2: Chief Financial Officer Update

**Target reaction:** CFO reads this, knows the DSO number, knows the resolution date, and knows what triggers an escalation to their level.

```
## Sprint Update — CFO Summary
[Date]

[Bullets + one financial figure · 100 words max · Technical depth: 1]
```

### Output 3: VP of Engineering Standup

**Target reaction:** VP reads this, has full situational awareness, knows exactly what needs to happen and who owns it, and has one clear decision to confirm.

```
## Sprint 2 Close — Engineering Status
[Date]

[Status table + technical detail + action items · No word limit · Technical depth: 9]
```

### Output 4: Vendor Escalation Notice

**Target reaction:** RCM platform reads this, understands it is a formal SLA event, knows exactly what is being requested, and cannot reasonably claim they were not notified.

```
## Formal Escalation Notice — API Release Documentation Failure
[Date]

[Formal structure · 250 words max · Technical depth: 5]
```

### Output 5: Clinical Operations Field FAQ

**Target reaction:** Field lead reads this, confirms nothing is changing for their clinicians, and returns to clinical operations without forwarding the message or asking a follow-up.

```
## Quick Update — Clinical Operations Team
[Date]

[FAQ format · 5 questions max · Technical depth: 0]
```

---


---

⏸️ **PAUSE POINT — PM JUDGMENT CHECKPOINT**

Before executing Layer 3, stop and review the five draft communications above.

For each output, ask yourself: **Am I reading this as the recipient, not the sender?**

- Does the CMO briefing make a busy medical officer feel informed, not alarmed?
- Does the CFO summary give a financial leader a number they can use?
- Does the engineering standup give the VP exactly what they need to act — nothing more?
- Does the vendor notice establish accountability without damaging the relationship?
- Does the field FAQ let the field lead confirm "nothing for my clinicians to do" in 30 seconds?

If any output would land wrong in the actual relationship — even if the facts are correct — revise it before proceeding.

**When you're satisfied with all five drafts, reply "proceed" to run the Layer 3 consistency check.**

---

## 🟢 LAYER 3: CONSISTENCY ENFORCEMENT

After all five outputs are drafted, perform the following validation before finalizing:

### Consistency Checklist

| Check | Question |
|---|---|
| Clinical impact | Do all five outputs agree on whether clinical operations are affected? |
| Financial exposure | Do the CMO and CFO outputs reference a consistent financial framing (even if CFO has more detail)? |
| Resolution timeline | Does every output that references a timeline use the same dates or date ranges? |
| Resolution probability | Does every output that references likelihood use consistent language (not “likely” in one and “expected” in another if they imply different probabilities)? |
| Stakeholder action | Does every output correctly state whether action is required from that recipient? |

### Consistency Failure Protocol
If any check fails:
1. Identify which output(s) contain the inconsistency
2. Determine which version is correct based on INPUT_A
3. Revise the inconsistent output(s)
4. Re-run the consistency checklist
5. Do not finalize until all checks pass

### Final Output
After consistency validation, output all five communications in final form, preceded by a brief consistency confirmation note.

---

*Prompt Version 1.0 · Framework: Audience Intelligence · Built June 2026*
*See [PROCESS.md](../PROCESS.md) for design decisions behind this prompt architecture.*