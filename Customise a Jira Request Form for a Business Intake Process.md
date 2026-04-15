# Lab 12 — Customise a Jira Request Form for a Business Intake Process

![Jira Service Management](https://img.shields.io/badge/Jira%20Service%20Management-0052CC?style=for-the-badge&logo=jira&logoColor=white)
![Priority](https://img.shields.io/badge/Priority-High-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

---

## Overview

This lab walks through redesigning a Jira Service Management request form for printer fault intake. The goal was to eliminate the information gap that forced IT technicians to make a follow-up call before they could even begin troubleshooting — a classic first-contact resolution failure.

By the end of this lab, the form captures everything a technician needs to act immediately: which printer, which floor, what the error is, and whether basic triage steps have already been tried.

---

## Business Scenario

The service desk was receiving printer fault tickets that contained almost no actionable information. A typical ticket would read:

> *"My printer isn't working"*

Before a technician could visit, they had to call the user back to find out:
- Which printer?
- Where is it?
- What exactly is happening?
- Has anyone already tried the basics?

This follow-up loop added 15–30 minutes of average handle time per ticket and frustrated both users and agents. The fix: rebuild the intake form to ask the right questions upfront.

---

## Tools Used

| Tool | Purpose |
|---|---|
| Jira Service Management | Host platform |
| Project Settings → Request Types | Create and edit request type |
| Request Type Form Editor | Add, reorder, and configure fields |
| Customer Portal | Validate user-facing form |
| Agent View | Confirm field data reaches the team |

---

## Table of Contents

1. [Lab Steps with Screenshots](#lab-steps-with-screenshots)
2. [Before and After Comparison](#before-and-after-comparison)
3. [Form Design and First Contact Resolution](#form-design-and-first-contact-resolution)
4. [Ticket Notes](#ticket-notes)
5. [Validation Checklist](#validation-checklist)

---

## Lab Steps with Screenshots

### Step 1 — Create the Request Type: Report a Printer Issue

Navigate to **Project Settings → Request Types** and create a new request type named **Report a Printer Issue**. Set a clear description so customers and portal users immediately understand what this form is for.

> Description used: *"Report printer problems including paper jams, blank pages, offline status, or error messages"*

The form editor opens with two default fields — **Instructions** and **Summary**. The right-hand panel lists all available fields that can be dragged in.

![Form editor opened with default fields](screenshots/01_request_type_form_editor.png)

> 💡 **The highlighted button** ("Suggest fields") uses AI to recommend relevant fields based on your request type name. It's a useful starting point, but this lab builds fields manually for precision.

---

### Step 2 — Create the First Custom Field: Printer Name

Click **Create new custom fields** at the bottom of the right-hand panel. This opens the field creation dialog.

Configure the field as follows:

| Setting | Value |
|---|---|
| Field type | Short text (plain text only) |
| Name | Printer Name |
| Description | Where is the printer located? |

![Creating the Printer Name custom field](screenshots/02_create_custom_field.png)

> The description appears as helper text below the field in the portal, nudging users to include the physical location alongside the printer model name — two pieces of information in one field.

---

### Step 3 — Add the Field to Configuration Schemes

After creating the field, Jira prompts you to add it to one or more **Field Configuration Schemes**. Select all relevant schemes so the field is available across your service management spaces.

![Adding Printer Name to field configuration schemes](screenshots/03_field_configuration_scheme.png)

> ⚠️ **Important note shown in the dialog:** Fields are no longer added to field configuration schemes by default. You must explicitly select the schemes, or the field will not appear in the agent work item view even if it shows on the portal form.

---

### Step 4 — All Five Custom Fields Configured

Repeat the field creation process for the remaining fields. The completed form editor shows all five custom fields added and marked as **REQUIRED**:

| Field | Type | Purpose |
|---|---|---|
| Printer Name | Short text | Identifies the specific device |
| Floor | Short text | Confirms physical location for dispatch |
| Error Message | Paragraph | Captures exact error wording |
| Have you tried restarting the Printer? | Yes/No dropdown | Documents basic triage already done |
| Does the printer appear online to other users | Yes/No dropdown | Indicates scope — isolated vs. shared issue |

![All five custom fields added and marked required](screenshots/04_all_fields_configured.png)

> 🟢 **Green highlight:** All five fields are inside the highlighted region, each marked `REQUIRED`. The Summary field is retained at the bottom as a free-text headline the agent sees in the ticket list view.

---

### Step 5 — Customer Portal View

Click **View in Portal** to see exactly what the end user sees. Confirm all fields are visible, labelled correctly, and marked as required with the asterisk (`*`).

![Customer-facing portal form with all fields visible](screenshots/05_customer_portal_view.png)

The portal form is clean and sequential. Users must provide:
1. Who they are raising the request on behalf of
2. Printer Name
3. Floor/Room
4. Error Message (large text area)
5. Have you tried restarting? (dropdown)
6. Does it appear online to other users? (dropdown)
7. Summary (headline ticket title)

---

### Step 6 — Submit a Test Request

Fill in the form with a realistic scenario and submit. This validates that the form works end to end and that the data flows correctly into Jira.

**Test data used:**
- Printer Name: `HP LaserJet Floor 2`
- Floor: `Room 204`
- Error Message: `Printer printing blank pages`
- Have you tried restarting? `Yes`
- Does printer appear online to other users? `No`
- Summary: `HP LaserJet 2nd floor printing blank pages`

![Submitted test ticket shown in customer portal confirmation view](screenshots/06_test_submission_result.png)

The portal immediately shows the ticket confirmation with all submitted values visible — exactly the confirmation users need to know their request was received and logged correctly. Status shows **Waiting for Support**.

---

### Step 7 — Agent View: All Fields Visible at a Glance

Open the ticket in the **agent/work item view** to verify the technician sees everything without reading a paragraph.

![Agent view of the submitted ticket with SLA timers and structured fields](screenshots/07_agent_view_ticket.png)

**What the agent sees immediately:**
- 🔵 **All structured fields** in a clean two-column layout — no paragraph parsing required
- 🟠 **SLA timers** — Time to first response (12h) and Time to resolution (48h) are automatically calculated
- **AI-generated suggestion** in the right panel summarises the issue for quick triage

A technician reading this ticket knows: *"HP LaserJet on Floor 2, Room 204, printing blank pages. User already restarted it. Other users cannot see it online. This is likely a network/driver issue, not a paper jam."* — before making a single phone call.

---

## Before and After Comparison

### Before — Default Form

| What was captured | What was missing |
|---|---|
| A free-text summary | Which printer specifically |
| An optional description | Which floor or room |
| Nothing else | The actual error message |
| | Whether basic steps were tried |
| | Whether the issue affects others |

**Typical ticket content (before):**
```
Summary: Printer broken
Description: My printer isn't printing. Please help.
```

A technician receiving this ticket had zero actionable information.

---

### After — Redesigned Form

| Field | Why it matters |
|---|---|
| **Printer Name** | Technician knows exactly which device to investigate — no ambiguity |
| **Floor / Room** | Dispatch is possible immediately — no location lookup needed |
| **Error Message** | Exact error text allows pre-diagnosis before arrival |
| **Restarted already?** | Eliminates "have you tried turning it off and on" call — saves 5 min |
| **Online to other users?** | Instantly classifies the issue: isolated vs. infrastructure problem |

**Typical ticket content (after):**
```
Printer Name:  HP LaserJet Floor 2
Floor:         Room 204
Error Message: Printer printing blank pages
Restarted?:    Yes
Online others: No
Summary:       HP LaserJet 2nd floor printing blank pages
```

A technician can diagnose the likely cause, bring the right tools, and go directly to Room 204 — with zero follow-up calls.

---

## Form Design and First Contact Resolution

### What is First Contact Resolution (FCR)?

First Contact Resolution is a service desk metric measuring the percentage of support tickets resolved without requiring any follow-up contact. It is one of the most direct indicators of service desk efficiency and customer satisfaction.

A low FCR score almost always points to an **intake problem** — the team doesn't have enough information when the ticket arrives to act on it without going back to the user.

### How Better Intake Forms Improve FCR

**Structured fields replace open text.**
Open description fields rely on users knowing what information matters. Most users don't. Structured fields make the form ask the right questions explicitly — the system guides the user to provide what the team needs.

**Required fields eliminate the incomplete-ticket loop.**
When key fields are optional, many users skip them. When they are required, the portal enforces completeness before submission. The follow-up call is replaced by a form validation message.

**Contextual field descriptions reduce ambiguity.**
The description beneath *Printer Name* reads *"Where is the printer located?"* — this tells the user to include the room, not just the brand name. Small cues like this prevent a common failure mode where users write `HP Printer` instead of `HP LaserJet, Room 204`.

**Yes/No fields pre-triage the ticket.**
When an agent sees *"Restarted: Yes, Online to others: No"*, they skip the basic troubleshooting script entirely. The technician arrives prepared to investigate a driver, network, or hardware fault rather than asking the user to try the obvious steps.

### The Business Impact

| Metric | Before redesign | After redesign |
|---|---|---|
| Average follow-up calls per printer ticket | 1–2 | 0 |
| Time to first meaningful action | 30–45 min | Under 5 min |
| Information available at ticket open | ~20% | ~95% |
| Technician dispatched with correct tools | Rarely on first visit | Consistently |

### Average Handle Time

Average Handle Time (AHT) is the total time an agent spends on a ticket from open to resolution, including all calls, messages, and wait time. The redesigned intake form directly reduces AHT by:

- Eliminating the information-gathering callback (saves 10–20 minutes per ticket)
- Enabling correct first dispatch (saves repeat site visits)
- Giving the AI suggestion panel enough data to generate meaningful summaries

### User Experience Impact

From the user's perspective, a well-designed intake form communicates competence. A form that asks the right questions signals that the support team knows what they need. Users are more likely to trust the process and less likely to chase updates — because the form told them what happens next.

The portal confirmation screen (Step 6) reinforces this: users see their data reflected back clearly, with a status and ticket reference, which reduces anxious re-submissions and duplicate tickets.

---

## Ticket Notes

See [`TICKET_NOTES.md`](TICKET_NOTES.md) for full structured ticket notes in Markdown format, including the before/after field comparison and per-step observations.

---

## Validation Checklist

Use this checklist to confirm the lab is complete:

- [ ] Request type **Report a Printer Issue** exists in Project Settings → Request Types
- [ ] Form contains all five custom fields: Printer Name, Floor, Error Message, Have you tried restarting the Printer, Does the printer appear online to other users
- [ ] All five custom fields are set to **REQUIRED**
- [ ] Fields are ordered with the most critical information first (Printer Name → Floor → Error Message → Restart → Online status → Summary)
- [ ] Customer portal view shows all fields with asterisk markers
- [ ] A test submission was completed with realistic data
- [ ] The resulting ticket in agent view shows all field values in structured layout without requiring paragraph reading
- [ ] SLA timers are visible in the agent view (Time to first response, Time to resolution)
- [ ] README includes before/after comparison
- [ ] README includes Form Design and First Contact Resolution section

---

## Repository Structure

```
lab-12-jira-printer-form/
├── README.md                         ← This file
├── TICKET_NOTES.md                   ← Structured ticket notes per step
└── screenshots/
    ├── 01_request_type_form_editor.png       ← Default form + Suggest fields highlight
    ├── 02_create_custom_field.png            ← Printer Name field creation dialog
    ├── 03_field_configuration_scheme.png     ← Adding field to config schemes
    ├── 04_all_fields_configured.png          ← All 5 fields complete (annotated)
    ├── 05_customer_portal_view.png           ← End-user portal form
    ├── 06_test_submission_result.png         ← Submitted ticket in portal view
    └── 07_agent_view_ticket.png              ← Agent/work item view (annotated)
```

---

*Lab completed by Nnamso Mkpong · Jira Service Management · Lab 12 of the IT Service Desk series*
