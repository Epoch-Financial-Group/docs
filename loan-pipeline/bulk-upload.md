# Bulk Upload

EpochOS supports importing loans in bulk via CSV file upload. This is the fastest way to onboard an existing pipeline, sync data from your Loan Origination System (LOS), or do periodic pipeline updates.

## Getting to the upload page

1. Navigate to the pipeline at `/{company}/loans`.
2. Click the **Upload CSV** button in the page header.
3. You will land on `/{company}/loans/upload`.

> **Screenshot placeholder:** *Upload CSV button in the pipeline header.*

---

## Upload types

Before selecting a file, choose an upload type. There are three options:

| Upload Type | Label | Description |
|-------------|-------|-------------|
| **pipeline** | Pipeline Report | The standard import mode. Creates new loans (matched by broker loan number) or updates existing loans. Affects commission calculations. |
| **analyticsOnly** | Analytics Only | Imports loans for reporting and analytics purposes only. Employees auto-created during this upload are marked as analytics-only and do not affect commission calculations. |
| **feeReport** | Fee Report | Updates fee fields on existing loans only. Does not create new loans. Used for importing fee data from lender reports. |

> **Screenshot placeholder:** *Upload type selection showing three radio cards.*

---

## Selecting a file

After choosing an upload type, select your CSV file by either:

- Dragging and dropping the file onto the drop zone
- Clicking the drop zone to open a file browser

**File requirements:**
- File format: `.csv` only
- Maximum file size: 10 MB
- Must have a header row

> **Screenshot placeholder:** *File drop zone with drag-and-drop area.*

---

## Preview and column mapping

After selecting a file, EpochOS parses it and shows a preview:

1. **Column mapping summary** -- Shows which CSV columns were recognized and mapped to loan fields. Recognized columns appear as colored pills.
2. **Ignored columns** -- Collapsible section showing CSV columns that were not recognized. These columns are skipped during import.
3. **Data preview table** -- Shows the first several rows of mapped data so you can verify the mapping is correct.
4. **Validation errors** -- Any parsing issues found during preview.

> **Screenshot placeholder:** *Column mapping preview showing recognized columns as pills and a data preview table.*

### Replacing a file

If the mapping looks wrong, click **Replace** to select a different file, or click **X** to clear the selection and start over.

---

## Column reference -- Pipeline and Analytics uploads

The CSV importer uses flexible header matching. It recognizes many common header names from popular LOS exports (including Arive, LendingPad, Encompass, and others). Headers are matched case-insensitively.

### Loan identifiers

| Recognized CSV Headers | Maps To | Notes |
|------------------------|---------|-------|
| `Broker Loan Number`, `Broker Loan #`, `Loan Number`, `Loan #`, `BrokerLoan#`, `BrokerLoanNo`, `Arive Loan ID` | Broker Loan # | **Required.** Used to match existing loans for updates. |
| `Lender Loan Number`, `Lender Loan #`, `LenderLoan#` | Lender Loan # | |

### Borrower

| Recognized CSV Headers | Maps To | Notes |
|------------------------|---------|-------|
| `Borrower First Name`, `Primary Borrower First Name`, `First Name`, `Borr First Name` | Borrower First | |
| `Borrower Last Name`, `Primary Borrower Last Name`, `Last Name`, `Borr Last Name` | Borrower Last | |
| `Primary Borrower`, `Borrower Name`, `Borrower` | Borrower Name | Full name; split into first/last automatically |
| `Credit Score`, `Borrower Credit Score`, `FICO`, `FICO Score`, `Loan FICO` | Credit Score | Must be 300-850 |

### Property

| Recognized CSV Headers | Maps To |
|------------------------|---------|
| `Property Address`, `Address`, `Subject Property Address`, `Street Address`, `Subject Address Line 1` | Address |
| `Property Unit`, `Unit`, `Unit #`, `Apt`, `Apt/Unit #` | Unit |
| `Property City`, `City`, `Subject Property City`, `Subject City` | City |
| `Property County`, `County`, `Subject County` | County |
| `Property State`, `State`, `Subject Property State`, `Subject State` | State |
| `Property Zip`, `Zip`, `Zip Code`, `ZipCode`, `Postal Code`, `Subject Zip` | ZIP |
| `Occupancy Type`, `Occupancy`, `Occupancy Status` | Occupancy |

