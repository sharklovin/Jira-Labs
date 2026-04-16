# Ticket Notes - Lab 12: Customise a Jira Request Form

> These notes document what happened at each step, the decisions made, and the things worth knowing if you are reproducing this lab or adapting it for a different request type. They are written the way a real handover note should be written - specific enough that someone else could pick this up and continue without asking questions.

---

## Pre-Lab State

**Project:** Support-1 (SUP)
**Platform:** Jira Service Management (Cloud)
**Existing request types:** Default set from project creation - no printer-specific form existed
**Problem identified:** Agents receiving printer tickets with almost no actionable information, averaging one to two follow-up calls per ticket before dispatch was possible

---

## Step-by-Step Notes

---

### Step 1 - Open the Request Type Form Editor

**Action taken:** Navigated to Project Settings, then Request Types, then selected Report a Printer Issue and opened the form editor.

**What was there by default:**
- Instructions field - collapsible, no content, visible to portal users
- Summary field - required, single line, becomes the ticket title in the queue
- No other fields

**Decision made:** Build all five custom fields manually rather than using the Suggest fields button. The AI suggestions are useful as a starting point but the field names they produce do not always match the language agents and technicians actually use. When a technician sees a field called "Device Identifier" they hesitate. When they see "Printer Name" they know exactly what to type. The language on the form has to match the language on the floor.

**Request type description set to:**
> Report printer problems including paper jams, blank pages, offline status, or error messages

This matters more than it looks. The description appears above the form in the portal before the user touches anything. If the description is vague, users second-guess whether they are in the right place. A specific description reduces mis-categorised tickets where users file printer issues under a general IT request because they were not sure which form to use.

---

### Step 2 - Create the Printer Name Field

**Action taken:** Clicked Create new custom fields at the bottom of the right-hand panel. The Create field dialog opened.

**Field configured as:**

| Setting | Value | Reason |
|---|---|---|
| Field type | Short text (plain text only) | Printer names are short identifiers - a paragraph field would encourage users to write a description instead of a name |
| Name | Printer Name | Clear and direct |
| Description | Where is the printer located? | Prompts the user to include the room alongside the model name |

**Key observation:** The field description box is the most underused tool in Jira form design. Most teams leave it blank or repeat the field name. Using it as a directive - "Where is the printer located?" - does two things. It tells users what format the answer should be in, and it prompts them to include information they might not have thought to add. "HP LaserJet" is less useful than "HP LaserJet, Room 204". The description is what gets you the second half.

---

### Step 3 - Add the Field to Configuration Schemes

**Action taken:** After saving the Printer Name field, Jira automatically showed the dialog: Add Printer Name to field configuration scheme.

**Schemes selected:**
- System Default Field Configuration
- Jira Service Management Field Configuration Scheme for Space SUP
- Jira Service Management Field Configuration Scheme for Space SUP1

**Critical note:** The dialog explicitly states that fields are no longer added to field configuration schemes by default. This is a change from older Jira behaviour where creating a field added it everywhere automatically. The current behaviour requires you to opt in. If you miss this step, the field will appear on the portal form and the user can fill it in. But when the ticket is created and the agent opens the work item view, the field value is invisible. There is no warning. No error message. The data just does not appear. This is one of the most common configuration mistakes in Jira Service Management and it is hard to diagnose because everything looks correct on the surface.

**What to do if you have already missed this step:** Go to Project Settings, then Fields, find the field, click the three-dot menu, and add it to the configuration schemes from there.

---

### Step 4 - Add All Five Fields and Confirm Required Status

**Fields added in order:**

1. Printer Name - Short text - Required
2. Floor - Short text - Required
3. Error Message - Paragraph - Required
4. Have you tried restarting the Printer? - Yes/No dropdown - Required
5. Does the printer appear online to other users - Yes/No dropdown - Required

**Field type decisions:**

Printer Name and Floor use short text because they are identifiers, not explanations. A user who types "HP LaserJet, Room 204" into a short text field has given the technician exactly what they need. A paragraph field on the same question produces sentences like "It's the HP printer on the second floor near the coffee machine" which requires interpretation.

Error Message uses paragraph because error outputs are unpredictable in length. Some users will type three words. Some will paste a full error code. A paragraph field handles both without cutting anything off.

The two yes/no fields use dropdowns because the answer is binary and the data needs to be consistent. "Yes" and "No" in a dropdown produces the same answer format every time. Free text on the same question produces "yes", "Yes I did", "tried it twice", "yep", and "no but I can try" - none of which can be reliably filtered or counted.

**Field ordering rationale:**

The order is not cosmetic. Printer Name and Floor come first because if a ticket arrives and the agent can only read one thing before they have to act, those two fields are the ones that matter. Error Message comes third because it requires the most thought from the user and it makes sense to ask about identity and location before asking about symptoms. The two yes/no questions come fourth and fifth because they are quick to answer and they build on the error message the user just described. Summary comes last because a user who has just answered five specific questions can write a clear one-line headline. A user who sees Summary first writes "printer not working."

