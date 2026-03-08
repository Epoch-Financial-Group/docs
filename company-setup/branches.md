# Branches

Branches represent the physical locations or organizational units within your mortgage company. Every employee can be assigned to a branch, and branch-level groupings are used throughout Keystone for reporting, analytics, and commission rule scoping.

## Why branches matter

- **Organizational structure** -- Branches let you model your company's real-world office locations (e.g., "Downtown Office," "West Side Branch").
- **Reporting and analytics** -- Many reports and analytics dashboards can be filtered or broken down by branch.
- **Commission rules** -- Commission templates can be scoped to specific branches, allowing different compensation structures per location.
- **Employee assignment** -- Each employee is assigned to exactly one branch. This drives which branch manager oversees them and how their production is grouped.

---

## Viewing the branch list

1. In the sidebar, expand **Administration**.
2. Click **Branches**.

This takes you to `/{your-company}/branches`, where you will see a list of all branches with their names and assigned managers.

> ![Screenshot: Branch list page showing branch names and managers](screenshots/branch-list.png)

---

## Adding a new branch

1. Navigate to **Administration > Branches**.
2. Click the **Add Branch** button.
3. Fill in the branch form:

| Field | Required | Description |
|-------|----------|-------------|
| **Branch Name** | Yes | A descriptive name for the branch (e.g., "Downtown Branch," "Remote Team") |
| **Branch Manager** | No | Select an existing employee to serve as this branch's manager. The dropdown shows all employees currently in the system. Select "No Manager" to leave it unassigned. |

4. Click **Create Branch**.

You will be redirected to the branch list after the branch is created.

> ![Screenshot: Add Branch form with name and manager fields](screenshots/branch-add.png)

{% hint style="info" %}
You can create branches before adding employees. In fact, this is recommended so that you can assign employees to branches during their initial setup.
{% endhint %}

---

## Editing a branch

1. Navigate to **Administration > Branches**.
2. Click the branch you want to edit, or navigate directly to `/{your-company}/branches/{branch-id}/edit`.
3. Update the **Branch Name** or **Branch Manager** as needed.
4. Click **Save Changes**.

---

## How branches relate to other data

### Employees

Each employee has an optional `branchId` field. When you assign an employee to a branch, they appear in branch-level reports and are associated with that branch's manager.

### Loans

Loans are connected to branches through their assigned loan officer. When a loan officer belongs to a branch, the loan inherits that branch association for reporting purposes.

### Commission rules

Commission rules can be scoped to specific branches. This allows you to create different compensation structures for different locations -- for example, a higher split for a newer branch that is still ramping up.

### Candidates (Recruiting)

If you use the recruiting module, candidates can also be associated with a target branch for onboarding purposes.

---

## Routes reference

| Route | Description |
|-------|-------------|
| `/{company}/branches` | Branch list |
| `/{company}/branches/add` | Add a new branch |
| `/{company}/branches/{id}/edit` | Edit an existing branch |

---

## Related pages

- [Company Settings](company-settings.md) -- global company configuration
- [Employees](employees.md) -- employees are assigned to branches
