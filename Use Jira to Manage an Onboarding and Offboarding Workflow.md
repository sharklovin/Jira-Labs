# Use Jira to Manage an Onboarding and Offboarding Workflow

> **Author:** Nnamso Mkpong
>
> **Domain:** Jira Service Management - HR Workflow, Sub-task Management, Status Transitions, Due Dates
>
> **Environment:** Jira Service Management free tier - Support-1 project (SUP1)
>
> **Completed:** April 2026

---

## Objective

Create a structured onboarding request in Jira with five checklist-style sub-tasks covering every provisioning step, complete the workflow end to end with completion notes on each sub-task, then repeat the process for an offboarding scenario demonstrating secure and auditable access removal before end of business. Both workflows must be fully documented so a colleague or auditor can read the tickets and confirm every action was completed without asking anyone.

---

## Business Scenario

> **Two HR Requests - Same Day - 17 April 2026**
>
> HR has submitted two requests at the same time. Chiamaka Bello is joining the Legal Department on Monday April 14 and needs full provisioning completed before her start date. James Okafor is leaving the Operations team today and needs all access removed by end of business. Both requests land in the queue simultaneously. You have to manage them in parallel, make sure the onboarding is done before Monday, and make sure the offboarding leaves no access gap by close of day.

This lab covers two of the most process-sensitive workflows in IT support. Onboarding failures mean a new employee cannot work on their first day - which creates a poor first impression and generates immediate escalations to HR. Offboarding failures mean a departing employee retains access to company systems, shared drives, and email after they have left - which is a security and compliance risk that has real consequences in audited environments. Both workflows benefit from the same approach: a parent issue with structured sub-tasks, assigned owners, clear due dates, and documented completion notes.

---

## Environment and Tools Used

| Component | Detail |
|---|---|
| **Platform** | Jira Service Management free tier |
| **Project** | Support-1 (SUP1) |
| **Onboarding Issue** | SUP1-8 |
| **Onboarding Sub-tasks** | SUP1-9, SUP1-10, SUP1-11, SUP1-12, SUP1-13 |
| **Offboarding Issue** | SUP1-15 |
| **Offboarding Sub-tasks** | SUP1-21, SUP1-22, SUP1-23, SUP1-24, SUP1-25 |
| **Feature Used** | Sub-tasks, Status transitions, Due dates, Internal notes |
| **Final Status - Both** | Done |

---

## Why Sub-tasks Matter for HR Workflows

> **A single parent ticket with no sub-tasks is not a workflow. It is a note. Sub-tasks turn a request into a trackable, auditable checklist.**

```
WITHOUT SUB-TASKS
  What the ticket says:    "Provision full access before start date"
  What the agent sees:     One item, no breakdown, no order, no assignee per step
  What gets missed:        Security group membership, welcome email, laptop build
  What happens at audit:   No evidence of what was done, when, or by whom

WITH SUB-TASKS
  What the ticket says:    Five discrete tasks, each with an owner and a status
  What the agent sees:     A checklist that progresses from 0% to 100% Done
  What gets missed:        Nothing - the list enforces completeness
  What happens at audit:   Every action is timestamped, named, and noted

KEY RULE
  Use sub-tasks when:
  - A request involves more than one person or team
  - Individual steps must be completed in a specific order
  - You need proof that each step was done, not just that the parent was closed
  - The workflow is repeated regularly and needs to be consistent every time
```

The onboarding and offboarding workflows are perfect examples of this. Every new starter needs the same five provisioning steps done in the right order. Every leaver needs the same five removal steps completed before they walk out. Sub-tasks make the standard the default.

---

## Steps Performed

---

### Phase 1 - Create the Onboarding Parent Issue

**Step 1.1 - Log the Onboarding Request as a New Issue**

Create a new issue in the Support-1 queue. Title it exactly as HR submitted it so there is no ambiguity about who this ticket belongs to and when the deadline is.

Title used:
> New Starter - Chiamaka Bello - Legal Department - Starts Monday April 14.

Description:
> HR request for onboarding. Provision full access before start date.

<img width="1105" height="319" alt="01 Onboarding Ticket Queue" src="https://github.com/user-attachments/assets/f0fd007c-fc70-4934-978f-678f8bf8e675" />


> **Highlighted:** The blue box marks SUP1-8 in the queue. Status is Open. Reporter is Nnamso Mkpong. Assignee is Unassigned at this point because individual sub-tasks will carry the assignees once the work is broken down. Created 17/Apr/26.

---

