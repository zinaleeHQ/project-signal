# Data: Risk Register

**Sprint:** 2 of 3 Â· Active as of Day 10
**Owner:** PM Â· Updated at sprint close

---

## Active Risks

| Risk ID | Description | Probability | Impact | Status | Owner | Mitigation |
|---|---|---|---|---|---|---|
| **RISK-002** | platform v2.4.1 undocumented API parameter change blocking Epic 2 billing dashboard integration | Medium | High | ð´ Active â In Mitigation | Data Engineer + PM | Integration layer field mapping patch Â· ETA Thursday EOD Â· QA Friday Â· Deploy Friday maintenance window |
| RISK-003 | HL7 schema drift identified at St. Francis Health System â intermittent batch transfer mismatches | Low | Medium | ð¡ Monitoring | Data Engineer | Root cause identified Sprint 2 Day 9. No active failure. Scheduled Sprint 3 investigation. |
| RISK-004 | QA team capacity at 95% through Friday â limited buffer for secondary issues in RCM platform patch | Medium | Medium | ð¡ Watching | QA Lead + Scrum Master | Sprint buffer allocated. Escalation trigger: if secondary integration issues found during patch QA, VP Engineering notified immediately for resource decision. |

---

## Closed Risks This Sprint

| Risk ID | Description | Resolution | Closed |
|---|---|---|---|
| RISK-001 | Partner Health System A cure notice â HL7 data drops | Translation layer patch deployed Â· Zero data drops confirmed over 72-hour monitoring window Â· Cure notice response delivered | Sprint 2 Day 7 |

---

## Risk Escalation Triggers

The following conditions automatically escalate the RISK-002 status to **Critical** and trigger a revised stakeholder communication cycle:

- QA identifies secondary integration issues during RCM platform patch validation
- RCM platform fails to acknowledge the escalation notice within 24 hours
- Friday deployment is missed for any reason
- DSO exposure duration extends beyond 6 business days

---

*Risk register is a structured input to the stakeholder reporting prompt Â· Provides context for what to escalate vs. what to monitor*