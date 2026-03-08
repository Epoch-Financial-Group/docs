# Adding Loans

You can add a loan to Keystone either manually through the loan form or in bulk via CSV upload (see [Bulk Upload](bulk-upload.md)). This page covers the manual creation process.

## Getting to the form

1. Navigate to the pipeline at `/{company}/loans`.
2. Click the **Add Loan** button in the top right.
3. You will land on `/{company}/loans/add`.

> **Screenshot placeholder:** *The Add Loan button in the pipeline header.*

## Form layout

The loan creation form is organized into four sections:

1. **Loan Information** -- identifiers, team assignments, and loan classification
2. **Financial Details** -- monetary amounts and interest rate
3. **Borrower Information** -- borrower name and credit score
4. **Property Information** -- subject property address and occupancy type

> **Screenshot placeholder:** *Full loan creation form showing all four sections.*

---

## Step-by-step walkthrough

### Step 1: Loan Information

| Field | Required | Description |
|-------|----------|-------------|
| **Broker Loan Number** | Yes | Your internal loan number. Must be unique within your company. This is the primary identifier used throughout Keystone and is searchable in the pipeline. |
| **Lender Loan Number** | No | The loan number assigned by the lender/investor. Useful for cross-referencing with lender systems. |
| **Loan Officer** | Yes | The originating loan officer. Select from a dropdown of active employees with the Loan Officer role. This assignment drives commission calculations. |
| **Lender** | No | The lender or investor for this loan. Select from your company's lender list. If the lender does not appear, add it first in the Lenders settings. |
| **Lead Source** | No | Where the borrower lead came from (e.g., referral partner, marketing campaign). Select from your company's configured lead sources. Used for reporting and analytics. |
| **Loan Purpose** | No | The purpose of the loan. Options: **Purchase** or **Refinance**. |
| **Loan Type** | No | The mortgage product type. Options: **Conventional**, **FHA**, **VA**, **USDA**, **Non-QM**, **Reverse Mortgage**, **HELOC**, **Commercial**, or **HELOAN**. |

> **Screenshot placeholder:** *Loan Information section with fields filled in.*

### Step 2: Financial Details

| Field | Required | Description |
|-------|----------|-------------|
| **Loan Amount** | Yes | The total loan amount in dollars. Enter the numeric value (e.g., `350000`). This is the base amount used for commission calculations. |
| **Broker Compensation** | No | The total broker compensation amount in dollars. Defaults to `0` if not provided. This is the gross revenue from the lender and is the basis for many commission calculations. |
| **Interest Rate** | No | The note interest rate as a percentage (e.g., `6.875`). Informational; does not affect commission calculations. |

> **Screenshot placeholder:** *Financial Details section showing dollar and percentage inputs.*

### Step 3: Borrower Information

| Field | Required | Description |
|-------|----------|-------------|
| **First Name** | No | Borrower's first name. Used in the pipeline display and search. |
| **Last Name** | No | Borrower's last name. Used in the pipeline display, search, and sorting. |
| **Credit Score** | No | Borrower's FICO score. Must be between 300 and 850. Informational field used for reporting. |

### Step 4: Property Information

| Field | Required | Description |
|-------|----------|-------------|
| **Street Address** | No | The subject property street address. Searchable in the pipeline. |
| **Unit/Apt** | No | Apartment, suite, or unit number. |
| **City** | No | City of the subject property. |
| **County** | No | County of the subject property. |
| **State** | No | State of the subject property. Select from a dropdown of all 50 US states plus DC. |
| **ZIP Code** | No | ZIP code of the subject property. |
| **Occupancy Type** | No | How the borrower will use the property. Options: **Primary Residence**, **Second Home**, or **Investment**. |

> **Screenshot placeholder:** *Property Information section with address fields and occupancy dropdown.*

---

## Saving the loan

Click the **Create Loan** button at the bottom of the form. If all required fields are filled in and valid, the loan is created with an initial status of **App Intake** and you are redirected to the loan detail page.

If there are validation errors, an error banner appears at the top of the form describing what needs to be corrected.

## After creation

Once the loan is created, you can:

- [Change its status](loan-statuses.md) as it progresses through the pipeline
- [Assign team members](loan-team.md) (assistants and processors)
- [Add adjustments](adjustments.md) for revenue or commission modifications
- [Add notes](notes.md) to track conversations and decisions
- [Edit any field](editing-loans.md) from the loan detail page

## Fields not available at creation

Some loan fields are only available after the loan is created, on the loan detail page:

- **Status** -- New loans start at App Intake; change status from the Overview tab
- **Payer Type** -- Set from the Overview tab (Lender, Borrower, Investor, or Seller)
- **Channel** -- Set from the Overview tab (Broker or Non-Delegated Correspondent)
- **Revenue line items** -- Managed from the Revenue tab
- **Milestone dates** -- Managed from the Dates tab
- **Team assignments** -- Assistants and processors are managed from the Overview tab
- **LTV** -- Calculated/set on the detail page
