## JIRA - Simulate a Major Incident Response Using Jira

**Platform:** Jira Service Management
**Priority:** Critical
**Lab Type:** Flagship Portfolio Piece
**Author:** Nnamso Mkpong
**Domain:** IT Service Management | Major Incident Coordination
**Environment:** Jira Service Management — Cloud | Project: Support-1
**Completed:** April 2026

---

## Objective

Simulate a P1 major incident in Jira Service Management, coordinate the response across multiple teams using issue links and comments, document each phase of the incident lifecycle, and produce a post-incident review summary.

---

## Business Scenario

> **Ticket Reference:** SUP1-26 | **Severity:** P1 Critical | **Date:** Tuesday, 23 April 2026 | **Time:** 09:15

At 09:15 on a Tuesday morning, the company email service went down for all 300 users. No one could send or receive email. The Microsoft 365 status page showed no outage, meaning the fault was internal. The service desk phone lines lit up immediately. As the major incident coordinator, the responsibility fell to manage the Jira ticket from first call through to a post-incident review, coordinate between the infrastructure team and Microsoft escalation team, keep all 300 affected users informed throughout, and produce a formal post-incident review within 24 hours. Total downtime: 45 minutes.

---

## Environment

| Component | Detail |
|---|---|
| Platform | Jira Service Management — Cloud |
| Project | Support-1 |
| Issue Key | SUP1-26 (Incident) + PIR issue |
| Incident Coordinator | Nnamso Mkpong |
| Infrastructure Lead | Maria |
| Microsoft Escalation | Support ticket raised |
| Users Affected | 300 |
| Downtime | 45 minutes (09:15 to 10:00) |

---

## Diagnostic Stack

```
LAYER 1 — Service Validation
  └── Microsoft 365 status page checked → No outage shown
  └── Exchange Online admin centre → Service reported healthy
  └── Conclusion: fault is tenant-side, not Microsoft infrastructure

LAYER 2 — Network and DNS Investigation
  └── MX records verified → Intact
  └── DNS resolution tested → Healthy
  └── DHCP and routing ruled out
  └── Conclusion: not a DNS or network layer fault

LAYER 3 — Identity and Access Investigation
  └── Azure AD sign-in logs reviewed → Bulk failures at 09:10
  └── Conditional access policies audited → Policy change at 09:10
  └── Policy change blocked Exchange Online globally
  └── Root cause confirmed: misconfigured conditional access policy
```

---

## Incident Timeline

| Time | Event | Action |
|---|---|---|
| 09:10 | Conditional access policy applied by admin account | Change applied without staged rollout |
| 09:15 | Incident detected — first user calls received | SUP1-26 raised, P1 Critical, response team assembled |
| 09:20 | Initial sitrep posted as internal note | Microsoft 365 status checked, team assembled |
| 09:22 | First customer communication sent | All users notified: investigating, update in 30 minutes |
| 09:30 | DNS and MX records ruled out | Timeline comment added — Azure AD suspected |
| 09:45 | Root cause identified in Azure AD logs | Conditional access policy change confirmed at 09:10 |
| 09:58 | Policy reverted by infrastructure team | Service restoration initiated |
| 10:00 | Email service restored | User confirmation gathered |
| 10:05 | Second customer communication sent | All users notified: service restored, steps if issue persists |
| 10:15 | Incident resolved and closed | Resolution documented, SLA confirmed met |
| 10:30 | PIR issue created and linked to SUP1-26 | Post-incident review opened |

---

## Phases Performed

### Phase 1: Raise the P1 Incident

The moment volume of calls confirmed a wide impact event, a new issue was created in Jira Service Management with Priority: Critical and the title making the scope immediately clear to anyone who opened the queue.

**Issue:** `SUP1-26 — MAJOR INCIDENT — Email Service Down — All 300 Users Affected — 09:15`

![P1 Incident Created in Queue](screenshots/01_p1_incident_created_annotated.png)

> **Annotation:** The incident row is highlighted red confirming scope and title. The Time to Resolution column is highlighted orange showing the SLA clock started immediately. The OPEN status badge is highlighted green confirming the ticket is active and visible to the team.

---

### Phase 2: Post the Initial Situation Report as an Internal Note

Within five minutes of raising the ticket, an internal note was added with a full situation report so that anyone joining the response team could read a single comment and be fully briefed without a call.

**Internal note content:**
- Email service offline since approximately 09:15
- Microsoft 365 status page shows no outage
- Initial reports suggest DNS or MX record involvement
- Response team assembled: Infrastructure Lead Maria, Microsoft Escalation via support ticket, Service Desk Coordinator Nnamso Mkpong

![Initial Sitrep Internal Note](screenshots/02_initial_sitrep_internal_note_annotated.png)

> **Annotation:** The full internal note block is highlighted orange. The Microsoft status check line is highlighted red as the first thing ruled out. The response team section is highlighted green confirming ownership is clear from minute one.

---

### Phase 3: Send the First Customer Communication

A customer-visible reply was posted immediately so that all 300 affected users knew their issue was acknowledged and that a timed update was committed to.

