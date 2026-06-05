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