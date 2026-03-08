# Candidate Management

This page covers the day-to-day tasks of working with candidates in the recruiting module -- viewing the candidate list, filtering and searching, editing candidate information, and tracking interactions through notes.

## Viewing candidates

The candidate list is located at `/{company}/recruiting`. It displays a paginated table of all candidates in your company.

### Candidate table columns

| Column | Description |
|--------|-------------|
| **Name** | Candidate first and last name (clickable link to detail page) |
| **Email** | Candidate email address |
| **Stage** | Current pipeline stage, displayed as a color-coded badge |
| **Role** | Desired role |
| **Source** | How the candidate was identified |
| **Branch** | Target branch |
| **Updated** | When the candidate record was last modified |

The table is sorted by most recently updated candidates first.

> ![Screenshot: Candidate table showing candidate rows with stage badges, roles, and sources](screenshots/candidate-table.png)

### Pagination

Candidates are displayed 25 per page by default. Navigation controls appear at the bottom of the table when there are multiple pages. The page size can be adjusted up to 100.

## Filtering candidates

The candidate list includes a filter bar above the table with the following filter options:

### Search

Type a query into the search bar and press Enter to search across:

- First name
- Last name
- Email
- NMLS number
- Current employer

Search is case-insensitive and matches partial text.

### Filter dropdowns

| Filter | Options | Description |
|--------|---------|-------------|
| **Stage** | All Stages, Lead, Screening, Interview, Offer, Accepted, Hired, Declined, Withdrawn | Filter by pipeline stage |
| **Role** | All Roles, Loan Officer, Loan Officer Assistant, Processor, Contractor, Branch Manager | Filter by desired role |
| **Source** | All Sources, Referral, Job Board, LinkedIn, Direct Outreach, Website, Other | Filter by candidate source |
| **Branch** | All Branches, plus each branch in your company | Filter by target branch |

> ![Screenshot: Candidate filter bar showing search input, stage dropdown, role dropdown, source dropdown, and branch dropdown](screenshots/candidate-filters.png)

### Combining filters

Filters can be combined. For example, you can filter for all **Loan Officer** candidates in the **Interview** stage who were sourced from **LinkedIn**. All active filters are reflected in the URL as query parameters, so filtered views can be bookmarked or shared.

### Archived candidates

By default, the candidate list shows only active (non-archived) candidates. To view archived candidates, use the archived filter parameter. Archived candidates are those who have been explicitly archived rather than those in a terminal stage.

## Candidate detail view

Clicking on a candidate's name in the table opens their detail page at `/{company}/recruiting/{id}`.

### Detail page layout

The candidate detail page is organized into tabs or sections:

#### Header

The header shows the candidate's name, stage badge, and action buttons:

- **Edit** -- Open the edit form
- **Convert to Employee** -- Begin the conversion process (available when not yet converted)
- **Archive** -- Archive the candidate

> ![Screenshot: Candidate detail page header showing name, stage badge, and action buttons](screenshots/candidate-detail-header.png)

#### Overview section

Displays all candidate information at a glance:

| Category | Fields |
|----------|--------|
| **Contact** | Email, phone |
| **Recruiting** | Stage, desired role, target branch, source, source detail |
| **Background** | Current employer, NMLS |
| **Production** | Average monthly volume, average monthly units |
| **Conversion** | Link to converted employee (if applicable) |

#### State licenses

A table of the candidate's state licenses showing:

- State
- License number
- Expiration date

#### Notes

A reverse-chronological timeline of all notes on the candidate, each showing:

- Note text
- Author name
- Timestamp

#### Compensation estimator

The compensation estimator section (documented in detail on the [Compensation Estimator](comp-estimator.md) page) appears on the detail page, pre-filled with the candidate's production history.

## Editing candidate information

To edit a candidate:

1. Navigate to the candidate's detail page.
2. Click **Edit**.
3. Update any fields. All fields from the creation form are editable.
4. Update state licenses if needed (add, modify, or remove entries).
5. Click **Save**.

You will be redirected back to the candidate's detail page after saving.

### Editable fields

All fields that were available during candidate creation are also editable:

- Basic information (name, email, phone, current employer, NMLS)
- Recruiting information (stage, desired role, target branch, source, source detail)
- Production history (average monthly volume, average monthly units)
- State licenses (add, edit, or remove)

### Updating state licenses

When you edit a candidate, the state licenses section allows you to:

- **Add** a new state license by providing the state, license number, and expiration date
- **Edit** an existing license's number or expiration date
- **Remove** a license by deleting the entry

License updates are saved as part of the overall candidate update.

## Changing a candidate's stage

The candidate's stage can be updated in two ways:

1. **From the detail page:** Use the stage dropdown selector, which saves the change immediately.
2. **From the edit form:** Change the stage field and save the form.

Both methods update the candidate's stage and refresh the candidate list to reflect the change.

> ![Screenshot: Stage dropdown on candidate detail page showing all available stages](screenshots/candidate-stage-change.png)

## Tracking interactions via notes

Notes serve as the primary record of interactions with a candidate throughout the recruiting process. See the [Candidate Pipeline](candidate-pipeline.md#adding-notes) page for detailed guidance on adding and using notes.

Key points:

- Notes are append-only. Once created, notes cannot be edited or deleted.
- Each note is attributed to the employee who created it.
- Notes are displayed newest first.
- The system automatically creates a note when a candidate is converted to an employee.

## Archiving candidates

To archive a candidate:

1. Navigate to the candidate's detail page.
2. Click **Archive**.
3. You will be redirected to the candidate list.

Archiving a candidate hides them from the default candidate list view. Archived candidates are not deleted -- they can still be viewed by filtering for archived candidates. Archiving is appropriate when a candidate's pipeline journey is over and you want to keep the record but remove it from the active view.

Archiving is distinct from the Declined or Withdrawn stages. A candidate can be in any stage and still be archived. Use stages to track pipeline position and archiving to manage list visibility.
