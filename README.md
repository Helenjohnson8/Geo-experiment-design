# Geo-Experiment Design and Synthetic Control Analysis

## Overview

This project develops a geo-experiment design to evaluate the incremental
impact of a 40% increase in paid-social advertising spend across selected
U.S. markets.

The analysis uses a weighted donor-pool synthetic-control approach to
construct a counterfactual for the treatment group and evaluates candidate
treatment combinations based on:

- Revenue-share constraints
- Incremental-spend constraints
- Pre-test model fit
- Minimum detectable lift (MDE)
- Statistical power
- Audience overlap
- Structural and operational confounding risks

## Objective

The objective is to identify a treatment design that satisfies the
business constraints while providing sufficient statistical power to
detect a target incremental revenue lift of 2.5%.

## Dataset

The dataset contains:

- Market-level information
- Daily revenue
- Orders
- Paid-social spend
- Platform-attributed revenue
- Revenue-feed completeness
- Audience overlap information
- Operations calendar

The raw data contains 16 states and 140 consecutive days after cleaning.

## Methodology

The analysis follows these major steps:

1. Data cleaning and validation
2. State-level revenue and spend analysis
3. Treatment eligibility screening
4. Structural-event identification
5. Candidate treatment combination generation
6. Synthetic-control model construction
7. Pre-test fit evaluation
8. Rolling-origin placebo simulation
9. MDE estimation
10. Power analysis
11. Candidate comparison
12. Risk and sensitivity analysis

## Synthetic Control

The treatment group's daily finance net revenue is modeled using a
weighted donor pool.

The model uses:

- Non-negative donor weights
- Ridge regularization
- A free intercept
- Finance net revenue as the primary outcome

GeoLift/GeoX were not directly run. The analysis uses an equivalent
weighted donor-pool implementation in Python.

## Selected Experimental Design

The selected treatment group is:

**Missouri + Ohio + Pennsylvania (MO + OH + PA)**

Key design characteristics:

| Metric | Value |
|---|---:|
| Revenue share | 16.0% |
| Additional spend | $274.1K |
| Spend cap | $300K |
| Pre-test NRMSE | 1.32% |
| Correlation | 0.983 |
| MDE | 0.84% |
| Modelled power at 2.5% lift | >99.9% |

## Expected Business Impact

At a hypothetical 2.5% incremental lift:

- Incremental revenue: $184.8K
- Incremental spend: $274.1K
- iROAS: 0.67
- Incremental orders: 1,848
- Cost per incremental order: $148.30

These are expected/target calculations rather than observed
post-treatment results.

## Repository Structure

```text
geo-experiment-design/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── Geo_Experiment_Analysis.ipynb
│
├── src/
│   ├── data_cleaning.py
│   ├── exploratory_analysis.py
│   ├── eligibility.py
│   ├── synthetic_control.py
│   ├── power_mde.py
│   └── visualization.py
│
├── results/
│   ├── figures/
│   └── tables/
│
├── report/
│   └── Geo_Experiment_Report.pdf
│
├── requirements.txt
├── .gitignore
└── README.md
