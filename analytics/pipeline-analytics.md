# Pipeline Analytics

Pipeline Analytics provides a real-time view of your active loan pipeline, showing where loans sit across processing stages, identifying bottlenecks, measuring stage-to-stage velocity, and breaking down activity by loan officer.

## Overview

The pipeline dashboard focuses on **active loans** -- loans that have not yet reached a terminal status (Funded, CommissionPaid, Adverse, CheckReceived, or ApprovedForPayout). It answers questions like:

- How many loans are in each stage right now?
- Which loans have been stuck in a stage too long?
- How fast are loans moving through the pipeline?
- Which loan officers have the largest active pipelines?

> ![Screenshot: Pipeline analytics overview](screenshots/pipeline-overview.png)

## Key Metrics

The top of the pipeline dashboard displays four summary KPIs:

| Metric | Description |
|--------|-------------|
| **Total Active Loans** | Count of all loans currently in the pipeline (excluding terminal statuses). |
| **Total Active Volume** | Sum of loan amounts for all active pipeline loans. |
| **Avg Days in Pipeline** | Average number of days active loans have been in the pipeline, measured from creation date. |
| **New Loans This Week** | Number of loans created since the start of the current week (Sunday). |
| **Loans Advanced This Week** | Number of loans that had any status update since the start of the current week. |

## Pipeline Stages

The stage breakdown shows every processing stage with counts, total volume, and average days loans spend in that stage.

> ![Screenshot: Pipeline stage breakdown](screenshots/pipeline-stages.png)

The pipeline tracks these stages in order:

1. **App Intake** -- Initial application received
2. **Qualification** -- Borrower qualification review
3. **Loan Setup** -- Loan file setup and documentation
4. **Disclosed** -- Initial disclosures sent
5. **Pre-Approved** -- Pre-approval issued
6. **Submitted to UW** -- Submitted to underwriting
7. **Approved w/ Conditions** -- Conditionally approved
8. **Resubmitted** -- Resubmitted after addressing conditions
9. **Clear to Close** -- Final approval, ready to close
10. **Docs Out** -- Closing documents sent
11. **Closed** -- Loan closed, awaiting funding

For each stage, the dashboard shows:
- **Count** -- Number of loans currently in this stage
- **Volume** -- Total dollar volume of loans in this stage
- **Avg Days in Stage** -- How long loans typically sit in this stage before advancing

## Bottleneck Detection

The bottleneck report identifies loans that have been in their current stage for more than **14 days**. These are loans that may need attention or intervention to move forward.

> ![Screenshot: Bottleneck loans table](screenshots/pipeline-bottlenecks.png)

Each bottleneck entry shows:

| Field | Description |
|-------|-------------|
| **Loan Number** | The broker loan number |
| **Borrower** | Borrower's full name |
| **Loan Officer** | Assigned LO |
| **Status** | Current pipeline stage |
| **Days in Stage** | How many days the loan has been in its current stage |
| **Loan Amount** | Dollar amount of the loan |

The list is sorted by days in stage (longest first), so the most critical bottlenecks appear at the top.

## Pipeline Velocity

The velocity analysis measures the average number of days it takes loans to move between consecutive pipeline stages. This helps you understand where your process is fast and where it slows down.

> ![Screenshot: Pipeline velocity chart](screenshots/pipeline-velocity.png)

Each velocity measurement shows:

| Field | Description |
|-------|-------------|
| **From** | The starting stage |
| **To** | The next stage |
| **Avg Days** | Average number of calendar days between the two stages |

Velocity is calculated by looking at loans that have date stamps for both stages and averaging the difference. Stages with no data show 0 days.

## By Loan Officer

The per-LO breakdown shows each loan officer's pipeline activity:

> ![Screenshot: Pipeline by loan officer](screenshots/pipeline-by-lo.png)

| Column | Description |
|--------|-------------|
| **Name** | Loan officer's full name |
| **Active Loans** | Number of loans currently in their pipeline |
| **Total Volume** | Sum of loan amounts in their pipeline |
| **Avg Days in Pipeline** | Average age of their active loans |

The table is sorted by total volume (highest first).

## Filtering

Pipeline analytics support filtering by **Loan Officer**, allowing you to focus on a single LO's pipeline. Use the loan officer dropdown in the filter bar to narrow the view.
