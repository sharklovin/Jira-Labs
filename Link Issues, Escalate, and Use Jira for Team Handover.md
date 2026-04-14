# Link Issues, Escalate, and Use Jira for Team Handover

> **Author:** Nnamso Mkpong
>
> **Domain:** Jira Service Management - Problem Management, Issue Linking, Escalation Workflow
>
> **Environment:** Jira Service Management free tier - Support-1 project (SUP1)
>
> **Completed:** April 2026

---

## Objective

Use Jira Service Management issue linking to connect three individual Wi-Fi incident tickets to a parent Problem record, investigate the pattern, write a structured internal investigation summary, escalate to the network team with a complete handover note, and transition the Problem to Under Review. Demonstrate that a colleague can pick up the Problem record and continue without a briefing.

---

## Business Scenario

> **Floor 2 Wi-Fi Incident — 14 April 2026, 08:30**
>
> Three users on the second floor have each reported the same Wi-Fi connectivity issue this morning. All three cannot obtain an IP address and are completely unable to connect to the company network. The calls arrived within minutes of each other. This pattern - multiple users on the same floor, same failure, same time is a strong signal of an infrastructure fault rather than individual device problems. You raise a Problem record in Jira, link all three incidents to it, complete the first-line investigation, and escalate to the network team with everything they need to continue without calling you back.

This lab demonstrates one of the most important diagnostic skills in IT support: recognising when multiple separate tickets are symptoms of a single underlying cause. The ability to identify this pattern quickly, raise the correct record type, link the evidence, and escalate with a structured handover note prevents duplicated investigation work and protects SLA compliance for all three affected users simultaneously.

---

## Environment and Tools Used

| Component | Detail |
|---|---|
| **Platform** | Jira Service Management free tier |
| **Project** | Support-1 (SUP1) |
| **Incident Keys** | SUP1-1, SUP1-2, SUP1-3 |
| **Problem Key** | SUP1-4 |
| **Link Type Used** | is caused by / causes |
| **Escalation Target** | Network Team |
| **Final Problem Status** | Under Review |

---

## When to Raise a Problem Record

> **This is the most important conceptual distinction in this lab. An Incident is a disruption. A Problem is the root cause of one or more incidents.**

```
INCIDENT
  Definition: A single disruption to normal service for one or more users
  Trigger:    One user reports a fault
  Goal:       Restore service as fast as possible even with a workaround
  Example:    SUP1-1  (Wi-Fi not working on WIN11-JO-07)
  Closure:    When the user confirms service is restored

PROBLEM
  Definition: The underlying cause of one or more incidents
  Trigger:    Pattern recognition - same fault, multiple users, same location/time
  Goal:       Find and fix the root cause to prevent future incidents
  Example:    SUP1-4 - Potential Wi-Fi infrastructure fault in floor 2 (multiple users affected)
  Closure:    When the root cause is identified, fixed, and incidents are prevented from recurring

KEY RULE
  Raise a Problem when:
  — Two or more incidents share the same symptom, location, or time window
  — A workaround resolves the incident but does not address the root cause
  — First-line investigation eliminates individual device or account causes
  — The fix requires infrastructure access beyond first-line scope
```

In this lab, three incidents share the same symptom (cannot obtain IP address), the same location (floor 2), and the same start time (approximately 08:30). This three-point pattern is strong enough to raise a Problem record immediately rather than investigating each ticket in isolation.

---

## Steps Performed

---

### Phase 1 - Create the Three Incident Tickets

**Step 1.1 - Log Each User Report as a Separate Incident**

Each of the three user calls is logged as an individual incident in the Support-1 queue. All three are type Report a system problem with the same description and the same SLA deadline.

<img width="1127" height="448" alt="01 3 incidents created" src="https://github.com/user-attachments/assets/f974698b-850d-4c75-8d20-a3e6eff45dda" />


