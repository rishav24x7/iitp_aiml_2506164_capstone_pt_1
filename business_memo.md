# Business Memo — Before You Launch a Retention Campaign

**To:** Growth & CRM leadership  **From:** Data team  **Re:** What to investigate first (Part 1 findings)

## Bottom line
Churn in the next 60 days is **47%** of the base — high enough that blanket
discounting would be ruinously expensive. The data shows churn is overwhelmingly a **disengagement**
problem, not a pricing problem. Five things to investigate **before** spending a rupee on retention:

## 1. Re-engage on activity signals, not discounts (highest priority)
Days since last visit and order recency are by far the strongest churn predictors (churn rises from
~12-16% for recently-active customers to ~88-91% for the long-inactive). A lapsing-customer trigger
(no visit in 15-30 days) will reach real risk earlier and cheaper than any broad discount.

## 2. Separate "silent" customers from "unhappy" customers
Customers who contact support churn *less* (33%) than those who never do (51%) — a ticket is a sign of
engagement. The real risk is **negative sentiment** among ticket-holders (38.5% churn vs 23.7%).
Investigate the open/negative-sentiment ticket queue before assuming all complainers are leaving.

## 3. Protect frequency and category breadth
One-and-done buyers (1 order in 180d) churn at 53%; customers with 3+ orders or 3+ categories churn under
20%. Cross-sell and replenishment nudges build the habit that prevents churn — investigate which
second-purchase journeys convert.

## 4. Audit discount dependence jointly with activity
The 0-10%-discount group churns at 80%, but only because those are barely-active customers — discount level
alone is misleading. Investigate customers who are *active AND* highly discount-reliant (30%+) as a margin risk.

## 5. Validate the existing manual priority list
The CRM team's `manual_priority_bucket = high` already churns at 75% vs 10% for `low`. It is a strong, free
baseline — confirm how it is maintained and use it as the bar any model or campaign must beat.

## Do NOT
- Launch a blanket discount: it pays customers who would have stayed and trains discount-seeking behaviour.
- Treat "raised a support ticket" as a churn signal — it is the opposite.
- Use post-snapshot order data or the churn label when scoring customers (leakage).
