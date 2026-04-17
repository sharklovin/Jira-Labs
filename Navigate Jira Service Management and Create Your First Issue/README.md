# Navigate Jira Service Management and Create Your First Issue

> **Author:** Nnamso Mkpong
>
> **Domain:** Jira Service Management - Ticket Creation, Queue Management, Agent Workflow
>
> **Environment:** Jira Service Management free tier - nnamsotechie.atlassian.net - Support project (SUP)
>
> **Completed:** April 2026

---

## Objective

Set up a free Jira Service Management workspace, explore both the agent view and the customer portal, create a realistic support issue, update it as an agent by assigning correct fields and priority, add an internal investigation note visible only to agents, reply to the customer, change the status to In Progress, and confirm the issue shows correct state across all views.

---

## Business Scenario

> **New Platform Orientation - April 9, 2026**
>
> Your company has just migrated from email-based ticketing to Jira Service Management. You are the first analyst to be trained on the platform. Before you take your first live call, your team lead asks you to log a test issue, explore the queue, update the ticket fields, add both types of comments, and confirm you can move a ticket through the workflow without assistance. Everything must be evidenced before you go live.

---

## Environment and Tools Used

| Component | Detail |
|---|---|
| **Platform** | Jira Service Management free tier |
| **Workspace URL** | nnamsotechie.atlassian.net |
| **Project** | Support (SUP) |
| **Issue Key Confirmed** | SUP-1 |
| **Request Type** | Get IT help |
| **Issue Created** | 09 April 2026 |
| **Agent Account** | Nnamso Techie |

---

## Steps Performed

---

### Phase 1 - Explore the Agent View Baseline

**Step 1.1 - Open the Agent Queue and Record the Empty State**

Log in to Jira Service Management and navigate to the Support project. Click Queues in the left sidebar then All open. Before any tickets are created, the queue is empty.

<img width="1365" height="720" alt="02 Agent view dashboard" src="https://github.com/user-attachments/assets/eacbda8c-2554-4277-97fe-799dccd0dbfe" />



> **Highlighted:** The All open queue shows zero items. The left sidebar confirms the full navigation structure which is the Queues, Service requests, Incidents, Journeys, Operations, and Knowledge Base. This is the primary working interface for every support analyst on the platform.

---

### Phase 2 - Create the First Issue

**Step 2.1 - Submit a Test Request via the Create Form**

Click the blue Create button and complete the issue creation form with a realistic IT support scenario.

<img width="600" height="508" alt="01 Create issue form" src="https://github.com/user-attachments/assets/ac59acd7-6108-45a1-b424-a018ae6c2462" />


> **Highlighted:** Project routes the issue to the correct team. Type determines the SLA that applies. Summary is the first thing an agent reads in the queue. Description provides the diagnostic context needed before the first investigation step.

---

### Phase 3 - Locate the Issue in the Agent Queue

**Step 3.1 - Confirm SUP-1 Appears in All Open Queue**

Return to Queues > All open. The new issue appears as 1 work item.

<img width="1117" height="315" alt="03 Ticket after creation" src="https://github.com/user-attachments/assets/bc6eca8f-b305-447d-a3a8-a9671341c52b" />


| Column | Value |
|---|---|
| **Issue Key** | **SUP-1** |
| Summary | Laptop cannot connect to company Wi-Fi |
| Reporter | Nnamso Techie |
| Assignee | Unassigned |
| Status | WAITING FOR SUPPORT |
| Created | 09/Apr/26 |

> **Issue key confirmed: SUP-1.** This is the reference number that appears in all communications, linked records, and audit trails. Record it in every ticket note and README as evidence of a real record.

---

### Phase 4 - Update Issue Fields

**Step 4.1 - Set Assignee and Priority**

Click SUP-1 to open the full issue. Navigate to the Details panel and update the fields.

<img width="370" height="478" alt="04 Open Ticket and Update Fields" src="https://github.com/user-attachments/assets/015f0959-ff06-43df-aaa1-ed0ecef06b8a" />



> **Highlighted:** Assignee (green) assigns ownership. Priority High (red) triggers the correct SLA target. Request Type (blue) confirms the customer portal form and SLA definition used.

---

### Phase 5 - Add an Internal Investigation Note

**Step 5.1 - Write the First Internal Note**

In the Activity section, click Add internal note. This comment is visible to agents only and never appears on the customer portal.

<img width="696" height="279" alt="05 Add internal comment" src="https://github.com/user-attachments/assets/d0b72cb4-cbb9-4677-a9a8-6f49b154fc90" />


Internal note content written:

> Contacted user to confirm issue. User on floor 2, machine WIN11-JO-07. Wi-Fi adapter visible in Device Manager but cannot obtain IP address.

> **Highlighted:** The yellow background and lock icon confirm this is an internal note. 

---

### Phase 6 - Change Status to In Progress

**Step 6.1 - Transition the Issue**

Click the status button at the top of the issue and select In Progress.

