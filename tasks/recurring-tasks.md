# Recurring Tasks

Recurring task schedules automatically generate tasks on a defined cadence. This ensures that repeating obligations -- monthly reports, quarterly reviews, annual license renewals -- are never forgotten. EpochOS creates tasks ahead of time based on a configurable lead-time window, giving assignees advance notice before the work is due.

---

## How recurring tasks work

A recurring schedule is a configuration that tells EpochOS to automatically create a new task at regular intervals. Each time the schedule triggers, a new standalone task is created with the schedule's title, description, priority, and assignee. The generated tasks appear in the main task table like any other task.

### Lifecycle

1. You create a recurring schedule with a frequency, start date, and other settings.
2. EpochOS checks active schedules and, based on the **lead days** setting, creates tasks in advance of each occurrence.
3. The generated task has a due date calculated from the occurrence date plus the **due-days-after** offset.
4. The schedule records the last date it generated a task so it does not create duplicates.
5. The cycle continues until the schedule is deactivated or its end date is reached.

---

## Creating a recurring schedule

1. Navigate to **Tasks > Recurring** in the sidebar, or go to `/{company}/tasks/recurring`.
2. Click **New Schedule**.
3. Fill in the schedule details:

| Field | Required | Description |
|-------|----------|-------------|
| **Title** | Yes | The title that will be used for each generated task (e.g., "Monthly BSA/AML Report") |
| **Description** | No | Description carried over to each generated task |
| **Recurrence Pattern** | Yes | How often the task recurs: Daily, Weekly, Monthly, Quarterly, or Annually |
| **Recurrence Day** | Depends | The specific day (see below for details per pattern) |
| **Recurrence Month** | Annually only | The month of the year (1-12) for annual schedules |
| **Category** | No | Category assigned to generated tasks |
| **Priority** | No | Defaults to Medium. Applied to each generated task. |
| **Assignee** | No | The employee who will be assigned each generated task |
| **Due Days After** | No | Number of days after the occurrence date when the task is due. Defaults to 0 (due on the occurrence date). |
| **Lead Days** | No | How many days before the occurrence date to create the task. Defaults to 7. |
| **Start Date** | Yes | The date from which the schedule begins generating tasks |
| **End Date** | No | Optional date after which the schedule stops. Leave empty for indefinite recurrence. |
| **Active** | No | Whether the schedule is active. Defaults to active. |

4. Click **Save**.

> **Screenshot placeholder:** *New recurring schedule form showing all fields, with the recurrence pattern set to "Monthly" and recurrence day set to 1.*

---

## Recurrence patterns

### Daily

A task is generated every day. No additional configuration is needed beyond the start date.

**Example:** Daily cash reconciliation task created every morning.

### Weekly

A task is generated once per week on a specific day.

- **Recurrence Day** -- Day of the week: 0 = Sunday, 1 = Monday, 2 = Tuesday, ..., 6 = Saturday. Defaults to Monday (1) if not specified.

**Example:** Weekly pipeline review task generated every Monday.

### Monthly

A task is generated once per month on a specific day of the month.

- **Recurrence Day** -- Day of the month (1-31). If the month has fewer days than specified (e.g., day 31 in a 30-day month), the task is created on the last day of the month.

**Example:** Monthly compliance report due on the 15th of each month.

### Quarterly

A task is generated once every three months on a specific day.

- **Recurrence Day** -- Day of the month (1-31), following the same last-day-of-month logic as monthly schedules.

**Example:** Quarterly HMDA data review due on the 1st of each quarter's first month.

### Annually

A task is generated once per year on a specific month and day.

- **Recurrence Month** -- Month of the year (1 = January, 12 = December). Defaults to January if not specified.
- **Recurrence Day** -- Day of the month (1-31).

**Example:** Annual BSA/AML policy review due on March 1 every year.

---

## Lead days and due-days-after

These two settings control when a task is created relative to when it is due.

### Lead days

The number of days **before** the occurrence date that the task is created. This gives the assignee advance notice and time to prepare.

- Default: 7 days
- A lead-days value of 0 means the task is created on the occurrence date itself.
- A lead-days value of 14 means the task appears two weeks before it is due.

### Due-days-after

The number of days **after** the occurrence date when the task is due.

- Default: 0 (due on the occurrence date)
- A due-days-after value of 5 means the task is due 5 days after the occurrence.

### Example timeline

For a monthly schedule set to the 1st of each month, with 7 lead days and 3 due-days-after:

| Date | Event |
|------|-------|
| December 25 | Task is created (7 days before January 1) |
| January 1 | Occurrence date |
| January 4 | Task due date (3 days after January 1) |

---

## Managing recurring schedules

### Viewing schedules

Navigate to **Tasks > Recurring** to see a list of all recurring schedules. Each entry shows:

- Schedule title
- Recurrence pattern (e.g., "Monthly")
- Assignee
- Active/inactive status
- Number of tasks generated so far

> **Screenshot placeholder:** *Recurring schedule list showing several schedules with their frequency, assignee, and active status.*

### Editing a schedule

1. Click a schedule to open its detail view.
2. Click **Edit**.
3. Modify any fields.
4. Click **Save**.

Changes apply to future task generation only. Tasks that have already been created are not modified.

### Activating and deactivating

Toggle the **Active** field to control whether a schedule continues generating tasks:

- **Active** -- Tasks will be generated on the next occurrence.
- **Inactive** -- No new tasks will be generated until the schedule is reactivated.

This is useful for temporarily pausing a schedule (e.g., during a company restructuring) without deleting it.

### Deleting a schedule

1. Open the schedule's detail view.
2. Click **Delete**.
3. Confirm the deletion.

Deleting a schedule is permanent. Tasks that were already generated from the schedule are not deleted -- they continue to exist as standalone tasks.

---

## Generated tasks

Tasks created by recurring schedules are standard EpochOS tasks. They appear in the main task table and can be:

- Edited (change title, description, assignee, priority, due date)
- Completed, cancelled, or deleted
- Assigned subtasks and comments

Each generated task includes a link back to its originating recurring schedule for reference.

> **Screenshot placeholder:** *A generated task's detail view showing the "Recurring Schedule" link in the metadata section.*

---

## Best practices

- **Set realistic lead days** -- Give assignees enough time to prepare. A quarterly compliance review might need 14 lead days; a daily reconciliation might need 0.
- **Use due-days-after for grace periods** -- If the work should start on the occurrence date but has a few days for completion, set due-days-after accordingly.
- **Combine with categories** -- Assign a category (e.g., Compliance, Licensing) to each recurring schedule so generated tasks are automatically categorized and filterable.
- **Set end dates for temporary schedules** -- If a recurring task is only needed for a specific period (e.g., during an audit cycle), set an end date rather than remembering to deactivate it later.
- **Review active schedules periodically** -- As processes change, deactivate or modify schedules that no longer apply. Stale recurring tasks create noise and reduce trust in the task system.
- **Monitor overdue counts** -- If recurring tasks are consistently going overdue, it may indicate that the frequency is too high, the lead time is too short, or the assignee is overloaded.