**Customer message:** We are aware of an issue affecting email service for all users. Our team is investigating urgently. Next update will be provided within 30 minutes.

![First Customer Communication](screenshots/03_first_customer_communication_annotated.png)

> **Annotation:** The customer-visible reply is highlighted blue. The 30-minute commitment is highlighted red as the SLA-backed promise that the coordinator is accountable for delivering.

---

### Phase 4: Timeline Comment at 09:30 — DNS Ruled Out

At 09:30, the first investigative update was posted as an internal note. DNS and MX records had been checked and were intact. The Exchange Online admin centre showed the service as healthy. Attention shifted to Azure AD sign-in logs.

![Timeline Comment 09:30](screenshots/04_timeline_0930_dns_checked_annotated.png)

> **Annotation:** The internal note block is highlighted orange. The DNS checked and cleared line is highlighted red. The redirect to Azure AD investigation is highlighted blue as the next diagnostic direction.

---

### Phase 5: Timeline Comment at 09:45 — Root Cause Identified

Azure AD sign-in logs showed a bulk conditional access policy change applied at 09:10 by an admin account. The policy was blocking all Exchange Online access for every user in the tenant. The infrastructure team began reverting the policy immediately.

![Timeline Comment 09:45 Root Cause](screenshots/05_timeline_0945_root_cause_found_annotated.png)

> **Annotation:** The entire note block is highlighted red to signal critical finding. The specific policy change line at 09:10 is highlighted orange confirming the exact time of the causative event. The reverting now confirmation is highlighted green as the fix in progress.

---

### Phase 6: Timeline Comment at 10:00 — Service Restored

At 10:00, the conditional access policy revert was confirmed complete and email service was restored. User confirmation was in progress.

![Timeline Comment 10:00 Restored](screenshots/06_timeline_1000_policy_reverted_annotated.png)

> **Annotation:** The service restored note is highlighted green. The 10:00 restoration confirmation is highlighted green. The user confirmation in progress line is highlighted blue as the final validation step before closure.

---

### Phase 7: Second Customer Communication — Service Restored

A second customer-visible update was posted confirming restoration and providing three clear self-service recovery steps for any user still experiencing issues. This prevents a secondary ticket wave.

**Customer message:** Email service has been restored as of 10:00. If you are still experiencing issues: Restart Outlook, Log out and back into Microsoft 365. Please raise a new ticket if the issue persists.

![Service Restored Customer Update](screenshots/07_service_restored_customer_update_annotated.png)

> **Annotation:** The whole message is highlighted green confirming the positive resolution communication. The restoration confirmation line is highlighted green. The Restart Outlook and Log out steps are highlighted blue as the self-service recovery instructions that reduce secondary ticket volume.

---

### Phase 8: Resolve the Incident and Confirm SLA Met

The incident was transitioned to Completed. The resolution note was posted as a formal internal note with the root cause, fix, and downtime metrics. The SLA panel confirmed both Time to First Response and Time to Resolution were met within their targets.

**Resolution note:**
- Root cause: Misconfigured conditional access policy applied at 09:10
- Impact: Blocked Exchange Online access for all users
- Fix: Policy reverted at 09:58
- Service restored: 10:00
- Total downtime: 45 minutes

![Incident Resolved SLA Met](screenshots/08_incident_resolved_sla_met_annotated.png)

> **Annotation:** The Completed badge is highlighted green. The SLA panel is highlighted blue as the compliance record. Time to First Response met is highlighted green. Time to Resolution met is highlighted green. The root cause closure note at the bottom is highlighted red as the formal record for audit purposes.

---

### Phase 9: Create the Post-Incident Review and Link to SUP1-26

A PIR issue titled `PIR — Email Major Incident — April 2026` was raised and linked to SUP1-26 as a relates-to relationship. This ensures the PIR is discoverable from the closed incident and that the full story is told across both records.

![PIR Linked to Incident](screenshots/09_pir_linked_to_incident_annotated.png)

> **Annotation:** The PIR title is highlighted blue confirming the record type. The Linked work items section is highlighted green. The SUP1-26 COMPLETED row is highlighted red confirming the relationship between the closed incident and the open PIR.

---

### Phase 10: Post the Full Timeline of Events in the PIR

The PIR received the full timestamped timeline of the incident as an internal note. This is the canonical record for anyone reviewing the incident, auditing the response, or using it for training.

| Time | Event |
|---|---|
| 09:10 | Conditional access policy applied |
| 09:15 | Incident detected |
| 09:30 | DNS ruled out |
| 09:45 | Root cause identified |
| 09:58 | Policy reverted |
| 10:00 | Service restored |

![PIR Full Timeline](screenshots/10_pir_full_timeline_annotated.png)

> **Annotation:** The whole timeline block is highlighted blue. The 09:10 causative event is highlighted orange. The 09:15 incident detection is highlighted red. The 09:58 and 10:00 recovery events are highlighted green.

---

### Phase 11: Post Root Cause Analysis in the PIR

The formal root cause analysis statement was added as an internal note in the PIR. One clear sentence establishes accountability without ambiguity.

