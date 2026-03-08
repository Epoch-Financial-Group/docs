# Financial Reports

EpochOS provides three standard financial reports that summarize your company's financial position and performance: the Trial Balance, Balance Sheet, and Income Statement. All reports are generated on demand from posted journal entries and can be exported to CSV and PDF.

## Navigating to reports

The Reports page is located at **Accounting > Reports**. It presents three report cards:

| Report | Description |
|--------|-------------|
| **Trial Balance** | Debits and credits for all accounts as of a specific date |
| **Balance Sheet** | Assets, liabilities, and equity snapshot as of a specific date |
| **Income Statement** | Revenue and expenses for a given period (P&L) |

Click any card to navigate to that report.

> **Screenshot placeholder:** *Reports landing page showing three cards for Trial Balance, Balance Sheet, and Income Statement.*

## Fiscal year configuration

Before generating reports, you may want to verify your fiscal year configuration. The fiscal year determines the reporting periods used by EpochOS.

- **Default**: January 1 (calendar year)
- **Custom**: Set any start month and day in the Settings area

To configure the fiscal year:

1. Navigate to **Settings** (or the Fiscal Year configuration area).
2. Set the **Fiscal Year Start Month** (1-12) and **Fiscal Year Start Day** (1-31).
3. Save the configuration.

Most mortgage companies use a calendar fiscal year (January 1 - December 31), but if your company uses a different fiscal year, configure it before generating reports so that period-based reports (like the Income Statement) align with your reporting cycle.

---

## Trial Balance

### What it shows

The Trial Balance lists every account that has a balance as of a specific date, with its debit or credit balance. The fundamental rule is: **total debits must equal total credits**. If they do not, something is wrong with your journal entries.

The Trial Balance is not a report you would show to external stakeholders. It is an internal verification tool that confirms your books are in balance before generating the Balance Sheet and Income Statement.

### How to generate a trial balance

1. Navigate to **Accounting > Reports > Trial Balance**.
2. Select an **As Of Date** using the date picker. This determines the point in time for the balance calculation.
3. The report generates automatically when you select a date.

> **Screenshot placeholder:** *Trial Balance report showing a date picker, an "As of" date label, and a table of accounts with debit and credit balance columns and totals in the footer.*

### Reading the trial balance

The Trial Balance table has four columns:

| Column | Description |
|--------|-------------|
| **Account Number** | The account code (e.g., 1010) |
| **Account Name** | The account name (e.g., Cash - Operating) |
| **Debit Balance** | The account's debit balance (shown only if the account has a net debit balance) |
| **Credit Balance** | The account's credit balance (shown only if the account has a net credit balance) |

The footer row shows:

- **Total Debits** -- The sum of all debit balances
- **Total Credits** -- The sum of all credit balances

If the totals are equal, your books are in balance. If they are not equal, a warning message appears showing the difference. This indicates a data integrity issue that should be investigated.

### What to do if the trial balance is out of balance

An out-of-balance trial balance means that somewhere in your journal entries, debits do not equal credits. This should not happen if all entries were created through EpochOS (which enforces balance), but can occur if:

- Data was imported incorrectly
- A database-level change was made outside the application
- A bug caused an unbalanced entry

To investigate, review recent journal entries for irregularities and check the general ledger for accounts with unexpected balances.

---

## Balance Sheet

### What it shows

The Balance Sheet provides a snapshot of your company's financial position at a specific point in time. It answers the question: "What does the company own, what does it owe, and what is left over for the owners?"

The Balance Sheet is organized around the accounting equation:

```
Assets = Liabilities + Equity
```

If your books are correct, total assets will always equal total liabilities plus total equity.

### How to generate a balance sheet

1. Navigate to **Accounting > Reports > Balance Sheet**.
2. Select an **As Of Date** using the date picker.
3. The report generates automatically.

> **Screenshot placeholder:** *Balance Sheet report showing three sections (Assets, Liabilities, Equity) with account balances grouped by subtype, subtotals, and a grand total comparison at the bottom.*

### Reading the balance sheet

The Balance Sheet is divided into three major sections:

#### Assets

Things your company owns or is owed. Grouped by subtype:

| Group | Includes |
|-------|----------|
| **Cash and Bank** | Checking accounts, savings accounts |
| **Accounts Receivable** | Money owed by lenders, investors |
| **Other Current Assets** | Short-term assets like prepaid expenses |
| **Fixed Assets** | Equipment, furniture, leasehold improvements |
| **Other Assets** | Miscellaneous long-term assets |

Each group shows individual accounts with their balances and a subtotal. The section ends with a **Total Assets** line.

#### Liabilities

Obligations your company owes. Grouped by subtype:

| Group | Includes |
|-------|----------|
| **Accounts Payable** | Amounts owed to vendors |
| **Credit Card** | Credit card balances |
| **Other Current Liabilities** | Short-term obligations, accrued expenses |
| **Long Term Liabilities** | Loans, notes payable |

