# Lead Sources

Lead sources track where your loans originate from. Each loan in EpochOS can be tagged with a lead source, giving you visibility into which marketing channels, referral partners, and business development efforts are driving your pipeline and revenue.

## What lead sources are

A lead source is a simple named record -- for example, "Zillow," "Realtor Referral," "Past Client," "Builder Partnership," or "Company Website." When a loan is entered or imported into EpochOS, it can be associated with one of these lead sources.

Lead sources serve two main purposes:

1. **Tracking and analytics** -- Understand which channels produce the most volume, the highest close rates, and the best revenue. EpochOS includes lead source analytics dashboards that break down performance by source.
2. **Commission rules** -- Commission templates can include rules that vary by lead source. For example, you might pay a lower commission split on company-provided leads (where the company spent marketing dollars) versus self-generated leads (where the loan officer sourced the business themselves).

---

## Where lead sources are managed

Lead sources are managed within **Administration > Company Settings**. They are part of the settings page rather than having their own top-level section because they are simple name-only records.

1. Navigate to **Administration > Company Settings** in the sidebar.
2. Scroll to the **Lead Sources** section.

> ![Screenshot: Lead Sources section on the Company Settings page](screenshots/lead-sources.png)

---

## Adding a lead source

1. On the **Company Settings** page, find the **Lead Sources** section.
2. Enter a name in the text field (1--100 characters, required).
3. Click **Add** (or press Enter).
4. The new lead source appears in the list immediately.

### Naming suggestions

Keep lead source names concise and consistent. Here are common examples:

| Lead Source | Description |
|-------------|-------------|
| Zillow | Leads from Zillow.com |
| LendingTree | Leads from LendingTree |
| Realtor Referral | Referrals from real estate agents |
| Past Client | Repeat or referral business from previous borrowers |
| Builder | Leads from builder partnerships |
| Company Website | Inbound leads from your company's website |
| Self-Generated | Loan officer's own personal network and marketing |
| Bank Statement | Specific product-driven leads (e.g., Non-QM marketing) |

---

## Editing a lead source

1. In the **Lead Sources** list, click the edit control next to the lead source you want to rename.
2. Update the name.
3. Save the change.

The updated name will be reflected on all existing loans that reference this lead source.

{% hint style="info" %}
Renaming a lead source updates it everywhere -- historical loans, reports, and commission rules will show the new name.
{% endhint %}

---

## Deleting a lead source

1. In the **Lead Sources** list, click the delete control next to the lead source you want to remove.
2. The lead source is removed immediately.

{% hint style="warning" %}
Deleting a lead source removes it from the system. If any loans or commission rules reference the deleted lead source, those associations will be cleared. Consider renaming instead of deleting if you want to preserve historical data under a different label.
{% endhint %}

---

## How lead sources are used

### In loan tracking

When creating or editing a loan, you can select a lead source from a dropdown. This tags the loan with its origination channel.

### In analytics

The analytics module includes lead source breakdowns. You can view:
- Volume and units by lead source
- Conversion rates by source
- Revenue contribution per channel
- Trends over time

This helps management understand which channels to invest in and which are underperforming.

### In commission rules

Commission templates support conditions based on lead source. Common patterns include:

- **Company leads vs. self-generated** -- A lower split (e.g., 50 bps instead of 100 bps) when the company provided the lead
- **Partner-specific overrides** -- Different compensation when the lead comes from a specific builder or referral partner
- **Bonus tiers** -- Additional bonuses for self-generated leads that close

---

## Data model

Each lead source is a simple record:

| Field | Description |
|-------|-------------|
| **Name** | The display name of the lead source (unique per company, 1--100 characters) |

Lead sources are scoped to your company -- each company in EpochOS maintains its own list. The name must be unique within your company.

---

## Related pages

- [Company Settings](company-settings.md) -- lead sources are managed on the settings page
- [Employees](employees.md) -- employees originate loans that are tagged with lead sources
- [Lenders](lenders.md) -- lenders and lead sources are both used as dimensions in commission rule conditions