> **Highlighted:** All 3 incidents share the same SLA deadline (Apr 21 09:11 AM) because they were created at the same time and have the same priority. The pattern is immediately visible in the queue which is 3 identical request types, 3 devices on the same floor, 3 identical symptoms, logged within minutes of each other. This is the signal to raise a Problem record.

---

### Phase 2 - Create the Parent Problem Record

**Step 2.1 - Raise a Problem Record as the Parent Issue**

Create a fourth issue of type Investigate a problem. Title: Potential Wi-Fi infrastructure fault - floor 2 multiple users affected. This is the parent record that will hold the investigation, the links, and the escalation.

<img width="1138" height="476" alt="02 parent problem record created " src="https://github.com/user-attachments/assets/a2a170b1-8ff3-4234-8702-94ba9a03a199" />


> **Highlighted:** Four issues now appear in the queue. The first 3 are the individual incidents. The fourth (green, bottom row) is SUP1-4. the Problem record of type Investigate a problem.

---

### Phase 3 - Link Each Incident to the Problem Record

**Step 3.1 - Link SUP1-1 to SUP1-4**

Open SUP1-1. Click the Link work item button. Select the relationship type is caused by and search for SUP1-4. Save the link.

<img width="735" height="508" alt="03 sup 1 linked to problem" src="https://github.com/user-attachments/assets/27c2c8d6-ba8b-48dd-b98a-79be87f79830" />


> **Highlighted:** The Linked work items section confirms the relationship is caused by pointing to SUP1-4 (Potential Wi-Fi infrastructure fault - floor 2 multiple users affected). The link type is caused by is directional. It means the incident exists because of the problem, not the other way around. 

---

**Step 3.2 - Link SUP1-2 to SUP1-4**

Open SUP1-2. Apply the same link: is caused by SUP1-4.

<img width="705" height="508" alt="04 sup 2  linked to problem" src="https://github.com/user-attachments/assets/b07b58b1-4207-47d4-af49-ca3249f03b1c" />


> **Highlighted:** SUP1-2 (Wi-Fi not working on WIN11-SA-03) is now linked to the same Problem record. The Linked work items section is identical in structure to SUP1-1 — consistent linking confirms all three incidents will be traceable from the Problem record.

---

**Step 3.3 - Link SUP1-3 to SUP1-4**

Open SUP1-3. Apply the same link: is caused by SUP1-4.

<img width="706" height="506" alt="04 sup 3  linked to problem" src="https://github.com/user-attachments/assets/81cdce2f-e14d-4d1f-bc36-63189042d704" />


> **Highlighted:** SUP1-3 (Wi-Fi not working on WIN11-AD-09) is linked to SUP1-4. All three incidents now carry the link. Any analyst who opens any of the three incident tickets will see the Problem record in the Linked work items section and can navigate directly to the investigation record.

---

### Phase 4 - Confirm All Three Links on the Problem Record

**Step 4.1 - Open SUP1-4 and Verify the Causes Section**

Open the Problem record SUP1-4. Navigate to the Linked work items section. Confirm all three incidents appear under the causes relationship.

<img width="704" height="176" alt="06problem linked issues confirmed" src="https://github.com/user-attachments/assets/560c18db-ab09-4be2-9220-3bab99596052" />

> **Highlighted:** All three incidents appear in the causes section of SUP1-4. This confirms the bidirectional linking is working correctly — each incident says is caused by the problem, and the problem says causes the incidents. The network team can now open SUP1-4 and see the full scope of impact (three users, three devices) without needing to search the queue.

---

### Phase 5 - Add the Investigation Summary

**Step 5.1 - Write the Internal Investigation Note on SUP1-4**

Add an internal note to the Problem record recording all first-line investigation findings. This is the evidence base for the escalation decision.

<img width="1153" height="593" alt="07 problem investogation notes" src="https://github.com/user-attachments/assets/69aeb579-d21e-4610-bb36-332f7a9bb010" />


