# Estimation model overview

> **Provenance:** Agent-facing summary of durable workbook facts, cross-checked 2026-11-23 (America/New_York) against Project store `docs/estimation-model-plan.md` (§1–2 / domain vocabulary / calc chain) and prior workbook notes for `Estimation_Model_1702.xlsx`.  
> **Not a substitute for the workbook.** Re-verify with the `.xlsx` (and Anthropic `xlsx` skill) before changing product calc behavior.  
> **Out of scope here:** MVP product choices, tech stack, and open questions from the plan (§3–6) — those are not domain “truth” until Brett decides.

Source of truth for behavior: Excel workbook `Estimation_Model_1702.xlsx`.

## Estimation modes

Basis of estimate (Setup / Configuration data list `BasisOfEstimateType`):

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

- Widget catalog (`Inventory Widgets`): Simple / Medium / Complex hour rates.
- Inventory lines (`Inventory Worksheet`): scope hierarchy + widget×complexity counts; build = `SUMPRODUCT` of counts × rates.
- Inventory Assumptions: Most Likely from inventory build; optional Best/Worst → PERT-style estimate `max(Likely, (Best + Worst + 4×Likely)/6)` when both ends present; σ ≈ `(Worst − Best) / 6`; contingency rollup from σ × factor.
- Non-build phases: Setup ratios of build; test splits TCP/TCE/TBF; then PM%, SA%, Contingency% on Hour Aggregation.

## Task path (summary)

- Sheet name in workbook: **Tasked Based**.
- Tasks under phase groups with Min / Likely / Max.
- Derived: PERT = `(Min + 4×Likely + Max) / 6` when all three present; Avg = midpoint of Min/Max; staffing statistic selectable (Min / Likely / PERT / Avg / Max).
- Non-build phases may use Setup ratios of Build or explicit task totals (`Override Ratios?`).

## Staffing & pricing (summary)

- **Staffed:** people × hrs/week × week grid of phase codes; compare to estimate (`COUNTIF`-style hours).
- **Unstaffed:** role hour buckets without week grid.
- **Additional Costs:** non-staff line items.
- Contract types: **Fixed-Fee** and **Time & Materials**.
- T&M: typically pulls **Staffed**; bill rates + loaded costs. Fixed: typically pulls **Unstaffed**; loaded costs + sales-entered retail price.
- Both pricing sheets expose a PM “baseline” block for paste into a separate budget workbook.

## Workbook workflow

1. Architecture → 2. Detailed scope → 3. Setup ratios → 4. Widget catalog → 5. Inventory (and/or tasks) → 6. Hand off for staffing/pricing.

## Known broken / peripheral sheets (in the source workbook)

- `Staffing w Built In CO` and `Agile` contain `#REF!` on build inputs.
- `Task Breakdown` is a standalone legacy example, not wired into Hour Aggregation.

Do not treat those broken sheets as required product behavior unless Brett says otherwise.
