# Incident Cluster Log - Floor 2 Wi-Fi Fault

**Problem Record:** SUP1-4

**Incidents:** SUP1-1, SUP1-2, SUP1-3

**Project:** Support-1 (SUP1)

**Date:** 14 April 2026

**Analyst:** Nnamso Mkpong

---

## Cluster Overview

Three separate incident tickets arrived between 08:30 and 09:00 on 14 April 2026. All three reported the same symptom, from the same floor, at approximately the same time. All three are linked to Problem record SUP1-4 using the is caused by relationship in Jira.

| Key | Summary | Device | Status | Linked To |
|---|---|---|---|---|
| SUP1-1 | Wi-Fi not working on WIN11-JO-07 | Floor 2 | Open | SUP1-4 (is caused by) |
| SUP1-2 | Wi-Fi not working on WIN11-SA-03 | Floor 2 | Open | SUP1-4 (is caused by) |
| SUP1-3 | Wi-Fi not working on WIN11-AD-09 | Floor 2 | Open | SUP1-4 (is caused by) |

---

---

## SUP1-1 - Wi-Fi not working on WIN11-JO-07

**Issue Key:** SUP1-1
**Request Type:** Report a system problem
**Priority:** (set at creation)
**Status:** Open
**Assignee:** Unassigned
**Reporter:** Nnamso Mkpong
**Created:** 14 April 2026
**SLA Deadline:** Apr 21 09:11 AM

**Description entered at creation:**

> User reports Wi-Fi not working. Located on floor 2. Device cannot obtain IP address.

**Linked work items:**

Is caused by SUP1-4 - Potential Wi-Fi infrastructure fault — floor 2 multiple users affected (Open)

**First response sent:**

Not yet sent - awaiting network team resolution before communicating to users. If the AP is restored today, users will receive a single communication confirming the issue is resolved rather than multiple interim updates.

**Triage note:**

This ticket arrived first among the three. Initial assumption was an individual device fault. When SUP1-2 arrived minutes later with the same symptom from the same floor, the pattern was recognised and SUP1-4 was raised. SUP1-1 was then linked to SUP1-4 using is caused by.

**Status at handover:** Open - awaiting resolution of Problem record SUP1-4.

---

---

## SUP1-2 - Wi-Fi not working on WIN11-SA-03

**Issue Key:** SUP1-2
**Request Type:** Report a system problem
**Priority:** (set at creation)
**Status:** Open
**Assignee:** Unassigned
**Reporter:** Nnamso Mkpong
**Created:** 14 April 2026
**SLA Deadline:** Apr 21 09:11 AM

**Description entered at creation:**

> User reports Wi-Fi not working. Located on floor 2. Device cannot obtain IP address.

**Linked work items:**

Is caused by SUP1-4 - Potential Wi-Fi infrastructure fault - floor 2 multiple users affected (Open)

**Triage note:**

This ticket was the second to arrive. Its arrival confirmed the pattern. SUP1-2 shares the same symptom (cannot obtain IP address), location (floor 2), and approximate start time (08:30) as SUP1-1. At this point the Problem record SUP1-4 was raised immediately without waiting for further tickets.

**Status at handover:** Open - awaiting resolution of Problem record SUP1-4.

---

---

## SUP1-3 - Wi-Fi not working on WIN11-AD-09

**Issue Key:** SUP1-3
**Request Type:** Report a system problem
**Priority:** (set at creation)
**Status:** Open
**Assignee:** Unassigned
**Reporter:** Nnamso Mkpong
**Created:** 14 April 2026
**SLA Deadline:** Apr 21 09:11 AM

**Description entered at creation:**

> User reports Wi-Fi not working. Located on floor 2. Device cannot obtain IP address.

**Linked work items:**

Is caused by SUP1-4 - Potential Wi-Fi infrastructure fault - floor 2 multiple users affected (Open)

**Triage note:**

This ticket arrived third, further confirming the infrastructure fault hypothesis. Three separate devices on the same floor with the same symptom and the same start time is a definitive infrastructure pattern. All first-line investigation was consolidated into Problem record SUP1-4 rather than duplicated across all three tickets.

**Status at handover:** Open - awaiting resolution of Problem record SUP1-4.

---

## Cluster Resolution Instructions

When the network team confirms the floor 2 access point has been restored:

Step one: Add a closure note to SUP1-4 confirming the root cause and the fix applied. Example: Root cause confirmed as access point hardware failure at 192.168.2.1. AP replaced by network team at 11:30. Floor 2 Wi-Fi restored. All three linked incidents to be closed.

Step two: Open each of the three incidents (SUP1-1, SUP1-2, SUP1-3) and send a customer reply confirming resolution. Example: Hi, the Wi-Fi connectivity issue on floor 2 has been resolved by the network team. Please confirm your device can connect to the company Wi-Fi. Let us know if you experience any further issues.

Step three: Transition all three incidents to Resolved after user confirmation.

Step four: Transition SUP1-4 to Resolved or Closed after all three linked incidents are confirmed resolved.

---

## Why Cluster Management Matters

Working these three tickets as a cluster rather than individually produced the following efficiency gains:

First-line investigation was performed once. The AD check, DHCP check, and cable test were completed once and documented in SUP1-4 rather than being repeated independently for each ticket.

Escalation was a single handover note rather than three separate escalations. The network team received one structured note covering all three users rather than three separate notifications that might have been actioned independently.

Resolution will be a coordinated close rather than three separate resolutions. All three incidents will receive the same customer communication at the same time, ensuring consistent user experience.

The total time saving from cluster management compared to individual investigation is estimated at 30 to 45 minutes for a single analyst, and significantly more if three separate analysts had been assigned one ticket each.

**Documented by:**
Nnamso Mkpong
IT Support Portfolio 
Jira Service Management Lab Series
