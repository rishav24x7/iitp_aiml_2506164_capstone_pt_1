# Part 1 — Data Audit, EDA & Business Understanding

**D2C Customer Churn Intelligence & Retention** · Capstone Part 1 of 4

This repository audits the raw D2C personal-care datasets, performs exploratory analysis, and derives
evidence-backed churn-risk hypotheses **before any model is built**. Every analytical claim is supported by
a chart or a churn-rate table computed from the actual data.

## Business context

A direct-to-consumer personal-care brand wants to reduce customer churn **without** blanket discounting.
Before designing retention campaigns, the company needs to understand its data, find quality issues, and
identify which behaviours actually precede churn. The target is `churn_next_60d` — whether a customer makes
**no purchase** in the 60 days after the snapshot date `2025-09-30`.

## Repository structure

```
d2c-churn-part1-eda/
├── eda_audit.ipynb          # Main notebook (run top-to-bottom, outputs included)
├── data_quality_report.md   # Generated: issues + recommended treatments
├── business_memo.md         # Generated: what to investigate before any campaign
├── charts/                  # 7 saved charts (also rendered inline in the notebook)
├── data/                    # The 7 source CSVs + DATA_DICTIONARY.md (committed for reproducibility)
├── requirements.txt
└── README.md
```

## Setup & run

```bash
python -m venv .venv && source .venv/bin/activate     # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook eda_audit.ipynb        # run all cells, OR execute headless:
jupyter nbconvert --to notebook --execute --inplace eda_audit.ipynb
```

The notebook reads from the relative `data/` folder, so it runs anywhere with no path changes. Running it
regenerates `data_quality_report.md`, `business_memo.md`, and every PNG in `charts/`.

## What the notebook covers

1. **Load & schema** — all 7 files; row counts verified against the data dictionary.
2. **Join integrity** — all `customer_id` foreign keys validated; left-join-from-customers confirmed.
3. **Data-quality audit** — duplicate-like `_DUP` orders, missing values, `gross_amount` outliers, date
   consistency, and **leakage** (post-snapshot orders), each with a recommended treatment.
4. **EDA** — demographics, churn balance, order/monetary/return behaviour, support tickets, web activity,
   and a correlation scan.
5. **Churn-risk hypotheses (5+)** — each backed by a churn-rate-by-bucket table and interpretation.

## Key findings

- **Churn is a disengagement problem.** `recency_days` (corr +0.56) and `last_visit_days_ago` (+0.53) are the
  strongest signals: churn rises from ~12-16% for recently-active customers to ~88-91% for the long-inactive.
- **Support contact is not a risk signal — negative sentiment is.** Customers with tickets churn *less* (33%
  vs 51%); within ticket-holders, mostly-negative sentiment churns at 38.5% vs 23.7%.
- **Frequency & breadth protect.** 0 orders in 180d → 91% churn; 5+ orders → 15%.
- **6 intentional data-quality defects** confirmed and given concrete treatments; leakage columns flagged.

See `business_memo.md` for the prioritized "investigate before you spend" recommendations.