Investigation note content:

> Three users affected on floor 2. All three machines cannot obtain a DHCP address from the floor 2 access point. Access point admin page not loading at 192.168.2.1. Issue began at approximately 08:30. Suspect access point hardware fault or VLAN configuration change overnight.

> **Highlighted:** The three linked incidents are visible at the top of the Problem record. The internal note (yellow background) contains the full investigation summary. The details panel on the right confirms the Request Type is Investigate a problem and Priority is Medium. This is the complete state of the record before escalation.

---

### Phase 6 - Add the Escalation Handover Comment

**Step 6.1 - Write the Network Team Handover Note**

Add a second internal note as the formal escalation handover. This note is addressed to the Network Team and must contain everything they need to continue without contacting first line.

)<img width="705" height="241" alt="08 escalation handover note" src="https://github.com/user-attachments/assets/dfb7d62f-e2b4-461b-9e86-18979c99420c" />


> **Highlighted:** The note is an internal note (yellow background, lock icon). It opens with the @NetworkTeam mention to ensure the correct team is notified. The body contains: the scope (three users, floor 2), the timeline (since 08:30), the suspected root cause (AP fault at 192.168.2.1), and all first-line steps already completed. A network engineer who reads this note can begin their investigation immediately without calling first line for a briefing.

> The three completed first-line steps are the most important element of the handover: AD accounts healthy (rules out authentication), DHCP server checked (rules out server-side DHCP), direct cable test confirmed (rules out general network failure). These three negative findings narrow the fault to the access point specifically  which is where the network team needs to look.

---

### Phase 7 - Transition the Problem to Under Review

**Step 7.1 - Update Status and Assignee**

Change the Problem record status to Under review. Assign to Nnamso Mkpong and confirm the details panel reflects the correct record type.

<img width="403" height="318" alt="09 project under review details" src="https://github.com/user-attachments/assets/73e3046a-adbf-4d5b-910f-e9779d2d5578" />


> **Highlighted:** The Under review status badge confirms the Problem has been escalated. The details panel confirms Request Type (Investigate a problem) and Priority (Medium). The Problem record is now the single source of truth for the floor 2 Wi-Fi fault.  Any update from the network team will be added here, and when the root cause is resolved, all three linked incidents can be updated and closed from the Problem record.

---

## Escalation Decision Reasoning

The escalation decision was made after completing three first-line diagnostic checks that eliminated individual causes and pointed to infrastructure:

**Check 1 - Active Directory accounts:** All three users confirmed healthy in AD. No account lockouts or authentication issues. This eliminates individual authentication failure as the cause.

**Check 2 - DHCP server:** DHCP server leases reviewed for other floors - normal activity confirmed. DHCP leases are failing only for floor 2 devices. This eliminates a server-side DHCP failure and narrows the fault to the floor 2 network segment.

**Check 3 - Direct cable test:** Connecting one device directly via Ethernet cable bypassed the wireless access point and confirmed full network connectivity. This confirms the wired infrastructure is healthy and the fault is specific to the wireless access point serving floor 2.

After these three checks, the access point at 192.168.2.1 is the only remaining candidate. The access point admin page is not loading which is consistent with either a hardware failure or a configuration change that isolated the management interface. Neither of these is within first-line scope. Escalation to the network team is the correct next action.

---

## Business Impact Note

> **Recognising a pattern and raising a Problem record is faster than solving three tickets individually.**

If SUP1-1, SUP1-2, and SUP1-3 had been worked independently, each analyst would have performed the same AD check, the same DHCP check, and the same cable test three times -wasting three sets of investigation effort on the same fault. By raising a Problem record after the first two tickets, all three investigation threads are consolidated into one record with one escalation.

This is also better for SLA management. Three individual High priority incidents with separate SLA clocks are harder to track than one Problem record that coordinates the response to all three. When the network team resolves the AP fault, all three incidents can be resolved simultaneously with a single update protecting SLA compliance for all three users at once.

