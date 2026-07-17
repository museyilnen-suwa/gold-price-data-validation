# XAUUSD Historical Data — QA & Reporting Project

**Portfolio project — data validation, cleaning, aggregation and reporting on a real 494,235-row financial dataset**

## Summary

I sourced a real 15-minute XAUUSD (Gold/USD) price feed covering 11 June 2004 to 30 January
2026 (494,235 records) and turned it into a validated, well-documented Excel deliverable —
the kind of workbook a trading desk, research team, or ops function could hand to a
non-technical stakeholder.

## What I did

1. **Parsed the raw feed.** The source file was semicolon-delimited with a non-standard
   `YYYY.MM.DD HH:MM` timestamp and mixed decimal precision — I standardised it into a clean,
   analysis-ready table.
2. **Validated data integrity.** I designed and ran eight checks across the full dataset:
   missing values, duplicate timestamps, negative/zero prices, OHLC logic (High is always the
   highest value in the bar, Low always the lowest), zero-volume bars, timestamp-gap review,
   and date-range continuity. Full results are logged in the workbook's **Validation Log** tab.
3. **Aggregated the data.** Rolled 494,235 fifteen-minute bars up into 5,531 daily OHLCV bars,
   then into a 23-year yearly summary — built with live Excel formulas
   (`SUMIFS`, `MAXIFS`, `MINIFS`, `COUNTIFS`, `INDEX`/`MATCH`) rather than pasted-in numbers, so
   the whole summary recalculates if the underlying data changes.
4. **Built a dashboard.** Year-end close price trend, annual trading volume, and yearly
   high/low range, all chart-driven from the formula tables.
5. **Documented everything.** A data dictionary, a validation log with method and result for
   every check, and this write-up, so the process is fully reproducible and auditable.

## Tools used

- **Python (pandas)** — parsing, cleaning, and resampling the 494k-row raw file (a workbook
  that size isn't practical to hand-check row by row).
- **Excel (openpyxl formulas)** — the deliverable itself: a formula-driven summary and
  dashboard that a reviewer can open, inspect, and recalculate.

## Key results

| Check | Result |
|---|---|
| Missing values | 0 |
| Duplicate timestamps | 0 |
| Invalid OHLC rows (High/Low logic) | 0 |
| Negative or zero prices | 0 |
| Zero-volume bars | 0 |
| Date coverage | 2004–2026, all 23 years present |

## Files in this deliverable

- `XAUUSD_Data_QA_Report.xlsx` — the full workbook (Overview, Data Dictionary, Validation Log,
  Raw Data Sample with live formulas, Daily Summary, Yearly Summary, Dashboard).
- `XAU_15m_data_clean.csv` — the full cleaned dataset (494,235 rows) in standard
  comma-delimited, ISO-timestamp format.
- This README as the project case study.

## Why this is relevant to a data entry / data quality role

This project is built around the core of the job: **getting large volumes of raw data into a
correct, standardised, and clearly documented state, and proving that it's correct.** It shows
I can work with a large real-world file without shortcuts, design my own validation rules
rather than assume the data is clean, use spreadsheet formulas properly (not hardcoded
numbers), and write it all up so someone else can follow exactly what I did and why.
