# Customise a Jira Request Form for a Business Intake Process

> **Author:** Nnamso Mkpong
>
> **Domain:** Jira Service Management - Request Type Customisation, Form Design, Field Configuration
>
> **Environment:** Jira Service Management free tier - Support-1 project (SUP1)
>
> **Completed:** April 2026

---

## Objective

Redesign the printer fault intake form in Jira Service Management to capture the information a technician actually needs before they leave their desk. Add five structured custom fields, set all of them as required, validate the form from the customer portal, submit a test request, and confirm every field value appears cleanly in the agent view without the agent having to read a paragraph.

---

## Business Scenario

> **Printer Fault Intake Problem - Ongoing**
>
> The service desk keeps receiving printer tickets that say things like "my printer isn't working." Before a technician can do anything, they have to call the user back to find out which printer, which floor, what the error message says, and whether anything has already been tried. That follow-up call takes 15 to 30 minutes and happens on almost every printer ticket. The fix is not a process change. It is a form change. If the intake form asks the right questions up front, the technician has everything they need before the ticket is even assigned to them.

This lab demonstrates something that is easy to overlook: the quality of your intake form directly determines the quality of your tickets. A bad form produces bad tickets. A structured form that asks the right questions produces tickets that are ready to act on immediately. This is one of the fastest wins available to any service desk team.

---

## Environment and Tools Used

| Component | Detail |
|---|---|
| **Platform** | Jira Service Management free tier |
| **Project** | Support-1 (SUP1) |
| **Request Type** | Report a Printer Issue |
| **Test Ticket** | SUP1-6 |
| **Fields Added** | Printer Name, Floor, Error Message, Have you tried restarting the Printer, Does the printer appear online to other users |
| **Final Status** | Waiting for Support |

---

## Why Intake Forms Matter

> **This is the core idea behind the lab. The form is not paperwork. It is your first diagnostic tool.**

```
BEFORE REDESIGN
  What the form captured:   A free-text summary
  What it missed:           Which printer, which floor, the error message,
                            whether the user restarted it, whether others are affected
  What happened next:       Technician calls user back before doing anything
  Time lost per ticket:     15 to 30 minutes

AFTER REDESIGN
  What the form captures:   Printer Name, Floor, Error Message, Restart attempted,
                            Online status for other users, Summary headline
  What it misses:           Nothing a first-line technician needs to begin work
  What happens next:        Technician reads the ticket and goes directly to the right room
  Time lost per ticket:     Zero

KEY RULE
  Add a custom required field when:
  - You find yourself asking the same follow-up question on every ticket
  - A free-text field is producing answers that vary too widely to be useful
  - You need a yes or no answer and users are writing paragraphs instead
  - The technician cannot dispatch without knowing the answer
```

A good intake form does not slow users down. It guides them. When the form asks "Where is the printer located?" the user does not have to figure out what information is useful. The form tells them. That shift - from open box to structured questions - is where the time saving comes from.

---

## Steps Performed

---

### Phase 1 - Create the Request Type and Open the Form Editor

**Step 1.1 - Navigate to Project Settings and Open the Request Type**

Go to Project Settings, then Request Types. Select or create a request type called Report a Printer Issue. Open the form editor. The default state shows two fields: Instructions (collapsible) and Summary (required). Nothing else.

Set the request type description to something specific. The description appears above the form in the portal, so it has to tell the user exactly what this form is for before they start filling it in.

Description used:
> Report printer problems including paper jams, blank pages, offline status, or error messages

<img width="1165" height="589" alt="01 Request type form editor" src="https://github.com/user-attachments/assets/114ea4e1-6394-404f-967f-524b65f20ed9" />


> **Highlighted:** For this lab, fields were built manually to match the exact language used in real printer tickets. The right-hand panel create new custom field where you can manually build your fields.

---

### Phase 2 - Create the Custom Fields

**Step 2.1 - Create the Printer Name Field**

Click Create new custom fields at the bottom of the right-hand panel. The Create field dialog opens.

| Setting | Value |
|---|---|
| **Field type** | Short text (plain text only) |
| **Name** | Printer Name |
| **Description** | Where is the printer located? |

<img width="339" height="549" alt="02 create custom field" src="https://github.com/user-attachments/assets/c6e0596d-0752-434c-9413-8d30f57e50ba" />


