# Manage Queues, Priorities, and SLA Targets in Jira

> **Author:** Nnamso Mkpong
>
> **Domain:** Jira Service Management  Queue Management, SLA Awareness, Triage Workflow
>
> **Environment:** Jira Service Management free tier, nnamsotechie.atlassian.net, Support project (SUP)
>
> **Completed:** April 2026

---

## Objective

Configure and work from a Jira queue with five real issues across different priorities. Observe how priority maps to SLA targets, sort the queue by SLA deadline to identify the most urgent work, triage each issue with an appropriate comment, action the highest-priority ticket, schedule a medium-priority issue, place one ticket on hold, resolve one end to end, and confirm all five issues have correct statuses and notes at the end of the session.

---

## Business Scenario

> **Morning Triage Session - 13 April 2026**
>
> Five support requests have arrived in the queue. All are currently unassigned with status Waiting for Support. You are the first analyst on shift. You need to triage the queue by SLA deadline, confirm each priority is correct, action the most urgent issue immediately, schedule lower-priority work for later in the day, place one ticket on hold while awaiting user information, and close one end to end with a full resolution note. Every action must be logged with a comment so the queue tells a complete story at handover.

---

## Environment and Tools Used

| Component | Detail |
|---|---|
| **Platform** | Jira Service Management free tier |
| **Project** | Support (SUP) |
| **Issues Created** | SUP-7, SUP-8, SUP-9, SUP-10, SUP-11 |
| **SLA Framework** | Service requests - Highest 24h, High 36h, Medium 48h, Low 60h |
| **Triage Method** | Sort by Time to resolution ascending |

---

## Steps Performed

---

### Phase 1 - Record the Baseline Queue State

**Step 1.1 - Open the Queue and Confirm the Baseline**

Navigate to Support > Queues > Open tasks. Before creating any issues, the queue is empty. This is the baseline state before the morning triage session begins.

<img width="1135" height="598" alt="01 open task queue basline" src="https://github.com/user-attachments/assets/88a31529-2604-43b5-9897-d4055629c966" />



> **Highlighted:** The Open tasks queue shows zero items. The filter bar at the top provides Request type, Status, Assignee, and More filters. The tools used throughout the triage session to slice the queue by category. The empty state is the baseline before the five test issues are created.

---

### Phase 2 - Create Five Issues Across All Priority Levels

**Step 2.1 - Create Five Realistic IT Support Issues**

Create one issue for each priority tier using realistic support scenarios. All five issues land in the Unassigned service requests queue with status Waiting for Support.

<img width="1137" height="407" alt="02  5 queqes created" src="https://github.com/user-attachments/assets/1db2ee3a-98ca-455f-9542-52c16ebf8848" />



> **Highlighted:** Each row is colour-coded by priority. SUP-7 (Highest, red) has the earliest SLA deadline (April 16) which makes it the first issue to action. The SLA deadlines in the right column are the primary sort key for triage. All five issues are unassigned and awaiting support. the queue is as it would appear on a Monday morning after a weekend of incoming requests.

---

### Phase 3 - Review the SLA Configuration

**Step 3.1 - Examine the SLA Targets Per Priority**

Navigate to Project Settings > SLAs. Review the time-to-resolution targets that apply to each priority level for Service requests.

<img width="660" height="313" alt="03 SLA config" src="https://github.com/user-attachments/assets/84d77ba2-38c7-4f04-bc69-6533ced3d1a6" />


SLA targets confirmed:

| Priority | Calendar | Time to Resolution |
|---|---|---|
| Highest | Sample 9-5 Calendar | **24 hours** |
| High | Sample 9-5 Calendar | **36 hours** |
| Medium | Sample 9-5 Calendar | **48 hours** |
| Low | Sample 9-5 Calendar | **60 hours** |
| All remaining | Sample 9-5 Calendar | 72 hours |
| All remaining work items | Sample 9-5 Calendar | No target |

