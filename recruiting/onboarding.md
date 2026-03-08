# Onboarding

Onboarding is the process of converting an accepted candidate into a fully operational employee. EpochOS provides a guided conversion workflow that creates the employee record, transfers data from the candidate profile, and optionally generates an onboarding checklist with tasks to complete before the new hire is ready to work.

## The conversion workflow

When a candidate reaches the **Accepted** stage (or any stage prior to conversion), you can convert them to an employee.

### Starting the conversion

1. Navigate to the candidate's detail page at `/{company}/recruiting/{id}`.
2. Click **Convert to Employee**.
3. You will be taken to the conversion form.

> ![Screenshot: Convert to Employee button on the candidate detail page](screenshots/convert-candidate-button.png)

### Conversion form fields

The conversion form is pre-filled with data from the candidate record. Review and adjust as needed.

#### Employee information

| Field | Required | Pre-filled from | Description |
|-------|----------|-----------------|-------------|
| **First Name** | Yes | Candidate first name | The employee's legal first name |
| **Last Name** | Yes | Candidate last name | The employee's legal last name |
| **Email** | No | Candidate email | Work email address for the employee |
| **Branch** | No | Candidate target branch | The branch the employee will be assigned to |
| **Tax Classification** | No | -- | W-2 or 1099 classification |
| **Start Date** | No | -- | The employee's start date |
| **Roles** | Yes | Candidate desired role | One or more roles for the employee. At least one role is required. |

Available roles:

| Role | Label |
|------|-------|
| LoanOfficer | Loan Officer |
| LoanOfficerAssistant | Loan Officer Assistant |
| Processor | Processor |
| Contractor | Contractor |
| BranchManager | Branch Manager |

> ![Screenshot: Convert to Employee form showing pre-filled fields and role checkboxes](screenshots/convert-candidate-form.png)

#### Onboarding checklist

If your company has task templates configured, you can optionally select one to generate an onboarding checklist for the new employee.

| Field | Required | Description |
|-------|----------|-------------|
| **Onboarding Checklist Template** | No | Select a task template to generate an onboarding checklist. Select "None" to skip. |

When a template is selected, the system creates a task checklist with all of the template's items. Each task's due date is calculated from the employee's start date plus the item's due-days offset defined in the template.

### What happens when you submit

The conversion process performs the following steps in a single transaction:

1. **Employee record is created** with the information from the form. The employee's `isSetupComplete` flag is set to `false`.
2. **State licenses are copied** from the candidate to the employee. Every state license on the candidate record is duplicated on the new employee record, preserving the state, license number, and expiration date.
3. **Candidate stage is updated** to **Hired** automatically.
4. **Candidate is linked** to the new employee via the `convertedEmployeeId` field.
5. **Onboarding checklist is created** (if a template was selected) with tasks and due dates.
6. **A note is added** to the candidate's notes timeline recording the conversion event.
7. **You are redirected** to the new employee's detail page.

## What data carries over

The following data is transferred from the candidate to the employee:

| Candidate field | Employee field | Notes |
|-----------------|----------------|-------|
| First name | First name | Editable during conversion |
| Last name | Last name | Editable during conversion |
| Email | Email | Editable during conversion |
| NMLS | NMLS | Copied automatically |
| Target branch | Branch | Editable during conversion |
| Desired role | Roles | Editable during conversion; can select multiple roles |
| State licenses | State licenses | All licenses copied automatically with state, number, and expiration |

The following candidate data is **not** copied to the employee but remains on the candidate record for reference:

- Phone number
- Current employer
- Source and source detail
- Production history (average monthly volume and units)
- All notes

## Post-hire setup steps

After conversion, the new employee typically needs additional setup before they are fully operational. The `isSetupComplete` flag on the employee record tracks whether this setup has been finished.

### Typical post-hire tasks

These tasks may be included in your onboarding checklist template or handled manually:

1. **Set up system access** -- Create login credentials and assign permissions.
2. **Commission template assignment** -- Assign the appropriate commission plan to the employee.
3. **Branch configuration** -- Confirm branch assignment and reporting structure.
4. **Lender access** -- Set up accounts with wholesale lenders.
5. **LOS onboarding** -- Configure the employee in your Loan Origination System (Encompass, Arive, etc.).
6. **Compliance training** -- Complete required regulatory training.
7. **State license verification** -- Verify that all state licenses are current and properly recorded.
8. **Equipment and email setup** -- Provide necessary hardware, software, and email accounts.
9. **Introduction** -- Introduce the new hire to the team and assign a mentor if applicable.
10. **Mark setup complete** -- Update the employee's `isSetupComplete` flag once all steps are done.

## Onboarding dashboard

The onboarding dashboard provides a view of all employees who have not yet completed setup.

### Accessing the dashboard

Navigate to `/{company}/recruiting/onboarding`.

### What the dashboard shows

For each employee in the onboarding process:

| Column | Description |
|--------|-------------|
| **Name** | Employee first and last name |
| **Email** | Employee email address |
| **Roles** | Assigned roles |
| **Branch** | Assigned branch |
| **Start Date** | Employee start date |
| **Checklists** | Onboarding checklists assigned, with task counts |
| **Progress** | Percentage of completed tasks across all checklists |

> ![Screenshot: Onboarding dashboard showing new employees with progress bars for their onboarding checklists](screenshots/onboarding-dashboard.png)

### Tracking progress

If an onboarding checklist was created during conversion, the dashboard shows real-time progress:

- **Total tasks** across all checklists
- **Completed tasks** that have been marked done
- **Progress percentage** displayed as a visual indicator

Clicking on an employee's name takes you to their employee detail page, where you can view and manage their checklists and tasks directly.

## Preventing duplicate conversions

A candidate can only be converted to an employee once. If the candidate already has a `convertedEmployeeId` set, the conversion button is disabled and the system displays a link to the existing employee record. This prevents accidental duplicate employee records.