### Phase 2 - Add the Five Onboarding Sub-tasks

**Step 2.1 - Open SUP1-8 and Create Each Sub-task**

Open the parent issue and click Create subtask for each provisioning step. Each sub-task gets its own issue key and can be assigned, tracked, and closed independently.

Sub-tasks created:

| Key | Task | Status at Creation |
|---|---|---|
| SUP1-9 | Create Active Directory account | Open |
| SUP1-10 | Assign Microsoft 365 licence and configure email | Open |
| SUP1-11 | Add to Legal shared drive security group | Open |
| SUP1-12 | Build and configure laptop (WIN11-CB-01) | Open |
| SUP1-13 | Send welcome email with first-day instructions | Open |

<img width="682" height="596" alt="02onboarding  subtasks queue" src="https://github.com/user-attachments/assets/f5c3516c-b370-4bcd-92b3-8d9fb9bd2f28" />



> **Highlighted:** The brown box covers all five sub-tasks. The progress bar at the top of the Subtasks section shows 0% Done. Every sub-task is Open and Unassigned at this stage. The order matters: AD account must exist before M365 can be configured, the security group requires the AD account, and the laptop and welcome email can only be sent once everything else is in place.

---

### Phase 3 - Set the Due Date on the Parent Issue

**Step 3.1 - Add Due Date of Friday April 11**

The start date is Monday April 14. The due date on the parent issue is set to Friday April 11 to give a three-day buffer for any issues discovered during provisioning. If provisioning hits a problem on Friday, there is still the weekend before Chiamaka arrives.

<img width="1131" height="552" alt="03 due date details" src="https://github.com/user-attachments/assets/ac3c9eb7-6b5b-4f01-a1f8-9bbc6b77bb51" />


> Due date confirmed as Apr 11, 2026. Priority is Medium. Assignee is Unassigned at parent level. Reporter is Nnamso Mkpong. The due date is on the parent issue because that is the deadline for the whole provisioning workflow - individual sub-tasks should all be done before that date.

---

### Phase 4 - Assign Sub-tasks and Move to In Progress

**Step 4.1 - Open Each Sub-task, Assign an Owner, and Transition Status**

Open each sub-task individually. Assign it to the relevant person. Change the status from Open to Work in Progress. This signals to everyone looking at the queue that work is actively underway on this ticket.

<img width="1130" height="593" alt="04 subtask work in progress" src="https://github.com/user-attachments/assets/b9b9fd0a-3f26-4117-af02-54db0f263af6" />



> SUP1-9 is now Work in Progress. Assignee is Nnamso Mkpong. The breadcrumb at the top confirms the hierarchy: Support-1 / SUP1-8 / SUP1-9. This sub-task sits under the parent onboarding issue and its status is tracked separately from the parent.

---

**Step 4.2 - Repeat for All Five Sub-tasks**

Move all five sub-tasks to Work in Progress and assign each one. The parent issue progress bar updates automatically as each sub-task status changes.

<img width="701" height="533" alt="05 all subtasks  in progress" src="https://github.com/user-attachments/assets/d5ed0262-1939-40fb-9802-2bde0b6325a6" />



> **Highlighted:** The box covers all five sub-tasks. Every one shows WORK IN PROGRESS in the status column. Every one is assigned to Nnamso Mkpong. The progress bar still reads 0% Done because no sub-tasks have been closed yet - Work in Progress updates the status but does not move the progress bar. Only moving a sub-task to Done increments the percentage.

---

### Phase 5 - Complete Each Sub-task With a Completion Note

**Step 5.1 - Mark the First Sub-task Done and Add an Internal Note**

Open SUP1-9. Complete the work. Add an internal note documenting exactly what was done. Change the status to Done.

Completion note added to SUP1-9:
> AD account created. UPN: c.bello@company.com. Groups: LegalUsers, AllStaff

<img width="1069" height="555" alt="06 subtask done with note" src="https://github.com/user-attachments/assets/98c91315-92f0-43d2-a153-bae4b26bdd95" />



> **Green highlight:** The Done status badge in the top right confirms this sub-task is closed. **Orange highlight:** The internal note at the bottom of the activity section contains the completion detail. The note records the UPN and group memberships so there is a permanent record of exactly what was configured. If c.bello@company.com cannot log in on Monday morning, this note is the first place to check.

---

### Phase 6 - Confirm All Sub-tasks Are Done

**Step 6.1 - Verify 100% Progress on the Parent Issue**

