# General Ledger

The General Ledger is the detailed, transaction-by-transaction record of activity for any account in your chart of accounts. While journal entries record what happened and financial reports summarize the big picture, the general ledger shows you exactly which transactions affected a specific account, when they occurred, and how the balance changed over time.

## What is the general ledger?

In accounting, the general ledger is the complete set of accounts and their transactions. In EpochOS, the General Ledger page provides a focused view: you select a single account and a date range, and the system shows every posted journal entry line that touched that account, along with a running balance.

Think of it as a bank statement for any account in your chart of accounts -- not just bank accounts, but also receivables, revenue, expenses, and any other account.

## Navigating to the general ledger

The General Ledger page is located at **Accounting > General Ledger**. You can also access it from the Accounting dashboard by clicking the "General Ledger" card.

> **Screenshot placeholder:** *General Ledger page showing the account selector, date range filter, and a table of transactions with running balances.*

## How to view the general ledger

**Step-by-step:**

1. Navigate to **Accounting > General Ledger**.
2. Select an **Account** from the dropdown at the top of the page. Accounts are listed by account number and name (e.g., "1010 - Cash - Operating").
3. Set the **date range** using the Start Date and End Date fields.
4. The ledger loads automatically when both an account and date range are selected.

The report refreshes whenever you change the account or date range -- there is no separate "Run" button.

## Understanding ledger entries

Each row in the general ledger table represents a single journal entry line that affected the selected account:

| Column | Description |
|--------|-------------|
| **Date** | The date of the journal entry |
| **Entry #** | The journal entry number (e.g., JE-42), shown in monospace font |
| **Memo** | The journal entry's header memo |
| **Description** | The line-level description (may differ from the header memo) |
| **Debit** | The debit amount, if this line was a debit to the account |
| **Credit** | The credit amount, if this line was a credit to the account |
| **Running Balance** | The cumulative balance of the account through this transaction |

The running balance updates with each row, giving you a clear picture of how the account balance changed over time. For debit-normal accounts (assets, expenses), debits increase the running balance and credits decrease it. For credit-normal accounts (liabilities, equity, revenue), credits increase it and debits decrease it.

### Example

For the account "Cash - Operating" (an asset with debit-normal balance) over one week:

| Date | Entry # | Memo | Debit | Credit | Running Balance |
|------|---------|------|-------|--------|----------------|
| 03/01 | JE-38 | Lender check - Loan #101 | $12,000 | | $12,000 |
| 03/03 | JE-39 | Commission payment - J. Smith | | $3,500 | $8,500 |
| 03/05 | JE-41 | Lender check - Loan #102 | $9,200 | | $17,700 |
| 03/07 | JE-42 | Office rent - March | | $2,800 | $14,900 |

## Relationship to journal entries

The general ledger is derived entirely from posted journal entries. Each row in the ledger corresponds to one line of a posted journal entry. The connection is:

- **Journal Entry** -- The complete transaction record with all its debit and credit lines across multiple accounts
- **General Ledger** -- A filtered view showing only the lines that affect a specific account

If a journal entry has four lines affecting four different accounts, each of those lines appears in the general ledger of its respective account.

Only **Posted** journal entries appear in the general ledger. Draft entries do not affect account balances and are not shown. Voided entries are excluded as well.

## Exporting the general ledger

The general ledger can be exported for use in external tools or for record-keeping:

- **CSV Export** -- Click the CSV export button to download the ledger data as a comma-separated values file. The export includes all columns: Date, Entry #, Memo, Description, Debit, Credit, and Running Balance.

- **PDF Export** -- Click the PDF export button to generate a printable PDF of the ledger. The PDF includes the account name, date range, and the full transaction table.

> **Screenshot placeholder:** *Export bar showing CSV and PDF export buttons above the general ledger table.*

## When to use the general ledger

The general ledger is your go-to tool for:

- **Investigating an account balance** -- If a number on the trial balance or balance sheet looks unexpected, drill into the general ledger to see exactly which transactions contributed to it.

- **Auditing specific transactions** -- Find all transactions that affected a particular account within a date range.

- **Tracking receivables** -- View the Accounts Receivable ledger to see which lender checks have been recorded and which are still outstanding.

- **Reviewing expense activity** -- Check the general ledger for an expense account to see every charge posted during a period.

- **Reconciliation support** -- Compare the general ledger for your Cash account against your bank statement to identify discrepancies.

## Tips

- If the ledger shows "No transactions found for this period," verify that you have posted journal entries for the selected account and date range. Draft entries are not included.
- The general ledger only shows activity within the selected date range. The running balance starts from zero at the beginning of the range. To see the full historical balance, set the start date to the earliest date you have entries.
- Use the general ledger in combination with the Trial Balance to understand how individual transactions roll up into summary totals.