**Root Cause Analysis:** An administrative change to conditional access policies unintentionally blocked Exchange Online access globally.

![PIR Root Cause Analysis](screenshots/11_pir_root_cause_analysis_annotated.png)

> **Annotation:** The RCA block is highlighted red to signal the severity of the finding. The root cause statement itself is highlighted orange confirming the single cause for all 300 user impact.

---

### Phase 12: Post What Could Be Improved and Action Items

The final PIR section captured what went wrong and three concrete action items with named owners and due dates. This is what separates a professional post-incident review from a simple fix log.

**What could be improved:**
- No validation before policy deployment
- No staged rollout
- Lack of alerting for global access impact

**Action Items:**

| Action | Owner | Due |
|---|---|---|
| Implement approval workflow for conditional access changes | Security Team | 10 May |
| Enable alerting for authentication failures | Infra Team | 5 May |
| Introduce staged rollout for policy changes | Cloud Team | 12 May |

![PIR Improvements and Action Items](screenshots/12_pir_improvements_action_items_annotated.png)

> **Annotation:** Action items block highlighted orange. Approval workflow item highlighted red as highest priority. Alerting item highlighted blue. Staged rollout item highlighted green. What went well and could be improved block highlighted orange. Root cause repeat block highlighted blue confirming consistency of the RCA statement across the PIR.

---

## Outcome

| Metric | Result |
|---|---|
| Incident Raised | SUP1-26 — P1 Critical |
| First Customer Communication | Within 7 minutes of detection |
| Root Cause Identified | 09:45 — 30 minutes into incident |
| Service Restored | 10:00 — 45 minutes total downtime |
| SLA: Time to First Response | Met |
| SLA: Time to Resolution | Met |
| PIR Completed | Within 24 hours |
| Action Items Raised | 3 with named owners and due dates |

---

## Major Incident Coordination Skills

The ability to manage a P1 and produce a post-incident review is a career-defining skill that moves analysts toward senior and management roles. Here is why this lab matters more than any other in the Jira series:

**1. P1 incidents test everything simultaneously.** While a standard ticket allows time to think, a major incident requires triage, communication, coordination, documentation, and escalation to happen in parallel. Coordinating all of these from a single Jira ticket under call pressure is the closest a lab can get to real on-call experience.

**2. The customer communication trail is a professional differentiator.** Most junior analysts focus entirely on the fix. Senior analysts know that the communication trail is what users remember, what managers review, and what the audit asks for. Two customer updates at the right times with the right tone show service maturity.

**3. The PIR is the most senior document in IT support.** A post-incident review demonstrates that you understand the difference between fixing a problem and preventing it from happening again. Analysts who produce PIRs are trusted with more complex incidents. Those who skip the PIR stay at tier one.

**4. Named action items with owners and due dates convert a review into accountability.** An action item without an owner is a wish. Assigning the Security Team, Infra Team, and Cloud Team to specific items with named deadlines shows process leadership.

**5. This is the document you bring to a senior analyst or team lead interview.** When asked to describe a major incident you have managed, this record is the evidence. Timeline, root cause, communications, review, actions. Every section maps to a real interview question.

---

## What I Learned

1. A P1 incident is a coordination problem as much as a technical one. The Jira ticket is the single source of truth for every team member and must be updated in real time.
2. Customer communication should happen before the fix is confirmed. Acknowledging the issue early with a timed update commitment reduces call volume and manages expectations.
3. Timeline comments are not optional extras. They are the audit trail that protects you, your team, and your organisation if the incident is reviewed by management or compliance.
4. The root cause of this incident was an ungated admin change. Approval workflows and staged rollouts are the standard controls that prevent this class of fault and every PIR action item should map back to a specific control gap.
5. A linked PIR with named action items is what separates a resolved ticket from a closed incident. The ticket ends at Resolved. The PIR is where the organisation learns.

---

## Real World Relevance

Every organisation running Microsoft 365, Azure, or any cloud platform is one misconfigured policy away from a tenant-wide outage. The scenario in this lab is not hypothetical. Conditional access policy misconfigurations are among the most common causes of Microsoft 365 outages in production environments. Being the person who can raise the P1, hold the timeline, communicate to 300 users, identify the root cause in Azure AD logs, coordinate the revert, and then produce a PIR with action items is the definition of a senior service desk analyst. This lab demonstrates that capability end to end. In a help desk or IT support interview, describing this incident and producing this record is the answer to the question: tell me about a major incident you have handled.

---

## Troubleshooting Reference

| Situation | First Check | Escalation Path |
|---|---|---|
| Email down, M365 status shows healthy | Azure AD sign-in logs | Conditional access policies |
| Bulk authentication failures in logs | Recent policy changes | Admin account activity log |
| Policy change with no change request | Conditional access audit | Security team and IT manager |
| Service restored but some users still affected | Client-side: restart Outlook | Individual ticket if not resolved in 15 minutes |
| PIR action items not followed up | Jira filter: open actions past due date | Escalate to team lead |

---

*Lab 15 of 15 — Jira Service Management Series*
*IT Support Portfolio — Nnamso Mkpong*
