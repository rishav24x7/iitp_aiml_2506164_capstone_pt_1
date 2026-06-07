# Part 1 — Data Audit, EDA & Business Understanding

**D2C Customer Churn Intelligence & Retention** · Capstone Part 1 of 4

This is the first step of the project: get to know the raw D2C personal-care data, clean up what's broken, and
work out which behaviours actually go hand-in-hand with churn — all *before* building any model. I've tried to
back every claim here with a chart or a churn-rate table straight from the data rather than hand-waving.

## The problem I'm working on

A direct-to-consumer personal-care brand wants to cut churn **without** just discounting everyone. Before
anyone designs a campaign, it's worth understanding the data, catching its quality issues, and figuring out
what tends to come before a customer leaves. The thing we're predicting is `churn_next_60d` — whether a
customer makes **no purchase** in the 60 days after the snapshot date, `2025-09-30`.

## Repository structure

```
iitp_aiml_2506164_capstone_pt_1/
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

## What I found

- **Churn is mostly about disengagement.** The clearest signals by far are how recently someone ordered
  (`recency_days`, correlation +0.56) and how recently they visited (`last_visit_days_ago`, +0.53) — churn
  runs ~12-16% for recently-active customers and climbs to ~88-91% for those who've gone quiet.
- **A complaint isn't a red flag — a *negative* complaint is.** Customers who raise tickets actually churn
  less (33% vs 51%); the danger is in mostly-negative tickets (38.5% vs 23.7%).
- **Buying often, and across categories, keeps people around.** Zero orders in 180 days → 91% churn; five or
  more → about 15%.
- **The six built-in data-quality issues** all check out, and I've noted how I'd handle each — plus flagged the
  columns that would leak the future into a model.

The prioritized "look here before you spend" version of all this is in `business_memo.md`.
