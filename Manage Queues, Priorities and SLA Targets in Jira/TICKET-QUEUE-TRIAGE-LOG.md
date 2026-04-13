# Morning Triage Session — Jira Queue Log

**Project:** Support (SUP)
**Date:** 13 April 2026
**Analyst:** Nnamso Mkpong
**Session Start:** 08:00
**Session End:** 11:30
**Total Issues:** 5 (SUP-7 through SUP-11)

---

## Queue State at Session Start

All five issues were in Waiting for Support status, unassigned, with SLA timers running from creation on 13/Apr/26.

| Key | Summary | Priority | SLA Deadline | Risk |
|---|---|---|---|---|
| SUP-7 | User locked out of laptop | Highest | Apr 16 09:09 AM | Critical — earliest deadline |
| SUP-8 | Outlook not syncing | High | Apr 17 01:11 PM | Elevated |
| SUP-9 | Printer offline | High | Apr 21 09:11 AM | Moderate |
| SUP-10 | Software installation request | Medium | Apr 21 09:11 AM | Low |
| SUP-11 | Password reset request | Low | Apr 22 01:12 PM | Minimal |

**Triage method used:** Sorted queue by Time to resolution ascending. SUP-7 moved to the top — earliest SLA deadline, actioned first.

---

---

## SUP-7 — User Locked Out of Laptop

**Priority:** Highest
**Status:** In Progress
**SLA:** Time to first response within 4h | Time to resolution within 24h (Apr 16 09:09 AM)
**Assignee:** Nnamso Mkpong

**Triage decision:** User is completely blocked. No workaround available — cannot log in to any system. Highest priority is confirmed correct. SLA target is 24 hours. Actioning immediately at start of shift.

**Customer reply sent:**

> We are investigating your issue urgently. Updates will follow shortly.

**Internal note:**

> User completely blocked, no workaround. SLA target: 24 hours. Actioning immediately.

**Status:** In Progress — active investigation underway.

**Next action:** Confirm whether the lockout is an Active Directory account lockout or a BitLocker/hardware issue. If AD lockout: unlock via ADUC, reset password, confirm user can log in. If BitLocker: retrieve recovery key from Azure AD and guide user through entry.

---

---

## SUP-8 — Outlook Not Syncing

**Priority:** High
**Status:** Waiting for Support
**SLA:** Time to resolution within 36h (Apr 17 01:11 PM)
**Assignee:** Nnamso Mkpong

**Triage decision:** High priority — user can partially work (can read older emails) but cannot receive new messages. SLA deadline is Apr 17 at 01:11 PM. Will be actioned after SUP-7 is stabilised. Within SLA target for current session.

**Internal note added:**

> High priority — Outlook sync failure. User has limited workaround (web browser OWA). SLA target: Apr 17 01:11 PM. Will action after P1 SUP-7.

**Status:** Waiting for Support — scheduled for mid-morning.

**Next action:** Check Outlook profile, cached credentials in Windows Credential Manager, and M365 service health dashboard for Exchange Online incidents.

---

---

## SUP-9 — Printer Offline

**Priority:** Medium
**Status:** Waiting for Support
**SLA:** Time to first response within 8h | Time to resolution within 36h (Apr 17 01:11 PM)
**Assignee:** Nnamso Mkpong

**Triage decision:** Medium priority — user has a functional workaround (PDF save and email for signature). SLA deadline is Apr 17 01:11 PM — within target for afternoon scheduling. No immediate breach risk.

**Internal note added:**

> User has a workaround available. SLA target: 24 hours. Scheduled for this afternoon.

**Status:** Waiting for Support — scheduled for afternoon session.

**Next action:** Check printer IP address in the print server, confirm whether the printer obtained a new DHCP address, and test connectivity from the print server. Likely cause is a DHCP lease expiry or network configuration change.

---

---

## SUP-10 — Software Installation Request

**Priority:** Medium
**Status:** Waiting for customer
**SLA:** Time to first response within 12h | Time to resolution within 48h (Apr 21 09:11 AM)
**Assignee:** Nnamso Mkpong

**Triage decision:** Medium priority — software installation request requires additional information before work can begin. Which application, which version, which user account, and whether admin approval has been obtained. Transitioning to Waiting for customer. SLA clock paused.

**Internal note added:**

> Awaiting additional information from user before proceeding.

**Customer reply sent:**

> Hi, thank you for your request. To process the software installation, I need the following information: the name and version of the application required, confirmation that this software has been approved by your manager, and the machine name or asset tag of the device it should be installed on. Please reply to this message with these details and I will proceed as soon as I receive them.

**Status:** Waiting for customer — SLA timer paused until user responds.

**Note for handover:** If no response by 17:00 today, send a chase reply. If no response by end of business tomorrow, escalate to the user's manager.

---

---

## SUP-11 — Password Reset Request

**Priority:** Low
**Status:** Resolved
**SLA:** Time to first response within 16h | Time to resolution within 60h (Apr 22 01:12 PM)
**Assignee:** Nnamso Mkpong

**Triage decision:** Low priority — straightforward password reset. No workaround needed for a password reset as the user simply needs their credentials updated. Resolved end to end in a single session. SLA well within target.

**Investigation:**

Opened SUP-11. Confirmed the user's identity via employee ID before performing the reset. Navigated to Active Directory Users and Computers (documented workflow — not available in JSM directly). Reset the password to a temporary value. Enabled the User must change password at next logon option. Confirmed the user logged in successfully with the new temporary password and set their own permanent password.

**Internal note:**

> Issue investigated. Password reset completed. User confirmed working.

**Customer reply:**

> Your password has been reset. Please confirm everything is working correctly.

**Status:** Resolved — Done badge confirmed. SLA met.

---

## Session Close Summary

| Key | Summary | Final Status | SLA |
|---|---|---|---|
| SUP-7 | User locked out of laptop | IN PROGRESS | Within target — 24h |
| SUP-8 | Outlook not syncing | WAITING FOR SUPPORT | Within target — 36h |
| SUP-9 | Printer offline | WAITING FOR SUPPORT | Within target — 36h |
| SUP-10 | Software installation request | WAITING FOR CUSTOMER | Paused — awaiting user info |
| SUP-11 | Password reset request | RESOLVED | Met — 60h target |

**SLA breach count this session:** 0

**Actions outstanding at session end:**

SUP-7: Investigation continues — update due before Apr 16 09:09 AM.

SUP-8: Action mid-morning — Outlook profile and credential review.

SUP-9: Action afternoon — print server and printer IP check.

SUP-10: Chase user if no reply by 17:00 today.

**Documented by:**
Nnamso Mkpong
IT Support Portfolio — Jira Service Management Lab Series
