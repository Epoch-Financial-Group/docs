# Commission Templates

A commission template defines the compensation structure for a specific employee role. Templates serve as blueprints -- once created, they are assigned to individual employees to generate the commission rules the engine uses during pay period calculations.

## What Is a Commission Template?

A commission template captures:

- **Name** -- a descriptive label (e.g., "Senior Loan Officer Plan", "Processor - Standard")
- **Role type** -- the employee role this template applies to
- **Base commission** -- the default commission amount, type, and basis
- **File fee** -- an optional per-loan fee deducted from the commission
- **Commission rules** -- optional overrides for specific loan scenarios (see [Commission Rules](commission-rules.md))
- **Special case groups** -- optional condition-based overrides (see [Special Cases](special-cases.md))
- **Performance booster** -- optional volume/unit bonus tiers (see [Performance Boosters](performance-boosters.md))
- **Effective date range** -- optional start and end dates for when the template is active

## Role Types

Each template targets one of the following roles:

| Role | Description |
|------|-------------|
| **Loan Officer** | The primary originator on a loan |
| **Loan Officer Assistant** | Supports the loan officer; commission can deduct from the LO |
| **Processor** | Handles loan processing; commission can deduct from the LO |
| **Branch Manager** | Receives an override commission on loans originated in their branch |
| **Contractor** | An independent contractor with their own compensation structure |

## Creating a New Commission Template

### Step 1: Navigate to Commission Templates

1. From the sidebar, click **Commission Templates**.
2. Click the **Add Template** button.

<!-- Screenshot placeholder: Commission Templates list page with Add Template button -->
> **[Screenshot]** The Commission Templates list page showing existing templates organized by role.

### Step 2: Set Template Name and Role

1. Enter a **Name** for the template (e.g., "LO Plan A - 50bps").
2. Select the **Role Type** from the dropdown.
3. Optionally set an **Effective Date** and **End Date** to control when the template is active.

<!-- Screenshot placeholder: Template name and role type fields -->
> **[Screenshot]** The template header section with name, role, and date fields.

### Step 3: Configure the Base Commission

The base commission is the default amount paid to an employee for each loan, before any rule overrides or adjustments.

1. **Commission Basis** -- Choose what the commission is calculated on:
   - **Loan Amount** -- The total loan amount (e.g., $400,000)
   - **Broker Compensation** -- The brokerage fee on the loan (e.g., $4,000)

2. **Amount Type** -- Choose how the commission is expressed:
   - **Percentage (%)** -- A percentage of the basis (e.g., 1.25%)
   - **Flat ($)** -- A fixed dollar amount per loan (e.g., $500)
   - **Basis Points (bps)** -- Hundredths of a percent (e.g., 50 bps = 0.50%)

3. **Amount** -- Enter the commission value.

4. **Minimum Commission** (optional) -- The lowest commission allowed per loan. If the calculated commission falls below this, the minimum is used instead.

5. **Maximum Commission** (optional) -- The highest commission allowed per loan. If the calculated commission exceeds this, the maximum is used instead.

<!-- Screenshot placeholder: Base commission configuration fields -->
> **[Screenshot]** The base commission section showing basis, amount type, amount, and min/max fields.

#### Example: Percentage-Based Commission

A loan officer template with **50 basis points on loan amount**:

| Field | Value |
|-------|-------|
| Commission Basis | Loan Amount |
| Amount Type | Basis Points (bps) |
| Amount | 50 |

For a $400,000 loan:
- Commission = $400,000 x 50 / 10,000 = **$2,000**

#### Example: Flat Commission

A processor template with a **flat $350 per loan**:

| Field | Value |
|-------|-------|
| Commission Basis | Loan Amount |
| Amount Type | Flat ($) |
| Amount | 350 |

For any loan amount:
- Commission = **$350**

#### Example: Percentage of Broker Compensation

A loan officer assistant template with **25% of broker compensation**:

| Field | Value |
|-------|-------|
| Commission Basis | Broker Compensation |
| Amount Type | Percentage (%) |
| Amount | 25 |

For a loan with $4,000 broker compensation:
- Commission = $4,000 x 25 / 100 = **$1,000**

### Step 4: Configure File Fee (Optional)

A file fee is a per-loan deduction from the commission. It is often used to cover administrative costs.