> **Highlighted:** Every priority tier has a distinct resolution target measured against the Sample 9-5 Calendar (business hours only). This means a Highest priority issue created on Friday at 17:00 has until Monday at 17:00 to be resolved within 24 business hours, not 24 calendar hours. Understanding this distinction prevents analysts from miscalculating breach risk when a ticket arrives on a Friday afternoon.

---

### Phase 4 - Sort the Queue by SLA Deadline

**Step 4.1 - Sort Time to Resolution Ascending to Identify Highest Risk**

Return to the Unassigned service requests queue. Click the Time to resolution column header to sort ascending. The issue closest to its SLA deadline moves to the top.

<img width="1128" height="415" alt="04 timer showing but not dates" src="https://github.com/user-attachments/assets/6f8e0339-bf1c-4b7b-9c78-1b3e3415d13b" />


> **Highlighted:** The Time to resolution column is sorted ascending (arrow indicator visible). SUP-7 (User locked out of laptop) is now at the top with an April 16 deadline which is the earliest of all five issues. This is the correct triage method: sorting by SLA rather than by creation time or issue key ensures the most at-risk ticket is always visible at the top of the working list regardless of when it arrived.

> Sorting by SLA ascending is the single most important queue management habit a new analyst can build. A queue sorted by creation date will always show the oldest tickets first which are often already actioned. A queue sorted by SLA shows the tickets that are most at risk of breach today.

---

### Phase 5 - Action the Highest Priority Issue (SUP-7)

**Step 5.1 - Open SUP-7 and Change Status to In Progress**

Open SUP-7 (User locked out of laptop — Priority: Highest). Change the status to In Progress. Add both a customer reply and an internal triage note.

<img width="1099" height="580" alt="05 issue in progress" src="https://github.com/user-attachments/assets/0633b6bc-a786-4acb-976f-0c854eb2c204" />


Actions taken on SUP-7:

| Action | Detail |
|---|---|
| Status | Changed to **In Progress** |
| Priority | Highest (confirmed correct) |
| Assignee | Nnamso Mkpong |
| SLA: Time to first response | Within 4h |
| SLA: Time to resolution | Within 24h (Apr 16 09:09 AM) |
| Customer reply | We are investigating your issue urgently. Updates will follow shortly. |
| Internal note | User completely blocked, no workaround. SLA target: 24 hours. Actioning immediately. |

> **Highlighted:** The In Progress status badge is confirmed (green on top right). The SLA panel shows two active timers: Time to first response (within 4h) and Time to resolution (within 24h on Apr 16, Time 09:09 AM). Priority is set to Highest. The internal note (yellow background) records the triage decision: user is completely blocked with no workaround — this justifies Highest priority and immediate action. The customer reply (white, above) confirms investigation has begun.

---

### Phase 6 - Triage the Medium Priority Issue (SUP-9)

**Step 6.1 - Open SUP-9 and Record Triage Decision**

Open SUP-9 (Printer offline with Priority: Medium). The user has a workaround (printing to PDF and emailing). Add an internal triage note and schedule for later in the afternoon.

<img width="1115" height="588" alt="06 p3 issue scheduled " src="https://github.com/user-attachments/assets/e56f70bb-849f-4eb3-9b85-c12dc066e00e" />


Actions taken on SUP-9:

| Action | Detail |
|---|---|
| Status | Remains Waiting for support |
| Priority | Medium  (confirmed correct) |
| SLA: Time to first response | Tomorrow 09:11 AM (within 8h) |
| SLA: Time to resolution | Apr 17 01:11 PM (within 36h) |
| Internal note | User has a workaround available. SLA target: 24 hours. Scheduled for this afternoon. |

> **Highlighted:** The status remains Waiting for support. No change needed yet because the SLA is not at risk and the user has a workaround. The SLA panel confirms first response is due tomorrow at 09:11 AM and resolution by Apr 17 01:11 PM  both within target. The internal note records the scheduling decision: workaround available, so this can wait until afternoon without breaching the SLA.

---

### Phase 7 - Place SUP-10 On Hold (Waiting for Customer)

**Step 7.1 - Transition SUP-10 to Waiting for Customer**

