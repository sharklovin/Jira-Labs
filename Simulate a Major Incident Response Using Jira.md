# Simulate a Major Incident Response Using Jira

**Platform:** Jira Service Management

**Priority:** Critical

**Lab Type:** Flagship Portfolio Piece

**Author:** Nnamso Mkpong

**Domain:** IT Service Management | Major Incident Coordination

**Environment:** Jira Service Management - Cloud | Project: Support-1


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
| Platform | Jira Service Management - Cloud |
| Project | Support-1 |
| Issue Key | SUP1-26 (Incident) + PIR issue |
| Incident Coordinator | Nnamso Mkpong |
| Infrastructure Lead | Maria |
| Microsoft Escalation | Support ticket raised |
| Users Affected | 300 |
| Downtime | 45 minutes (09:15 to 10:00) |

---

# Simulate a Major Incident Response Using Jira

**Platform:** Jira Service Management
**Priority:** Critical
**Lab Type:** Flagship Portfolio Piece
**Author:** Nnamso Mkpong
**Domain:** IT Service Management | Major Incident Coordination
**Environment:** Jira Service Management - Cloud | Project: Support-1
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
| Platform | Jira Service Management - Cloud |
| Project | Support-1 |
| Issue Key | SUP1-26 (Incident) + PIR issue |
| Incident Coordinator | Nnamso Mkpong |
| Infrastructure Lead | Maria |
| Microsoft Escalation | Support ticket raised |
| Users Affected | 300 |
| Downtime | 45 minutes (09:15 to 10:00) |

---


---

## Incident Timeline

| Time | Event | Action |
|---|---|---|
| 09:10 | Conditional access policy applied by admin account | Change applied without staged rollout |
| 09:15 | Incident detected - first user calls received | SUP1-26 raised, P1 Critical, response team assembled |
| 09:20 | Initial sitrep posted as internal note | Microsoft 365 status checked, team assembled |
| 09:22 | First customer communication sent | All users notified: investigating, update in 30 minutes |
| 09:30 | DNS and MX records ruled out | Timeline comment added - Azure AD suspected |
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

**Issue:** `SUP1-26 - MAJOR INCIDENT - Email Service Down - All 300 Users Affected - 09:15`

<img width="1150" height="329" alt="01 created new issue" src="https://github.com/user-attachments/assets/5027a7d6-dac4-4cb0-a9d2-ae8e5e5d32ec" />


---

### Phase 2: Post the Initial Situation Report as an Internal Note

Within five minutes of raising the ticket, an internal note was added with a full situation report so that anyone joining the response team could read a single comment and be fully briefed without a call.

**Internal note content:**
- Email service offline since approximately 09:15
- Microsoft 365 status page shows no outage
- Initial reports suggest DNS or MX record involvement
- Response team assembled: Infrastructure Lead Maria, Microsoft Escalation via support ticket, Service Desk Coordinator Nnamso Mkpong

<img width="701" height="400" alt="02 Added internal Note" src="https://github.com/user-attachments/assets/09b89100-36db-4251-a63f-363767ca8bcc" />


---

### Phase 3: Send the First Customer Communication

A customer-visible reply was posted immediately so that all 300 affected users knew their issue was acknowledged and that a timed update was committed to.

**Customer message:** We are aware of an issue affecting email service for all users. Our team is investigating urgently. Next update will be provided within 30 minutes.

<img width="700" height="228" alt="03 FIRST comment to customer" src="https://github.com/user-attachments/assets/f817969b-5f3f-4663-8c96-3c9b2d0e0030" />


> **Annotation:** The customer-visible reply is highlighted blue.

---

### Phase 4: Timeline Comment at 09:30 - DNS Ruled Out

At 09:30, the first investigative update was posted as an internal note. DNS and MX records had been checked and were intact. The Exchange Online admin centre showed the service as healthy. Attention shifted to Azure AD sign-in logs.

<img width="697" height="255" alt="04 time line comment 1" src="https://github.com/user-attachments/assets/50b616a9-8096-461e-92b7-30289a78ee5d" />



---

### Phase 5: Timeline Comment at 09:45 - Root Cause Identified

