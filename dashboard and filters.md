# Use Jira Dashboards and Filters to Demonstrate Service Desk Performance

> **Author:** Nnamso Mkpong
>
> **Domain:** Jira Service Management - Dashboards, Gadgets, Saved Filters, JQL, Performance Reporting
>
> **Environment:** Jira Service Management free tier - Support-1 project (SUP1)
>
> **Completed:** April 2026

---

## Objective

Build a Jira dashboard called Weekly Service Desk Review containing four gadgets that together tell the complete story of service desk performance for the week. Create saved filters for recurring use. Write two JQL queries to extract resolved and high priority issue counts. Produce an analyst summary of the data as if presenting at the Friday afternoon team stand-up.

---

## Business Scenario

> **Weekly Service Desk Performance Review - Friday 19 April 2026**
>
> Your team lead has asked you to prepare the weekly performance dashboard before the Friday afternoon stand-up. The team needs to see three things at a glance: how many open issues there are and at what priority, how many were created and resolved this week, and whether anything high priority is sitting unresolved. You need to build the dashboard, configure each gadget correctly, save the filters so they can be reused every week, and write a five-sentence summary that a team lead could read out at the stand-up without any additional context.

This lab covers the reporting side of service desk work. Logging and resolving tickets is one half of the job. The other half is being able to look at the data, understand what it means, and communicate it clearly to people who were not in the queue all week. A dashboard that shows numbers without context is not a performance report. A written summary that interprets the numbers and recommends a focus for next week is.

---

## Environment and Tools Used

| Component | Detail |
|---|---|
| **Platform** | Jira Service Management free tier |
| **Project** | Support-1 (SUP1) |
| **Dashboard name** | Weekly Service Desk Review |
| **Gadgets added** | Pie Chart (Priority), Created vs Resolved Chart, Filter Results, Pie Chart (Status) |
| **Saved filters** | Filter for SUP, Filter for SUP1, Open High Priority Issues |
| **JQL Query 1** | project = "Support-1" AND status = Done AND resolved >= 2026-04-13 |
| **JQL Query 1 result** | 12 issues |
| **JQL Query 2** | project = "Support-1" AND status = Done |
| **JQL Query 2 result** | 12 of 12 issues |
| **Period reviewed** | 13 April 2026 to 19 April 2026 |

---

## What a Service Desk Dashboard Should Answer

> **A dashboard is not a collection of numbers. It is a set of answers to the questions a team lead asks every Friday. Build the gadgets around the questions, not the other way around.**

```
QUESTION 1 - What is the current priority split of open issues?
  Gadget:   Pie Chart grouped by Priority
  Why:      Shows whether the queue is dominated by high-urgency work
             or whether the team has capacity to handle lower priorities

QUESTION 2 - How many issues were created and resolved this week?
  Gadget:   Created vs Resolved Chart (last 7 days, daily)
  Why:      Shows throughput and whether the queue is growing or shrinking
             A resolved line above the created line means the queue is clearing
             A created line above the resolved line means backlog is building

QUESTION 3 - What high priority issues are still open?
  Gadget:   Filter Results using a saved JQL filter
  Why:      Forces a named list of tickets that need immediate attention
             The team lead can assign owners directly from this view

QUESTION 4 - What is the overall status health of the queue?
  Gadget:   Pie Chart grouped by Status
  Why:      Shows the proportion of issues in Done, In Progress, Open
             A queue that is mostly Done is healthy
             A queue with many Open and no In Progress means work is stalled

KEY RULE
  Place the most critical information in the top left gadget.
  Readers scan left to right, top to bottom.
  The first thing they see should be the most important thing they need to know.
```

---

## Steps Performed

---

### Phase 1 - Create the Dashboard

**Step 1.1 - Navigate to Dashboards and Create a New One**

Click Dashboards in the top navigation bar. Click Create dashboard. The Create dashboard dialog opens with a Name field, Description, and access controls for Viewers and Editors.

| Field | Value | Reason |
|---|---|---|
| **Name** | Weekly Service Desk Review | Descriptive, includes the cadence so it is findable in a list of dashboards |
| **Viewers** | Private | Only you can see it during setup - share after it is complete and validated |
| **Editors** | Private | Same reason - restrict edit access until the dashboard is production-ready |

<img width="450" height="520" alt="Create dashboard dialog with name Weekly Service Desk Review and Private access settings" src="screenshots/01_create_dashboard_dialog.png" />