Open SUP-10 (Software installation request with Priority: Medium). Additional information is needed from the user before work can begin. Transition to Waiting for customer. Observe the SLA timer behaviour.

<img width="997" height="539" alt="07 waiting for customer sla paused" src="https://github.com/user-attachments/assets/25ba01fa-c6e4-42af-b693-35133c848fa7" />


> **Highlighted:** The status badge shows Waiting for customer (blue). In Jira Service Management, the Waiting for customer state pauses the SLA clock. The resolution timer stops running while the issue is in this state and resumes only when the ticket transitions back to an active state. This is a critical feature for managing SLA compliance on tickets where the delay is attributable to the user rather than the support team.

> The internal note records that the analyst is awaiting information before proceeding. This is the correct documentation for a ticket placed on hold as it makes the reason visible to any colleague who picks up the ticket and prevents it from being escalated unnecessarily.

---

### Phase 8 - Resolve SUP-11 End to End

**Step 8.1 - Work SUP-11 to Resolved Status**

Open SUP-11 (Password reset request with Priority: Low). This issue is straightforward and can be resolved in one session. Add investigation notes, send a resolution reply to the customer, and change the status to Resolved.

<img width="1090" height="591" alt="08 Issue resolved end to end" src="https://github.com/user-attachments/assets/aba9819b-6c10-451b-bb32-99ed7811ca6a" />


Actions taken on SUP-11:

| Action | Detail |
|---|---|
| Status | Changed to **Resolved** |
| Done badge | Confirmed |
| Priority | Low (confirmed correct) |
| SLA: Time to first response | Apr 15 09:12 AM (within 16h) |
| SLA: Time to resolution | Apr 22 01:12 PM (within 60h) |
| Customer reply | Your password has been reset. Please confirm everything is working correctly. |
| Internal note | Issue investigated. Password reset completed. User confirmed working. |

> **Highlighted:** The Resolved status badge (green) and Done badge are both confirmed. The SLA panel shows time to first response within 16h and time to resolution within 60h — both well within the Low priority targets. The customer reply (white, above) communicates the resolution in clear user-facing language. The internal note (yellow, below) records the technical action taken. This is the complete end-to-end resolution pattern: investigate, act, notify user, confirm, resolve.

---

### Phase 9 - Review the Final Queue State

**Step 9.1 - Confirm All Five Issues Have Correct Statuses**

Return to the full queue view and confirm each of the five issues shows the correct status reflecting all triage actions taken in this session.

<img width="1076" height="335" alt="09 final queue status summary" src="https://github.com/user-attachments/assets/aaadb0f3-3e07-40e2-b4a4-d40ebc21d909" />


> **Highlighted:** Every status badge in the final queue reflects a deliberate triage decision. SUP-11 is RESOLVED. SUP-10 is WAITING FOR CUSTOMER with SLA paused. SUP-9 and SUP-8 are WAITING FOR SUPPORT with internal notes recording their scheduled order. SUP-7 is IN PROGRESS as the highest-priority blocked user. All five issues are now assigned to Nnamso Mkpong with no tickets remain unowned after the triage session.

---

## Business Impact Note

> **Queue management is not a technical skill but professional discipline. The difference between a good analyst and a great analyst is often visible in the queue at handover.**

A queue where every ticket has an internal note explaining its current status, a correct priority, and an assigned owner is a queue that any colleague can pick up at shift change without a briefing. A queue with unassigned tickets, no notes, and incorrect priorities is a liability. SLA breaches happen not because the work is too hard but because no one knew which ticket needed attention first.

Sorting by SLA deadline rather than by creation time is the single most impactful habit change for a new analyst. It ensures that the ticket closest to breach is always visible at the top of the working list, regardless of how many other tickets arrived first.

The Waiting for Customer state demonstrates another critical discipline: when a ticket is delayed by the user rather than by the team, the SLA clock should be paused and documented. This protects the team's SLA performance metrics and creates a clear audit trail showing that the delay was not caused by the support team.

---

## Help Desk Ticket Notes