---

## Help Desk Ticket Notes

See `TICKET-SUP1-4-wifi-problem.md` and `TICKET-INCIDENT-CLUSTER.md` in this folder.

---

## Outcome and Validation

| Check | Result |
|---|---|
| Three incidents created - SUP1-1, SUP1-2, SUP1-3 | Pass |
| Problem record created - SUP1-4 type: Investigate a problem | Pass |
| SUP1-1 linked to SUP1-4 with is caused by relationship | Pass |
| SUP1-2 linked to SUP1-4 with is caused by relationship | Pass |
| SUP1-3 linked to SUP1-4 with is caused by relationship | Pass |
| SUP1-4 shows all three incidents in causes section | Pass |
| Internal investigation summary added to SUP1-4 | Pass |
| Escalation handover note addressed to @NetworkTeam | Pass |
| All first-line steps documented in handover | Pass |
| Problem status transitioned to Under Review | Pass |
| Colleague can read SUP1-4 and continue without a briefing | Pass |

---

## What I Learned

1. **Pattern recognition is a diagnostic skill, not a technical one.** Three identical tickets from the same floor in the same 30-minute window is a pattern that any experienced analyst recognises immediately. Learning to spot this pattern early and raise a Problem record is faster and more effective than solving each ticket in isolation.

2. **The is caused by link type is directional and meaningful.** The relationship points from the incident to the problem: this incident exists because of this problem. This directionality allows the Problem record to display all affected incidents in its causes section, giving any analyst a complete impact picture from a single record.

3. **A handover note must contain three elements: scope, evidence, and completed steps.** Scope tells the receiving team how many users and what the impact is. Evidence tells them what the suspected root cause is. Completed steps tell them what has already been ruled out so they do not duplicate investigation. All three are required for a handover that enables continuation without a briefing.

4. **A Problem record is closed when the root cause is fixed, not when the service is restored.** Restoring service via a workaround (such as moving users to a different access point) resolves the incidents. It does not close the Problem - the root cause of the original AP failure still needs to be identified and corrected to prevent recurrence.

5. **Jira issue linking transforms a queue of individual tickets into a structured investigation.** Without linking, SUP1-1, SUP1-2, and SUP1-3 look like three unrelated tickets. With linking, they become a cluster that points to a single root cause. The linking is the difference between a reactive queue and an investigation record.

---

## Real World Relevance

Problem management is a core ITIL discipline that separates reactive support from proactive service management. In organisations that take ITIL seriously - financial services, healthcare, large enterprise - the ability to identify incident patterns, raise Problem records, and manage escalations through structured handover notes is a valued skill that distinguishes analysts who are ready for progression beyond first line.

In Jira Service Management specifically, the issue linking feature is one of the most commonly used but least understood features at first-line level. Analysts who can confidently raise a Problem, link three incidents to it, write a structured internal investigation, and escalate with a complete handover note are demonstrating second-line thinking while working from a first-line queue  which is exactly the profile that team leads look for when evaluating progression candidates.

---

## Troubleshooting Reference

| Situation | Correct Action | Common Mistake |
|---|---|---|
| Two or more tickets share the same symptom and location | Raise a Problem record and link the incidents | Investigating each ticket independently |
| Cannot find the Link work item button | Check the issue toolbar - look for the chain link icon or the three-dot menu | Trying to find it in the details panel |
| Link type is unclear | Use is caused by from the incident pointing to the problem | Using relates to which is correct but less precise |
| Problem record shows no linked incidents | Confirm the link was created from the incident side, not the problem side | Creating the link from the problem without the correct direction |
| Network team has no context when escalated | Add a handover note before changing the assignee | Changing the assignee without a note |
| Problem status does not include Under Review | Check Project Settings > Workflows for the Investigate a problem issue type | Trying to use a status from a different issue type |