> **Blue highlight:** The Name field is required and pre-filled with the dashboard name. This is what appears in the Dashboards menu for every user with access.
>
> **Orange highlight:** Both Viewers and Editors are set to Private. This is the correct starting state. Once the dashboard is built and verified, Viewers can be changed to a specific group or All project roles so the team can access it. Do not share a dashboard until you have confirmed every gadget is showing the right data.

---

### Phase 2 - Add the Pie Chart Gadget (Priority View)

**Step 2.1 - Add a Pie Chart Grouped by Priority**

Click Add gadget on the empty dashboard. Search for Pie Chart and add it. In the gadget configuration, set the Project or Saved Filter to Support-1 and the Statistic Type to Priority. Enable Auto refresh every 15 minutes so the chart updates throughout the day without a manual page refresh.

<img width="410" height="580" alt="Pie Chart gadget configuration showing Support-1 as source and Priority as Statistic Type" src="screenshots/02_pie_chart_priority_config.png" />

> **Green highlight:** The project source is set to Support-1. This scopes the chart to the service desk project only. A chart sourced from All projects would include issues from other project types and would make the priority distribution meaningless.
>
> **Red highlight:** Statistic Type is set to Priority. This is the field the pie chart slices on. Each slice represents one priority level. The legend below the chart shows the count per slice, which is more useful than percentages for a small dataset.

---

### Phase 3 - Add the Created vs Resolved Chart

**Step 3.1 - Configure the Weekly Throughput Chart**

Add the Created vs Resolved Chart gadget. Configure it to show the last 7 days at daily granularity. Collection Operation is set to Count so each data point shows the actual number of issues on that day, not a running total.

| Setting | Value | Effect |
|---|---|---|
| **Project or Saved Filter** | Support-1 | Scopes to service desk project |
| **Period** | Daily | Shows day-by-day breakdown, not weekly aggregates |
| **Days Previously** | 7 | Shows the last 7 calendar days including today |
| **Collection Operation** | Count | Individual day totals, not cumulative |
| **Display Trend of Unresolved** | No | Keeps the chart clean - unresolved trend is shown in the status pie chart gadget |
| **Auto refresh** | Every 15 minutes | Keeps the data current during the stand-up |

<img width="410" height="640" alt="Created vs Resolved Chart configuration showing Daily period, 7 days previously, and Count collection operation" src="screenshots/03_created_vs_resolved_config.png" />

> **Blue highlight:** Period set to Daily and Days Previously set to 7. These two settings together define the time window. Daily granularity is the right choice for a weekly stand-up - it shows which specific day had high volume rather than blending the week into a single bar.
>
> **Green highlight:** Auto refresh is enabled. During a live stand-up, someone might resolve a ticket while the dashboard is being presented. The 15-minute refresh means the chart will update within a reasonable window without requiring a manual page reload.

---

### Phase 4 - Create the Saved Filter and Add the Filter Results Gadget

**Step 4.1 - Navigate to Filters and Create the Open High Priority Issues Filter**

Before adding the Filter Results gadget, the filter must exist as a saved filter. Navigate to the Filters section in Jira and click Create filter. Build the filter using JQL and save it with a descriptive name.

JQL used:
```
project = "Support-1" AND priority in (Highest, High) AND status != Done ORDER BY created ASC
```

<img width="1120" height="225" alt="Saved filters list showing Filter for SUP, Filter for SUP1, and Open High Priority Issues with star" src="screenshots/04_saved_filters_list.png" />

> **Blue highlight:** Three saved filters are present. Each one serves a specific purpose: Filter for SUP scopes to the SUP project key, Filter for SUP1 scopes to Support-1 with All roles visibility, and Open High Priority Issues is the filter used in the Filter Results gadget.
>
> **Orange highlight:** Open High Priority Issues has a gold star and shows 1 person has starred it. Starring a filter adds it to your quick navigation and makes it appear in gadget filter dropdowns immediately. Star any filter you plan to use regularly on dashboards.

**Step 4.2 - Configure the Filter Results Gadget**

Add the Filter Results gadget to the dashboard. Set the Saved Filter to Open High Priority Issues. Set Number of results to 10. Configure the columns to display Issue Type, Key, Summary, and Priority.

<img width="410" height="600" alt="Filter Results gadget configuration showing Open High Priority Issues filter and four columns" src="screenshots/05_filter_results_gadget_config.png" />

