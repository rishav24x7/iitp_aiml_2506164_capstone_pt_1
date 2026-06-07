# Before We Spend Anything on Retention — A Quick Read of the Data

**To:** Growth & CRM leadership  **From:** Data team  **Re:** Where to look first (Part 1)

## The short version
About **47%** of customers are on track to churn in the next 60 days. At that
scale, handing everyone a discount would cost a fortune and mostly pay people who weren't going to leave. And
when I look at *what* separates churners from the rest, it's almost always disengagement — people drifting
away — not price. So before we fund a single campaign, here's what I'd dig into.

## 1. Watch activity, not price (this is the big one)
Nothing predicts churn as cleanly as how recently someone showed up. Churn climbs from roughly 12-16% for
customers who visited or ordered in the last few weeks to 88-91% for those who've gone quiet for a month or
more. A simple "haven't seen you in 15-30 days" trigger would catch people while we can still win them back —
far earlier and cheaper than any blanket offer.

## 2. A complaint is not the same as a goodbye
This one surprised me. Customers who open a support ticket actually churn *less* (33%) than those who never
contact us at all (51%) — reaching out is a sign they still care. The people to worry about are the ones whose
tickets skew negative: their churn jumps to 38.5% versus 23.7% for everyone else with tickets. So the queue
worth reviewing is the negative-sentiment one, not "anyone who complained".

## 3. Get people to a second and third purchase
One-and-done buyers (a single order in 180 days) churn at 53%, while customers with 3+ orders or 3+ categories
sit under 20%. Repeat buying and trying new categories build a habit that's hard to walk away from. I'd look
at which second-purchase journeys actually convert and lean into those.

## 4. Be careful reading discounts
At first glance the heaviest "0-10% discount" group churns at 80% — but that's misleading: those are mostly
barely-active customers, so it's their inactivity talking, not the discount. The group actually worth a closer
look is customers who are still active *and* lean on heavy discounts (30%+), because that's where we're
quietly eroding margin.

## 5. We may already have a useful list
The CRM team's own `manual_priority_bucket = high` already churns at 75%, versus 10% for `low`. That's a
strong, free signal. I'd confirm how it's kept up to date and treat it as the bar any model or campaign has to
beat before we call it an improvement.

## A few things I'd avoid
- A blanket discount — it rewards customers who'd have stayed and teaches everyone to wait for a deal.
- Treating "raised a ticket" as a churn flag — the data says it's the opposite.
- Letting any post-snapshot order data or the churn label sneak into scoring — that's leakage.
