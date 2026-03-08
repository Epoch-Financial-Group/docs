# Creating Tasks

This page covers how to create tasks, fill in their properties, break work into subtasks, and use comments for collaboration.

---

## Creating a new task

1. Navigate to **Tasks** in the sidebar.
2. Click the **New Task** button.
3. Fill in the task form:

| Field | Required | Description |
|-------|----------|-------------|
| **Title** | Yes | A short, descriptive name for the task (e.g., "Review Q1 HMDA data") |
| **Description** | No | A longer explanation of what needs to be done, any relevant context, or links to related resources |
| **Status** | No | Defaults to **To Do**. You can also set it to In Progress if work is already underway. |
| **Priority** | No | Defaults to **Medium**. Set to Low, High, or Urgent as appropriate. |
| **Due Date** | No | The date by which the task should be completed. Tasks without a due date are sorted to the end of the list. |
| **Assignee** | No | Select an employee from the dropdown. The assignee is the person responsible for completing the task. |
| **Category** | No | Select a category (e.g., Compliance, Onboarding, HR) to organize the task. Categories can be managed in settings. |

4. Click **Save**. You are redirected to the task detail page.

> **Screenshot placeholder:** *New task form showing all fields: title, description, status dropdown, priority dropdown, due date picker, assignee selector, and category selector.*

---

## Task detail view

After creating a task, you land on its detail page. This page shows:

- All task properties (title, description, status, priority, due date, assignee, category).
- The **subtasks** list.
- The **comments** thread.
- Metadata including who created the task, when it was created, and its completion timestamp (if completed).
- A link to the parent checklist or recurring schedule, if the task was generated from one.

> **Screenshot placeholder:** *Task detail view showing task properties, subtask list, and comment thread.*

---

## Editing a task

1. Open the task by clicking its row in the task table, or navigate directly to `/{company}/tasks/{id}`.
2. Click **Edit**.
3. Modify any fields.
4. Click **Save** to apply the changes.

### Quick status change

You can change a task's status directly from the task table or detail view without entering edit mode. Click the status badge or use the status dropdown to move the task between To Do, In Progress, Completed, and Cancelled.

When you mark a task as **Completed**, the system automatically records the current date and time as the completion timestamp. Changing the status back to To Do or In Progress clears the completion timestamp.

---

## Subtasks

Subtasks let you break a task into smaller, trackable steps. Each subtask is a full task in its own right -- it has a title, status, assignee, and all other task properties -- but it is linked to a parent task.

### Adding a subtask

1. Open the parent task's detail page.
2. In the **Subtasks** section, enter the subtask title.
3. Click **Add** (or press Enter).
4. The subtask is created and appears in the subtask list.

Subtasks inherit the parent task's checklist association (if any). They do not appear in the main task table -- they are only visible from the parent task's detail page.

### Managing subtasks

- Click a subtask to view its detail page.
- Change a subtask's status independently of the parent task.
- Each subtask can have its own assignee, priority, and due date.

### Subtask counts

The main task table shows a subtask count badge next to tasks that have subtasks, so you can see at a glance how many steps a task has.

> **Screenshot placeholder:** *Subtask section on a task detail page showing three subtasks with status checkboxes.*

---

## Comments

Comments provide a discussion thread on a task. Use them to ask questions, provide updates, share context, or document decisions.

### Adding a comment

1. Open the task's detail page.
2. Scroll to the **Comments** section at the bottom.
3. Type your comment in the text field.
4. Click **Add Comment**.
5. Your comment appears in the thread with your name and a timestamp.

Comments are displayed in chronological order (oldest first). They cannot be edited or deleted after submission.

### When to use comments

- Providing a progress update ("Submitted the data to HMDA, waiting for confirmation").
- Asking the assignee for clarification.
- Documenting why a task was cancelled or deferred.
- Attaching context that future reviewers might need.

> **Screenshot placeholder:** *Comment thread showing two comments from different employees with timestamps.*

---

## Deleting a task

1. Open the task's detail page.
2. Click the **Delete** button.
3. Confirm the deletion.

Deleting a task is permanent. All subtasks and comments associated with the task are also deleted. If you want to preserve the record but mark it as no longer needed, consider changing the status to **Cancelled** instead.

---

## Filtering and searching tasks

The task table supports several filters to help you find specific tasks:

| Filter | Options |
|--------|---------|
| **Status** | To Do, In Progress, Completed, Cancelled |
| **Priority** | Low, Medium, High, Urgent |
| **Assignee** | Any active employee |
| **Category** | Any configured category |
| **Due Date Range** | From date / To date |
| **Search** | Free-text search across title and description |

Filters can be combined. For example, filter by Status = "In Progress" and Priority = "Urgent" to see all urgent work in flight.

The task table is paginated with 25 tasks per page by default. Tasks are sorted by due date (ascending, with tasks without a due date appearing last), then by creation date (newest first).

> **Screenshot placeholder:** *Task table with the filter panel open showing status, priority, assignee, and category filters.*

---

## Categories

Categories help you organize and filter tasks by function or department. They are configured at the company level.

### Default categories

Keystone provides a set of default categories out of the box:

- Compliance
- Onboarding
- Offboarding
- Licensing
- HR
- IT
- General

### Managing categories

Categories can be added, renamed, and deleted from the company settings page. See your company administrator for category changes. When a category is deleted, tasks in that category are not deleted -- they simply lose their category assignment.