> **Red highlight:** The Saved Filter field is set to Open High Priority Issues. This connects the gadget to the filter created in the previous step. The gadget will show whatever the filter returns at the time of page load or refresh.
>
> **Green highlight:** Four columns are configured - Issue Type, Key, Summary, and Priority. These four columns give the team lead everything needed to triage from the dashboard without opening individual tickets. If the gadget showed only Key and Summary, the team lead would have to open each ticket to see the priority. Adding Priority to the column display saves that click.

---

### Phase 5 - Add the Status Pie Chart

**Step 5.1 - Add a Second Pie Chart Grouped by Status**

Add a second Pie Chart gadget. Set the Project or Saved Filter to Support-1 and the Statistic Type to Status. This gives a different view from the priority chart - instead of showing urgency distribution, it shows workflow state distribution. A healthy queue has most issues in Done or In Progress with few stuck in Open.

<img width="410" height="460" alt="Second Pie Chart gadget configuration showing Support-1 as source and Status as Statistic Type" src="screenshots/06_pie_chart_status_config.png" />

> **Red highlight:** Statistic Type is set to Status. This is the key difference from the first pie chart. The first pie chart slices by Priority (urgency). This one slices by Status (workflow state). Together they answer two different questions: how urgent is the work, and how far through the process is the work.

---

### Phase 6 - Dashboard in Use - Part A

**Step 6.1 - Review the Priority Chart and Created vs Resolved Trend**

With all gadgets saved and the dashboard refreshed, the first view shows the Priority pie chart on the left and the Created vs Resolved chart on the right.

<img width="1153" height="520" alt="Dashboard view showing Priority pie chart with 7 Medium and 5 Highest, and Created vs Resolved chart with spike on April 19" src="screenshots/07_dashboard_view_a.png" />

> **Blue highlight:** The Priority pie chart shows 12 total issues. 7 are Medium priority (blue slice) and 5 are Highest priority (red slice). The split is roughly 58% Medium and 42% Highest. This is a relatively high proportion of Highest priority work for a week - a normal week might see 20% or less at that level.
>
> **Orange highlight:** The Created vs Resolved chart shows a spike on 19 April 2026 where 12 issues were both created and resolved on the same day. The green line (resolved) matches the orange line (created) exactly - every issue raised this week was resolved the same week. The flat line for the preceding days shows no ticket activity before April 19, which is consistent with this being a lab environment where all tickets were created and completed in a single session.

---

### Phase 7 - Dashboard in Use - Part B

**Step 7.1 - Review the Status Chart and Filter Results Table**

Scrolling down the dashboard reveals the Status pie chart on the left and the Filter Results table on the right.

<img width="1153" height="620" alt="Dashboard view showing Status pie chart with all 12 issues Done, and Filter Results table listing all high priority issues" src="screenshots/08_dashboard_view_b.png" />

> **Green highlight:** The Status pie chart is entirely blue. All 12 of 12 issues in the project are in Done status. There are zero issues in Open, In Progress, or any other state. This is an exceptional result - a 100% resolution rate for the week. In a live service desk this would be a notable achievement worth calling out at the stand-up.
>
> **Red highlight:** The Filter Results table shows all 12 issues from the Open High Priority Issues filter. The table includes the issue key, parent reference, summary, status, and assignee. All items show DONE in the status column with Nnamso Mkpong as the assignee. The display shows 1-10 of 12 with page 2 containing the remaining two issues. Every high priority item was resolved.

---

### Phase 8 - JQL Query 1 - Issues Resolved This Week

**Step 8.1 - Run the Resolved This Week Query**

Navigate to the issue navigator (Issues > Search for Issues or the JQL bar at the top of a board view). Enter the following JQL and run it.

JQL Query 1:
```
project = "Support-1" AND status = Done AND resolved >= 2026-04-13
```

<img width="1127" height="530" alt="JQL query showing project Support-1 status Done resolved after April 13 2026 returning 12 results" src="screenshots/09_jql_query_resolved_this_week.png" />

> **Red highlight:** The JQL bar shows the complete query with the resolved date filter. The `resolved >= 2026-04-13` clause filters to issues that were moved to Done on or after April 13 - the start of the current week. This is the clause that makes this a weekly query rather than an all-time query.
>
> **Green highlight:** 12 results returned. All 12 are in Done status with Highest or Medium priority. The top five rows show the offboarding sub-tasks for James Okafor (SUP1-21 through SUP1-25) at Highest priority, followed by the Leaver parent issue, then the onboarding sub-tasks and parent issue from Lab 13.