Each group shows individual accounts with their balances and a subtotal. The section ends with a **Total Liabilities** line.

#### Equity

The owners' residual interest. Grouped by subtype:

| Group | Includes |
|-------|----------|
| **Owners Equity** | Capital invested by owners |
| **Retained Earnings** | Accumulated profits from prior periods |

The section ends with a **Total Equity** line.

#### Balance verification

At the bottom of the report, two lines compare:

- **Total Assets**
- **Total Liabilities + Equity**

These should be equal. If they are not, a warning message appears indicating the balance sheet is out of balance.

### Interpreting the balance sheet for a mortgage company

Key things to look for:

- **Accounts Receivable** -- This should represent lender checks that have not yet been received. A growing AR balance may indicate delays in check receipt.
- **Cash balances** -- Monitor available cash relative to upcoming commission payouts and operating expenses.
- **Draw Advances** -- If you use draw programs, the draw advance balance (an asset) shows how much employees owe back to the company.
- **Liabilities** -- Monitor accrued commission obligations and other payables.

---

## Income Statement

### What it shows

The Income Statement (also called the Profit & Loss or P&L) shows your company's financial performance over a period of time. It answers: "How much did the company earn, how much did it spend, and what was the net result?"

The key formula:

```
Net Income = Total Revenue - Total Expenses
```

### How to generate an income statement

1. Navigate to **Accounting > Reports > Income Statement**.
2. Select a **date range** using the Start Date and End Date pickers.
3. The report generates automatically when both dates are set.

> **Screenshot placeholder:** *Income Statement report showing Revenue and Expense sections with account balances, section totals, and a bold Net Income line at the bottom.*

### Reading the income statement

The Income Statement is divided into two sections:

#### Revenue

Income earned during the period. Grouped by subtype:

| Group | Includes |
|-------|----------|
| **Operating Revenue** | Broker compensation, origination fees, processing fees |
| **Other Revenue** | Interest income, miscellaneous income |

Each group shows individual accounts with their balances for the period and a subtotal. The section ends with a **Total Revenue** line.

#### Expenses

Costs incurred during the period. Grouped by subtype:

| Group | Includes |
|-------|----------|
| **Operating Expense** | Rent, utilities, office supplies, marketing |
| **Cost of Goods Sold** | Direct costs tied to loan production |
| **Payroll Expense** | Commissions, salaries, payroll taxes |
| **Other Expense** | Miscellaneous expenses |

Each group shows individual accounts with their balances for the period and a subtotal. The section ends with a **Total Expenses** line.

#### Net Income

The bottom line:

```
Net Income = Total Revenue - Total Expenses
```

A positive net income means the company was profitable during the period. A negative net income (displayed in red) means expenses exceeded revenue.

### Interpreting the income statement for a mortgage company

Key things to look for:

- **Revenue trends** -- Is broker compensation revenue growing or declining? Compare periods to spot trends.
- **Commission ratio** -- What percentage of revenue is paid out as commissions? This is the key profitability lever for mortgage brokerages.
- **Expense control** -- Are operating expenses staying within budget?
- **Net margin** -- Net Income / Total Revenue tells you how much of each revenue dollar you keep.

---

## Exporting reports

All three reports support two export formats:

### CSV Export

Click the **CSV** button in the export bar to download the report data as a comma-separated values file. CSV exports can be opened in Excel, Google Sheets, or any spreadsheet application. The export includes all rows and columns visible in the report.

### PDF Export

Click the **PDF** button in the export bar to generate a printable PDF version of the report. The PDF includes the report title, date range, and the full report content formatted for printing.

> **Screenshot placeholder:** *Export bar showing CSV and PDF buttons in the report header area.*

## How reports are calculated

All reports are derived from **posted journal entries only**. Draft and Voided entries are excluded.

- **Trial Balance** and **Balance Sheet** use the "as of" date: they include all posted entries with a date on or before the selected date.
- **Income Statement** uses a date range: it includes all posted entries with a date within the selected start and end dates.

This means:

- If you have unposted draft entries, they will not appear on reports. Post them first.
- If you void an entry, its amounts are removed from future report calculations.
- Reports are generated in real time from current data -- they always reflect the latest posted entries.

## Tips

- **Generate the Trial Balance first** -- Before reviewing the Balance Sheet or Income Statement, run a Trial Balance to confirm your books are in balance. If the Trial Balance is off, the other reports will also be incorrect.
- **Use consistent date ranges** -- When comparing periods, use the same date range length (e.g., full calendar months) for meaningful comparisons.
- **Export monthly reports** -- At the end of each month, export the Trial Balance, Balance Sheet, and Income Statement as PDFs for your records.
- **Check the accounting equation** -- On the Balance Sheet, Total Assets should equal Total Liabilities + Total Equity. If it does not, investigate before relying on the report.
- **Post before reporting** -- Ensure all journal entries for the period have been posted before generating final reports. Draft entries are invisible to reports.