> The description beneath the field name is not a label. It is a prompt. "Where is the printer located?" tells the user to include the physical location alongside the printer model. That small addition means one field does the work of two without making the form longer.

---

**Step 2.2 - Add the Field to Configuration Schemes**

After saving the field, Jira shows a dialog to add the new field to field configuration schemes. This step is not optional. If you skip it, the field will appear on the portal form but will not appear in the agent's work item view.

<img width="337" height="550" alt="03 printer name config" src="https://github.com/user-attachments/assets/393ea5c6-b72e-4561-a24b-7c761f66c8ef" />


> **Important:** The dialog warns that fields are no longer added to field configuration schemes by default. This changed in recent Jira Cloud versions. Select all relevant schemes before clicking confirm. In this lab, all three schemes were selected: System Default Field Configuration, Jira Service Management Field Configuration Scheme for Space SUP, and Jira Service Management Field Configuration Scheme for Space SUP1.

---

### Phase 3 - Add All Five Custom Fields

**Step 3.1 - Complete the Remaining Four Fields**

Repeat the field creation process for each remaining field. The full set of five fields added to the form:

| Field | Type | Why This Field |
|---|---|---|
| **Printer Name** | Short text | Identifies the specific device - technician knows which printer before arrival |
| **Floor** | Short text | Confirms the physical location so dispatch is immediate |
| **Error Message** | Paragraph | Captures the exact error wording - enables pre-diagnosis before site visit |
| **Have you tried restarting the Printer?** | Yes/No dropdown | Documents whether basic triage is done - technician does not ask the same question again |
| **Does the printer appear online to other users** | Yes/No dropdown | Tells the technician if this is an isolated fault or a shared infrastructure issue |

All five fields were set to REQUIRED. The Summary field was kept at the bottom as the one-line ticket headline that appears in the queue.

<img width="870" height="595" alt="04 All fields configured" src="https://github.com/user-attachments/assets/836bca6c-db18-4824-aa2c-4a7aac0e7363" />


> **Highlighted:** The green box covers all five custom fields. Every one of them shows the REQUIRED badge. The field order was set deliberately: Printer Name and Floor first so the technician knows where to go, then Error Message so they know what to expect, then the two yes/no fields to establish what has already been ruled out, then Summary last as the headline. This order mirrors the order a technician thinks through a printer fault.

---

### Phase 4 - Validate the Portal View

**Step 4.1 - Switch to Portal View and Check Every Field**

Click View in Portal from the form editor. This shows exactly what the customer sees when they raise a request.

<img width="1132" height="625" alt="06 Test submission results" src="https://github.com/user-attachments/assets/3ee3e2d8-bbff-4623-983b-a1a63f7abc40" />


Confirmed in the portal:
- All five custom fields are visible
- All five are marked with an asterisk (required)
- Error Message renders as a multi-line text area
- Have you tried restarting and Does the printer appear online both render as dropdowns
- Summary is present at the bottom
- The form is clean and the sequence of questions makes logical sense from a user's perspective

---

### Phase 5 - Submit a Test Request

**Step 5.1 - Fill in the Form With Realistic Data and Submit**

Use the portal form to submit a test ticket that matches a real printer fault scenario. Do not use placeholder text. Fill in the fields the way an actual user would.

Test data used:

```
Printer Name:                              HP LaserJet Floor 2
Floor:                                     Room 204
Error Message:                             Printer printing blank pages
Have you tried restarting the Printer?:    Yes
Does the printer appear online?:           No
Summary:                                   HP LaserJet 2nd floor printing blank pages
```

<img width="1132" height="625" alt="06 Test submission results" src="https://github.com/user-attachments/assets/51c16e4f-1d10-4611-9e73-58069bb40548" />


> The portal confirmation screen shows the ticket as SUP1-6. All submitted values are visible on screen. Status is Waiting for Support. The user can see exactly what was recorded without opening anything else. This reduces re-submissions and duplicate tickets because the user can confirm their own data before walking away.

---

### Phase 6 - Confirm the Agent View

**Step 6.1 - Open the Ticket in the Work Item View**

Click View work item from the portal confirmation. This opens the ticket in the agent view - the same view a technician would see when the ticket lands in their queue.