Once all five sub-tasks have been completed and noted, the parent issue shows 100% Done in the progress bar. All five sub-tasks display the DONE badge.

<img width="702" height="291" alt="07 subtask completed" src="https://github.com/user-attachments/assets/3fca0e63-e941-44f4-9dd4-88607c4b0216" />


> **Highlighted:** The green box at the top marks the progress bar now reading 100% Done. All five sub-tasks show DONE in the status column. All are assigned to Nnamso Mkpong. The names are struck through which is Jira's visual confirmation that these items are closed. At this point the parent issue can be transitioned to Done.

---

### Phase 7 - Close the Onboarding Parent Issue

**Step 7.1 - Transition SUP1-8 to Done**

Open the parent issue SUP1-8. Change the status to Done. The parent issue now shows the Done badge and the full sub-task list with 100% completion, all assigned, all with completion notes.

<img width="1153" height="593" alt="08 parent issue done" src="https://github.com/user-attachments/assets/9ede7a3f-eef9-47ab-8218-397ec27aabaf" />


> Parent issue SUP1-8 is Done. Due date was Apr 11, 2026. All five sub-tasks are Done. Reporter is Nnamso Mkpong. The ticket is now a complete auditable record of the Chiamaka Bello onboarding - every step, every assignee, every completion note is captured under one parent issue key.

---

### Phase 8 - Create the Offboarding Parent Issue

**Step 8.1 - Log the Offboarding Request as a Separate Issue**

Create a new issue for the James Okafor offboarding. This is a separate workflow from the onboarding and must be tracked independently. The title makes the urgency clear.

Title used:
> Leaver - James Okafor - Operations - Last Day Today

Description:
> HR request for urgent offboarding. Remove all access immediately.

<img width="1140" height="307" alt="09 offboarding issue created" src="https://github.com/user-attachments/assets/e542bcfe-c22c-4d0d-aeb3-0f9103dba241" />


> SUP1-15 appears in the queue as a separate ticket from the onboarding work. Status is Open. Reporter is Nnamso Mkpong. This ticket must be completed today - James Okafor's last day. Unlike the onboarding which had a three-day buffer, this has a hard end-of-business deadline with no flexibility.

---

### Phase 9 - Add the Five Offboarding Sub-tasks

**Step 9.1 - Create Each Access Removal Step as a Sub-task**

Open SUP1-15 and create a sub-task for each removal action. The offboarding checklist is the mirror of the onboarding checklist: every system that was provisioned on arrival must be deprovisioned on departure.

Sub-tasks created:

| Key | Task | Priority Set |
|---|---|---|
| SUP1-21 | Disable Active Directory account | Highest |
| SUP1-22 | Revoke Microsoft 365 licence and forward email to manager | Highest |
| SUP1-23 | Remove from all security groups and shared drives | Highest |
| SUP1-24 | Retrieve laptop and wipe device | Highest |
| SUP1-25 | Confirm no active sessions (VPN, remote desktop) | Highest |

<img width="699" height="542" alt="10 offboarding ticket queue" src="https://github.com/user-attachments/assets/867be4ad-e5f7-4c62-8393-0de8e0fb82f0" />


> Five sub-tasks created under SUP1-15. All are Open. Progress bar reads 0% Done. The task names mirror the onboarding steps in reverse: what was created is disabled, what was assigned is revoked, what was added is removed, what was built is wiped.

---

### Phase 10 - Set Due Date to Today and Escalate Priority

**Step 10.1 - Add Today as the Due Date and Mark All Sub-tasks as Highest Priority**

Set the due date on the parent issue to today, April 17. Change the priority on all five sub-tasks from Medium to Highest. This ensures the offboarding tasks surface at the top of any filtered view and no one treating them as routine can miss the urgency.

<img width="1132" height="584" alt="11 due date added to today" src="https://github.com/user-attachments/assets/8fd15079-da5d-42d2-82bd-34e3561df19e" />


> **Red highlight:** The compliance note in the description field: "All access confirmed removed at 16:45. Device collected. No active sessions. HR notified." This note is on the parent issue, not a sub-task, because it is the summary confirmation for the whole offboarding - the equivalent of a sign-off. **Blue highlight:** The pinned Due date field in the right panel shows Apr 17, 2026. All five sub-tasks are Done with Highest priority assigned to Nnamso Mkpong.

---

### Phase 11 - Confirm Offboarding Complete and Close the Parent Issue

**Step 11.1 - Transition SUP1-15 to Done**

All five sub-tasks are Done. The compliance note is recorded on the parent issue. Change the status of SUP1-15 to Done.

