# Jira Ticket - SUP-7

**Issue Key:** SUP-7

**Project:** Support (SUP)

**Summary:** User locked out of laptop

**Priority:** Highest

**Status:** In Progress

**Assignee:** Nnamso Mkpong

**Reporter:** Nnamso Mkpong

**Created:** 13 April 2026

**SLA - Time to first response:** Within 4h

**SLA - Time to resolution:** Within 24h (Apr 16 09:09 AM)

---

## Ticket Details

| Field | Value |
|---|---|
| Issue Key | SUP-7 |
| Request Type | Get IT help |
| Priority | **Highest** |
| Urgency | None (set at creation) |
| Impact | None (set at creation) |
| Assignee | Nnamso Mkpong |
| Reporter | Nnamso Mkpong |
| SLA Response Target | Within 4 business hours |
| SLA Resolution Target | Within 24 business hours — Apr 16 09:09 AM |
| Status | In Progress |

---

## Priority Justification

Highest priority was assigned because the user is completely locked out of their laptop. There is no workaround available as the user cannot log in to Windows, cannot access any company applications, and cannot perform any work. This is the textbook definition of a Highest priority issue: complete user blockage with no alternative path.

SLA target of 24 business hours applies. Given the issue was created on 13 April at 09:09 AM, the resolution deadline is 16 April at 09:09 AM on the Sample 9-5 Calendar.

---

## Timeline

**13 April 2026 - 09:09 AM - Issue Created**

SUP-7 created in the Support project. Assigned Highest priority. Status: Waiting for Support. All five issues from the morning rush are now in the queue.

**13 April 2026 - 08:00 (shift start) - Triage Session**

Queue sorted by SLA time to resolution ascending. SUP-7 identified as the most urgent issue and earliest deadline of all five open tickets. Assigned to Nnamso Mkpong. Investigation begun.

**13 April 2026 - 08:05 - Status Changed to In Progress**

Status transitioned from Waiting for Support to In Progress. SLA timer continues running — In Progress does not pause the clock.

**13 April 2026 - 08:06 - Customer Reply Sent**

> We are investigating your issue urgently. Updates will follow shortly.

First response sent within the 4-hour SLA target. Time from creation to first response: less than 1 business hour.

**13 April 2026 - 08:06 - Internal Note Added**

> User completely blocked, no workaround. SLA target: 24 hours. Actioning immediately.

Triage decision documented. Note explains the priority rationale and confirms immediate action.

---

## Investigation

**Possible causes for laptop lockout:**

Active Directory account lockout: the most common cause. Three or more failed password attempts trigger a lockout policy. Resolved by unlocking the account in Active Directory Users and Computers (ADUC) and resetting the password.

BitLocker recovery screen: triggered by a firmware update, hardware change, or TPM configuration change. Resolved by retrieving the recovery key from Azure AD or Active Directory and guiding the user through entry.

Hardware failure preventing boot: screen or keyboard issue preventing login screen from appearing correctly. Less likely if the user can see a login prompt.

Windows profile corruption: user profile fails to load, presenting a temporary profile or a blank desktop. Resolved by logging in with a local admin account and repairing or rebuilding the domain profile.

**Next diagnostic steps:**

Confirm with the user whether the screen is showing a Windows login prompt, a BitLocker recovery screen, or something else entirely. This one question narrows the cause to one of the above categories before any remote session is opened.

---

## Escalation Assessment

At the time of this lab session, the investigation is in progress. If the root cause is confirmed as an AD lockout, resolution is expected within 15 minutes via standard ADUC procedure. If the cause is BitLocker, resolution requires the recovery key retrieval workflow documented in Lab 19. If the cause is hardware failure, escalation to the hardware team would be required with a potential loan device arranged for the user.

No escalation has been triggered at the time of this note.

---

## Handover Note

If this ticket reaches another analyst before resolution:

The user is completely blocked. SUP-7 is the highest priority item in the queue and must be actioned before any other issue. SLA deadline is Apr 16 09:09 AM. First response has been sent. The next action is to open a remote session with the user and identify the specific lockout type (AD lockout vs BitLocker vs hardware) before attempting any fix.

Do not close this ticket without user confirmation that access has been restored.

---

## Closure Note (Pending)

This ticket was not resolved in this lab session. It remains In Progress. The closure note will be added when resolution is confirmed by the user.

Expected closure content: root cause identified (AD lockout / BitLocker / other), fix applied, user confirmed access restored, no further action required.

**Documented by:**
Nnamso Mkpong
IT Support Portfolio 
Jira Service Management Lab Series