<img width="1102" height="588" alt="07  agent view ticket" src="https://github.com/user-attachments/assets/acc90184-f6d4-4c60-a863-16f75fdadd03" />


> **Blue highlight:** Every field value is visible in a clean structured layout. The technician reads down the left side and immediately knows the printer (HP LaserJet Floor 2), the room (Room 204), the fault (blank pages), what has been tried (restarted - yes), and the scope (not visible to other users - no).
>
> **Orange highlight:** SLA timers appear automatically in the right panel. Time to first response is set to within 12 hours. Time to resolution is set to within 48 hours. These were calculated from the moment the ticket was submitted, not from when an agent opened it.
>
> The AI suggestion panel on the right has already summarised the issue: "User reports blank pages when printing from an HP LaserJet on the 2nd floor." The agent has enough context to diagnose before they even get up from their desk.

---

## Before and After Comparison

### Before - What the Default Form Captured

| What was captured | What was missing |
|---|---|
| A free-text summary | Which printer specifically |
| An optional description field | Which floor or room number |
| Nothing else | The exact error message |
| | Whether the user had already restarted |
| | Whether other users were also affected |

A real ticket before the redesign looked like this:

```
Summary:     Printer not working
Description: My printer stopped working this morning and I cannot print anything.
             Please help as soon as possible.
```

A technician reading that ticket has nothing to work with. They cannot go anywhere, prepare anything, or make any diagnostic assumptions. The follow-up call is unavoidable.

---

### After - What the Redesigned Form Captures

A real ticket after the redesign looks like this:

```
Printer Name:    HP LaserJet Floor 2
Floor:           Room 204
Error Message:   Printer printing blank pages
Restarted?:      Yes
Online others?:  No
Summary:         HP LaserJet 2nd floor printing blank pages
```

A technician reading that ticket knows: go to Room 204, the HP LaserJet is printing blank pages, the user has already restarted it so that is ruled out, and the printer is not visible to other users on the network which points to a local driver or hardware fault rather than a network issue. They can bring the right tools and go directly to the right room. No call needed.

---

## Form Design and First Contact Resolution

### What First Contact Resolution Means

First Contact Resolution (FCR) is the percentage of support requests that are fully resolved without any follow-up contact. It is one of the most direct measures of service desk quality. A high FCR score means users get answers quickly and agents are not spending time chasing information they should have had from the start.

A low FCR score almost always points to an intake problem. If agents are constantly calling users back to ask basic questions, the form is not doing its job.

### How a Better Form Improves FCR

**Structured fields replace guesswork.** When a user sees a free-text description box, they write whatever comes to mind. When they see a field labelled Floor with the description "Which room is the printer in?", they write Room 204. The structure of the question shapes the quality of the answer.

**Required fields close the gaps.** Optional fields get skipped. When the five key fields are required, the portal will not let the user submit until all five are filled in. The follow-up call is replaced by a form validation step that happens in the user's browser.

**Yes/No dropdowns create consistent data.** When a user types their answer to "did you restart it?", you might get "yes", "I tried that", "I restarted it twice", or "yes but it didn't help". When a dropdown has two options - Yes and No - you always get a clean answer. That clean answer can be filtered, reported on, and used in automation rules. Free text cannot.

**Field order shapes the user's thinking.** The sequence of questions on the form is not arbitrary. Printer Name and Floor come first because those are the most urgent pieces of information for dispatch. Error Message comes next because it requires the most user effort. The yes/no questions come last because they are fast to answer and build on what the user has already described. Summary comes last of all because by the time a user has answered five specific questions, they can write a clear one-line headline.

### The Business Impact

| Metric | Before | After |
|---|---|---|
| Average follow-up calls per printer ticket | 1 to 2 | 0 |
| Time before technician can act | 15 to 30 minutes | Under 5 minutes |
| Information available when ticket opens | Around 20% | Around 95% |
| Technician dispatched with correct preparation | Rarely on first visit | Consistently |

### What This Looks Like for the Technician

Before the redesign, a technician picking up a printer ticket had to open it, read a vague description, call the user, wait for the user to answer, ask four or five questions, write the answers in a comment, and then start investigating. That process took 20 to 30 minutes before any actual work began.

After the redesign, the technician opens the ticket, reads five structured fields in about 10 seconds, and goes to Room 204 with the right tools. The form has done the triage work that the phone call used to do.