**Query explanation:**

| Clause | Purpose |
|---|---|
| `project = "Support-1"` | Restricts results to the Support-1 service desk project |
| `status = Done` | Only includes issues that have been resolved, not open or in progress |
| `resolved >= 2026-04-13` | Only includes issues resolved on or after the start of this week |

---

### Phase 9 - JQL Query 2 - All Resolved Issues in the Project

**Step 9.1 - Run the Total Done Query**

Run a second query without the date filter to show the total resolved count across all time in the project. This is useful for comparing this week's performance against the overall project total.

JQL Query 2:
```
project = "Support-1" AND status = Done
```

<img width="1127" height="530" alt="JQL query showing project Support-1 and status Done returning 12 of 12 results total" src="screenshots/10_jql_query_all_done.png" />

> **Red highlight:** The JQL bar shows the simpler query - project and status only, no date filter. This returns every Done issue in Support-1 regardless of when it was resolved.
>
> **Green highlight:** The result count at the bottom shows 12 of 12. This is the same as Query 1 because all 12 issues in the project were created and resolved this week. In a mature project with months of history, Query 2 would return a much larger number than Query 1, and the ratio between them would show what percentage of the total project work was completed this week.

---

## Friday Stand-Up Analyst Summary

> This section is written as a verbal briefing for the Friday afternoon team stand-up. It should take under two minutes to read aloud.

---

This week the Support-1 service desk handled 12 issues across two HR workflows - a new starter onboarding for Chiamaka Bello and an urgent offboarding for James Okafor - with all 12 tickets created and resolved within the same day, giving us a 100% weekly resolution rate and a clean queue going into the weekend. The priority split was 7 Medium and 5 Highest, with the Highest priority tickets all belonging to the offboarding workflow which was correctly escalated and completed before end of business on Thursday. The Created vs Resolved chart confirms no backlog carry-over - the resolved line matched the created line exactly, meaning we closed every ticket we opened this week with zero outstanding work. There were no SLA breaches recorded - all 12 issues show Done resolution with the offboarding sub-tasks completed at 16:45 on the day of departure, well within any reasonable same-day SLA. For next week, the focus should be on two areas: first, confirming that the Chiamaka Bello onboarding completed successfully now that her start date has passed, which means checking her systems access is live and logging any follow-up issues if she reports problems on her first day; second, reviewing whether the volume of Highest priority tickets this week was a one-off driven by the urgent offboarding or whether there is a pattern emerging that warrants adjusting our triage thresholds.

---

## JQL Reference - Weekly Reporting Queries

These queries are designed to be run every Friday as part of the weekly reporting process. Save each one as a filter for quick access.

```sql
-- Query 1: Issues resolved this week (update the date every Monday)
project = "Support-1" AND status = Done AND resolved >= 2026-04-13

-- Query 2: All resolved issues in the project (all-time total)
project = "Support-1" AND status = Done

-- Query 3: Open high priority issues (live queue health check)
project = "Support-1" AND priority in (Highest, High) AND status != Done ORDER BY created ASC

-- Query 4: Issues created this week (volume intake check)
project = "Support-1" AND created >= 2026-04-13 ORDER BY created ASC

-- Query 5: Issues still open with no assignee (routing gap check)
project = "Support-1" AND status != Done AND assignee is EMPTY ORDER BY priority DESC
```

---

## Help Desk Ticket Notes

See `TICKET_NOTES.md` in this folder for gadget-by-gadget configuration notes, filter design decisions, JQL clause explanations, and observations on how to read the dashboard data correctly.

---

## Outcome and Validation

| Check | Result |
|---|---|
| Dashboard Weekly Service Desk Review created | Pass |
| Pie Chart gadget added - grouped by Priority | Pass |
| Created vs Resolved Chart added - last 7 days daily | Pass |
| Saved filter Open High Priority Issues created | Pass |
| Filter Results gadget added - uses saved filter | Pass |
| Filter Results shows Issue Type, Key, Summary, Priority columns | Pass |
| Second Pie Chart added - grouped by Status | Pass |
| Dashboard shows all four gadgets rendering correctly | Pass |
| JQL Query 1 run - resolved this week - returns 12 results | Pass |
| JQL Query 2 run - all Done - returns 12 of 12 | Pass |
| Priority split documented - 7 Medium, 5 Highest | Pass |
| 100% resolution rate confirmed from Status pie chart | Pass |
| No SLA breaches identified | Pass |
| Five-sentence analyst summary written in README | Pass |
| Analyst summary includes: volume, priority, resolution rate, breaches, recommendation | Pass |

