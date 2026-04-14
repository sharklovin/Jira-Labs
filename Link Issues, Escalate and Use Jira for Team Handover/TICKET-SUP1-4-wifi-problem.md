# Jira Problem Record — SUP1-4

**Issue Key:** SUP1-4
**Project:** Support-1 (SUP1)
**Issue Type:** Investigate a problem
**Summary:** Potential Wi-Fi infrastructure fault — floor 2 multiple users affected
**Priority:** Medium
**Status:** Under Review
**Assignee:** Nnamso Mkpong
**Reporter:** Nnamso Mkpong
**Created:** 14 April 2026

---

## Problem Record Details

| Field | Value |
|---|---|
| Issue Key | SUP1-4 |
| Request Type | Investigate a problem |
| Priority | Medium |
| Status | Under Review |
| Assignee | Nnamso Mkpong |
| Reporter | Nnamso Mkpong |
| Source | None |
| Knowledge Base | No related articles |
| Created | 14 April 2026 |
| Updated | 14 April 2026 (31 minutes after creation) |

---

## Linked Incidents (causes)

| Relationship | Key | Summary | Status |
|---|---|---|---|
| causes | SUP1-1 | Wi-Fi not working on WIN11-JO-07 | Open |
| causes | SUP1-2 | Wi-Fi not working on WIN11-SA-03 | Open |
| causes | SUP1-3 | Wi-Fi not working on WIN11-AD-09 | Open |

All three incidents are linked to this Problem record with the causes relationship. This means SUP1-4 is the root cause of all three incidents. When this Problem is resolved, all three linked incidents can be closed simultaneously.

---

## Incident Pattern Recognition — Trigger for Problem Raise

The following pattern triggered the Problem record creation:

Three separate incident tickets arrived within minutes of each other at approximately 08:30 on 14 April 2026. All three reported the same symptom (Wi-Fi not working, cannot obtain IP address), from the same location (floor 2), on different devices (WIN11-JO-07, WIN11-SA-03, WIN11-AD-09).

A single user with a Wi-Fi issue is an Incident. Three users on the same floor with the same symptom at the same time is a Problem.

The Problem record was raised after the second ticket arrived — before all three first-line checks were completed — because the two-ticket pattern was sufficient to indicate infrastructure fault.

---

## First-Line Investigation Log

**14 April 2026 — 08:45 — Initial triage**

Three incidents confirmed sharing the same symptom, location, and approximate start time. Problem record SUP1-4 raised. All three incidents linked using is caused by relationship.

**14 April 2026 — 09:00 — Active Directory check**

Reviewed all three user accounts in Active Directory Users and Computers. All three accounts are active, not locked, and have no authentication errors. Domain membership confirmed for all three devices. This eliminates individual authentication failure as the cause.

**14 April 2026 — 09:10 — DHCP server check**

Reviewed DHCP server lease table. Normal lease activity confirmed for floors 1, 3, and 4. No new leases issued for floor 2 devices since 08:25. This indicates the floor 2 devices stopped requesting DHCP leases at approximately the time the issue began — consistent with the access point failing rather than the DHCP server refusing leases.

**14 April 2026 — 09:20 — Direct cable test**

Connected WIN11-JO-07 directly to the nearest wall port on floor 2 via Ethernet cable, bypassing the wireless access point. Full network connectivity confirmed via DHCP lease obtained and internet access working. This confirms the wired infrastructure is healthy and the fault is specific to the wireless access point.

**14 April 2026 — 09:25 — Access point admin page check**

Attempted to load the access point admin page at 192.168.2.1 from a wired device on floor 2. Page did not load. Attempted ping to 192.168.2.1 — no response. The access point is not responding to either management traffic or wireless client association requests.

**Root cause hypothesis confirmed:** The floor 2 wireless access point at 192.168.2.1 has either failed (hardware fault) or lost network connectivity due to a configuration change applied overnight. This is outside first-line scope.

---

## Internal Investigation Note (Added to SUP1-4)

> Three users affected on floor 2. All three machines cannot obtain a DHCP address from the floor 2 access point. Access point admin page not loading at 192.168.2.1. Issue began at approximately 08:30. Suspect access point hardware fault or VLAN configuration change overnight.

---

## Escalation Handover Note (Added to SUP1-4)

> @NetworkTeam — escalating this to you. Three users on floor 2 affected since 08:30. All machines healthy — suspect AP fault at 192.168.2.1. First-line steps completed: AD accounts healthy, DHCP server checked (leases normal for other floors), direct cable test confirmed connectivity when bypassing the AP. Please review AP logs and the overnight change window.

---

## Escalation Decision Record

**Escalation decision made at:** 09:28 on 14 April 2026

**Reason for escalation:** The root cause has been isolated to the floor 2 access point at 192.168.2.1. The access point is not responding to management traffic or wireless association requests. Diagnosing and resolving an unresponsive access point requires physical access to the device and access to network infrastructure management systems — both outside first-line scope.

**Steps completed before escalation:** Three first-line checks completed and documented. No step was skipped. Each check eliminated one possible cause and narrowed the fault to the access point specifically.

**Information passed at escalation:** Scope (three users, floor 2), timeline (08:30), suspected root cause (AP fault at 192.168.2.1), all first-line steps completed with findings, AP admin page unreachable at 192.168.2.1, direct cable test result confirming wired infrastructure is healthy.

**Next action required by network team:** Review access point logs for 192.168.2.1. Review the overnight change window for any VLAN or network configuration changes applied between 20:00 on 13 April and 08:30 on 14 April. If AP has failed, arrange replacement or failover.

---

## Impact Assessment

| Metric | Value |
|---|---|
| Users affected | 3 |
| Floor | 2 |
| Devices affected | WIN11-JO-07, WIN11-SA-03, WIN11-AD-09 |
| Department affected | Not confirmed — pending user information |
| Workaround available | Wired connection via Ethernet cable |
| Business impact | Users can work via wired connection — partial workaround |
| Estimated downtime | Ongoing since 08:30 — network team to confirm resolution ETA |

---

## Handover Note for Next Analyst

If this Problem record is picked up by another analyst before the network team responds:

Do not close the linked incidents (SUP1-1, SUP1-2, SUP1-3) without confirming with the users that Wi-Fi has been restored. The current workaround (wired connection) is adequate for continued work but does not resolve the Problem.

If more than 2 hours pass with no update from the network team, send a chase note on SUP1-4 requesting an ETA and update the three linked incidents with a status note to keep the users informed.

If the AP has been replaced or reconfigured, request confirmation from the network team that floor 2 Wi-Fi is fully restored before closing this Problem record.

---

## Closure Note (Pending)

This Problem record remains open pending network team investigation and resolution of the floor 2 access point fault. Closure note will be added when the root cause is confirmed and all three linked incidents are resolved.

**Documented by:**
Nnamso Mkpong
IT Support Portfolio — Jira Service Management Lab Series