State values accept both full state names (e.g., "California") and abbreviations (e.g., "CA").

Occupancy values are mapped flexibly: "Primary Residence", "Owner Occupied", "Second Home", "2nd Home", "Investment Property" all map correctly.

### Loan details

| Recognized CSV Headers | Maps To | Accepted Values |
|------------------------|---------|-----------------|
| `Loan Purpose`, `Purpose`, `Transaction Type` | Purpose | Purchase, Refinance, Cash Out Refinance, No Cash Out Refinance, Streamlined Refinance |
| `Loan Type`, `Type`, `Product Type`, `Mortgage Type` | Loan Type | Conventional, FHA, VA, USDA, Non-QM, NonQM, Reverse Mortgage, HELOC, Commercial, HELOAN |
| `Payer Type`, `Payer`, `Comp Payer` | Payer | Lender, Lender Paid, Borrower, Borrower Paid, Investor, Seller |
| `Channel` | Channel | Broker, Non-Del, NonDelegatedCorrespondent |
| `Status`, `Loan Status`, `Milestone`, `Current Milestone` | Status | See [Loan Statuses](loan-statuses.md); flexible matching |
| `Lead Provided By`, `Lead Source` | Lead Source | Matched by name; creates new lead source if not found |

### Financial

| Recognized CSV Headers | Maps To |
|------------------------|---------|
| `Loan Amount`, `Amount`, `Total Loan Amount`, `Base Loan Amount` | Loan Amount |
| `Broker Compensation`, `Compensation`, `Broker Comp`, `Comp Amount`, `Compensation Amount` | Broker Comp |
| `Rate`, `Interest Rate`, `Note Rate` | Rate |
| `Company Margin` | Company Margin |
| `Net Discount Points`, `Discount Points` | Discount Points |
| `Amortization Term` | Amort. Term |

Dollar values are cleaned automatically -- currency symbols (`$`), commas, and whitespace are stripped before parsing.

### Timeline dates

| Recognized CSV Headers | Maps To |
|------------------------|---------|
| `App Intake` | App Intake Date |
| `App/TRID Completed Date` | TRID App Date |
| `Qualification` | Qualification Date |
| `Loan Setup` | Loan Setup Date |
| `Disclosed` | Disclosed Date |
| `Preapproval Date` | Pre-Approved Date |
| `Approved With Conditions` | Approved w/ Conditions Date |
| `Submit to Underwriting` | Submitted to UW Date |
| `Re Submittal Date` | Resubmitted Date |
| `Clear to Close` | CTC Date |
| `Docs Out` | Docs Out Date |
| `Loan Funded` | Funded Date |
| `Docs Signed / Loan Closed` | Closed Date |
| `Adverse` | Adverse Date |
| `Lock Date` | Lock Date |
| `Lock Expiration` | Lock Expiration Date |
| `Broker Check Received Date` | Check Received Date |

Dates are parsed flexibly. The importer accepts US format `MM/DD/YYYY` (common in LOS exports) and falls back to standard date parsing.

### Team members

| Recognized CSV Headers | Maps To |
|------------------------|---------|
| `Loan Officer`, `Loan Officer Name`, `LO`, `LO Name`, `Originator`, `Originator Name`, `Primary Loan Officer Name` | Loan Officer |
| `Primary Loan Officer Email`, `Loan Officer Email` | LO Email |
| `Primary Loan Officer Assistant Name` | LOA 1 Name |
| `Primary Loan Officer Assistant Email` | LOA 1 Email |
| `Loan Officer Assistant #2 Name` / `Email` | LOA 2 |
| `Loan Officer Assistant #3 Name` / `Email` | LOA 3 |
| `Loan Officer #2 Name` / `Email` | LO 2 (added as assistant) |
| `Loan Officer #3 Name` / `Email` | LO 3 (added as assistant) |
| `Primary Loan Processor Name` | Processor 1 Name |
| `Primary Loan Processor Email` | Processor 1 Email |
| `Loan Processor #2 Name` / `Email` | Processor 2 |
| `Loan Processor #3 Name` / `Email` | Processor 3 |