<img width="1137" height="592" alt="12 offboarding with note" src="https://github.com/user-attachments/assets/9e191847-b823-4543-bde0-b3a6312b3701" />


> Parent issue SUP1-15 is Done. Due date was Apr 17, 2026 - today. All five sub-tasks show Done at Highest priority. The compliance note confirms the timestamp of access removal, device collection, and HR notification. This ticket can be presented to a security or compliance team as evidence that the offboarding was completed in full on the correct date.

---

## Before and After Comparison

### Before - A Single Unstructured Ticket

| What the ticket contained | What was missing |
|---|---|
| "Provision full access before start date" | Which systems, in which order |
| No sub-tasks | Who is responsible for each step |
| No due date | When it needs to be done by |
| No completion notes | Proof that each step was actually done |

A ticket like that closes when someone decides everything is probably done. There is no way to know which steps were completed, which were skipped, and what exactly was configured.

---

### After - Structured Sub-task Workflow

| Element | Onboarding SUP1-8 | Offboarding SUP1-15 |
|---|---|---|
| Sub-tasks | 5 - one per provisioning step | 5 - one per removal step |
| Due date | Apr 11 - 3 days before start | Apr 17 - day of departure |
| Priority | Medium | Highest |
| Completion notes | Per sub-task (AD UPN, groups) | Compliance note on parent issue |
| Final status | Done - 100% sub-tasks complete | Done - 100% sub-tasks complete |
| Audit trail | Full - every step timestamped | Full - sign-off at 16:45 |

---

## Onboarding and Offboarding as Security Controls

### Why Offboarding is a Security Workflow, Not Just an IT Task

Most IT teams treat onboarding and offboarding as simple service desk tasks. That is the wrong frame. Offboarding is a security control. Every hour a departing employee retains active system access after their employment ends is an hour of residual risk. A disgruntled leaver with an active M365 account, active VPN credentials, and access to shared drives can do significant damage in that window.

The sub-task structure in this lab enforces completeness by design. You cannot mark the parent issue Done while sub-tasks are still Open without deliberately overriding them. The checklist is the control. If "Confirm no active sessions" is the last sub-task and it cannot be closed until VPN and remote desktop access is confirmed removed, then the parent ticket cannot close while those sessions are still live.

### The Compliance Note Pattern

The compliance note added to SUP1-15:

> All access confirmed removed at 16:45. Device collected. No active sessions. HR notified.

This note contains four elements that matter in an audit:
- A timestamp (16:45) so the record shows when removal was confirmed, not just that it happened
- Physical asset confirmation (Device collected) so the hardware chain of custody is documented
- Session confirmation (No active sessions) so there is no ambiguity about remote access
- HR notification (HR notified) so the HR team has a record tied to the Jira ticket

A compliance team reviewing this ticket weeks or months later can read that note and answer any question about the offboarding without having to call anyone.

### The Onboarding Note Pattern

The completion note on SUP1-9:

> AD account created. UPN: c.bello@company.com. Groups: LegalUsers, AllStaff

This note contains the configuration details so if Chiamaka cannot log in on Monday morning, the support team has a starting point immediately. The UPN tells them what to look for in Active Directory. The groups tell them what access she should have. A note that says "AD account done" is not useful on Monday morning. A note that records the UPN and group memberships is.

---

## Parallel Workflow Management

Running two HR workflows simultaneously - one onboarding, one offboarding - on the same day is normal in any organisation with staff turnover. The key is that they are tracked as separate parent issues. They share no state. Closing one does not affect the other. If the offboarding hits a problem - the laptop cannot be wiped remotely because the device is not returning to the office - that issue is raised on SUP1-15 without touching the onboarding ticket at all.

The queue view makes the parallel nature visible. Two open tickets, both active, both with sub-tasks progressing independently. Any analyst looking at the queue can see what is in flight without having to open each ticket.

---

## Help Desk Ticket Notes

See `TICKET_NOTES.md` in this folder for full per-step observations on both workflows, decisions made at each point, and the reasoning behind the offboarding priority escalation and compliance note structure.

---

## Outcome and Validation

