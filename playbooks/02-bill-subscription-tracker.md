# Playbook 02: Bill & Subscription Tracker

**Outcome:** one clean table of every recurring charge, with due dates, a monthly and annual total, a list of possible cuts, and reminder text you can paste into your calendar.
**Works with:** ChatGPT, Claude, Grok, Cursor (Cursor and coding agents can also write the table to a CSV). **Time:** ~10 minutes.

## Inputs

| Input | Example |
|---|---|
| `{{TRANSACTIONS}}` | 1–3 months of bank or card transactions, pasted or uploaded as CSV. **Mask account numbers.** |
| `{{KNOWN_BILLS}}` | Rent $1,400 on the 1st; car insurance $96 on the 15th |
| `{{GOAL}}` | Cut $50/month; never miss a due date |
| `{{CURRENCY}}` | USD |

## Prompt

```text
You are my bills-and-subscriptions agent. Find every recurring charge and help me control it.

INPUTS
- Transactions: {{TRANSACTIONS}}
- Bills I already know about: {{KNOWN_BILLS}}
- My goal: {{GOAL}}
- Currency: {{CURRENCY}}

STEPS
1. Find recurring charges: the same merchant at a similar amount, about weekly, monthly, or yearly. Add my known bills to the list.
2. For each one, record: the merchant, a category (housing, utilities, insurance, streaming, software, fitness, other), the amount, how often it repeats, the next expected date, and a confidence level (high/med/low).
3. Calculate the monthly and annual totals for each category and overall.
4. Flag: duplicate services (e.g. 2 music apps), price increases between months, free trials that turned into paid plans, and charges I may have forgotten.
5. Suggest cuts that reach my goal. Rank them by savings, and for each give the effort ("cancel online", "call needed", "downgrade plan").
6. Write a reminder list: one line for each bill, due 3 days before the due date, in this format: "YYYY-MM-DD – Pay <merchant> <amount>".
7. Offer the full table as CSV.

RULES
- Never cancel, change, or pay anything. Never log in to any account. Only recommend; I decide and act.
- If I pasted a full account or card number, tell me to remove it, and do not repeat it.
- Mark uncertain matches as such. Do not guess.
```

## Steps (what the agent does)
1. Finds recurring charges by merchant name and how often they repeat.
2. Sorts them into categories and estimates the next due dates.
3. Totals spending by month and year.
4. Flags duplicates, price increases, and forgotten trials.
5. Ranks possible savings and writes the reminder lines.

## Example output (abridged)

| Merchant | Category | Amount | Cycle | Next date | Confidence |
|---|---|---|---|---|---|
| Rent | Housing | $1,400.00 | Monthly | 2026-11-01 | High |
| StreamFlix | Streaming | $17.99 | Monthly | 2026-10-21 | High |
| TuneBox | Streaming | $10.99 | Monthly | 2026-10-25 | High |
| SongCloud | Streaming | $11.99 | Monthly | 2026-10-28 | High |
| FitApp Pro | Fitness | $59.99 | Yearly | 2027-01-04 | Med |

**Totals:** $1,629/month · $19,548/year
**Flags:** ⚠️ 2 music services (TuneBox + SongCloud) · ⚠️ StreamFlix went up from $15.49 to $17.99 in September
**Suggested cuts:** cancel SongCloud (-$11.99, cancel online) · move StreamFlix to the ad tier (-$10.00) · … **→ saves -$52/month, which meets the goal**
**Reminders:** `2026-10-18 – Pay StreamFlix $17.99` …

## Guardrails
- Recommends only. It never cancels, pays, or logs in.
- Remove sensitive numbers before you paste.
- Not financial advice.