This is not a small improvement. Across a service desk handling 20 or 30 printer tickets a week, eliminating the follow-up call from each one saves hours of agent time every single week. And from the user's perspective, the experience is better too. They filled in a form, got a confirmation, and a technician arrived who already knew what the problem was.

---

## Help Desk Ticket Notes

See `TICKET_NOTES.md` in this folder for full per-step observations, decisions made at each point, and lessons from the field configuration scheme step that catches a lot of people out.

---

## Outcome and Validation

| Check | Result |
|---|---|
| Request type Report a Printer Issue created | Pass |
| Form description set and visible in portal | Pass |
| Printer Name field created as short text with location prompt | Pass |
| All five fields added to the form | Pass |
| All five fields set to required | Pass |
| Fields added to all three configuration schemes | Pass |
| Customer portal shows all fields with asterisk markers | Pass |
| Yes/No fields render as dropdowns in the portal | Pass |
| Test submission completed with realistic data | Pass |
| Ticket SUP1-6 created and confirmed in portal | Pass |
| Agent view shows all five field values in structured layout | Pass |
| SLA timers visible in agent view | Pass |
| Zero follow-up information needed after ticket submission | Pass |

---

## What I Learned

1. **The field description is more valuable than the field name.** "Printer Name" as a label tells users what to type. "Where is the printer located?" as the description tells users why it matters and what level of detail to include. Small copy changes like this produce measurably better responses.

2. **The configuration scheme step is the one that breaks everything silently.** If you skip adding the field to configuration schemes, the field shows up on the portal form and vanishes from the agent view. There is no error. It just disappears. Always confirm field configuration scheme assignment after creating a custom field.

3. **Field order is not just aesthetic - it is functional.** Putting Summary first sounds logical but it produces worse summaries because users have not thought through the details yet. Putting Summary last means users write it after answering four specific questions, which produces cleaner one-line headlines that are genuinely useful in the queue view.

4. **Yes/No dropdowns are worth the extra setup.** It feels like a minor choice at the time, but a yes/no dropdown produces consistent filterable data. A free-text field produces noise. Six months later when you want to run a report on how many printer tickets were submitted by users who had already restarted the device, the dropdown field gives you the answer in two seconds. The free-text field gives you nothing.

5. **The form is the first impression.** A well-designed form tells users that the support team knows what information they need. It builds confidence before anyone speaks to anyone. Users who fill in a clear structured form are more patient about resolution time than users who submitted a vague ticket and heard nothing back for two hours.

---

## Real World Relevance

Form design in ITSM is a first-line skill that has second-line and management-level impact. At first-line level, a better intake form means fewer callbacks and faster resolution. At team lead level, structured field data means you can build dashboards, automate routing, and identify recurring issues by filtering on field values. At management level, clean intake data is what makes SLA reporting meaningful rather than just a count of tickets opened and closed.

Jira Service Management's request type editor is one of the most direct ways a support analyst can influence team performance without needing any permissions above project settings. Being able to identify a broken intake process, redesign the form, configure the fields correctly, and validate the full flow from portal to agent view is a skill that translates directly into process improvement work, which is exactly the kind of contribution that gets noticed at progression reviews.

---

## Troubleshooting Reference

| Situation | Correct Action | Common Mistake |
|---|---|---|
| Field appears on portal but not in agent view | Go back to the field settings and add it to all field configuration schemes | Assuming the field was saved correctly - the config scheme step is separate |
| Suggest fields button recommends wrong fields | Ignore it and create fields manually with precise names | Using suggested fields without reviewing them against real ticket language |
| Users are submitting blank required fields | Check the field is set to required in the form editor, not just labelled as required | Labelling a field "Required" in the name without actually setting the required toggle |
| Yes/No field is not showing as a dropdown in the portal | Confirm the field type was set to dropdown or select list during creation | Creating it as a short text field and adding yes/no as a placeholder |
| Field order in agent view does not match portal order | The portal order and the work item view order are controlled separately - reorder in the work item view tab | Assuming changing the portal order changes the agent view automatically |
| Test ticket shows but fields are empty | The field was not added to the request type form - it exists in the system but is not on this specific form | Confusing a field existing in the field library with it being on the form |