| Check | Result |
|---|---|
| Onboarding issue SUP1-8 created with correct title | Pass |
| Five onboarding sub-tasks created (SUP1-9 to SUP1-13) | Pass |
| Due date set to Apr 11 on parent onboarding issue | Pass |
| All sub-tasks assigned and moved to Work in Progress | Pass |
| Each sub-task closed with a completion note | Pass |
| Progress bar reached 100% Done on onboarding parent | Pass |
| Onboarding parent issue SUP1-8 transitioned to Done | Pass |
| Offboarding issue SUP1-15 created with correct title | Pass |
| Five offboarding sub-tasks created (SUP1-21 to SUP1-25) | Pass |
| Due date set to today (Apr 17) on offboarding parent | Pass |
| All offboarding sub-tasks escalated to Highest priority | Pass |
| All offboarding sub-tasks completed and closed | Pass |
| Compliance note added to offboarding parent issue | Pass |
| Offboarding parent issue SUP1-15 transitioned to Done | Pass |
| Both tickets auditable without any follow-up questions | Pass |

---

## What I Learned

1. **Sub-tasks enforce completeness in a way that description text cannot.** A description that says "provision everything" relies on the analyst remembering what everything means. A sub-task list that says exactly which five things need to be done does not rely on memory. It relies on the checklist.

2. **The due date belongs on the parent issue, not the sub-tasks.** The deadline is for the whole workflow. Individual sub-tasks should all be done before that date, but managing a due date on each one creates five separate deadlines to track instead of one. Keep the due date on the parent and let the sub-task progress bar show how far along the workflow is.

3. **Completion notes on sub-tasks are evidence, not admin.** Writing "AD account done" closes the sub-task. Writing "AD account created. UPN: c.bello@company.com. Groups: LegalUsers, AllStaff" creates a record that is useful at 8am on a Monday when someone cannot log in. The extra 20 seconds it takes to write the note is worth it.

4. **Offboarding priority should always be higher than onboarding.** A new starter who is not provisioned on day one is inconvenienced. A leaver who retains access past their last day is a security risk. Those are not equivalent situations. Highest priority on offboarding sub-tasks is the correct setting.

5. **The compliance note on the offboarding parent is a different document from the sub-task notes.** Sub-task notes record what was done on each specific task. The compliance note on the parent records that the whole workflow is complete, at what time, with confirmation of the key risk points. Both are needed. One without the other leaves gaps.

6. **Running two workflows in parallel is not harder than running one - it just requires discipline about keeping them as separate tickets.** The temptation is to combine onboarding and offboarding admin into a single session of work. Keeping them as separate issues with separate keys, separate due dates, and separate sub-tasks means the audit trail is clean and one ticket's complications cannot contaminate the other.

---

## Real World Relevance

Onboarding and offboarding are the two most frequently repeated structured workflows in any IT support team. Getting them right is not just about efficiency - it is about security posture and compliance. In regulated industries like financial services, healthcare, and legal, the offboarding record is often a document that gets reviewed in audits. The ability to open a ticket and show an auditor exactly when each access was removed, who confirmed it, and what the device status was at close of business is the difference between passing an audit and receiving a finding.

From a career perspective, analysts who demonstrate they understand the difference between closing a ticket and completing a workflow - who add completion notes, who escalate priority correctly, who use sub-tasks to enforce process - are the ones who get involved in process improvement work. Service desk teams that run clean onboarding and offboarding workflows produce better data, better SLA compliance, and better security outcomes than teams where these processes live in spreadsheets or email threads.

---

## Troubleshooting Reference

| Situation | Correct Action | Common Mistake |
|---|---|---|
| Parent issue shows less than 100% Done but all sub-tasks look complete | Check if any sub-task is stuck on Work in Progress rather than Done - the progress bar only counts Done status, not In Progress | Closing the parent without checking sub-task statuses |
| Sub-task does not appear under the parent in the queue | Confirm the issue was created using Create subtask from within the parent, not as a standalone issue with a manual link | Creating a new top-level issue and trying to link it as a child afterwards |
| Due date is not visible on the parent issue | Check Project Settings to confirm the Due date field is enabled for this issue type | Looking for the due date in the wrong panel - it is in Details, not the main body |
| Offboarding sub-tasks are showing Medium priority instead of Highest | Open each sub-task individually and change Priority in the Details panel - priority changes on the parent do not cascade to existing sub-tasks | Changing priority on the parent and assuming it applies to existing sub-tasks |
| Compliance note is not appearing as an internal note | Make sure Add internal note is selected before typing, not Reply to customer - internal notes have the yellow background and lock icon | Adding the compliance note as a customer-visible comment instead of an internal note |
| Progress bar does not reach 100% after closing all sub-tasks | Refresh the parent issue page - the progress bar sometimes does not update in real time without a page refresh | Assuming the count is wrong and trying to add or remove sub-tasks |