---

### Step 5 - Portal View Verification

**Action taken:** Clicked View in Portal from the form editor toolbar.

**What was confirmed:**
- All five custom fields visible in the correct order
- All five showing the asterisk required marker
- Error Message rendering as a resizable multi-line textarea
- Both yes/no fields rendering as dropdowns with a blank default option
- Summary present at the bottom
- Raise this request on behalf of field pre-populated with the logged-in user

**Observation worth noting:** The portal preview is a live view, not a cached one. Changes saved in the form editor appear in the portal preview immediately. If a field is missing from the portal view, it means the field was not saved to the form correctly - go back to the editor and check the field is actually on the form canvas, not just in the right-hand panel.

---

### Step 6 - Test Submission

**Action taken:** Submitted a test ticket via the portal using realistic data. No placeholder text. Every field filled in the way an actual user in a real fault scenario would fill it.

**Data entered:**

```
Raise on behalf of:                        Nnamso Mkpong (nnamsotechie@gmail.com)
Printer Name:                              HP LaserJet Floor 2
Floor:                                     Room 204
Error Message:                             Printer printing blank pages
Have you tried restarting the Printer?:    Yes
Does the printer appear online?:           No
Summary:                                   HP LaserJet 2nd floor printing blank pages
```

**Ticket created:** SUP1-6

**Portal confirmation screen showed:** All field values displayed correctly. Status set to Waiting for Support immediately on submission. Ticket reference SUP1-6 visible. Actions available: Escalate, Resolve this issue, Cancel request.

**Why using realistic test data matters:** If you test with placeholder text like "test" and "123", you confirm the form works mechanically but you do not learn anything about how the form performs in real use. Filling in the form the way a real user would reveals things like whether the question wording makes sense, whether the dropdown options cover the actual answers users will give, and whether the summary a real user writes at the end is actually useful as a ticket title. All three of those are things you can fix before the form goes live.

---

### Step 7 - Agent View Validation

**Action taken:** Clicked View work item from the portal confirmation screen. This opened ticket SUP1-6 in the agent work item view.

**What the agent sees:**

| Field | Value displayed |
|---|---|
| Printer Name | HP LaserJet Floor 2 |
| Floor | Room 204 |
| Error Message | Printer printing blank pages |
| Have you tried restarting? | Yes (shown as a tagged pill) |
| Does it appear online to others? | No (shown as a tagged pill) |

**SLA panel (right side):**
- Time to first response: Apr 17 01:00 PM - within 12h
- Time to resolution: Apr 23 05:00 PM - within 48h

**AI suggestion panel:** "User reports blank pages when printing from an HP LaserJet on the 2nd floor." - Uses AI. Verify Results.

**What a technician can conclude from this ticket without making any calls:**
- Go to Room 204
- The printer is an HP LaserJet
- It is printing blank pages - this points to toner, drum, or paper feed
- The user has already restarted it, so a soft reset is already ruled out
- The printer is not visible online to other users, which means this is probably a local issue rather than a network or print server fault
- Bring toner and drum inspection tools. Do not bring network troubleshooting kit as the first priority.

**Lab objective confirmed:** The technician can act immediately on this ticket without any follow-up contact. The form has done the triage work.

---

## Summary of What Changed

| Element | Before | After |
|---|---|---|
| Number of meaningful fields | 1 (free text summary) | 6 (5 structured + summary) |
| Required fields | 1 | 6 |
| Follow-up calls needed | 1 to 2 per ticket | 0 |
| Time before technician can act | 15 to 30 minutes | Under 5 minutes |
| Data available for filtering and reporting | None | 2 yes/no fields immediately filterable |

---

## Things Worth Knowing Before You Run This Lab

**The configuration scheme step trips people up every time.** Do not skip it and do not assume it happens automatically. After every field you create, confirm the scheme assignment. It takes 10 seconds and it is the difference between a field that works and a field that appears to work but silently drops data in the agent view.

**Required does not mean required in the description.** Setting a field as required in the form editor is a toggle, not a naming convention. A field named "Printer Name (required)" that does not have the required toggle enabled will not enforce completion. The asterisk in the portal comes from the toggle, not the name.

**Test with realistic data before going live.** Mechanical testing confirms the plumbing works. Realistic testing tells you whether the form is actually usable. They are different things and you need both.

**The yes/no dropdown options need to be configured to say Yes and No.** When you create a dropdown field, it does not automatically populate with Yes and No. You have to add those options during field creation. If the dropdown in the portal is empty or shows different options, go back to the field configuration and check the option values.

---

*Nnamso Mkpong - Lab 12 - Jira Service Management IT Service Desk Series*
