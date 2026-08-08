# Trend & Predict

A self-contained, browser-only tool for spotting trends and building quick forecasts from any sales/market spreadsheet. Built and tested against a real pharma market-data export (MAT, sales, quantity and price by brand/company across periods), but works on any wide-format dataset with repeating time-based columns.

**Live app:** https://coldop69.github.io/Cipla-Ai-agent/

## What it does

- **Upload a CSV** (drag-and-drop or file picker) — nothing leaves the browser, there's no backend.
- **Auto-detects trend metrics** by recognizing repeating column headers like `MAT FEB'24` / `MAT FEB'25` / `MAT FEB'26` or `Sales Jan` / `Sales Feb`, and groups them into timelines automatically.
- **Trend charts** — pick a metric and an optional "group by" dimension (company, brand, segment, etc.), see the top movers as a line chart with gridlines, a linear-trend forecast for the next period, and a full breakdown table.
- **Top gainers / decliners** — automatically ranked by % change across the detected timeline.
- **Predictive model** — pick a target column and feature columns, and it fits a multiple linear regression (with standardization + ridge regularization) entirely in JavaScript: equation, R², RMSE, an actual-vs-predicted scatter, a live "what-if" calculator, and a button to download predictions for every row as CSV.
- **Report tab** — a plain-text summary of every detected trend, forecast, and the trained model, downloadable in one click.

## Using it

Open `index.html` (or the GitHub Pages link above) in any modern browser and drop in a CSV. If your data is in Excel, use **File → Save As → CSV** first.

## Tech notes

Single HTML file, no build step, no dependencies — vanilla JS, hand-rolled CSV parsing, and inline SVG charts. Designed to be redeployed by just replacing `index.html`.
