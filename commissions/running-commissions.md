# Running Commissions

Running commissions is the process of grouping funded loans into pay periods, calculating each employee's compensation, reviewing the results, and finalizing the pay period. This page covers the full workflow from pay period creation through finalization.

## What Is a Pay Period?

A **pay period** is a date range that groups funded loans and expenses for commission calculation. Each pay period tracks:

- **Start date** and **end date** -- the date range
- **Status** -- Draft or Finalized
- **Loans** -- funded loans whose funded date falls within the period
- **Expenses** -- employee expenses allocated to the period
- **Employee records** -- per-employee draw balance and wage data

Pay periods are the core unit of the commission process. Loans are assigned to pay periods, commissions are calculated per period, and reports are generated from finalized periods.

## Pay Period Frequency

The frequency of pay periods is configured in the company's payroll settings. Keystone supports four options:

| Frequency | Description | Typical Date Ranges |
|-----------|-------------|---------------------|
| **Weekly** | One period per week | e.g., Mon-Sun or any 7-day span based on configured start day |
| **Biweekly** | One period every two weeks | 14-day spans |
| **Semi-Monthly** | Two periods per month | 1st-15th and 16th-end of month (default), or custom split dates |
| **Monthly** | One period per month | 1st through end of month (default), or custom start date |

### Semi-Monthly Options

Semi-monthly periods can be configured as:
- **First and Fifteenth**: 1st-15th and 16th-end of month
- **Fifteenth and Last**: Same default split
- **Custom**: Specify custom start and end day-of-month boundaries

### Monthly Options

Monthly periods can be configured as:
- **First**: 1st through end of month
- **Last**: Same as above
- **Custom**: Specify a custom start day (e.g., start on the 16th of each month through the 15th of the next)

## The Commission Run Workflow

### Step 1: Navigate to Run Commissions

1. From the sidebar, click **Run Commissions**.
2. The page displays a list of all pay periods, ordered by date (most recent first).

<!-- Screenshot placeholder: Run Commissions list page -->
> **[Screenshot]** The Run Commissions page showing pay periods with their date ranges, loan counts, and statuses (Draft or Finalized).

### Step 2: Auto-Assignment of Loans

When you visit the Run Commissions page, the system automatically checks for unassigned funded loans and expenses:

