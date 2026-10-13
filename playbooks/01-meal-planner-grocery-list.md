# Playbook 01: Meal Planner + Grocery List

**Outcome:** a 7-day meal plan that fits your diet, budget, and schedule, plus one grocery list grouped by aisle that subtracts what you already have.
**Works with:** ChatGPT, Claude, Grok, Cursor, or any chat or coding agent. **Time:** ~5 minutes.

## Inputs

| Input | Example |
|---|---|
| `{{PEOPLE}}` | 2 adults, 1 child (age 8) |
| `{{DIET}}` | No pork; one adult is vegetarian |
| `{{BUDGET}}` | $120/week |
| `{{SCHEDULE}}` | Weeknights: under 30 min. Sunday: can batch-cook |
| `{{PANTRY}}` | Rice, pasta, canned tomatoes, eggs, frozen peas |
| `{{MEALS}}` | Dinners only (or breakfast/lunch/dinner) |
| `{{STORE}}` | Optional: preferred store, e.g. Aldi |

## Prompt

```text
You are my meal-planning agent. Use the inputs below to build a practical week of meals.

INPUTS
- People: {{PEOPLE}}
- Diet/allergies: {{DIET}}
- Weekly budget: {{BUDGET}}
- Schedule constraints: {{SCHEDULE}}
- Already in pantry: {{PANTRY}}
- Meals to plan: {{MEALS}}
- Store: {{STORE}}

STEPS
1. If any input is missing or unclear, ask me up to 3 short questions first. Then continue.
2. Plan 7 days. Reuse ingredients across meals to cut waste and cost. Include at least 2 leftover or batch-cook nights.
3. For each meal, give: the name, prep+cook time, a 1-line method, and which diet needs it meets.
4. Build ONE grocery list. Combine quantities, leave out pantry items, and group by aisle (Produce, Meat/Protein, Dairy, Grains/Bakery, Canned/Dry, Frozen, Other).
5. Estimate the cost for each aisle and in total, using typical US prices. Mark these clearly as estimates. If the total is over budget, suggest 2 swaps.
6. End with a "Prep ahead" list for Sunday.

RULES
- Never place an order or add items to any cart without my explicit approval.
- Flag any allergen conflict loudly.
- Output in Markdown tables. Be concise.
```

## Steps (what the agent does)
1. Asks clarifying questions, but only if needed.
2. Drafts a 7-day plan that shares ingredients across meals.
3. Combines everything into one grocery list grouped by aisle.
4. Estimates cost and suggests swaps if the plan is over budget.
5. Gives you a prep-ahead checklist.

## Example output (abridged)

| Day | Dinner | Time | Notes |
|---|---|---|---|
| Mon | Veggie fried rice with eggs | 20 min | Vegetarian; uses pantry rice + peas |
| Tue | Sheet-pan chicken & roasted veg (tofu tray for veg adult) | 30 min | Make 2× veg for Wed |
| Wed | Pasta with tomato sauce + leftover roasted veg | 15 min | Leftover night |
| … | … | … | … |

**Grocery list**
- **Produce:** onions (3), bell peppers (4), broccoli (2 heads), lemons (2) ≈ $11
- **Protein:** chicken thighs (2 lb), extra-firm tofu (2 blocks) ≈ $14
- **Dairy:** shredded mozzarella (8 oz), Greek yogurt (32 oz) ≈ $8
- …
**Estimated total: ~$104 (under the $120 budget)**

**Prep ahead (Sun):** cook 4 cups rice · chop onions/peppers · marinate chicken.

## Guardrails
- No purchases or cart changes without your "yes".
- Prices are estimates. Check them at your store.

## Upgrade ideas (Pro Pack)
Connect to a grocery cart through an MCP or browser agent, so the agent can fill your cart for you to approve.