See the individual ticket files in this folder for the full five-ticket triage log:

`TICKET-SUP7-user-locked-out.md` - Highest priority, In Progress, immediate action.

`TICKET-QUEUE-TRIAGE-LOG.md` - Full morning triage session log covering all five issues.

---

## Outcome and Validation

| Check | Result |
|---|---|
| Five issues created across all priority tiers | Pass |
| SLA configuration reviewed - all priority targets confirmed | Pass |
| Queue sorted by SLA time to resolution ascending | Pass |
| SUP-7 (Highest) identified as most urgent - earliest deadline | Pass |
| SUP-7 moved to In Progress with customer reply and internal note | Pass |
| SUP-9 (Medium) triaged - workaround noted, scheduled for afternoon | Pass |
| SUP-10 placed in Waiting for Customer - SLA paused | Pass |
| SUP-11 resolved end to end - customer reply, internal note, Resolved status | Pass |
| All five issues assigned - no unowned tickets in queue | Pass |
| Final queue reflects all triage decisions at handover | Pass |

---

## What I Learned

1. **Sorting by SLA deadline rather than creation time is the most important queue habit.** The issue at the top of a creation-date-sorted queue is the oldest — often already actioned. The issue at the top of an SLA-sorted queue is the one most at risk of breach today.

2. **Priority must be confirmed, not assumed.** A ticket created by a user with the wrong priority (or no priority) can sit in the queue with an incorrect SLA target. Triage includes reviewing each ticket's priority and correcting it before the deadline is calculated from the wrong baseline.

3. **The Waiting for Customer state is an SLA management tool, not a workaround.** Placing a ticket on hold pauses the resolution timer. This protects the team's SLA performance on tickets where the delay is the user's responsibility. It also requires documentation as the internal note must explain what information is being awaited and when a follow-up will be sent.

4. **Every triage decision must have a comment.** A ticket with no internal note is invisible to the next analyst. A ticket with a clear internal note with even one sentence explaining why it was prioritised or deferred  can be picked up instantly at shift change. This is the difference between a queue that supports the team and a queue that creates confusion.

5. **Resolving a ticket end to end requires three things: investigation, action, and confirmation.** The internal note records what was done. The customer reply communicates the result. The Resolved status closes the SLA timer. All three are required as a ticket that is fixed but not communicated is not resolved from the customer's perspective.

---

## Real World Relevance

Queue management under SLA pressure is the daily reality of every service desk analyst. The five-issue morning triage in this lab is a simplified but structurally accurate simulation of what analysts face in large queues. The habits built here sort by SLA, confirm priority, comment every decision, document on-hold reasons, resolve with a full note are scale directly to queues of 50, 100, or 500 tickets.

Jira Service Management is used by the majority of technology and scale-up companies because its queue, SLA, and workflow features integrate with the broader Atlassian toolchain. Analysts who can manage a Jira queue confidently including understanding SLA behaviour in different workflow states  are immediately productive in any organisation using Atlassian tools.

In technical interviews for JSM-based roles, queue triage scenarios are a common assessment. Candidates who can describe the SLA implications of priority, the pause behaviour of Waiting for Customer, and the comment requirements for each status transition demonstrate operational fluency that goes beyond basic platform navigation.

---

## Troubleshooting Reference

| Situation | Correct Action | Common Mistake |
|---|---|---|
| Queue is cluttered and hard to prioritise | Sort by SLA time to resolution ascending | Leaving queue sorted by creation date |
| Issue priority appears wrong | Open the issue and correct the priority field before actioning | Actioning based on incorrect priority |
| SLA timer still running while awaiting user | Transition to Waiting for customer to pause the timer | Leaving ticket in In Progress while waiting |
| Ticket has no internal note | Add a note before changing status or moving to next ticket | Changing status without documenting the reason |
| SLA target appears too long or too short | Check Project Settings > SLAs - priority may be misconfigured | Assuming the SLA shown is always correct |
| User not notified after resolution | Add a customer reply before changing status to Resolved | Resolving without sending a customer-facing message |