---

## What I Learned

1. **Build gadgets around questions, not around available chart types.** The temptation is to add every available gadget and see what data appears. The correct approach is to write down the four or five questions the team lead asks every week and then find the gadget that answers each one. Gadgets without a clear question they are answering add visual noise without adding information.

2. **The saved filter is the foundation of the Filter Results gadget.** The gadget does not have its own JQL editor. It depends on a filter that already exists. Creating the filter first and then connecting the gadget to it is the right sequence. It also means the filter can be shared, starred, and reused independently of the dashboard.

3. **Auto refresh on gadgets matters for live presentations.** A dashboard that showed the correct data at 9am but is presented at 3pm without a refresh is showing stale information. Enabling 15-minute auto refresh on every gadget means the data is no more than 15 minutes old at any point during the stand-up.

4. **The Created vs Resolved chart tells a different story from the issue count.** A total of 12 issues resolved sounds like a good number. The chart adds the dimension of when - all 12 on the same day, not spread across the week. That spike pattern tells the team lead the workload was concentrated, not steady. Understanding workload distribution is more useful for staffing and planning than knowing the total.

5. **JQL date filters must be updated weekly.** The `resolved >= 2026-04-13` clause in Query 1 is hardcoded to a specific date. Every Monday that date needs to be changed to the start of the new week. Saving the filter with a note reminding you to update it prevents the dashboard from silently showing stale weekly data.

6. **A 100% resolution rate in a single session is a lab artefact.** In a real service desk environment, a 100% resolution rate for the week is exceptional. The Status pie chart showing all Done is accurate for this lab but would be unusual in production. When presenting real dashboards, the pattern to watch for is not 100% Done but rather the ratio of Done to In Progress to Open - and specifically whether anything has been sitting Open for more than 48 hours without moving to In Progress.

---

## Real World Relevance

Dashboard literacy is one of the skills that separates a first-line agent from someone ready for a team lead or analyst role. Any analyst can resolve tickets. Fewer can look at a week of ticket data and tell a coherent story about what happened, why the priority split looks the way it does, and what it implies for next week's workload.

In organisations with formal service desk governance - weekly reviews, monthly SLA reports, quarterly trend analysis - the ability to build a dashboard, write the JQL queries, and produce a written summary that non-technical stakeholders can read is a valued skill. Team leads who can do their own reporting are not dependent on a separate analytics team. They own the narrative about their team's performance.

The JQL skills developed in this lab are also directly transferable. Every Jira-based organisation uses JQL for filtering, reporting, automation, and escalation rules. An analyst who can write and read JQL is more effective at every level of the platform - from individual ticket management to organisation-wide dashboards.

---

## Troubleshooting Reference

| Situation | Correct Action | Common Mistake |
|---|---|---|
| Gadget shows no data after configuration | Check that the project or filter selected actually contains issues matching the criteria - an empty result set looks the same as a misconfiguration | Assuming the gadget is broken when the filter returns zero results |
| Filter does not appear in the gadget dropdown | Navigate to the filter, star it, then return to the gadget configuration - starred filters appear at the top of the dropdown | Searching for the filter name without starring it first |
| Created vs Resolved chart shows flat line | The date range may not match when issues were created - change Days Previously to a larger number like 30 to confirm the chart is working | Assuming the chart is misconfigured when the issue is the date range |
| JQL query returns no results | Remove clauses one by one starting from the right to find which clause is filtering out all results | Changing multiple clauses at once and not knowing which one was the problem |
| Priority pie chart shows unexpected categories | The chart uses whatever priority values exist in the project - if issues were logged with non-standard priorities they will appear as separate slices | Expecting only High, Medium, Low when the project has custom priority schemes |
| Dashboard refresh does not update gadget data | Each gadget has its own refresh button in the gadget header - the dashboard-level Refresh button refreshes all gadgets simultaneously | Refreshing the browser page which reloads the page but does not force gadget data to recalculate |
| Saved filter JQL returns different results than expected | Run the JQL in the Issue Navigator directly to see what it returns outside the gadget context - this isolates whether the issue is the JQL or the gadget configuration | Editing the gadget configuration without first testing the JQL in the Issue Navigator |
