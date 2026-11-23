# Source model attachment

Canonical workbook name: **`Estimation_Model_1702.xlsx`**

Behavioral summary for agents: [estimation-model-overview.md](./estimation-model-overview.md).

## Preferred options (pick one)

1. **Cursor Project store** — keep the workbook in the Project `docs/` store (already used for HNCH). Agents read it from there; no need to commit the binary here.
2. **Local sibling / absolute path** — place or copy the file outside git and note the path for humans/agents on this machine.
3. **Local symlink** (optional) — e.g. on Windows PowerShell:

   ```powershell
   # Example only — adjust source and target paths
   New-Item -ItemType SymbolicLink `
     -Path ".\Estimation_Model_1702.xlsx" `
     -Target "C:\path\to\Estimation_Model_1702.xlsx"
   ```

   Real `.xlsx` files are gitignored so accidental copies are not committed.

## Do not

- Commit secrets or customer rate books.
- Treat broken sheets (`Agile`, `Staffing w Built In CO` `#REF!`) as required product behavior without confirmation.

## Typical local layout (example — adjust per machine)

```
repos/hnch
repos/hnch-meta-repo
```

Record the workbook’s real path in a local note outside git if needed; do not commit customer workbooks.
