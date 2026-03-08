# Commissions

The commission system in EpochOS handles compensation calculations for mortgage lending employees -- loan officers, processors, loan officer assistants, and branch managers. It supports flexible commission structures with rule-based overrides, special case logic, and performance-based bonuses.

## Documentation

| Page | Description |
|------|-------------|
| [Overview](overview.md) | Conceptual overview of the full commission lifecycle |
| [Commission Templates](commission-templates.md) | Creating and configuring commission templates |
| [Commission Rules](commission-rules.md) | Filter-based rule overrides for specific loan scenarios |
| [Special Cases](special-cases.md) | Condition groups for complex commission logic |
| [Performance Boosters](performance-boosters.md) | Volume and unit-based bonus tiers |
| [Running Commissions](running-commissions.md) | Pay periods, calculation, draws, and finalization |
| [Commission Reports](commission-reports.md) | Viewing and exporting commission reports |

## Quick Reference

- **Commission Templates** define the base compensation structure for a role (e.g., "Loan Officer - Standard Plan").
- **Commission Rules** override the base commission when a loan matches specific filters (lender, loan type, state, etc.).
- **Special Case Groups** apply alternate commissions when a combination of conditions is met.
- **Performance Boosters** add bonus commissions when an employee hits volume or unit thresholds over a time period.
- **Pay Periods** group funded loans into date ranges, calculate commissions for all employees, and track draw balances.
- **Reports** provide per-employee and per-loan breakdowns of finalized pay periods.

## Key Concepts

- A template is assigned to one or more employees. When assigned, the template's base commission and rules are copied into employee-bound commission rules.
- The commission engine evaluates all active rules against each loan in a pay period, matching the most specific rule first.
- Commission amounts can be expressed as a **percentage**, a **flat dollar amount**, or **basis points (bps)**.
- Commissions can be calculated on either the **loan amount** or the **broker compensation** (the fee the brokerage earns).
- File fees can be deducted from commissions before or after the commission calculation.
- Draw balances allow employees to receive a guaranteed minimum pay, with deficits tracked and recovered from future commissions.
