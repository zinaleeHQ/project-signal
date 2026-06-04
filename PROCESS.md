# PROCESS.md — How I Built This Project

*By Zina Lee, Enterprise Product Manager*

---

## Why This Project Exists

Project Horizon decided what to build. Project Clarity changed how people work. Project Signal addresses the third failure mode that kills enterprise PM credibility: **the moment a risk materializes mid-sprint and the PM doesn’t know how to talk to five different people about it at the same time.**

Every PM has been in this situation. The Commure API breaks. The CFO is asking about DSO. The CMO wants to know if patients are affected. The VP of Engineering wants the root cause. The vendor needs to be held accountable. The field team is hearing rumors.

Most PMs write one email. It’s either too technical or too vague. It either alarmed the CMO unnecessarily or failed to give the engineering team the specificity they needed to act. Either way, someone is unhappy and someone is underinformed.

This project demonstrates that I don’t do that. And I have the artifact to prove it.

---

## The Strategic Decisions I Made

### Why the Stakeholder Registry Is a Structured Data File

The most important design decision in this project was treating the stakeholder registry as a **data input**, not as narrative context inside the prompt.

When you say in a prompt “remember the CMO doesn’t want technical details,” the AI treats that as a soft preference. When you give the AI a structured registry with explicit parameters — `technical_depth: 0`, `word_count_ceiling: 150`, `hard_omit: [API details, sprint velocity, team capacity]` — it treats those as rules. The difference in output quality is significant.

It also makes the registry reusable. The stakeholder parameters for a CMO at a healthcare organization are largely stable. If this same communication engine runs next sprint with a different risk, the registry doesn’t change. Only the sprint status data changes. That’s good system design.

### Why Consistency Enforcement Is a Separate Prompt Layer

The most dangerous failure mode of a multi-audience communication engine isn’t saying the wrong thing to one audience. It’s saying slightly different things to two audiences who then compare notes.

If the CMO briefing says “resolution expected by end of sprint” and the CFO update says “resolution expected within 5 business days” — those might mean the same thing, but they don’t read the same way. The CFO hears “five days” as longer than “end of sprint.” That inconsistency erodes trust faster than the original risk does.

Building consistency enforcement as an explicit third layer — a validation step that runs after all five outputs are drafted and before any are finalized — addresses this directly. The AI is instructed to treat a consistency violation as a blocker, not a style note.

### Why I Included the Vendor Escalation

Most PM communication portfolios show upward communication (to executives) and downward communication (to teams). Almost none show lateral vendor management communication.

The vendor escalation notice is the hardest communication in this set to get right. It has to be firm enough to establish accountability without being aggressive enough to damage a relationship you depend on. It has to reference SLA terms without sounding like a legal threat. It has to ask for a specific remedy without demanding something the vendor can’t deliver.

Including it here demonstrates that I understand PM communication isn’t just about managing up — it’s about managing the full ecosystem of relationships that delivery depends on.

### Why the Field FAQ Uses Plain Language Instead of a Summary

Every other output in this set is built around what the stakeholder needs to *know*. The field FAQ is built around what the clinician needs to *do* — which is nothing. The entire communication is designed to prevent unnecessary action, not to inform.

That’s a different writing objective than the other four outputs, and it requires a different structure. A narrative brief or a bullet summary would leave a field clinician wondering what it means for them. A direct FAQ with a “no action required” answer to every question gives them permission to stop reading and get back to patients.

---

## How I Directed the AI

### What the AI Did
- Generated the five output communications from the structured data inputs
- Applied audience variable logic once I defined the registry parameters
- Enforced consistency across outputs once I defined what consistency means
- Formatted each output in its correct structural form (narrative / bullets / table / formal notice / FAQ)

### What I Decided
- The five stakeholder audiences and why each one matters for this specific risk
- The communication parameters in the stakeholder registry (technical depth, word count, hard omits)
- The decision to make consistency enforcement a separate explicit layer
- The decision to include the vendor escalation (and how to frame it)
- Why the field FAQ needed a different objective than the other four outputs
- The framing and narrative of every public-facing document

### Why This Is the Most Sophisticated Prompt of the Three

The WSJF prompt (Project Horizon) is analytical: score these items against a framework.
The process analysis prompt (Project Clarity) is generative: analyze this data and produce a new artifact.
This prompt is **contextually adaptive**: take the same data and produce five structurally different outputs that must all be internally consistent.

Contextual adaptation is a harder prompt engineering challenge than either analysis or generation. It requires the AI to maintain a clear model of both the underlying facts AND the audience’s context simultaneously — and to apply different filters to the same information without losing the thread.

---

## What I’d Do Differently With Real Data

**1. Validate the stakeholder registry with the stakeholders themselves.**
The communication parameters I defined are based on role assumptions. A real CMO might actually want more financial detail than I’ve given them. A real CFO might be more technically fluent than the registry assumes. Validating the registry through one conversation with each stakeholder before a crisis hits is the kind of relationship-building that makes the engine work when it matters.

**2. Build the registry before the first sprint, not during a risk event.**
The worst time to figure out how your CMO likes to receive bad news is while you’re delivering it. The stakeholder registry should be built in Week 1 of any new product engagement — as a standard PM onboarding artifact, not a crisis response tool.

**3. Add a feedback loop.**
After each real communication, note whether the recipient asked follow-up questions that should have been answered in the original output. Those questions are a signal that the registry parameters need adjustment. A registry that improves over time is dramatically more valuable than one that stays static.

---

*This document reflects my actual decision-making process in building this project.*
*[Back to README](./README.md)*