Azure AD sign-in logs showed a bulk conditional access policy change applied at 09:10 by an admin account. The policy was blocking all Exchange Online access for every user in the tenant. The infrastructure team began reverting the policy immediately.

<img width="697" height="264" alt="05 time line comment 2" src="https://github.com/user-attachments/assets/a25ed4cc-dd6f-4bdb-b239-0a0fc82528ec" />


> **Annotation:** The entire note block is highlighted red to signal critical finding. The specific policy change line at 09:10 is highlighted orange confirming the exact time of the causative event. 

---

### Phase 6: Timeline Comment at 10:00 - Service Restored

At 10:00, the conditional access policy revert was confirmed complete and email service was restored. User confirmation was in progress.

<img width="701" height="254" alt="06 timeline comment 3" src="https://github.com/user-attachments/assets/1ebb6349-3975-4cb9-87ff-dfb713234412" />



---

### Phase 7: Second Customer Communication - Service Restored

A second customer-visible update was posted confirming restoration and providing three clear self-service recovery steps for any user still experiencing issues. This prevents a secondary ticket wave.

**Customer message:** Email service has been restored as of 10:00. If you are still experiencing issues: Restart Outlook, Log out and back into Microsoft 365. Please raise a new ticket if the issue persists.

<img width="691" height="332" alt="07 customer comment 2 " src="https://github.com/user-attachments/assets/75e9ac71-a444-42c9-bdd0-edad289c3df2" />


> **Annotation:** The whole message is highlighted green confirming the positive resolution communication.
---

### Phase 8: Resolve the Incident and Confirm SLA Met

The incident was transitioned to Completed. The resolution note was posted as a formal internal note with the root cause, fix, and downtime metrics. The SLA panel confirmed both Time to First Response and Time to Resolution were met within their targets.

**Resolution note:**
- Root cause: Misconfigured conditional access policy applied at 09:10
- Impact: Blocked Exchange Online access for all users
- Fix: Policy reverted at 09:58
- Service restored: 10:00
- Total downtime: 45 minutes

<img width="1126" height="481" alt="08 resolved" src="https://github.com/user-attachments/assets/8d91bda5-0e27-4b8e-b21e-9766c01aea21" />

---

### Phase 9: Create the Post-Incident Review and Link to SUP1-26

A PIR issue titled `PIR - Email Major Incident - April 2026` was raised and linked to SUP1-26 as a relates-to relationship. This ensures the PIR is discoverable from the closed incident and that the full story is told across both records.

<img width="703" height="461" alt="09 both issues linked" src="https://github.com/user-attachments/assets/1ffe7135-5b5d-4037-bfb4-418cda4a59d2" />


> **Annotation:** The PIR title is highlighted blue confirming the record type. The Linked work items section is highlighted green. 

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

<img width="696" height="342" alt="10 Time of events comments " src="https://github.com/user-attachments/assets/cf277f35-3dfb-45aa-a008-8dd3330fbc41" />


---

### Phase 11: Post Root Cause Analysis in the PIR

The formal root cause analysis statement was added as an internal note in the PIR. One clear sentence establishes accountability without ambiguity.

**Root Cause Analysis:** An administrative change to conditional access policies unintentionally blocked Exchange Online access globally.

<img width="696" height="251" alt="11 root cause analysis comment" src="https://github.com/user-attachments/assets/a901feda-33a4-4ea7-b604-229c379454ef" />


> **Annotation:** The RCA block is highlighted red to signal the severity of the finding. 

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

<img width="705" height="477" alt="12 What could be improved, and Action items with owners and due dates" src="https://github.com/user-attachments/assets/314ddd91-c51e-49d9-af57-7ec695b26f8d" />

---

## Outcome

| Metric | Result |
|---|---|
| Incident Raised | SUP1-26 - P1 Critical |
| First Customer Communication | Within 7 minutes of detection |
| Root Cause Identified | 09:45 - 30 minutes into incident |
| Service Restored | 10:00 - 45 minutes total downtime |
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

*Lab 15 of 15 - Jira Service Management Series*
*IT Support Portfolio - Nnamso Mkpong*
