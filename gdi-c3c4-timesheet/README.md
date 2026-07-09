# GDI c3/c4 Timesheet Generator

Internal tool for the AI Safety team (Trooper, Brian, Hiru) to generate separate monthly timesheets for the c3 (GDI Solutions) and the c4 (State AI Safety Action Fund). Single static HTML file — no build step, no server, no accounts.

## Using it

1. **Employee & period** — pick your name and the reporting month. Click calendar days to mark holidays, vacation, or sick days; these auto-log at standard hours on the c3 timesheet and are excluded when hours are spread. "Duplicate previous month" copies last month's setup (with or without hours).
2. **Select activities** — pick a program group (mirrors Asana), then the kind of work. Coding defaults come from the "Timesheet Coding: C3 vs C4" staff guidance (built into the page — open the quick reference). Each program has a General catch-all; custom activities can be added.
3. **Monthly hours** — enter total hours per activity for the month. Override any coding (c3 / c4 / split %), and flag gray-area calls for review with a note.
4. **Review & edit** — the tool spreads hours across working days into two daily grids. Every cell is editable. If you change entries after building, a warning tells you to rebuild before exporting.
5. **Export** — two Excel workbooks in the exact GDI timesheet template layout (flags and notes on a second sheet), or a landscape PDF of both sheets via print.

Work saves automatically in your browser (per month). Use "Save month to file" / "Load month from file" to archive or move between computers. Each person should use their own browser profile — storage is local and single-user.

## Deploying

Any static host works. For Netlify (same setup as the per diem calculator): connect this repo, no build command, publish directory = repo root. Or drag the folder into Netlify Drop.

Note: Excel export loads ExcelJS from cdnjs at page load, so the page needs internet on first open.

## Maintaining

- **Activities or coding defaults**: edit the `PROGRAMS` array at the top of the `<script>` block in `index.html` — one line per activity (`code: "C3" | "C4" | "SPLIT"`, `gray: true` for gray areas, `grayNote` for the tooltip).
- **People**: edit the `empName` `<select>` options.
- **Source policy**: "Timesheet Coding: C3 vs C4 — Staff Guidance" in the C3/C4 Compliance folder in Drive. If the policy changes, update both the `PROGRAMS` defaults and the built-in quick reference in step 2.
