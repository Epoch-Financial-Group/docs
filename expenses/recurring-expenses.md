# Recurring Expenses

Recurring expenses let you define costs that repeat on a schedule, so you do not have to manually enter the same expense every week or month. The system automatically generates individual expense records based on the recurrence pattern you configure.

## Overview

A recurring expense is a template that describes a repeating cost. It specifies an employee, an amount, a recurrence pattern, and an effective date range. The system uses this template to automatically create individual `Expense` records at the defined intervals.

Each generated expense links back to its parent recurring expense via the `recurringExpenseId` field, so you can always trace where an auto-generated expense came from.

## Recurrence Patterns

Keystone supports three recurrence patterns:

| Pattern | Behavior |
|---------|----------|
| **One-Time** | The expense is created once on the effective date. Useful for scheduled future expenses that you want to set up in advance. |
| **Weekly** | The expense repeats every N weeks, where N is the recurrence value. For example, a recurrence value of 2 means "every 2 weeks." |
| **Monthly** | The expense repeats every N months. A recurrence value of 1 means every month; a value of 3 means quarterly. |

### Recurrence Value

The **recurrence value** controls the interval between occurrences. It defaults to 1, meaning the expense occurs every single period (every week or every month). Setting it to a higher number spaces out the occurrences:

- Weekly with value 1 = every week
- Weekly with value 2 = every other week
- Monthly with value 1 = every month
- Monthly with value 3 = every quarter
- Monthly with value 6 = twice a year

## Creating a Recurring Expense

On the Expenses page, navigate to the **Recurring Expenses** section and click **Add Recurring Expense**. A dialog will open with the following fields:

> ![Screenshot: Add recurring expense dialog](screenshots/add-recurring-expense.png)

### Required Fields

| Field | Description |
|-------|-------------|
| **Employee** | The employee this recurring expense is assigned to. |
| **Amount** | The dollar amount per occurrence. |
| **Effective Date** | The date the recurring expense begins generating expenses. |

### Optional Fields

| Field | Description |
|-------|-------------|
| **Recurrence Pattern** | Choose from One-Time, Weekly, or Monthly. Defaults to Monthly. |
| **Every X** | The recurrence interval. Defaults to 1. |
| **Expiration Date** | The date the recurring expense stops generating expenses. If left blank, it continues indefinitely. |
| **Note** | A description that will be copied to each generated expense (e.g., "Office rent" or "Software license"). |

Click **Create** to save the recurring expense.

## Managing Recurring Expenses

The recurring expenses table displays all defined recurring expenses for your company.

> ![Screenshot: Recurring expenses table](screenshots/recurring-expenses-table.png)

### Table Columns

| Column | Description |
|--------|-------------|
| **Employee** | The assigned employee's name |
| **Amount** | The dollar amount per occurrence |
| **Pattern** | The recurrence pattern and interval (e.g., "Monthly", "Every 2 weeks") |
| **Effective Date** | When the recurring expense starts |
| **Expiration** | When it ends, or "Ongoing" if no expiration is set |
| **Note** | The description |
| **Actions** | Edit and delete buttons |

### Editing a Recurring Expense

Click the pencil icon on any row to open the edit dialog. All fields can be modified. Changes take effect for future expense generation -- expenses already generated from the previous configuration are not retroactively changed.

> ![Screenshot: Edit recurring expense dialog](screenshots/edit-recurring-expense.png)

### Deleting a Recurring Expense

Click the trash icon on any row to delete a recurring expense. A confirmation dialog will appear. Deleting a recurring expense stops future expense generation but does not remove expenses that were already generated from it.

## How Auto-Generation Works

The system processes recurring expenses to generate individual expense records:

1. **Effective date check** -- The recurring expense must have reached or passed its effective date.
2. **Expiration date check** -- If an expiration date is set and has passed, no new expenses are generated.
3. **Pattern application** -- Based on the recurrence pattern and value, the system determines the next occurrence date.
4. **Expense creation** -- An individual `Expense` record is created with the amount, note, and employee from the template, linked back via `recurringExpenseId`.

### Tracing Generated Expenses

Every expense generated from a recurring template carries a `recurringExpenseId` that links it back to the source. This means you can:

- Identify which expenses were auto-generated versus manually entered.
- Trace a specific expense back to its recurring template.
- See all expenses produced by a given recurring expense.

## Common Use Cases

| Scenario | Configuration |
|----------|--------------|
| Monthly office rent for an employee | Monthly, value 1, no expiration |
| Quarterly software license | Monthly, value 3, no expiration |
| Weekly marketing budget | Weekly, value 1, no expiration |
| One-time equipment purchase scheduled for next month | One-Time, effective date set to the purchase date |
| Bi-weekly phone stipend | Weekly, value 2, no expiration |
| Annual training fee | Monthly, value 12, no expiration |
| Temporary contractor cost for 6 months | Monthly, value 1, with an expiration date 6 months out |
