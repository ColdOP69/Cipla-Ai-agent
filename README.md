# Trend & Predict

A self-contained, browser-only tool for spotting trends and building quick forecasts from any sales/market spreadsheet. Built and tested against a real pharma market-data export (MAT, sales, quantity and price by brand/company across periods), but works on any wide-format dataset with repeating time-based columns.

**Live app:** https://coldop69.github.io/Cipla-Ai-agent/

## What it does

- **Upload a CSV or Excel file** (`.csv`, `.xlsx`, `.xlsm` — drag-and-drop or file picker) — nothing leaves the browser, there's no backend. Multi-sheet workbooks get a sheet picker, pre-selecting the largest sheet.
- **Auto-detects trend metrics** by recognizing repeating column headers like `MAT FEB'24` / `MAT FEB'25` / `MAT FEB'26` or `Sales Jan` / `Sales Feb`, and groups them into timelines automatically.
- **Dashboard overview** — sparkline KPI cards per detected metric (with a linear-trend forecast) and a composition donut that auto-picks a sensible category to break any metric down by.
- **Trend charts** — pick a metric and an optional "group by" dimension (company, brand, segment, etc.); toggle between line and bar, click a legend item to isolate a series, hover any point for the exact value, and see a full breakdown table.
- **Top gainers / decliners** — automatically ranked by % change across the detected timeline (only genuine gains/declines — no mislabeling a small positive as a "decline" just because it's the weakest mover in the group).
- **Predictive model** — pick a target column and feature columns, and it fits a multiple linear regression (with standardization + ridge regularization) entirely in JavaScript: equation, R², RMSE, a standardized feature-importance chart, an actual-vs-predicted scatter, a live "what-if" calculator, and a button to download predictions for every row as CSV.
- **Report tab** — a dashboard summary (KPI cards, biggest movers, model summary) plus the full text report in a collapsible section, with Copy and Download actions.

## Using it

Open `index.html` (or the GitHub Pages link above) in any modern browser and drop in a `.csv`, `.xlsx`, or `.xlsm` file.

## Tech notes

Single HTML file, no build step, no external dependencies — vanilla JS, hand-rolled CSV and XLSX parsing (the latter reads the `.xlsx` zip container directly using the browser's native `DecompressionStream`, no library), and inline SVG charts. Designed to be redeployed by just replacing `index.html`.
