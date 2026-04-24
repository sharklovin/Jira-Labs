# TICKET NOTE - PIR - Email Major Incident - April 2026
## Post-Incident Review | Linked to SUP1-26

---

**Ticket Title:** PIR - Email Major Incident - April 2026
**Linked Incident:** SUP1-26 - MAJOR INCIDENT - Email Service Down - All 300 Users Affected
**Type:** Post-Incident Review
**Status:** Completed
**PIR Owner:** Nnamso Mkpong
**Participants:** Nnamso Mkpong (Coordinator), Maria (Infrastructure Lead), Security Team, Cloud Team
**Incident Date:** 23 April 2026
**PIR Completed:** 23 April 2026 (within 24 hours of incident closure)

---

## 1. Incident Summary

On 23 April 2026 at 09:15, the company email service went down for all 300 users. No one could send or receive email. Investigation confirmed that a conditional access policy applied at 09:10 by an admin account had blocked Exchange Online access for the entire tenant. The policy was reverted at 09:58 and service was restored at 10:00. Total downtime was 45 minutes. No data loss occurred. All SLAs were met.

---

## 2. Timeline of Events

| Time | Event | Category |
|---|---|---|
| 09:10 | Conditional access policy applied by admin account without approval or staged rollout | Change |
| 09:15 | First user calls received - email service confirmed down for all users | Detection |
| 09:15 | SUP1-26 raised as P1 Critical - SLA clock started | Response |
| 09:20 | Initial sitrep posted as internal note - response team assembled | Communication |
| 09:22 | First customer communication sent - investigating, update in 30 minutes | Communication |
| 09:30 | DNS and MX records ruled out - attention moved to Azure AD | Investigation |
| 09:45 | Azure AD sign-in logs reviewed - conditional access policy change at 09:10 confirmed | Root Cause |
| 09:45 | Infrastructure Lead Maria begins policy revert | Remediation |
| 09:58 | Policy revert confirmed complete | Remediation |
| 10:00 | Email service confirmed restored | Resolution |
| 10:05 | Second customer communication sent - service restored, self-service steps provided | Communication |
| 10:15 | Incident closed - resolution documented, SLAs confirmed met | Closure |
| 10:30 | PIR raised and linked to SUP1-26 | Review |


---

## 3. Root Cause Analysis

**Root Cause Statement:**

An administrative change to conditional access policies was applied at 09:10 without validation testing, change approval, or staged rollout. The policy unintentionally blocked Exchange Online access for all users in the tenant simultaneously.

**Contributing Factors:**

| Factor | Detail |
|---|---|
| No approval workflow | The policy change was applied directly by an admin account without peer review or approval gate |
| No staged rollout | The policy was applied to all users simultaneously rather than to a pilot group first |
| No real-time alerting | No automated alert fired when authentication began failing at scale at 09:10 - detection relied on user calls at 09:15 |
| No change freeze period | The change was applied during core business hours rather than a scheduled maintenance window |



---

## 4. What Went Well

| Item | Assessment |
|---|---|
| Speed of incident detection | First call received within 5 minutes of the causative change |
| Response team assembly | Infrastructure Lead contacted and briefed within 10 minutes |
| Customer communication | Two timed updates sent at the right points - no SLA breach on first response |
| Diagnostic methodology | Systematic elimination of DNS, MX, and service health before identifying identity layer fault |
| Root cause identification | Azure AD logs correctly identified within 30 minutes of incident opening |
| Service restoration | Policy revert completed within 48 minutes of incident opening |
| SLA performance | All SLA targets met |

---

## 5. What Could Be Improved

| Area | Problem Identified | Risk if Unaddressed |
|---|---|---|
| Policy change validation | No validation before deployment | Next policy change could cause identical or longer outage |
| Staged rollout | Policy applied to all users simultaneously | 300-user impact when 10-user pilot would have caught the fault |
| Real-time alerting | 5-minute gap between policy applied and detection via user calls | Impact window could be longer if call volume was lower |
| Change management | No approval required for conditional access changes | Single admin can cause tenant-wide outage unilaterally |



---

## 6. Action Items

| Action Item | Owner | Due Date | Priority |
|---|---|---|---|
| Implement approval workflow for all conditional access policy changes | Security Team | 10 May 2026 | High |
| Enable automated alerting for bulk authentication failures across Exchange Online | Infra Team | 5 May 2026 | Critical |
| Introduce mandatory staged rollout policy for conditional access changes (pilot group first) | Cloud Team | 12 May 2026 | High |
| Document conditional access change procedure and add to IT change management policy | IT Manager | 17 May 2026 | Medium |
| Run tabletop exercise with response team using this incident as the scenario | Nnamso Mkpong | 24 May 2026 | Medium |

---

## 7. Preventive Controls Summary

Once all action items are complete, the following controls will be in place to prevent recurrence:

1. No conditional access policy can be deployed without a second approver sign-off
2. All policies must be deployed to a named pilot group and monitored for 30 minutes before tenant-wide rollout
3. Authentication failure rate alerting will fire within 2 minutes of a threshold breach, reducing detection time from 5 minutes to under 2 minutes
4. Conditional access changes will be documented in the change management log with ticket reference

---

## 8. PIR Completion Record

| Section | Status |
|---|---|
| Timeline of events | Complete |
| Root cause analysis | Complete |
| What went well | Complete |
| What could be improved | Complete |
| Action items with owners and due dates | Complete - 5 items raised |
| PIR linked to incident SUP1-26 | Confirmed |

**PIR Owner:** Nnamso Mkpong
**PIR Closed:** 23 April 2026
**Next review of action items:** 26 April 2026

---

*Post-Incident Review - SUP1-26*
*Major Incident Coordination - Jira Service Management*
*IT Support Portfolio - Nnamso Mkpong*
