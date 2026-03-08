# Multi-Company Management

EpochOS is built as a multi-tenant platform, meaning a single deployment can serve multiple independent companies. Each company has its own data, employees, loans, settings, and configurations. This page explains how multi-tenancy works, how to create and manage companies, and how data isolation is maintained.

## How multi-tenancy works

### The company model

Every piece of data in EpochOS belongs to a company. The Company record is the root entity that all other records reference:

| Field | Description |
|-------|-------------|
| **Name** | The display name of the company (e.g., "Acme Mortgage") |
| **Slug** | A unique, URL-safe identifier used in routing (e.g., "acme-mortgage") |
| **NMLS** | The company's NMLS number (optional) |
| **Is Active** | Whether the company is enabled. Inactive companies cannot be accessed by their employees. |
| **LOS** | The company's Loan Origination System (Arive, LendingPad, Encompass, BytePro, or Other) |
| **Other LOS** | Free-text field for specifying the LOS name when "Other" is selected |
| **Email Domains** | A list of email domains associated with the company |
| **Stripe Customer ID** | The Stripe customer identifier for billing (set automatically) |
| **Stripe Session ID** | The Stripe checkout session identifier (set automatically) |
| **API Key** | A unique UUID used for API access (generated automatically) |

### Company slugs and routing

The company slug is a critical part of how EpochOS routes requests. All company-scoped pages use the slug in the URL:

```
/{companySlug}/loans
/{companySlug}/employees
/{companySlug}/commissions
/{companySlug}/recruiting
/{companySlug}/qc
/{companySlug}/settings
```

**Slug requirements:**

- Must be lowercase
- Must contain only alphanumeric characters and hyphens
- Must start and end with an alphanumeric character
- Must be unique across all companies in the platform

**Examples of valid slugs:** `acme-mortgage`, `first-national`, `pacific-lending-group`

**Examples of invalid slugs:** `Acme Mortgage` (spaces and uppercase), `-acme` (starts with hyphen), `acme_mortgage` (underscores)

### Data isolation

Data isolation between companies is enforced at the database level through Supabase Row Level Security (RLS). Every database table includes a `companyId` column, and queries are scoped to the authenticated user's company.

This means:

- A user at Company A cannot see, query, or modify data belonging to Company B.
- Database queries automatically include the `companyId` filter.
- Even if a user knows the ID of a record in another company, they cannot access it.
- Super admins bypass this isolation for administrative purposes.

Each company effectively operates as its own isolated instance, sharing only the platform infrastructure.

## Creating a company

Only super admins can create new companies.

### Step by step

1. Navigate to `/admin/companies`.
2. Click **Add Company**.
3. Fill in the company form:

| Field | Required | Description |
|-------|----------|-------------|
| **Company Name** | Yes | The display name for the company |
| **Slug** | Yes | The URL identifier. Must be unique, lowercase, alphanumeric with hyphens. |
| **NMLS** | No | The company's NMLS number |
| **LOS** | No | The company's Loan Origination System |
| **Other LOS** | No | LOS name when "Other" is selected |
| **Email Domains** | No | Email domains associated with the company |
| **Active** | -- | Whether the company is active. Defaults to active. |

4. Click **Create Company**.
5. You will be redirected to the company list.

> ![Screenshot: Create Company form showing name, slug, NMLS, LOS dropdown, and email domains fields](screenshots/create-company.png)

### Slug validation

The system validates the slug before creating the company:

- If the slug does not match the required pattern (lowercase alphanumeric with hyphens), the form displays a validation error.
- If a company with the same slug already exists, the creation fails with an error message.

### After creation

Once a company is created, it needs additional setup before employees can use it:

1. **Add branches** -- Create at least one branch for employee assignment.
2. **Add employees** -- Create employee records for the people who will use the platform.
3. **Configure settings** -- Set up payroll, commission templates, and other company-specific settings.
4. **Import data** -- Upload existing loans, set up lenders, and configure lead sources.

See [Company Setup](../company-setup/README.md) for detailed guidance on initial configuration.

## Managing companies

### Company list

The company list at `/admin/companies` shows all companies with the following information:

| Column | Description |
|--------|-------------|
| **Name** | Company name (clickable link to detail page) |
| **Slug** | URL slug |
| **Active** | Active/inactive status |
| **Employees** | Number of employee records |
| **Branches** | Number of branches |
| **Created** | When the company was created |

> ![Screenshot: Company list table in the admin panel showing company names, slugs, employee counts, and status](screenshots/company-list.png)

### Company detail page

Click on a company name to view its detail page at `/admin/companies/{id}`. The detail page shows:

- All company fields
- Employee roster with names, emails, roles, and archive status
- Branch and employee counts

> ![Screenshot: Company detail page showing company info, employee roster, and counts](screenshots/company-detail.png)

### Editing a company

To edit a company:

1. Navigate to the company detail page at `/admin/companies/{id}`.
2. Click **Edit**.
3. Modify any fields.
4. Click **Save**.

When changing a company's slug, the system validates that the new slug is not already in use by another company. Note that changing a slug will change all of the company's URLs and may break bookmarks.

### Activating and deactivating companies

To toggle a company's active status:

1. Navigate to the company detail page.
2. Click **Activate** or **Deactivate**.

Deactivating a company prevents its employees from accessing the platform. The company's data is preserved and can be reactivated at any time. This is useful for:

- Suspending a company that has not paid
- Temporarily disabling access during a migration
- Keeping historical data for a company that has closed

## Stripe integration

EpochOS includes Stripe integration fields for billing and subscription management:

| Field | Description |
|-------|-------------|
| **Stripe Customer ID** | A unique identifier in Stripe that links the EpochOS company to a Stripe customer record. Used for billing, invoicing, and subscription management. |
| **Stripe Session ID** | The checkout session identifier from Stripe, used during the initial signup or subscription change process. |

These fields are managed automatically by the platform's billing system. Super admins can view them on the company detail page but typically do not need to modify them directly.

### Billing workflow

The typical billing workflow is:

1. A company is created in EpochOS.
2. When the company subscribes, a Stripe customer record is created and the `stripeCustomerId` is saved.
3. Stripe handles recurring billing and payment processing.
4. If payment lapses, the super admin can deactivate the company until billing is resolved.

## Platform statistics

The admin dashboard at `/admin` provides a high-level view of the entire platform:

| Statistic | Description |
|-----------|-------------|
| **Total Companies** | How many companies exist in the platform |
| **Active Companies** | How many companies are currently active |
| **Total Employees** | Total non-archived employees across all companies |

These statistics help super admins monitor platform growth and identify potential issues (e.g., a high number of inactive companies).

> ![Screenshot: Admin dashboard showing total companies, active companies, and total employees cards](screenshots/admin-platform-stats.png)
