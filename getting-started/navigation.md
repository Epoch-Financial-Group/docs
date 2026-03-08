# Navigation

This guide explains how to navigate EpochOS, covering the sidebar layout, every navigation item, the company switcher, responsive behavior, and how active pages are highlighted.

---

## Overview

EpochOS uses a **persistent sidebar** on the left side of the screen as the primary navigation mechanism. The sidebar is always visible while you are working inside a company workspace and provides access to every major section of the application.

The main content area fills the rest of the screen to the right of the sidebar.

> ![Screenshot: Full application layout with sidebar](screenshots/full-layout-sidebar.png)

---

## Sidebar Layout

The sidebar is organized into two types of navigation entries:

1. **Direct links** -- Single-click entries that take you directly to a page.
2. **Collapsible groups** -- Sections that expand to reveal multiple sub-pages.

Each entry has an **icon** on the left and a **label** to the right of the icon. Collapsible groups display a **chevron arrow** on the right side that rotates to indicate whether the group is expanded or collapsed.

Direct links appear at the top of the sidebar, followed by collapsible groups separated by thin horizontal dividers.

---

## Navigation Items

Below is a complete reference of every navigation entry, organized in the order they appear in the sidebar.

### Direct Links

These items appear at the top of the sidebar and navigate directly to a page when clicked.

| Icon | Label | Route | Description |
|------|-------|-------|-------------|
| Home | **Dashboard** | `/[company]` | The main landing page. Provides an overview of your lending operations with summary metrics and recent activity. |
| Bar Chart | **Data Analytics** | `/[company]/analytics` | Advanced analytics and reporting. Includes pipeline analysis, conversion metrics, leaderboards, turn-time tracking, profitability analysis, commission analytics, expense tracking, and more. |
| List Checks | **Loan Pipeline** | `/[company]/loans` | Your active loan pipeline. View, filter, and manage all loans from application intake through funding and commission payout. |
| Book | **Policies** | `/[company]/policies` | Company policy document management. Create, organize, and share internal policies with folder-based organization and permission controls. |

---

### Collapsible Groups

These items expand to reveal sub-pages. Click the group header to toggle it open or closed.

#### Tasks

Manage operational tasks, templates, checklists, and recurring schedules.

| Sub-item | Route | Description |
|----------|-------|-------------|
| Dashboard | `/[company]/tasks` | Overview of all tasks, filterable by status, assignee, priority, and category. |
| Templates | `/[company]/tasks/templates` | Create reusable task templates that can be applied to new tasks or checklists. |
| Checklists | `/[company]/tasks/checklists` | Multi-step checklists that can be assigned to employees (e.g., onboarding checklists, loan file review checklists). |
| Recurring | `/[company]/tasks/recurring` | Set up tasks that automatically recur on a schedule (daily, weekly, monthly, quarterly, or annually). |

#### Quality Control

Manage QC review processes for loan files.

| Sub-item | Route | Description |
|----------|-------|-------------|
| QC Dashboard | `/[company]/qc` | Overview of quality control reviews -- pending, in-progress, and completed. Includes loan selection for QC review. |
| Templates | `/[company]/qc/templates` | Create and manage QC review templates that define the checklist items reviewers evaluate. |

#### Recruiting

Track recruiting candidates and manage onboarding.

| Sub-item | Route | Description |
|----------|-------|-------------|
| Pipeline | `/[company]/recruiting` | Kanban-style view of recruiting candidates across stages: Lead, Screening, Interview, Offer, Accepted, Hired, Declined, and Withdrawn. |
| Onboarding | `/[company]/recruiting/onboarding` | Manage the onboarding process for newly hired candidates transitioning into active employees. |

#### Commission

Calculate, review, and manage employee commissions.

| Sub-item | Route | Description |
|----------|-------|-------------|
| Reports | `/[company]/reports` | Commission reports and summaries by pay period, employee, or date range. |
| Run Commissions | `/[company]/run-commissions` | Execute commission calculations for a pay period. Review, adjust, and approve calculated commissions before payout. |
| Plan Templates | `/[company]/commission-templates` | Create and manage commission plan templates that define how employees are compensated. See [Initial Setup](initial-setup.md) for details. |

#### Accounting

Full double-entry accounting system for mortgage lending operations.

| Sub-item | Route | Description |
|----------|-------|-------------|
| Overview | `/[company]/accounting` | Accounting dashboard with key financial metrics and recent activity. |
| Chart of Accounts | `/[company]/accounting/chart-of-accounts` | Manage your chart of accounts -- the categories used to classify all financial transactions. |
| Journal Entries | `/[company]/accounting/journal-entries` | Create and review journal entries. Entries can be manual or automatically generated from loan events (funding, check received, commission payment, etc.). |
| General Ledger | `/[company]/accounting/general-ledger` | View the general ledger with all posted transactions, filterable by account, date range, and source. |
| Financial Reports | `/[company]/accounting/reports` | Generate financial statements and reports (income statement, balance sheet, etc.). |
| Expenses | `/[company]/expenses` | Track and manage company and employee expenses, including recurring expenses. |
| Sales Ledger | `/[company]/sales-ledger` | A loan-centric view of revenue and commission data tied to funded loans. |

#### Directories

Lookup directories for key entities.

| Sub-item | Route | Description |
|----------|-------|-------------|
| Lenders | `/[company]/lenders` | Directory of wholesale lenders and correspondent partners. Manage lender details, contacts, product types, and program IDs. |
| People | `/[company]/employees` | Directory of all employees. Search, filter, and manage employee profiles, roles, licenses, and compensation settings. |

