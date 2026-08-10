# The PROCESS — How I Built This Project

*Zina Lee, Product Manager*

---

## Why This Project Exists

Horizon decided what to build. Clarity changed how people work. This one addresses a failure mode that quietly damages a PM's credibility more than almost anything else: the moment a risk materializes mid-sprint, and the instinct is to write one email and send it to everyone.

That email always fails somebody. Too technical for the CMO, too vague for the engineering VP, too soft for the CFO, too internal for the vendor, too alarming for the field team hearing rumors before they hear facts. Someone ends up unhappy. Someone else ends up underinformed. This project is the artifact proving I don't default to that email.

If you haven't read [the README](./README.md) yet, start there. This page goes deeper into the same reasoning, including the two design calls I didn't fully understand the weight of until I read the live output as an actual recipient would.

---

## The Strategic Decisions I Made

### Why the Stakeholder Registry Is a Structured File, Not a Sentence in the Prompt

This was the single most important design choice in the project. Write "remember, the CMO doesn't want technical detail" into a prompt as prose, and the AI treats it as a soft preference — something to weigh against everything else. Give it a structured registry instead, with explicit values like `technical_depth: 0` and `hard_omit: [API details, sprint velocity, team capacity]`, and it gets treated as a rule that filters the output before drafting even starts. The gap in output quality between those two approaches is significant, and it held up every time I tested it.

It's also reusable in a way prose never is. A CMO's communication preferences at a healthcare org are fairly stable over time. Run this same engine next sprint against a completely different risk, and the registry doesn't need to change at all — only the sprint data does. That's what good system design actually looks like: the thing that costs effort to build gets used more than once.

### Why Consistency Enforcement Got Its Own Layer

The most dangerous failure mode in a five-audience system isn't saying the wrong thing to one person. It's saying two slightly different true things to two people who later compare notes. "Resolution by end of sprint" and "resolution within 5 business days" might describe the exact same date, but they don't read the same way — and a CFO who hears the second version might reasonably think the timeline just slipped. That kind of inconsistency erodes trust faster than the underlying risk ever could.

So consistency enforcement runs as an explicit third layer, after all five outputs are drafted and before any of them are finalized — checking every fact, timeline, and figure against the other four. A mismatch is treated as a blocker, not a style note worth a second look later.

### Why the Vendor Escalation Belongs in This Set at All

Most PM communication portfolios show upward communication to executives and downward communication to teams. Almost none show the lateral relationship — vendor management — even though delivery usually depends on it just as much.

The vendor notice is the hardest output in this set to get right, because it has to reference SLA terms without sounding like a legal threat, establish accountability without damaging a relationship the team still depends on, and ask for a specific remedy without demanding something the vendor genuinely can't deliver. Including it here is a deliberate statement that PM communication isn't just about managing up. It's about managing the entire ecosystem delivery actually runs on.

### Why the Field FAQ Reads Nothing Like the Other Four

Every other output in this set is built around what the audience needs to *know*. The field FAQ is built around what the clinician needs to *do* — which, in this specific risk, is nothing at all. The whole point of that document is preventing unnecessary action, not delivering information, and that's a genuinely different writing objective requiring a genuinely different structure. A narrative brief would leave a field clinician wondering what any of it means for them personally. A direct FAQ with "no action required" as the answer to every question gives them permission to stop reading and get back to actual patients.

---

## How I Directed the AI, and Why This Prompt Is the Hardest of the Three

The AI generated all five outputs from the structured data inputs, applied the audience logic once I'd defined the registry parameters, enforced consistency once I'd defined what consistency actually meant in this context, and formatted each output in its correct structural form — narrative, bullets, table, formal notice, FAQ.

What I owned was every judgment call that carries real risk if it's wrong: which five audiences mattered for this specific risk and why, every parameter in the registry, the decision to make consistency enforcement its own explicit layer rather than trusting the drafting step to self-correct, the call to include the vendor escalation at all and how firm to make it, and the entire framing of every document a stakeholder would actually read.

Horizon's prompt is analytical — score these items against a fixed framework. Clarity's is generative — analyze this data and produce one new artifact. This one is something harder than either: contextually adaptive, meaning it has to take one set of facts and produce five structurally different outputs that all still have to agree with each other. That requires the AI to hold two models at once — the underlying truth, and five different audience filters — without losing the thread between them. Analysis is hard. Generation is hard. Doing both at once, five times, without contradiction, is a different order of difficulty.

---

## What the Live Run Actually Showed Me

The engine passed every consistency check on the first run — clinical impact, financial figures, and timelines all agreed across all five outputs. Technically, it did exactly what it was built to do.

That's the floor. It's not the ceiling, and the live run made the gap between those two things obvious in a way the mock never could have.

None of what the registry specifies accounts for the actual people receiving these messages. It doesn't know the CMO has been quietly nervous about this rollout for two months and needed a different calibration of "calm" than the default setting called for. It doesn't know the CFO has been asking pointed questions about DSO exposure since Q1, which means a number that reads as reassuring on the page might land as a fresh alarm given the history behind it. It doesn't know the VP of Engineering is already having a difficult sprint with their team, so a resource-confirmation request needed to be framed as a conversation, not an assignment handed down. It doesn't know a specific field lead has been skeptical of every single update for six weeks running, and one wrong sentence in their FAQ generates three phone calls before lunch.

None of that lives in a data file, and none of it can. It lives in whoever's been paying attention to these relationships over time — which is, functionally, the actual job.

The vendor escalation carries the highest stakes of the five, because it has real contractual weight and the narrowest acceptable tone register of anything in the set. Too soft, and the SLA obligation doesn't register. Too sharp, and a relationship the team still depends on takes damage before the technical fix is even done. But every output in this set carries consequences if it misreads the room — the vendor notice is just where that's most visible. The AI produces five drafts in parallel, with zero context about any of the humans receiving them. The PM reads them one at a time, with full context about each person. That gap is where the actual judgment lives, and no registry parameter closes it.

---

## What I'd Do Differently With Real Data

The registry parameters here are built from role assumptions, not from actual conversations — a real CMO might want more financial detail than I've given them credit for; a real CFO might be more technically fluent than the default assumption allows. The fix is simple and almost embarrassingly obvious: one short conversation with each stakeholder before a crisis hits, validating how they actually want to receive difficult news, rather than guessing on their behalf.

That validation belongs in Week 1 of any new engagement, not mid-crisis. The worst possible moment to learn how your CMO prefers to receive bad news is while you're actively delivering it — the registry should be a standard onboarding artifact, built calmly, long before it's ever needed under pressure.

And the registry should improve over time instead of staying static. After any real communication goes out, it's worth noting whether the recipient asked a follow-up question that should have already been answered in the original message — because that follow-up is a signal the registry's parameters need adjusting, not just a one-off surprise to shrug off.

---

*This document reflects my actual decision-making process in building this project.*

*[Back to README](./README.md)*
