# Sales Ledger

The Sales Ledger provides a detailed, loan-level transaction report for funded loans. It supports filtering by pay period or date range, displays summary totals, and includes CSV export for external reporting.

## Overview

The Sales Ledger is your go-to view for reviewing the specific loans that make up your production. Unlike the aggregate charts in the Funded Loans module, the Sales Ledger shows individual loan records with full detail, making it ideal for reconciliation, auditing, and reporting.

The Sales Ledger is accessed from the main sidebar navigation, separate from the analytics tab system.

> ![Screenshot: Sales Ledger overview](screenshots/sales-ledger-overview.png)

## Viewing Modes

The Sales Ledger supports two viewing modes:

### By Pay Period

Select a pay period from the dropdown to see all funded loans assigned to that pay period. This is useful for:
- Reviewing which loans are included in a commission run
- Reconciling payroll against funded production
- Verifying that the correct loans are associated with each pay period

### By Date Range

Select a start and end date to see all funded loans within that range. This is useful for:
- Monthly or quarterly production reports
- Comparing production across arbitrary time periods
- Ad-hoc reporting needs

> ![Screenshot: Sales Ledger filter controls](screenshots/sales-ledger-filters.png)

## Loan Details

Each loan in the ledger shows:

| Column | Description |
|--------|-------------|
| **Loan #** | Broker loan number |
| **Borrower** | Borrower's full name |
| **Loan Officer** | Assigned loan officer |
| **Lender** | The lender for this loan |
| **Funded Date** | Date the loan was funded |
| **Loan Amount** | Principal loan amount |
| **Broker Comp** | Broker compensation received |
| **Gross Revenue** | Gross loan revenue (if tracked) |
| **Net Revenue** | Net loan revenue after adjustments (if tracked) |
| **Status** | Current loan status |
| **Loan Purpose** | Purchase or Refinance |
| **Loan Type** | Conventional, FHA, VA, etc. |
| **Channel** | Broker or Non-Delegated Correspondent |

### Included Statuses

The Sales Ledger includes loans with any of these statuses:
- Funded
- CommissionPaid
- CheckReceived
- ApprovedForPayout

These represent loans that have completed the funding process and are in various stages of commission processing.

## Summary Totals

At the top of the ledger (or in a summary section), the following totals are displayed for the current view:

| Total | Description |
|-------|-------------|
| **Total Loan Amount** | Sum of all loan amounts in the view |
| **Total Broker Comp** | Sum of all broker compensation |
| **Total Gross Revenue** | Sum of all gross loan revenue |
| **Total Reimbursements** | Sum of all reimbursements across loans (calculated from the reimbursements JSON field on each loan) |

> ![Screenshot: Sales Ledger summary totals](screenshots/sales-ledger-totals.png)

## Pagination

Results are paginated with a default page size of 50 loans per page. The response includes:
- Current page number
- Total number of pages
- Total number of matching loans

Use the pagination controls to navigate through large result sets.

## CSV Export

The Sales Ledger supports exporting the current view to CSV format. The export includes all matching loans (not just the current page) with the following columns:

| CSV Column | Source |
|------------|--------|
| Loan # | Broker loan number |
| Borrower | First and last name combined |
| Loan Officer | LO's first and last name |
| Lender | Lender name |
| Funded Date | Formatted date |
| Loan Amount | Decimal amount |
| Broker Comp | Decimal amount |
| Gross Revenue | Decimal amount (if available) |
| Net Revenue | Decimal amount (if available) |
| Status | Loan status |
| Loan Purpose | Purchase or Refinance |
| Loan Type | Product type |
| Channel | Broker or Non-Delegated Correspondent |

The exported CSV also includes the property address (address, city, state, zip) for each loan, which is not shown in the web view.

> ![Screenshot: CSV export button](screenshots/sales-ledger-export.png)

## Pay Period Selection

When viewing by pay period, the dropdown shows the 50 most recent pay periods sorted by start date (most recent first). Each entry displays:
- Start date
- End date
- Whether the pay period is still in draft status

## Use Cases

### Monthly Production Report
Set a date range for the month and review all funded loans. Export to CSV for distribution to stakeholders.

### Commission Reconciliation
Select a pay period and compare the loans shown against the commission run details. Verify that all expected loans are included.

### Quarterly Business Review
Set a quarterly date range and use the summary totals for total volume, revenue, and reimbursement figures.

### Lender Reconciliation
Export loans by date range, then filter or sort the CSV by lender to reconcile broker compensation received against lender statements.
