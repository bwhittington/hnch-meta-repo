---
name: estimation-fidelity
description: >-
  Keep HNCH estimation behavior faithful to Estimation_Model_1702.xlsx when
  changing product design, calc engine, or domain docs.
---

# estimation-fidelity

When changing estimation behavior or proposing product design for HNCH:

1. Treat `Estimation_Model_1702.xlsx` (and `docs/estimation-model-overview.md`) as the behavioral source of truth. Re-verify with the workbook / `xlsx` skill before shipping calc changes — the overview is a summary, not a substitute.
2. Preserve Inventory / Task / Hybrid modes, phase codes (PL…WA), staffing vs unstaffed, Additional Costs, and Fixed-Fee vs T&M pricing semantics unless Brett explicitly overrides.
3. Do not “simplify away” PERT/Avg statistics, Setup ratios, or test phase splits (TCP/TCE/TBF) without asking.
4. Broken workbook sheets (`Staffing w Built In CO`, `Agile` `#REF!`, unwired `Task Breakdown`) are not required product scope by default.
5. Implement code only in https://github.com/bwhittington/hnch ; keep agent assets and model notes in this meta-repo.
