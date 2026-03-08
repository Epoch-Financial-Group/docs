# Accounting

The accounting module in Keystone provides a full double-entry bookkeeping system designed for mortgage lending companies. It connects directly to the loan pipeline, so journal entries can be generated automatically when loans fund, checks are received, and commissions are paid -- keeping your books in sync with your operations.

## Documentation

| Page | Description |
|------|-------------|
| [Overview](overview.md) | Conceptual overview of double-entry accounting in Keystone |
| [Chart of Accounts](chart-of-accounts.md) | Account types, subtypes, hierarchy, and management |
| [Journal Entries](journal-entries.md) | Creating, posting, voiding, and reversing journal entries |
| [General Ledger](general-ledger.md) | Viewing transaction detail by account |
| [Account Mappings](account-mappings.md) | Automating journal entries for loan events |
| [Bank Accounts](bank-accounts.md) | Managing bank connections and balances |
| [Bank Reconciliation](bank-reconciliation.md) | Matching bank transactions to journal entries |
| [Financial Reports](financial-reports.md) | Trial balance, balance sheet, and income statement |

## Quick Reference

- **Chart of Accounts** is the foundation -- every transaction flows through accounts organized by type (Asset, Liability, Equity, Revenue, Expense).
- **Journal Entries** record every financial event as balanced debits and credits. They can be created manually or generated automatically from loan events.
- **Account Mappings** tell Keystone which accounts to debit and credit when specific loan events occur (funding, check receipt, commission payment, etc.).
- **Bank Accounts** track your real-world bank balances and transactions, linked to corresponding accounts in the chart of accounts.
- **Bank Reconciliation** matches imported bank transactions against journal entries to verify your books agree with your bank.
- **Financial Reports** (Trial Balance, Balance Sheet, Income Statement) summarize your financial position and performance on demand.

## Key Concepts

- Keystone uses **double-entry bookkeeping**: every transaction has equal debits and credits, ensuring the accounting equation (Assets = Liabilities + Equity) always holds.
- Journal entries start as **Drafts** and must be explicitly **Posted** to affect account balances and financial reports. Posted entries can be **Voided** or **Reversed**.
- The **General Ledger** is the detailed transaction-by-transaction record for any account, with a running balance.
- Reports can be exported to **CSV** and **PDF** for external use.
- A **QuickBooks Online** integration is available for syncing chart of accounts data with your existing QBO instance.
- The **Fiscal Year Configuration** lets you set a custom fiscal year start date (defaults to January 1).
