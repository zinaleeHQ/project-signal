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