<img width="423" height="493" alt="06 status showing in progress" src="https://github.com/user-attachments/assets/f45cbee7-243f-44e2-9b5e-dc41e8c1f27f" />


> **Highlighted:** In Progress tells the queue that ownership has been taken. It tells the SLA timer that active work is happening. It also  signals to the customer portal that their request is being investigated. A ticket left in Waiting for Support when work has started is providing false information to all three audiences simultaneously.

---

### Phase 7 - Add a Customer Reply and Compare Both Comment Types

**Step 7.1 - Write the Customer Reply and Confirm the Difference**

In the Activity section, click Reply to customer and write a professional response. After saving, both comment types are visible side by side.

<img width="695" height="395" alt="07 reply to customer" src="https://github.com/user-attachments/assets/53f4359a-f776-4fe2-a17d-7a2bc4a5a644" />


| Type | Background | Visible To | Content |
|---|---|---|---|
| Reply to customer | White | Agent and Customer | Hi, thank you for raising this. We have received your request and a technician is investigating now. We will update you within 2 hours. |
| Internal note | Yellow | Agents only | Contacted user to confirm issue. User on floor 2, machine WIN11-JO-07. Wi-Fi adapter visible in Device Manager but cannot obtain IP address. |

> **Highlighted:** The white customer reply is at the top. The yellow internal note is below it. Both show the author name and timestamp. This side-by-side view is how analysts confirm the correct comment type was used before saving. Sending an internal note to a customer by mistake is a real and common error on platforms where both types exist.

---

## Issue Record

| Field | Value |
|---|---|
| **Issue Key** | **SUP-1** |
| Project | Support (SUP) |
| Summary | Laptop cannot connect to company Wi-Fi |
| Priority | High |
| Assignee | Nnamso Techie |
| Status | In Progress |
| Internal note | Confirmed - yellow background |
| Customer reply | Confirmed - white background |
| Created | 09 April 2026 |

---

## Help Desk Ticket Note

See `TICKET-SUP1-wifi-connectivity.md` in this folder.

---

## Outcome and Validation

| Check | Result |
|---|---|
| JSM workspace created - nnamsotechie.atlassian.net | Pass |
| Agent view explored - queue navigation confirmed | Pass |
| Issue created: Laptop cannot connect to company Wi-Fi | Pass |
| Issue key SUP-1 confirmed in queue | Pass |
| Priority set to High | Pass |
| Assignee set to Nnamso Techie | Pass |
| Internal note added - yellow background confirmed | Pass |
| Status changed to In Progress | Pass |
| Customer reply added - white background confirmed | Pass |
| Both comment types visible in Activity section | Pass |

---

## What I Learned

1. **The agent view and the customer portal serve two completely different audiences.** The portal is simple and reassuring for users. The agent queue is designed for triage, investigation, and communication management. Understanding both perspectives is the foundation of strong JSM practice.

2. **The comment type distinction is a professional and security boundary.** Internal notes (yellow) exist so analysts can record diagnostic detail without exposing it to the user. Customer replies (white) are the formal communication channel. Mixing them up is a real and recurring mistake.

3. **The issue key (SUP-1) is the single most important reference in any JSM ticket.** It appears in every notification, link, report, and audit query. Recording it at creation is the minimum documentation standard.

4. **Changing status to In Progress is both a workflow step and a communication signal.** It updates the queue, signals the SLA timer, and informs the customer portal simultaneously. Accurate status management is what makes queue reporting trustworthy.

5. **JSM is the dominant ticketing platform at technology companies** because it integrates with the full Atlassian suite. Fluency in JSM means you can work in any organisation using Atlassian tools, which represents a significant portion of the technology sector.

---

## Real World Relevance

Jira Service Management appears in the majority of help desk and IT support job descriptions at technology companies. It is built on the same foundation as Jira Software, meaning support analysts work alongside development and operations teams in the same toolchain. Escalations, change requests, and incident investigations can all be tracked without leaving the platform.

The ability to navigate JSM confidently is often the first skill evaluated in a live interview demonstration. A candidate who has already built and documented a JSM lab is demonstrating platform knowledge and the initiative to learn independently — which is precisely the combination that hiring managers in growing technology teams value most.

---

## Troubleshooting Reference

| Symptom | Likely Cause | Resolution |
|---|---|---|
| Issue not appearing in queue after creation | Status filter excluding the new issue | Set Status filter to All or Waiting for Support |
| Internal note visible to customer | Reply to customer used instead of Add internal note | Delete and re-add using Add internal note - confirm yellow background before saving |
| Cannot change Assignee | Insufficient permissions or no agent licences | Check Project Settings > Members - confirm Service Desk Agent role |
| Status button not showing In Progress | Workflow does not include In Progress transition | Check Project Settings > Workflows |
| SLA timer not visible | SLA not configured for this request type | Check Project Settings > SLAs |
| Priority field not visible | Priority not enabled for this project | Check Project Settings > Fields |