1. **Fee Name** -- A label for the fee (e.g., "Admin Fee", "Technology Fee").
2. **File Fee** -- The fee amount.
3. **File Fee Type** -- How the fee is expressed:
   - **Flat ($)** -- A fixed dollar amount (e.g., $150)
   - **Percentage (%)** -- A percentage of a basis
   - **Basis Points (bps)** -- Hundredths of a percent
4. **File Fee Applied On** -- What the percentage/bps fee is calculated on:
   - **Loan Amount**
   - **Loan Revenue**
   - **Gross Commission**
   - **Net Commission**

<!-- Screenshot placeholder: File fee configuration section -->
> **[Screenshot]** The file fee section with fee name, amount, type, and applied-on fields.

#### Example: Flat File Fee

| Field | Value |
|-------|-------|
| Fee Name | Admin Fee |
| File Fee | 150 |
| File Fee Type | Flat ($) |

For each loan, $150 is deducted from the commission.

#### The "Apply File Fee First" Option

When enabled, the file fee is subtracted from the **basis** before the commission is calculated, rather than being subtracted from the commission after.

**Without "Apply File Fee First"** (default):
1. Commission = basis x rate
2. Net = commission - file fee

**With "Apply File Fee First"**:
1. Adjusted basis = basis - file fee
2. Commission = adjusted basis x rate

This results in a lower commission when using percentage-based calculations.

### Step 5: Configure the "Deducts From Loan Officer" Option

When creating templates for assistants, processors, or branch managers, the **"Deducts From Loan Officer"** checkbox controls whether the commission paid to this role is subtracted from the loan officer's commission on the same loan.

- **Enabled**: The loan officer's net commission is reduced by the amount paid to this role.
- **Disabled**: The commission is paid independently; the loan officer's commission is unaffected.

This is commonly enabled for processor and LOA commissions so that the LO effectively "pays" for their support staff out of their own commission.

### Step 6: Add Commission Rules (Optional)

Commission rules override the base commission for specific loan scenarios. For example, you might want a different commission rate for FHA loans or for loans from a specific lender.

See [Commission Rules](commission-rules.md) for full details.

### Step 7: Configure Performance Booster (Optional)

A performance booster adds bonus commissions when the employee exceeds production thresholds.

See [Performance Boosters](performance-boosters.md) for full details.

### Step 8: Save the Template

Click **Save** to create the template. The template will appear in the list and can be assigned to employees.

## Assigning a Template to Employees

Once a template is saved, you assign it to employees with the matching role.

### Step-by-Step Assignment

1. Open the template detail page by clicking on the template name in the list.
2. In the **Assignments** section, click **Assign Employees**.
3. Select one or more employees from the list. Only employees with the template's role type who are not already assigned are shown.
4. Set the **Effective Date** -- the date from which the commission structure takes effect for these employees.
5. Click **Assign**.

<!-- Screenshot placeholder: Template detail page with assignment section -->
> **[Screenshot]** The template detail page showing the Assignments section with a list of assigned employees and the Assign Employees button.

### What Happens During Assignment

When employees are assigned to a template, Keystone creates **commission rules** bound to each employee:

1. A **base rule** is created using the template's base commission settings, linked to the employee as both the loan officer (for LO templates) and the recipient.
2. For each **override rule** on the template (rules with filters), an employee-bound copy is created with the same filters and commission settings.
3. These rules are set to **Active** status with the specified effective date.

The commission engine later uses these employee-bound rules when calculating commissions for funded loans.

### Unassigning an Employee

To remove an employee from a template:

1. On the template detail page, find the employee in the Assignments list.
2. Click the **Remove** action.
3. All commission rules generated from this template for that employee are deleted.

### Syncing Template Changes

When you update a template (change the base commission, add/remove rules, etc.), existing employee assignments are not automatically updated. To propagate changes:

1. On the template detail page, click **Sync Assignments**.
2. This deletes all employee-bound rules for the template and re-creates them from the current template settings, preserving each employee's effective date.

## Managing Templates

### Activating and Deactivating

Templates can be toggled between active and inactive states. Inactive templates are not used during commission calculations, but their assignments remain in place.

### Duplicating a Template

To create a new template based on an existing one:

1. On the template detail page, click **Duplicate**.
2. A copy is created with "(Copy)" appended to the name, set to **Draft** and **Inactive**.
3. Edit the copy as needed, then activate it.

### Deleting a Template

Deleting a template removes it and all associated rules, special case groups, and performance boosters. Employee-bound rules generated from the template are also removed.

> **Caution**: Deleting a template that has active employee assignments will remove those employees' commission rules. Ensure employees are reassigned to another template before deleting.