#### Administration

Company-wide settings and configuration.

| Sub-item | Route | Description |
|----------|-------|-------------|
| Company Settings | `/[company]/settings` | Configure company name, NMLS number, LOS selection, payroll settings, and lead sources. See [Initial Setup](initial-setup.md). |
| Branches | `/[company]/branches` | Create and manage branches (office locations or organizational units). Assign branch managers and view employee counts. |

---

## How Active Pages Are Highlighted

EpochOS visually indicates which page you are currently viewing:

### Direct Links

The currently active direct link receives:

- A **filled background** (accent color).
- **Bold text** with full foreground color.
- A **left border accent** -- a 2-pixel vertical line on the left edge of the item, providing a clear visual indicator.
- The icon changes from muted to **full foreground color**.

### Collapsible Group Sub-Items

When you are viewing a page within a collapsible group:

- The **sub-item** receives a filled background and bold text.
- The **parent group** automatically shows its contents (it does not collapse while a child is active).

### Inactive Items

Inactive direct links and group headers use muted text colors and have no background fill. On hover, they display a subtle background highlight to indicate interactivity.

> ![Screenshot: Active navigation state showing highlighted item](screenshots/nav-active-state.png)

---

## Collapsible Groups

### Expanding and Collapsing

- Click the **group header** (the row with the icon, label, and chevron) to toggle the group open or closed.
- When **expanded**, the chevron points upward and the sub-items are revealed with a smooth animation. Sub-items are indented and connected to the group header by a thin vertical line on the left.
- When **collapsed**, the chevron rotates to point downward and the sub-items are hidden.

### Default State

All groups start in the **expanded** state when the page first loads. Your expand/collapse preferences are maintained during your current session but reset when you reload the page.

### Visual Hierarchy

Collapsible groups are visually separated from the direct links at the top of the sidebar by a horizontal divider. Additional dividers appear between consecutive groups to help distinguish sections.

> ![Screenshot: Sidebar with some groups expanded and some collapsed](screenshots/nav-groups-expanded-collapsed.png)

---

## Collapsed Sidebar Mode

The sidebar supports a **collapsed mode** where it shrinks to show only icons, without labels. This gives more horizontal space to the main content area.

### Behavior in Collapsed Mode

- **Direct links** display only their icon, centered in the narrow sidebar. Hovering over an icon reveals a **tooltip** with the item's label.
- **Collapsible groups** display only the group icon. Clicking the icon navigates to the group's **first sub-item** (e.g., clicking the Tasks icon navigates to the Tasks Dashboard). Hovering shows a tooltip with the group name.
- If any sub-item in a group is the current active page, the group icon receives the active highlight treatment.

> ![Screenshot: Collapsed sidebar with tooltips](screenshots/nav-collapsed-sidebar.png)

---

## Company Switcher

If your account is associated with multiple companies, you can switch between them:

1. Navigate to the `/companies` page (accessible from the application header or by visiting the URL directly).
2. The **"Your Companies"** page displays a card for each company you belong to.
3. Click a company card to switch to that company's workspace.

When you switch companies, the entire URL structure changes to reflect the new company's slug (e.g., from `/acme-mortgage/loans` to `/pacific-lending/loans`), and all data displayed in the application reflects the selected company.

> **Note:** Each company is a completely isolated workspace. Data, settings, employees, loans, and all other records are entirely separate between companies.

> ![Screenshot: Company switcher page](screenshots/company-switcher.png)

---

## Mobile and Responsive Behavior

EpochOS is built with responsive design principles using a modern CSS framework (Tailwind CSS):

- **Desktop (large screens)** -- The sidebar is fully visible alongside the main content area. Both direct links and collapsible groups display their full labels and icons.
- **Tablet (medium screens)** -- The sidebar may automatically collapse to icon-only mode to preserve horizontal space for the main content. Tooltips provide access to labels on hover.
- **Mobile (small screens)** -- The sidebar may be hidden behind a hamburger menu or slide-out drawer, allowing the main content to use the full screen width. Tapping the menu icon reveals the sidebar as an overlay.

The main content area is fully responsive and adjusts its layout (grid columns, padding, font sizes) based on the available screen width.

> ![Screenshot: Mobile view with sidebar as overlay](screenshots/nav-mobile-responsive.png)

---

## Keyboard and Accessibility

- All navigation items are **focusable** and can be activated with the keyboard.
- Collapsible group headers are rendered as `<button>` elements, ensuring screen readers announce them as interactive controls.
- Sub-items within groups are standard `<a>` links, navigable with Tab and activated with Enter.
- Tooltips in collapsed mode provide accessible labels for icon-only buttons.

---

## Quick Reference

| Section | Type | Items |
|---------|------|-------|
| Dashboard | Direct link | 1 page |
| Data Analytics | Direct link | 1 page |
| Loan Pipeline | Direct link | 1 page |
| Policies | Direct link | 1 page |
| Tasks | Collapsible group | 4 sub-pages |
| Quality Control | Collapsible group | 2 sub-pages |
| Recruiting | Collapsible group | 2 sub-pages |
| Commission | Collapsible group | 3 sub-pages |
| Accounting | Collapsible group | 7 sub-pages |
| Directories | Collapsible group | 2 sub-pages |
| Administration | Collapsible group | 2 sub-pages |
| **Total** | | **25 pages** |
