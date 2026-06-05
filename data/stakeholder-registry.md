# Data: Stakeholder Registry

**Purpose:** Defines communication parameters for each stakeholder audience. Loaded into the prompt engine as structured input â these are rules, not preferences.

---

## Registry

### 1. Chief Medical Officer

| Parameter | Value |
|---|---|
| **Format** | Narrative prose brief |
| **Word Count Ceiling** | 150 words maximum |
| **Technical Depth** | 0 â zero jargon. No API references, sprint terminology, or system names. |
| **Lead With** | Clinical operations status â are patients or clinicians affected? |
| **Primary Metric** | Clinical continuity (affected / not affected) |
| **Hard Omit** | API parameter details Â· Sprint velocity Â· Story points Â· Vendor SLA terms Â· Team capacity |
| **Single Ask** | Awareness only â no action required unless resolution fails |
| **Tone** | Calm, confident, brief. CMO should finish reading and feel informed, not alarmed. |

---

### 2. Chief Financial Officer

| Parameter | Value |
|---|---|
| **Format** | Bullet summary + one financial figure |
| **Word Count Ceiling** | 100 words maximum |
| **Technical Depth** | 1 â may reference âbilling integrationâ but not APIs, parameters, or code |
| **Lead With** | DSO exposure window and dollar range |
| **Primary Metric** | Days Sales Outstanding (DSO) impact in dollars |
| **Hard Omit** | Root cause technical detail Â· Sprint terminology Â· Team capacity Â· Vendor relationship dynamics |
| **Single Ask** | Awareness. No CFO action required unless Friday resolution fails â state this explicitly. |
| **Tone** | Direct, quantified, no hedging on the number. |

---

### 3. VP of Engineering

| Parameter | Value |
|---|---|
| **Format** | Status table + technical detail + action items with owners |
| **Word Count Ceiling** | No limit â completeness over brevity |
| **Technical Depth** | 9 â full technical detail including field names, parameter schema, root cause chain |
| **Lead With** | Epic status table â what is on track, what is at risk, what is blocked |
| **Primary Metric** | Story points complete Â· Blocker resolution ETA Â· QA risk |
| **Hard Omit** | Executive narrative framing Â· Clinical impact language Â· Financial impact language |
| **Single Ask** | Confirm QA resource allocation for ThursdayâFriday patch validation |
| **Tone** | Peer-to-peer. Factual, specific, no softening language. |

---

### 4. RCM Platform Vendor

| Parameter | Value |
|---|---|
| **Format** | Formal escalation notice |
| **Word Count Ceiling** | 250 words maximum |
| **Technical Depth** | 5 â sufficient technical specificity to establish the incident clearly, without internal system detail |
| **Lead With** | The undocumented breaking change as the triggering event |
| **Primary Metric** | SLA compliance: 24-hour acknowledgment Â· 72-hour root cause documentation |
| **Hard Omit** | Internal team capacity Â· Financial impact dollar figures Â· Internal escalation status |
| **Single Ask** | Written acknowledgment Â· Root cause confirmation Â· SLA credit review |
| **Tone** | Professional and firm. Establishes accountability without being adversarial. Relationship must survive this. |

---

### 5. Clinical Operations Field Lead

| Parameter | Value |
|---|---|
| **Format** | Plain-language FAQ |
| **Word Count Ceiling** | 5 questions maximum Â· 1â2 sentences per answer |
| **Technical Depth** | 0 â zero jargon. No system names, no financial figures, no sprint references. |
| **Lead With** | âWill anything change for my clinicians?â â answer is No. |
| **Primary Metric** | Workflow impact (yes / no) |
| **Hard Omit** | Everything except clinical workflow impact and timeline |
| **Single Ask** | No action required. Permission to stop reading and return to clinical operations. |
| **Tone** | Reassuring, plain, brief. Every answer should make the reader feel less concerned, not more. |

---

*Loaded as structured logic rules in the stakeholder reporting prompt Â· See [stakeholder-reporting-prompt.md](../prompts/stakeholder-reporting-prompt.md)*