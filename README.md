# Bike Data European Customer Segment Conversion Analysis

# Overview

This project analyzes a bike sales dataset to identify which European customer segments convert best (and worst) into bike buyers, and what factors are driving those differences. The workbook takes raw customer-level data through cleaning, segmentation, and visualization to answer a specific business question rather than reporting generic summary statistics.

# Business Question

**Which European customer segments have the highest and lowest conversion rates for bike purchases, and what are their primary deciding factors?**

The objective was intentionally narrowed from a vague brief into a testable question using an **Objective → KPI → Dimension** framing: conversion rate (KPI) broken out across demographic and behavioral dimensions (occupation, income, age, commute distance), first individually and then in combination.

# Workbook Structure

| Sheet | Purpose |
|---|---|
| `ReadMe` | In-file project summary — purpose, methodology, key findings, and limitations |
| `bike_buyers` | Untouched raw data source (1,026 records, all regions) |
| `Europe` | Cleaned dataset filtered to Europe, with helper columns for bracketing and standardized labels |
| `Segment Analysis` | Live conversion-rate tables by individual dimension (occupation, education, cars owned, commute bracket, etc.) |
| `Combined Segment Analysis` | Two-way conversion-rate tables combining the strongest single drivers (e.g., Age × Occupation, Income × Commute) |
| `Dashboard` | Chart-based visual summary of headline metrics |

# Data Fields

**Raw fields (`bike_buyers`):** ID, Marital Status, Gender, Income, Children, Education, Occupation, Home Owner, Cars, Commute Distance, Region, Age, Purchased Bike

**Added in `Europe` (cleaning/enrichment):** Income Bracket, Commute Bracket, Age Bracket, Purchase Count — derived columns used to group continuous variables into analyzable segments and standardize category labels (e.g., `M`/`F` → `Married`/`Married`, `Female`).

# Methodology

1. **Data Understanding** — Identified the primary key (`ID`), separated dimensions from measures, and verified the workbook's actual contents before trusting the initial project brief.
2. **Business Framing** — Converted a vague objective into a specific, testable question following an Objective → KPI → Dimension chain.
3. **Exploratory Data Analysis** — Filtered to the Europe region, built bracketed helper columns, and calculated live conversion rates via `COUNTIFS` and `INDEX` against the cleaned data (not hardcoded values), so all tables update if the source data changes.
4. **Segmentation** — Analyzed single dimensions first, then combined the two strongest drivers to surface sharper targeting/de-targeting opportunities.

# Key Findings

- **Skilled Manual** occupation converts best of all single segments at **63.3%** (n=30)
- **Young age bracket** converts best by age at **56.9%** (n=137)
- **Low income bracket** converts best by income at **50.6%** (n=241)
- **Short commute distance** converts best by commute at **53.5%** (n=226)
- Combined segments: **Young × Clerical** converts highest overall at **90%** (n=10, small sample), followed by **Young × Skilled Manual** at **67.1%** (n=70)
- **Low Income × Short Commute** is the strongest reliable combined segment at **53.1%** (n=209)
- Overall Europe conversion rate: **49.3%** (n=300)
- Weakest single segment: **Management** occupation at **18.8%**

# Limitations

Some combined segments (e.g., Young × Skilled Manual) have sample sizes under 15 and should be treated as **directional**, not statistically robust.

# How to Use This Workbook

1. Start with the `ReadMe` tab inside the workbook for the condensed in-file summary.
2. Review `Europe` to see how raw data was cleaned and bracketed.
3. Explore `Segment Analysis` for single-dimension conversion rates.
4. Explore `Combined Segment Analysis` for two-way segment interactions.
5. View `Dashboard` for the headline chart summary.

All conversion rate tables are calculated live with `COUNTIFS` and `INDEX`, so they will recalculate automatically if the underlying `Europe` data is edited.
