# Jira Service Management Ticket

**Issue Key:** SUP-1
**Project:** Support (SUP)
**Platform:** nnamsotechie.atlassian.net
**Status:** In Progress

---

## Ticket Details

| Field | Value |
|---|---|
| Issue Key | SUP-1 |
| Request Type | Get IT help |
| Summary | Laptop cannot connect to company Wi-Fi |
| Priority | High |
| Assignee | Nnamso Techie |
| Reporter | Nnamso Techie |
| Created | 09 April 2026 |
| Last Updated | 09 April 2026 |
| Status | In Progress |
| SLA | Time to resolution — running |

---

## User Request (Customer Portal Submission)

**Summary entered by user:** Laptop cannot connect to company Wi-Fi

**Description entered by user:**

My laptop will not connect to the company Wi-Fi after this morning's Windows update.

---

## First Response to Customer

**Sent:** 09 April 2026 (visible on customer portal)

> Hi, thank you for raising this. We have received your request and a technician is investigating now. We will update you within 2 hours.

---

## Internal Investigation Notes (Agents Only)

**Note 1 — 09 April 2026 — 4 minutes after creation — Nnamso Techie:**

> Contacted user to confirm issue. User on floor 2, machine WIN11-JO-07. Wi-Fi adapter visible in Device Manager but cannot obtain IP address.

---

## Investigation Log

**09 April 2026 — Ticket received via agent Create form**

Issue logged as SUP-1 under the Support (SUP) project. Type set to Get IT help. Summary: Laptop cannot connect to company Wi-Fi. Description confirms the issue began after a Windows update this morning.

Initial triage: Wi-Fi connectivity failure following a Windows update is a known failure pattern. Likely candidates are a driver update that changed the network adapter configuration, a Windows Update that reset a DHCP or DNS setting, or a Group Policy change applied alongside the update. This is a High priority issue — the user has no workaround and cannot connect to company resources.

**09 April 2026 — Fields updated**

Assignee: Nnamso Techie. Priority: High. Request Type: Get IT help confirmed.

**09 April 2026 — Status changed to In Progress**

Ticket moved from Waiting for Support to In Progress. SLA timer continues running.

**09 April 2026 — Internal note added**

Contacted user to confirm the issue. User is on floor 2 using machine WIN11-JO-07. Wi-Fi adapter is visible in Device Manager — this rules out a driver removal or hardware fault. The adapter exists but cannot obtain an IP address — this points to a DHCP client service issue, a network profile corruption, or an IP conflict introduced by the update.

Next diagnostic steps: check the DHCP client service status (services.msc), run ipconfig /release and ipconfig /renew to test DHCP lease renewal, check Event Viewer Application and System logs for network-related errors around the time of the update, and review the Windows Update history for any network adapter or TCPIP stack-related updates.

---

## Planned Resolution Path

If DHCP client service stopped: restart the service and test connection.

If network profile corrupted: delete the saved Wi-Fi profile, reconnect fresh, and test.

If IP conflict: check DHCP server for duplicate leases and release the conflicting address.

If driver update caused regression: roll back the network adapter driver in Device Manager and test.

---

## Outcome (Lab Simulation)

This ticket was created as part of a Jira Service Management orientation lab. The full resolution workflow — investigation, diagnostic steps, fix, and closure — would follow the planned resolution path above in a live environment.

**Evidence confirmed at end of lab session:**

Issue key SUP-1 exists in the Support project. Priority is High. Assignee is Nnamso Techie. Status is In Progress. One internal note is present with yellow background and lock icon. One customer reply is present with white background. Both are visible side by side in the Activity section.

---

## Comment Audit Trail

| Timestamp | Author | Type | Content Summary |
|---|---|---|---|
| 09/Apr/26 (creation) | Nnamso Techie | System | Issue created |
| 09/Apr/26 + 2 sec | Nnamso Techie | Reply to customer | Acknowledgement — investigating, update within 2 hours |
| 09/Apr/26 + 4 min | Nnamso Techie | Internal note | User on floor 2, WIN11-JO-07, Wi-Fi adapter visible, cannot obtain IP |
| 09/Apr/26 + 5 hrs | System | Status change | In Progress |

---

## Closure Note (To be completed in Lab 10)

This ticket will be resolved and closed as part of the Lab 10 queue management exercise. Resolution and closure note to follow.

**Documented by:**
Nnamso Mkpong
IT Support Portfolio — Jira Service Management Lab Series
