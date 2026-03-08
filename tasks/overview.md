# Task Management Overview

Task management in EpochOS gives your mortgage company a structured way to track work items, assign responsibility, enforce deadlines, and automate repeating obligations. It integrates with the rest of the platform so that compliance tasks, onboarding checklists, licensing renewals, and day-to-day operational work all live in one place.

---

## Why task management matters in mortgage operations

Mortgage companies juggle a constant stream of operational, compliance, and administrative work that goes beyond individual loan files. Examples include:

- **Compliance deadlines** -- Quarterly HMDA reporting, annual BSA/AML reviews, policy update cycles.
- **Employee onboarding** -- License verification, system access provisioning, training completion tracking.
- **Employee offboarding** -- Revoking access, transferring pipeline, collecting equipment.
- **Licensing** -- State license renewals, continuing education tracking, NMLS updates.
- **IT and HR** -- Equipment requests, benefits enrollment, performance reviews.
- **Recurring audits** -- Monthly QC file reviews, branch compliance checks, investor document audits.

Without a centralized system, these tasks scatter across email threads, spreadsheets, and sticky notes. EpochOS consolidates them into a single dashboard with clear ownership, priority, and due dates.

---

## Key concepts

### Tasks

A task is a single unit of work with a title, description, and a set of properties that track its lifecycle:

| Property | Description |
|----------|-------------|
| **Title** | A short, descriptive name for the task |
| **Description** | Optional longer explanation of what needs to be done |
| **Status** | Current state: To Do, In Progress, Completed, or Cancelled |
| **Priority** | Urgency level: Low, Medium, High, or Urgent |
| **Due Date** | When the task should be completed |
| **Assignee** | The employee responsible for completing the task |
| **Category** | An organizational label (e.g., Compliance, Onboarding, HR) |
| **Subtasks** | Child tasks that break the work into smaller steps |
| **Comments** | A threaded discussion attached to the task |

### Categories

Categories are labels that group tasks by function or department. EpochOS ships with a set of default categories:

- Compliance
- Onboarding
- Offboarding
- Licensing
- HR
- IT
- General

You can add, rename, and remove categories to match your company's needs.

### Templates

Templates are reusable blueprints for sets of tasks that you perform repeatedly. A template defines a list of ordered items -- each with a title, description, and a due-date offset -- that can be instantiated into a checklist with one click. This eliminates the need to recreate the same task list every time you onboard an employee, conduct a quarterly review, or run a compliance audit.

### Checklists

A checklist is a specific instance of a template. When you instantiate a template, EpochOS creates a checklist containing individual tasks for each template item. Checklists track completion progress -- how many items are done out of the total -- and can be assigned to a specific employee.

### Recurring schedules

Recurring schedules automatically generate tasks on a defined cadence. You configure the frequency (Daily, Weekly, Monthly, Quarterly, or Annually), the assignee, the priority, and optionally a start and end date. EpochOS creates tasks ahead of time based on a configurable lead-time window, so assignees have advance notice.

---

## Task dashboard

The task dashboard at `/{company}/tasks` provides an at-a-glance view of your company's task workload. It displays four key metrics:

| Metric | Description |
|--------|-------------|
| **Overdue** | Tasks with a due date in the past that are not yet completed |
| **Due Today** | Tasks due today that are still open |
| **In Progress** | Tasks currently being worked on |
| **Completed This Week** | Tasks completed since the start of the current week |

Below the metrics, a filterable task table shows all top-level tasks. You can filter by status, priority, assignee, category, and due date range. A search bar lets you find tasks by title or description.

> **Screenshot placeholder:** *Task dashboard showing the four metric cards and the task table with filters applied.*

---

## Task statuses

Tasks move through a lifecycle represented by four statuses:

| Status | Badge Color | Meaning |
|--------|-------------|---------|
| **To Do** | Gray | The task has been created but work has not started |
| **In Progress** | Blue | Work is actively underway |
| **Completed** | Green | The task has been finished. A completion timestamp is recorded automatically. |
| **Cancelled** | Muted | The task was cancelled and no longer needs to be done |

### Status transitions

You can change a task's status at any time by editing the task or using quick-action controls. When a task is marked as Completed, EpochOS records the completion timestamp. If the status is changed back to To Do or In Progress, the completion timestamp is cleared.

---

## Task priorities

Priority levels indicate urgency and are displayed as color-coded badges throughout the interface:

| Priority | Badge Color | Suggested use |
|----------|-------------|---------------|
| **Low** | Gray | Nice-to-have tasks, no time pressure |
| **Medium** | Blue | Standard tasks with normal deadlines (default) |
| **High** | Yellow/Orange | Important tasks that should be addressed soon |
| **Urgent** | Red | Critical tasks that need immediate attention |

---

## Where to find tasks

Task management is accessible from the left-hand sidebar under **Tasks**. The section includes links to:

- **All Tasks** -- The main task dashboard and list
- **Templates** -- Manage reusable task templates
- **Checklists** -- View and manage instantiated checklists
- **Recurring** -- Configure and monitor recurring task schedules

> **Screenshot placeholder:** *Sidebar navigation with the Tasks section expanded showing sub-links.*
