# Checklists

Checklists are specific instances of task templates. When you instantiate a template, EpochOS creates a checklist containing individual tasks for each template item, with due dates calculated from the start date you provide. Checklists give you a structured way to track multi-step processes from start to finish.

---

## What a checklist contains

A checklist consists of:

| Property | Description |
|----------|-------------|
| **Name** | A descriptive name for this specific instance (e.g., "Onboarding - Jane Smith") |
| **Template** | The template the checklist was created from (for reference) |
| **Status** | Overall checklist status: To Do, In Progress, Completed, or Cancelled |
| **Subject Employee** | The employee this checklist is about (optional -- e.g., the new hire being onboarded) |
| **Created By** | The employee who created the checklist |
| **Start Date** | The date used to calculate due dates for individual items |
| **Due Date** | Optional overall due date for the checklist |
| **Tasks** | The individual task items generated from the template |
| **Progress** | Completion count -- how many tasks are done out of the total |

---

## Creating a checklist from a template

1. Navigate to **Tasks > Checklists** in the sidebar, or go to `/{company}/tasks/checklists`.
2. Click **New Checklist**.
3. Fill in the checklist details:
   - **Template** (required) -- Select the template to instantiate.
   - **Name** (required) -- Give this instance a descriptive name. For example, if using the "New Hire Onboarding" template for a specific employee, name it "Onboarding - Jane Smith".
   - **Subject Employee** -- Optionally select the employee this checklist is about. This is useful for onboarding/offboarding checklists where the checklist tracks work related to a specific person.
   - **Assignee** -- Optionally assign all generated tasks to a specific employee. If left empty, tasks are unassigned and can be assigned individually later.
   - **Start Date** (required) -- The reference date used to calculate due dates. Each task's due date is calculated as: start date + the item's due-days offset.
4. Click **Create**.

EpochOS creates the checklist and generates a task for each item in the template. You are redirected to the checklist detail page.

> **Screenshot placeholder:** *New checklist form showing template selector, name field, subject employee dropdown, assignee dropdown, and start date picker.*

---

## How due dates are calculated

When a checklist is created, each task's due date is calculated from the start date plus the template item's **due-days offset**:

```
Task due date = Checklist start date + Item due-days offset
```

For example, if the start date is March 1 and a template item has a due-days offset of 7, that task's due date is March 8.

Items with a due-days offset of 0 are due on the start date itself.

---

## Viewing a checklist

1. Navigate to **Tasks > Checklists**.
2. The checklist list shows all checklists with:
   - Checklist name
   - Associated template
   - Subject employee (if set)
   - Created by
   - Progress bar (completed / total tasks)
3. Click a checklist to open its detail view.

> **Screenshot placeholder:** *Checklist list showing several checklists with progress indicators.*

### Checklist detail view

The detail view shows:

- Checklist metadata (name, template, subject employee, created by, start date, due date).
- A **task list** showing every task generated from the template, with:
  - Task title
  - Status (with quick-toggle capability)
  - Assignee
  - Due date
  - Sort order matching the template item order
- **Completion progress** -- A count and/or progress bar showing how many tasks are completed out of the total.

> **Screenshot placeholder:** *Checklist detail page showing metadata at the top and a list of tasks with status toggles and progress indicator.*

---

## Working with checklist tasks

Tasks within a checklist are standard EpochOS tasks. You can:

- **Change status** -- Mark individual tasks as In Progress, Completed, or Cancelled directly from the checklist view.
- **Assign tasks** -- Assign individual tasks to different employees if the work is distributed across a team.
- **Add subtasks** -- Break a checklist task into smaller steps if needed.
- **Add comments** -- Attach notes and updates to individual tasks.
- **View task detail** -- Click a task to open its full detail page.

Checklist tasks do not appear in the main task table by default -- they are accessed through the checklist. This keeps the main task view focused on standalone tasks.

---

## Tracking progress

The checklist list and detail view both display completion progress:

- **Total tasks** -- The number of tasks generated from the template.
- **Completed tasks** -- The number of tasks with a status of Completed.
- **Progress** -- Displayed as "X of Y completed" or as a percentage.

This makes it easy to see at a glance how far along a process is. For example, "5 of 8 completed" tells you the onboarding is more than halfway done.

---

## Deleting a checklist

1. Open the checklist detail view.
2. Click **Delete**.
3. Confirm the deletion.

Deleting a checklist removes the checklist record and all associated tasks. This action is permanent.

---

## Checklists vs. standalone tasks

| Feature | Checklist tasks | Standalone tasks |
|---------|----------------|-----------------|
| Created from | Template instantiation | Manual creation |
| Appears in main task table | No | Yes |
| Grouped together | Yes, under the checklist | No |
| Progress tracking | Yes (X of Y completed) | Individual status only |
| Subtask support | Yes | Yes |
| Comments | Yes | Yes |

Use checklists when you have a defined, repeatable process with multiple steps. Use standalone tasks for one-off work items.

---

## Best practices

- **Name checklists descriptively** -- Include the process name and the relevant person or period (e.g., "Onboarding - John Doe", "Q1 2026 HMDA Review").
- **Set the start date carefully** -- All task due dates are calculated from the start date. If the process should begin today, use today's date. If it should begin on the employee's start date, use that date.
- **Review and customize after creation** -- After creating a checklist, review the generated tasks. Assign individual tasks to specific team members, adjust due dates if needed, and add any additional context via comments.
- **Monitor progress regularly** -- Use the checklist list view to quickly see which processes are on track and which are falling behind.
