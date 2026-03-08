# Loan Statuses

Every loan in Keystone has a status that indicates where it stands in the mortgage origination lifecycle. There are 16 statuses organized across four phases: origination, underwriting, closing, and post-closing.

## Status overview

| # | Status | Display Name | Phase | Description |
|---|--------|-------------|-------|-------------|
| 1 | `AppIntake` | App Intake | Origination | The loan application has been received and initial data entry is underway. This is the default status for newly created loans. |
| 2 | `Qualification` | Qualification | Origination | The borrower is being pre-qualified. The loan officer is reviewing income, assets, and credit to determine eligibility. |
| 3 | `LoanSetup` | Loan Setup | Origination | The loan file is being set up in the LOS (Loan Origination System). Documents are being gathered and organized. |
| 4 | `Disclosed` | Disclosed | Origination | The Loan Estimate and other TRID-required disclosures have been sent to the borrower. The regulatory clock has started. |
| 5 | `PreApproved` | Pre-Approved | Origination | The borrower has been pre-approved based on initial underwriting review. The loan is ready for full submission. |
| 6 | `SubmittedToUW` | Submitted to UW | Underwriting | The full loan package has been submitted to the lender's underwriting department for review. |
| 7 | `ApprovedWithConditions` | Approved w/ Conditions | Underwriting | The underwriter has approved the loan subject to conditions (e.g., additional documentation, explanations, verifications). The team is now working to satisfy those conditions. |
| 8 | `Resubmitted` | Resubmitted | Underwriting | The loan has been resubmitted to underwriting after conditions were addressed. Awaiting final review. |
| 9 | `ClearToClose` | Clear to Close | Closing | All underwriting conditions have been satisfied. The loan is approved and ready for closing document preparation. |
| 10 | `DocsOut` | Docs Out | Closing | Closing documents have been sent out to the title company or closing agent. The loan is scheduled to close. |
| 11 | `Closed` | Closed | Closing | The borrower has signed closing documents. The loan is closed but not yet funded. |
| 12 | `Funded` | Funded | Post-Closing | The loan has been funded -- money has been disbursed. This is a critical milestone that triggers automatic journal entry generation for accounting. |
| 13 | `CheckReceived` | Check Received | Post-Closing | The broker compensation check has been received from the lender. This triggers check-received journal entries for accounting. |
| 14 | `ApprovedForPayout` | Approved for Payout | Post-Closing | The loan revenue has been verified and approved for commission payout to the loan officer and team. |
| 15 | `CommissionPaid` | Commission Paid | Post-Closing | All commissions have been paid out. The loan is fully settled from a compensation standpoint. |
| 16 | `Adverse` | Adverse | Terminal | The loan has been denied, withdrawn, or otherwise terminated. This is a terminal status used for any negative outcome. |

## Typical lifecycle flow

The standard progression for a loan that closes successfully:

```
App Intake
  |
  v
Qualification
  |
  v
Loan Setup
  |
  v
Disclosed
  |
  v
Pre-Approved
  |
  v
Submitted to UW
  |
  v
Approved w/ Conditions  <-->  Resubmitted  (may cycle multiple times)
  |
  v
Clear to Close
  |
  v
Docs Out
  |
  v
Closed
  |
  v
Funded  (triggers accounting journal entries)
  |
  v
Check Received  (triggers accounting journal entries)
  |
  v
Approved for Payout
  |
  v
Commission Paid
```

### Underwriting loop

It is common for a loan to cycle between **Approved w/ Conditions** and **Resubmitted** multiple times. The underwriter may issue additional conditions after each resubmission. The loan remains in this loop until all conditions are cleared, at which point it moves to **Clear to Close**.

### Terminal status

**Adverse** is the terminal status for loans that do not close. Use it for:

- Denied applications (underwriter declined the loan)
- Withdrawn applications (borrower decided not to proceed)
- Cancelled loans (deal fell through for any reason)

A loan can move to Adverse from any other status.

## Status badges

Each status is displayed with a color-coded badge throughout the application:

| Color | Statuses |
|-------|----------|
| **Gray (muted)** | App Intake |
| **Yellow (warning)** | Qualification, Submitted to UW, Approved w/ Conditions |
| **Blue (info)** | Disclosed, Pre-Approved, Resubmitted |
| **Default** | Clear to Close, Closed |
| **Secondary** | Loan Setup, Docs Out |
| **Green (success)** | Funded, Check Received, Approved for Payout, Commission Paid |
| **Red (destructive)** | Adverse |

## How to change a loan's status

### From the loan detail page (Overview tab)

1. Navigate to the loan detail page by clicking a loan in the pipeline.
2. Click the **Edit** button on the Overview tab.
3. Change the **Status** field using the dropdown.
4. Click **Save**.

> **Screenshot placeholder:** *Overview tab in edit mode showing the status dropdown.*

### Important: Status change side effects

Changing a loan's status can trigger automated actions:

- **Moving to Funded:** When a loan's status changes to `Funded`, Keystone automatically generates accounting journal entries to record the loan revenue. This only happens the first time the loan moves to Funded.

- **Setting the Funded Date:** On the Dates tab, setting the `fundedDate` for the first time also triggers funded journal entries, independently of the status field.

- **Setting the Check Received Date:** On the Dates tab, setting the `checkReceivedDate` for the first time triggers check-received journal entries.

## Milestone dates

Each status has a corresponding date field on the **Dates** tab that records when the loan reached that milestone. These dates are independent of the status field itself -- you can set dates without changing the status, and vice versa.

### Processing dates

| Date Field | Label | Corresponding Status |
|------------|-------|---------------------|
| `appIntakeDate` | App Intake | AppIntake |
| `tridAppDate` | TRID App | (disclosure timing) |
| `qualificationDate` | Qualification | Qualification |
| `loanSetupDate` | Loan Setup | LoanSetup |
| `disclosedDate` | Disclosed | Disclosed |
| `preApprovedDate` | Pre-Approved | PreApproved |
| `submittedToUWDate` | Submitted to UW | SubmittedToUW |
| `approvedWithConditionsDate` | Approved w/ Conditions | ApprovedWithConditions |
| `resubmittedDate` | Resubmitted | Resubmitted |
| `clearToCloseDate` | Clear to Close | ClearToClose |
| `docsOutDate` | Docs Out | DocsOut |

### Closing and funding dates

| Date Field | Label | Corresponding Status |
|------------|-------|---------------------|
| `lockDate` | Lock Date | (rate lock) |
| `lockExpirationDate` | Lock Expiration | (rate lock expiry) |
| `closedDate` | Closed | Closed |
| `fundedDate` | Funded | Funded |
| `estimatedFundingDate` | Estimated Funding | (projected date) |
| `adverseDate` | Adverse | Adverse |
| `checkReceivedDate` | Check Received | CheckReceived |
| `finalizedDate` | Finalized | (internal finalization) |
| `approvedForPayoutDate` | Approved for Payout | ApprovedForPayout |
| `commissionPaidDate` | Commission Paid | CommissionPaid |

## Status-derived date in the pipeline

The pipeline table shows a **Status Date** column. This date is automatically derived from the loan's current status -- it shows the date field that corresponds to the active status. For example, if a loan is in `ClearToClose` status, the Status Date column shows the `clearToCloseDate` value.