### Agent information

| Recognized CSV Headers | Maps To |
|------------------------|---------|
| `Buyer Agent Name`, `Buyer Agent Email` | Buyer Agent |
| `Seller Agent Name`, `Seller Agent Email` | Seller Agent |

---

## Column reference -- Fee Report uploads

Fee report uploads only require the broker loan number to match existing loans. All other columns update fee fields:

| Recognized CSV Headers | Maps To |
|------------------------|---------|
| `Broker Loan Number` (and variants) | Broker Loan # (match key) |
| `Origination Fees` | Origination Fees |
| `Pass-Through Fees` | Pass-Through Fees |
| `Check Amount` | Check Amount |
| `Holdback` | Holdback |
| `Net Loan Revenue` | Net Loan Revenue |
| `Gross Loan Revenue` | Gross Loan Revenue |

---

## How data is mapped

### New loans vs updates

For Pipeline and Analytics uploads, the importer uses the **Broker Loan Number** as the match key:

- If a loan with that broker loan number already exists in your company, the row **updates** the existing loan with any non-empty values from the CSV.
- If no matching loan exists, a new loan is **created**.

For Fee Report uploads, only existing loans are updated. Rows with unrecognized broker loan numbers are skipped with an error.

### Employee matching

Loan officers, LOAs, and processors are matched by:

1. **Email** (exact match, case-insensitive) -- checked first
2. **Full name** (exact match, case-insensitive) -- checked second

If no match is found and the CSV includes a name, EpochOS **auto-creates** the employee with the appropriate role. The upload result summary lists any auto-created employees.

### Lender matching

Lenders are matched by name (case-insensitive). If no match is found, a new lender is auto-created. The upload result summary lists any newly created lenders.

### Lead source matching

Lead sources are matched by name (case-insensitive). If no match is found, a new lead source is auto-created.

### Status derivation

If the CSV does not include an explicit status column, the importer derives the status from the timeline dates. It checks dates in reverse order of the pipeline (from Adverse down to App Intake) and sets the status to the most advanced milestone that has a date.

---

## Processing the upload

After reviewing the preview:

1. Click **Upload {N} rows** to start the import.
2. The system processes all rows and displays results:
   - **Success banner:** Shows count of loans created and updated.
   - **Errors:** Lists any rows that could not be processed, with row number and reason.
   - **Warnings:** Lists non-fatal issues (e.g., unrecognized enum values).
   - **New lenders:** Lists any lenders that were auto-created.
   - **New employees:** Lists any employees that were auto-created.

3. If there are no errors, you are automatically redirected to the pipeline.
4. If there are errors, you remain on the upload page to review them.

> **Screenshot placeholder:** *Upload results showing success count, errors, warnings, and auto-created entities.*

---

## Tips for preparing your CSV

1. **Always include a Broker Loan Number column.** This is the only required column and is used to match existing loans.
2. **Use headers from your LOS export as-is.** The importer recognizes headers from Arive, LendingPad, Encompass, and other common systems. You usually do not need to rename columns.
3. **Leave cells empty for unknown values.** Empty cells are skipped; they do not overwrite existing data.
4. **Dollar amounts can include `$` and commas.** Values like `$350,000.00` are parsed correctly.
5. **Dates can be in MM/DD/YYYY format.** This is the most common format in LOS exports.
6. **Check the column mapping preview** before uploading. Make sure your important columns (loan number, LO name, status) are recognized.
7. **Unrecognized columns are safely ignored.** Extra columns in your CSV will not cause errors.
8. **Maximum file size is 10 MB.** For very large imports, consider splitting into multiple files.
