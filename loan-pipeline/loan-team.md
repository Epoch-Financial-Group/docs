# Loan Team

Every loan in EpochOS has a team responsible for originating and processing it. The team consists of a Loan Officer, optional Loan Officer Assistants (LOAs), and optional Processors. Team assignments are managed from the **Team** card on the loan detail page's **Overview** tab.

## Team roles

| Role | Assignment | Cardinality | Description |
|------|-----------|-------------|-------------|
| **Loan Officer** | Required | Exactly one | The originating loan officer. Set when the loan is created and can be changed via the edit form. Drives commission calculations based on the officer's commission plan. |
| **Loan Officer Assistant (LOA)** | Optional | Multiple allowed | Assists the loan officer with file preparation, document collection, and borrower communication. Each assistant can have their own commission split. |
| **Processor** | Optional | Multiple allowed | Handles the operational processing of the loan -- ordering appraisals, managing conditions, coordinating with the lender. Each processor can have their own commission split. |

> **Screenshot placeholder:** *Team card on the Overview tab showing Loan Officer, Assistants, and Processors sections.*

---

## Assigning a Loan Officer

The Loan Officer is set when the loan is created (it is a required field). To change the Loan Officer after creation:

1. Navigate to the loan detail page.
2. Click **Edit Loan** in the page header, or click **Edit** on the Overview tab.
3. Change the **Loan Officer** dropdown.
4. Save the changes.

The dropdown shows all active employees in your company who have the **Loan Officer** role.

> **Screenshot placeholder:** *Loan Officer dropdown on the edit form.*

---

## Adding Loan Officer Assistants

A loan can have multiple LOAs. Each LOA is tracked via a bridge table (`LoanAssistant`) that links the loan to an employee.

### How to add an LOA

1. Navigate to the loan detail page.
2. Scroll to the **Team** card on the Overview tab.
3. Under **Loan Officer Assistants**, click the **Add Assistant** button.
4. A dropdown appears showing all active employees (excluding the Loan Officer and employees already assigned as assistants on this loan).
5. Select an employee from the dropdown.
6. Click **Add**.

The assistant appears immediately in the list below.

> **Screenshot placeholder:** *Add Assistant dropdown with employee selection and Add button.*

### How to remove an LOA

Click the **X** button next to the assistant's name. The removal takes effect immediately.

---

## Adding Processors

A loan can have multiple Processors. Each processor is tracked via a bridge table (`LoanProcessor`) that links the loan to an employee.

### How to add a Processor

1. Navigate to the loan detail page.
2. Scroll to the **Team** card on the Overview tab.
3. Under **Processors**, click the **Add Processor** button.
4. A dropdown appears showing all active employees (excluding the Loan Officer and employees already assigned as processors on this loan).
5. Select an employee from the dropdown.
6. Click **Add**.

> **Screenshot placeholder:** *Add Processor dropdown with employee selection.*

### How to remove a Processor

Click the **X** button next to the processor's name. The removal takes effect immediately.

---

## How team assignments affect commissions

Team assignments are directly tied to EpochOS's commission engine. Each team member's commission is calculated based on their individual commission plan:

- **Loan Officer:** Their commission plan defines their percentage or flat-rate split of the broker compensation or loan amount. Commission plans can be based on either `LoanAmount` or `BrokerCompensation`.
- **LOAs and Processors:** Each can have their own commission deduction from the loan officer's commission. Their deduction basis can be `LoanAmount`, `LoanRevenue`, `NetCommission`, or `GrossCommission`.

### Important considerations

- Changing the Loan Officer on a loan changes whose commission plan applies to that loan.
- Adding or removing an LOA or Processor affects the commission split calculations.
- Commission calculations are visible on the **Commissions** tab of the loan detail page.
- Team changes do not retroactively affect already-paid commissions. Only the current team assignment is used when calculating future payouts.

## Team in CSV uploads

When uploading loans via CSV, you can assign team members by including columns for:

- `Loan Officer` / `Loan Officer Name` -- matches by name or email
- `Primary Loan Officer Assistant Name` / `Email` -- up to 3 LOA slots
- `Primary Loan Processor Name` / `Email` -- up to 3 processor slots
- `Loan Officer #2 Name` / `Email` and `Loan Officer #3 Name` / `Email` -- secondary and tertiary LOs (added as assistants)

If an employee name or email is included in the CSV but does not match an existing employee, EpochOS will auto-create the employee record for you. See [Bulk Upload](bulk-upload.md) for details.
