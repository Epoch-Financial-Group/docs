# Company Settings

Company Settings is the central configuration page for your EpochOS account. Here you define your company identity, select your Loan Origination System, enter your NMLS number, and configure payroll schedules that drive commission and draw calculations across the platform.

## Accessing Company Settings

1. Open the sidebar and expand the **Administration** section.
2. Click **Company Settings**.

This takes you to the settings page at `/{your-company}/settings`.

> ![Screenshot: Administration section in sidebar with Company Settings highlighted](screenshots/company-settings-nav.png)

---

## Company name

The company name appears throughout EpochOS -- in headers, reports, and exported documents.

### To change your company name

1. Navigate to **Administration > Company Settings**.
2. Locate the **Company Name** field.
3. Enter the new name.
4. Click **Save Changes**.

---

## NMLS number

Your company-level NMLS (Nationwide Multistate Licensing System) number is stored here. This is separate from individual employee NMLS numbers.

### To set or update your NMLS number

1. Navigate to **Administration > Company Settings**.
2. Find the **NMLS** field.
3. Enter your company NMLS number (e.g., `123456`).
4. Click **Save Changes**.

---

## Loan Origination System (LOS)

EpochOS integrates with several popular Loan Origination Systems. Selecting your LOS helps the platform tailor import behavior and field mappings when you upload loan data.

### Supported systems

| LOS | Description |
|-----|-------------|
| **Arive** | Arive by Fiserv |
| **LendingPad** | LendingPad cloud-based LOS |
| **Encompass** | ICE Mortgage Technology Encompass |
| **BytePro** | Byte Software BytePro Enterprise |
| **Other** | Any LOS not listed above |

### To select your LOS

1. Navigate to **Administration > Company Settings**.
2. Open the **Loan Origination System** dropdown.
3. Select your LOS from the list. If yours is not listed, choose **Other** and fill in the **Other LOS** text field that appears.
4. Click **Save Changes**.

> ![Screenshot: Loan Origination System dropdown on Company Settings page](screenshots/los-selection.png)

---

## Payroll settings

Payroll settings control how EpochOS calculates pay periods, commission schedules, and draws for your employees. The configuration is stored as flexible JSON, which means it can accommodate a wide range of payroll structures.

### Commission schedule

The commission schedule determines the date ranges used when grouping funded loans into pay periods for commission calculation.

| Setting | Options | Description |
|---------|---------|-------------|
| **Commission Period Type** | Weekly, Biweekly, SemiMonthly, Monthly | How frequently commissions are calculated |
| **Commission Period Day** | 0--6 (Sun--Sat) | For Weekly/Biweekly, the day of the week the period starts |
| **Semi-Monthly Type** | FirstAndFifteenth, FifteenthAndLast, Custom | Which days of the month to split on |
| **Monthly Type** | First, Last, Custom | Whether the period starts on the 1st, last day, or a custom day |
| **Custom Period Start / End** | 1--31 | Specific day-of-month boundaries for custom schedules |

### Payroll / draw schedule

The payroll schedule can differ from the commission schedule. For example, commissions may be calculated monthly while draws are paid biweekly.

| Setting | Options | Description |
|---------|---------|-------------|
| **Pay Period Type** | Weekly, Biweekly, SemiMonthly, Monthly | How frequently draws/payroll are processed |
| **Payroll Period Day** | 0--6 (Sun--Sat) | Day of the week for Weekly/Biweekly payroll |
| **Payroll Semi-Monthly Type** | FirstAndFifteenth, FifteenthAndLast, Custom | Semi-monthly split dates for payroll |
| **Payroll Monthly Type** | First, Last, Custom | Monthly payroll start day |

### Draw settings

| Setting | Description |
|---------|-------------|
| **Draw Calculation Type** | Default draw type for new employees: None, Hourly, or FlatAmount |
| **Draw Balances Enabled** | Whether to track cumulative draw balances that carry over between periods |
| **Daily Payroll Enabled** | Enable daily payroll mode |
| **Paycheck Date Offset** | Number of days between the end of a period and the actual paycheck date (0--31) |

### To update payroll settings

1. Navigate to **Administration > Company Settings**.
2. Scroll to the **Payroll Settings** section.
3. Adjust the fields as needed. Changes are validated before saving.
4. Click **Save Changes**.

> ![Screenshot: Payroll settings form with commission and draw configuration](screenshots/payroll-settings.png)

{% hint style="info" %}
Payroll settings are stored as a JSON object on the company record. This means they are extensible -- new settings can be added without database migrations.
{% endhint %}

---

## Related pages

- [Branches](branches.md) -- branches are organizational units within the company
- [Employees](employees.md) -- individual employee draw settings can override company defaults
- [Lead Sources](lead-sources.md) -- also managed under Company Settings