1. All funded loans without a pay period assignment are identified.
2. For each loan, the system determines which pay period date range covers the loan's funded date.
3. If a matching draft pay period exists, the loan is assigned to it.
4. If no matching period exists, a new draft pay period is created with the appropriate date range (based on the company's payroll settings) and the loan is assigned.
5. Expenses without a pay period assignment are similarly matched to draft periods by date.

Loans in finalized pay periods are not reassigned. If a funded loan's date falls within a finalized period, it is skipped during auto-assignment.

### Step 3: Open a Pay Period

Click on a pay period to view its details. The pay period detail view is organized as a **three-step wizard**:

1. **Review** -- Examine the loans, expenses, and draw settings
2. **Preview** -- See calculated commissions before finalizing
3. **Finalize** -- Lock in the commissions and close the period

<!-- Screenshot placeholder: Pay period detail view with step indicator -->
> **[Screenshot]** The pay period detail view showing the three-step wizard with "Review" active, and tabs for Earnings, Unassigned Loans, Expenses, and Draws.

### Step 4: Review (Step 1 of 3)

The Review step has multiple tabs:

#### Earnings Tab

Displays all loans in the pay period with:
- Loan number and borrower name
- Funded date
- Loan amount and broker compensation
- Loan officer name
- Calculated commission amounts (gross, file fee, net)

<!-- Screenshot placeholder: Earnings tab showing loan list -->
> **[Screenshot]** The Earnings tab with a table of loans and their commission calculations.

From this tab you can:
- **Remove a loan** from the pay period (it becomes unassigned and can be moved to a different period)
- Review commission calculations per loan

#### Unassigned Loans Tab

Shows funded loans that fall within this pay period's date range but are not yet assigned. This can happen when loans are manually removed or when new loans are funded after the period was created.

- Click **Add** to assign an unassigned loan to this pay period.

#### Expenses Tab

Displays expenses allocated to this pay period, showing:
- Employee name
- Expense amount
- Date and notes

Expenses are deducted from the employee's commission during the calculation.

#### Draws Tab

Shows draw balance information for employees with commissions in this period:
- Previous draw balance (carried over from prior periods)
- Draw balance payment (amount paid down from this period's commissions)
- Draw balance carried over (remaining balance after this period)
- Wage paid (the guaranteed minimum payment)

Draw values can be manually adjusted before finalization if needed.

### Step 5: Preview (Step 2 of 3)

When you advance to the Preview step, the commission engine runs a full calculation. This shows:

- **Per-employee summary cards** with:
  - Employee name
  - Number of loans
  - Gross commission
  - File fee deductions
  - Expenses
  - Previous draw balance
  - Wage paid
  - Draw balance changes
  - Net pay

<!-- Screenshot placeholder: Preview step showing employee summary cards -->
> **[Screenshot]** The Preview step displaying summary cards for each employee with their calculated commission totals.

This is a preview -- nothing is saved yet. You can go back to the Review step to make changes (add/remove loans, adjust draws) and re-preview.

### Step 6: Finalize (Step 3 of 3)

When everything looks correct, the Finalize step presents a confirmation screen:

1. Click **Finalize Pay Period**.
2. The system:
   - Runs the commission engine one final time
   - Creates or updates **PayPeriodEmployee** records for each employee with their draw data
   - Updates each employee's running **draw balance** on their employee record
   - Records which **commission rules** were applied (PayPeriodCommissionRule snapshot)
   - Marks the pay period as **Finalized** with a timestamp and the finalizing user's ID
   - Generates **commission accrual journal entries** in the accounting system
3. The pay period is now locked.

<!-- Screenshot placeholder: Finalize step with confirmation and export buttons -->
> **[Screenshot]** The Finalize step showing the "Ready to Finalize" confirmation with Finalize, Export Detail, and Export Summary buttons.

After finalization, you can:
- **Export Detail CSV** -- A line-by-line export of every commission result (loan, recipient, rule, amounts)
- **Export Summary CSV** -- A per-employee summary export

## The Commission Calculation Process

When the engine runs (either for preview or finalization), it performs these steps for every loan in the pay period:

### 1. Load Data

The engine loads:
- All loans in the pay period with their attributes (amount, type, lender, state, etc.)
- All associated employees (loan officers, assistants, processors, branch managers)
- All active commission rules
- Special case groups and performance boosters
- Expenses for the period

### 2. Process Each Loan

For each loan:

**a. Find the loan officer's matching rule:**
- Filter rules to those for the LO role (not processor, not LOA, not BM)
- Sort by specificity (employee-specific rules first)
- Evaluate each rule's filters and special cases against the loan
- Use the first matching rule

**b. Calculate the LO's gross commission:**
- Determine the basis (loan amount or broker compensation)
- Apply the commission rate (percentage, flat, or bps)
- Clamp to min/max if configured

**c. Calculate the file fee:**
- If the rule has a file fee, calculate it based on the fee type
- If "apply file fee first" is set, the fee adjusts the basis before commission calculation

**d. Check performance booster:**
- If the matched rule is linked to a performance condition, query the LO's production stats
- If the threshold is met, calculate the bonus and add it

**e. Process assistants, processors, branch managers:**
- For each assistant on the loan, find a matching LOA rule and calculate their commission
- For each processor, find a matching processor rule and calculate
- If the loan's LO is in a branch, check for a branch manager override rule
- Any of these that are marked "deducts from loan officer" reduce the LO's net

**f. Apply loan adjustments:**
- Loan-level adjustments that apply to commissions are added to the LO's net

### 3. Build Employee Summaries

After all loans are processed:
- Commission results are aggregated by employee
- Expenses are added per employee
- Draw balances are calculated:
  - If net earnings exceed the draw wage, excess pays down prior draw balance
  - If net earnings are below the draw wage, the deficit increases the draw balance
- Net pay is determined

## Draw Balance Handling

The draw system ensures employees receive a minimum payment each period.

### Draw Calculation Types

Each employee has a **draw calculation type**:

| Type | Description |
|------|-------------|
| **Hourly** | Draw = hourly rate x hours per period |
| **Flat Amount** | Draw = a fixed dollar amount |
| **None** | No draw; the employee receives only their commissions |

### Draw Balance Flow

```
Previous Draw Balance (from prior periods)
  + Deficit (if commissions < draw this period)
  - Payment (if commissions > draw this period)
  = Draw Balance Carried Over (to next period)
```

**When commissions exceed the draw:**
1. The employee is paid their full commission earnings
2. Any excess above the draw amount can pay off prior draw balance
3. Net pay = net commission earnings - draw balance payment

**When commissions are below the draw:**
1. The employee receives the draw amount (guaranteed minimum)
2. The shortfall (draw - commissions) is added to their draw balance
3. Net pay = draw amount - expenses

### Draw Carry-Over

By default, draw balances carry over between periods. If an employee's `isDrawCarryOverDisabled` flag is set, the draw balance resets to zero at the end of each period (the company absorbs the deficit).

### Example

An employee has:
- Draw type: Flat Amount, $3,000
- Previous draw balance: $1,500
- This period's gross commissions: $5,000
- File fees: $300
- Expenses: $200

Calculation:
1. Net earned = $5,000 - $300 - $200 = $4,500
2. $4,500 > $3,000 draw, so excess = $1,500
3. Draw balance payment = min($1,500 excess, $1,500 prior balance) = $1,500
4. Draw balance carried over = $1,500 - $1,500 = $0
5. Net pay = $4,500 - $1,500 = $3,000

## Pay Period Statuses

| Status | Description | Actions Available |
|--------|-------------|-------------------|
| **Draft** | The pay period is open for editing | Add/remove loans, adjust draws, preview, finalize |
| **Finalized** | The pay period is locked | View, export, unfinalize |

### Unfinalizing a Pay Period

If corrections are needed after finalization, an administrator can **unfinalize** a pay period:

1. On the pay period detail page, click **Unfinalize**.
2. The system:
   - Restores each employee's draw balance to their **previous** value (before this period)
   - Deletes the PayPeriodCommissionRule snapshots
   - Deletes the PayPeriodEmployee records
   - Sets the pay period back to Draft status
3. The pay period can now be edited and re-finalized.

> **Caution**: Unfinalizing a pay period reverses draw balance changes. If subsequent pay periods have already been finalized, their draw calculations may become inconsistent. Unfinalize only when necessary and consider the downstream impact.

## Managing Pay Periods

### Creating a Pay Period Manually

While pay periods are typically auto-created when funded loans are detected, you can create one manually:

1. On the Run Commissions page, click **Create Pay Period**.
2. Enter the **Start Date** and **End Date**.
3. Click **Create**.

The new pay period is created as a Draft. Funded loans within its date range can be assigned to it.

### Removing a Loan from a Pay Period

On the Earnings tab of a pay period:

1. Click the **Remove** action on a loan row.
2. The loan is unassigned from the pay period and marked as manually unassigned (it will not be auto-assigned back).

### Adding a Loan to a Pay Period

On the Unassigned Loans tab:

1. Find the loan you want to add.
2. Click **Add**.
3. The loan is assigned to this pay period and the manual unassignment flag is cleared.

## CSV Export

Both detail and summary exports are available after commissions have been calculated.

### Detail Export

The detail CSV contains one row per commission result:

| Column | Description |
|--------|-------------|
| Loan ID | The loan identifier |
| Loan Amount | The total loan amount |
| Broker Compensation | The broker fee |
| Recipient ID | The employee receiving the commission |
| Recipient Role | LoanOfficer, LoanOfficerAssistant, Processor, or BranchManager |
| Rule ID | The commission rule that was applied |
| Gross Commission | The calculated gross commission |
| File Fee | The file fee deduction |
| Performance Bonus | Any performance booster bonus |
| Net Commission | The final commission amount |
| Deducts From LO | Whether this amount deducts from the loan officer |

### Summary Export

The summary CSV contains one row per employee:

| Column | Description |
|--------|-------------|
| Employee ID | The employee identifier |
| Loan Count | Number of loans |
| Gross Commission | Total gross commission |
| File Fees | Total file fee deductions |
| Deductions | Total deductions |
| Expenses | Total expenses |
| Adjustments | Total adjustments |
| Previous Draw Balance | Draw balance from prior periods |
| Wage Paid | Guaranteed minimum pay |
| Draw Balance Payment | Amount paid toward draw balance |
| Draw Balance Carried Over | Remaining draw balance |
| Net Pay | Final payment amount |
