# Estimation model overview

Source of truth for behavior: Excel workbook `Estimation_Model_1702.xlsx`.  
This file is a durable, agent-facing summary — not a substitute for the workbook.

## Estimation modes

Basis of estimate (Setup / Configuration):

| Mode | Behavior |
|------|----------|
| **Inventory-Based** | Widgets × Simple/Medium/Complex rates → build hours; other phases as ratios of build |
| **Task-Based** | Tasks under Plan/Analyze/Design/Build/Test/Deploy with Min/Likely/Max; PERT/Avg; selectable staffing statistic |
| **Hybrid** | Inventory + task hours **added** per phase |

## Phase / hour buckets

| Code | Meaning |
|------|---------|
| PL | Plan |
| AN | Analyze |
| DE | Design |
| BU | Build |
| TCP | Test Prep |
| TCE | Test Execution |
| TBF | Test Bug Fix |
| DP | Deploy |
| PM | Project Management |
| SA | Solutions Architect |
| CO | Contingency |
| WA | Warranty |

## Inventory path (summary)

- Widget catalog: Simple / Medium / Complex hour rates.
- Inventory lines: scope hierarchy + widget×complexity counts; build = weighted sum of counts × rates.
- Inventory Assumptions: optional Best/Likely/Worst (PERT-style) and 1σ-style build contingency rollup.
- Non-build phases: Setup ratios of build; test splits TCP/TCE/TBF; then PM%, SA%, Contingency%.

## Task path (summary)

- Tasks under phase groups with Min / Likely / Max.
- Derived: PERT and Avg; staffing statistic selectable (Min / Likely / PERT / Avg / Max).
- Non-build phases may use Setup ratios of Build or explicit task totals.

## Staffing & pricing (summary)

- **Staffed:** people × hrs/week × week grid of phase codes; compare to estimate.
- **Unstaffed:** role hour buckets without week grid.
- **Additional Costs:** non-staff line items.
- Contract types: **Fixed-Fee** and **Time & Materials**.
- T&M: bill rates + loaded costs. Fixed: loaded costs + sales-entered retail price.
- Both pricing sheets expose a PM “baseline” block for paste into a separate budget workbook.

## Workbook workflow

1. Architecture → 2. Detailed scope → 3. Setup ratios → 4. Widget catalog → 5. Inventory (and/or tasks) → 6. Hand off for staffing/pricing.

## Known broken / peripheral sheets (in the source workbook)

- `Staffing w Built In CO` and `Agile` contain `#REF!` on build inputs.
- `Task Breakdown` is a standalone legacy example, not wired into Hour Aggregation.

Do not treat those broken sheets as required product behavior unless Brett says otherwise.
