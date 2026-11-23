# Excel model attachment

Canonical workbook name: **`Estimation_Model_1702.xlsx`**

## Preferred options (pick one)

1. **Cursor Project store** — keep the workbook in the Project `docs/` store (already used for HNCH). Agents read it from there; no need to commit the binary here.
2. **Local sibling / absolute path** — place or copy the file outside git and record the path below for humans/agents on this machine.
3. **Symlink into this folder** (optional, local only) — e.g. on Windows PowerShell:

   ```powershell
   # Example only — adjust source path
   New-Item -ItemType SymbolicLink `
     -Path ".\Estimation_Model_1702.xlsx" `
     -Target "C:\path\to\Estimation_Model_1702.xlsx"
   ```

   Add the real `.xlsx` to `.gitignore` (already ignored) so a symlink target or accidental copy is not committed.

## Do not

- Commit secrets or customer rate books.
- Treat broken sheets (`Agile`, `Staffing w Built In CO` `#REF!`) as required product behavior without confirmation.

## Machine note (Brett / FatherBox2026)

Typical repos:

- App: `C:\Users\brett\repos\hnch`
- Meta: `C:\Users\brett\repos\hnch-meta-repo`

Update this note if the workbook’s local path is standardized later.
