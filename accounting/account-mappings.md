# Account Mappings

Account mappings are the configuration layer that connects your loan pipeline to your accounting system. They define which accounts should be debited and credited when specific financial events occur -- enabling Keystone to generate journal entries automatically instead of requiring manual data entry for every transaction.

## What are account mappings?

An account mapping is a rule that says: "When *this event* happens, debit *this account* and credit *that account*." Each mapping consists of three parts:

1. **Mapping Type** -- The category of event (e.g., Loan Property, Revenue Line Item, Commission Role)
2. **Mapping Key** -- The specific event within that category (e.g., "brokerCompensation," "loanOfficer")
3. **Debit Account / Credit Account** -- The chart of accounts entries to use for the journal entry

When the mapped event occurs (for example, a loan is funded), Keystone looks up the corresponding mapping and creates a journal entry using the specified debit and credit accounts.

## Navigating to account mappings

Account mappings are typically configured in the **Settings** area or within the Accounting section. The mappings configuration page shows all mappings grouped by type, with dropdowns to select the debit and credit accounts for each.

> **Screenshot placeholder:** *Account Mappings configuration page showing mappings grouped by type (Loan Properties, Revenue Line Items, Commission Roles) with debit and credit account selectors.*

## How account mappings automate journal entries

Without account mappings, every financial event would require someone to manually create a journal entry -- selecting the right accounts, entering the right amounts, and ensuring everything balances. Account mappings eliminate this by pre-configuring the accounting treatment for each event type.

The automation flow works as follows:

1. A loan event occurs (e.g., loan funded, check received, commission calculated).
2. Keystone checks whether an account mapping exists for that event.
3. If a mapping is found, the system creates a journal entry using the mapped debit and credit accounts.
4. The entry is created as a **Draft**, so it can be reviewed before posting.
5. The entry is linked to the source loan for traceability.

If no mapping exists for an event, no automatic journal entry is created. The event can still be recorded manually.

## Mapping types

Account mappings are organized by type:

### Loan Properties

These mappings handle financial events tied to loan-level properties:

| Mapping Key | Typical Event | Example Debit Account | Example Credit Account |
|------------|---------------|----------------------|----------------------|
| **brokerCompensation** | Broker compensation earned on a loan | Accounts Receivable | Broker Compensation Revenue |
| **loanAmount** | The principal loan amount (for tracking purposes) | Varies | Varies |

### Revenue Line Items

These mappings handle specific revenue components that may be tracked separately:

| Mapping Key | Typical Event | Example Debit Account | Example Credit Account |
|------------|---------------|----------------------|----------------------|
| **originationFee** | Origination fee charged | Accounts Receivable | Origination Fee Revenue |
| **processingFee** | Processing fee charged | Accounts Receivable | Processing Fee Revenue |
| **appraisalReimbursement** | Reimbursement for appraisal cost | Cash - Operating | Appraisal Expense |

### Commission Roles

These mappings handle commission payouts by role:

| Mapping Key | Typical Event | Example Debit Account | Example Credit Account |
|------------|---------------|----------------------|----------------------|
| **loanOfficer** | Commission paid to a loan officer | Commission Expense - LO | Cash - Operating |
| **processor** | Commission paid to a processor | Commission Expense - Processor | Cash - Operating |
| **branchManager** | Commission paid to a branch manager | Commission Expense - Branch Mgr | Cash - Operating |

## Setting up account mappings

**Step-by-step:**

1. Navigate to the Account Mappings configuration page.
2. Mappings are displayed in groups by mapping type (Loan Properties, Revenue Line Items, Commission Roles).
3. For each mapping row:
   - The **Mapping Key** column shows the name of the event (e.g., "Broker Compensation").
   - The **Debit Account** dropdown shows all accounts from your chart of accounts. Select the account that should receive the debit.
   - The **Credit Account** dropdown shows all accounts from your chart of accounts. Select the account that should receive the credit.
4. Click the **Save** button (disk icon) on each row after making changes. The button is only enabled when you have unsaved changes.
5. A success notification confirms the mapping was saved.

> **Screenshot placeholder:** *A single mapping row showing "Broker Compensation" with debit account set to "1200 - Accounts Receivable" and credit account set to "4000 - Broker Compensation Revenue," with a save button on the right.*

## Debit and credit account selection

When choosing accounts for a mapping, follow the standard double-entry bookkeeping rules:

- **When money comes in** (revenue earned, check deposited): Debit an asset account, credit a revenue account.
- **When money goes out** (commission paid, expense incurred): Debit an expense account, credit an asset account (usually cash).
- **When an obligation is created** (accrued expense, payable): Debit an expense account, credit a liability account.
- **When an obligation is settled** (payable paid): Debit a liability account, credit cash.

If you are unsure which accounts to use, consult the [Chart of Accounts](chart-of-accounts.md) documentation for account type descriptions.

## Common mapping configurations for mortgage companies

Here is a typical set of account mappings for a mortgage brokerage:

### When a loan is funded

| Mapping | Debit Account | Credit Account |
|---------|--------------|----------------|
| Broker Compensation | Accounts Receivable - Lender | Broker Compensation Revenue |

This records the revenue earned and the amount owed by the lender.

### When a lender check is received

| Mapping | Debit Account | Credit Account |
|---------|--------------|----------------|
| Lender Check | Cash - Operating | Accounts Receivable - Lender |

This deposits the check and clears the receivable.

### When commissions are paid

| Mapping | Debit Account | Credit Account |
|---------|--------------|----------------|
| Loan Officer Commission | Commission Expense - LO | Cash - Operating |
| Processor Commission | Commission Expense - Processor | Cash - Operating |
| Branch Manager Commission | Commission Expense - Branch Mgr | Cash - Operating |

These record the commission payments as expenses against cash.

### When a draw payment is issued

| Mapping | Debit Account | Credit Account |
|---------|--------------|----------------|
| Draw Payment | Draw Advances (Asset) | Cash - Operating |

This records the draw advance as an asset (money owed back to the company).

### When a draw is repaid

| Mapping | Debit Account | Credit Account |
|---------|--------------|----------------|
| Draw Repayment | Commission Expense | Draw Advances (Asset) |

This reduces the draw advance balance when commissions exceed the draw.

## Tips

- **Set up mappings before processing loans** -- If mappings are not configured, no automatic journal entries will be created. Set them up as part of your initial accounting configuration.
- **You can change mappings at any time** -- Updating a mapping affects only future events. Existing journal entries are not modified.
- **Use specific accounts for clarity** -- Rather than mapping everything to a generic "Revenue" account, use specific accounts like "Broker Compensation Revenue" and "Processing Fee Revenue" so your reports show detailed breakdowns.
- **Review generated entries** -- Automatic entries are created as Drafts. Build a habit of reviewing and posting them regularly.
