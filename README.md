# IT Delivery & BAU Operations Tracker

**Jira Cloud · Confluence · Microsoft Excel**  
**Personal portfolio project — simulated IT Operations and software-delivery coordination**

> All incidents, work items, risks, dates, and team interactions are **simulated for learning**. This project does not use real banking data and is not affiliated with or endorsed by HSBC or any bank.

## Overview

This project simulates how an IT delivery and BAU operations coordinator tracks work items, documents blockers, maintains ticket hygiene, and prepares stakeholder reporting in a controlled enterprise-technology environment.

**Tools:** Jira Kanban, JQL and dashboards; Confluence playbooks and runbooks; Excel status and ageing reports.

## Verified Jira Snapshot — 30 October 2026

| Metric | Value |
|---|---:|
| Total tickets | 25 |
| To Do | 7 |
| In Progress | 8 |
| Blocked | 4 |
| Done (simulated status) | 6 |
| Open tickets | 19 |
| Overdue open tickets (due date before report date) | 9 |
| Actual stale tickets (not updated for 7+ days) | 0 |
| Simulated stale labels | 3 |
| Unassigned | 0 |

**Evidence:** This snapshot was checked against an exported `Jira.csv` file. The public dataset in `data/` is sanitized and contains a limited field subset. These metrics are a snapshot, not a live Jira integration. Jira created and updated timestamps are from the export; some due dates intentionally precede ticket creation because this is a historical simulation. Status `Done` is a simulation state and must not be interpreted as verified production deployment or remediation.

## What I Built

### Jira — tracking and governance

- Team-managed Kanban board: **To Do → In Progress → Blocked → Done**.
- 25 simulated BAU and IT delivery tasks, with priorities, assignees, descriptions, and deadlines.
- JQL filters for overdue open work, blocked work, unassigned work, and simulated stale cases.
- Jira dashboard with status and priority distributions, blocker lists, and overdue lists.

### Confluence — documentation

- IT Delivery & BAU Operations Knowledge Base (home page).
- How We Work — Operations Playbook.
- Daily BAU Operations Checklist.
- Incident Response & Escalation Runbook.
- Weekly IT Operations Status Report.

> Add exports of your **published** Confluence pages to `docs/` before claiming them as portfolio evidence. Do not upload private pages or internal data.

### Excel — management reporting

The workbook at `excel/IDBO_Day5_Validated_Jira_Tracker.xlsx` contains:

1. `START_HERE` — report date, definitions, and snapshot notes.
2. `Jira_Tickets` — imported tickets, blocker follow-ups, and calculated quality flags.
3. `Dashboard` — status KPIs, overdue metrics, and priority distribution.
4. `Weekly_Report` — stakeholder-report template linked to the reporting data.
5. `Portfolio_Guide` — publication checklist.
6. `Audit_Findings` — data-quality review and recommended follow-ups.

The workbook does **not** synchronize automatically with Jira; update it from a new Jira export for any future reporting period.

## Sample JQL

**Overdue open tickets**

```jql
project = IDBO AND statusCategory != Done AND due < startOfDay() ORDER BY due ASC
```

**Blocked tickets**

```jql
project = IDBO AND status = Blocked ORDER BY priority DESC
```

**Actual stale tickets (7 days)**

```jql
project = IDBO AND statusCategory != Done AND updated <= "-7d" ORDER BY updated ASC
```

**Simulated stale tickets**

```jql
project = IDBO AND labels = "stale-simulated" AND statusCategory != Done
```

The simulated stale label **is not evidence** that a Jira work item has genuinely been inactive for seven days.

## Example Blocker Coordination

The dashboard tracks four simulated blockers:

| Key | Example dependency |
|---|---|
| IDBO-4 | Pending API performance logs |
| IDBO-12 | Pending mobile UAT sign-off |
| IDBO-13 | Missing change-management details |
| IDBO-14 | Pending monitoring alert history |

For each blocker, the training procedure is to record the impact, responsible team, next action, follow-up date, and escalation condition.

## Portfolio Screenshots

**Add only real screenshots you captured of your completed project.** Suggested file names:

- `screenshots/jira-kanban-board.png`
- `screenshots/jira-operations-dashboard.png`
- `screenshots/confluence-knowledge-base.png`
- `screenshots/confluence-incident-runbook.png`
- `screenshots/excel-dashboard.png`

Before publication, crop browser tabs, email addresses, avatars, private URLs, and account-specific identifiers. Optional: insert the screenshots here using Markdown once they are uploaded.

## Repository Structure

```text
it-delivery-bau-operations-tracker/
├── README.md
├── data/
│   └── IDBO_Validated_Public_Snapshot.csv
├── excel/
│   └── IDBO_Day5_Validated_Jira_Tracker.xlsx
├── docs/                            # Add the 5 Confluence PDF exports here
└── screenshots/                     # Add screenshots captured from your project here
```

## Lessons Learned

- Maintaining Jira issue quality, assignment, and lifecycle status.
- Tracking blockers, due dates, and escalation follow-ups.
- Building reporting views with JQL, saved filters, and Jira dashboard gadgets.
- Linking work tracking to Confluence runbooks and playbooks.
- Producing a consistent weekly operations report in Excel.

---
**Disclaimer:** Solely an educational / recruitment portfolio simulation. No real bank systems, risk approvals, vulnerability remediation, or production incidents were involved.
# it-delivery-bau-operations-tracker
