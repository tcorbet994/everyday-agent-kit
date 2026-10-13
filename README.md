# Everyday Agent Kit

**Ready-to-run AI agent playbooks for everyday tasks.** You copy one in, fill in a few inputs, and the agent does the work. Use it with ChatGPT, Claude, Grok, Cursor, or any agent that takes a prompt.

Most people would hand an AI agent at least one chore, but few know how to set that up. This kit gives you tested, structured playbooks with **safety guardrails built in**. Every playbook stops and asks you before it buys, sends, cancels, or deletes anything.

## Playbooks (free)

| # | Playbook | What you get | Time |
|---|---|---|---|
| 1 | [Meal Planner + Grocery List](playbooks/01-meal-planner-grocery-list.md) | A 7-day meal plan and a grocery list grouped by store aisle | ~5 min |
| 2 | [Bill & Subscription Tracker](playbooks/02-bill-subscription-tracker.md) | A table of your recurring charges, due dates, and suggested cuts | ~10 min |
| 3 | [Inbox Triage](playbooks/03-inbox-triage.md) | Emails sorted into action buckets, with draft replies (nothing gets sent) | ~5 min |

## Quickstart (2 minutes)

1. Open a playbook in `playbooks/`.
2. Copy everything in the **Prompt** block.
3. Paste it into your agent:
   - **ChatGPT / Claude / Grok:** start a new chat and paste it. You can save it as a Project, Custom GPT, or custom instruction to reuse later.
   - **Cursor / Claude Code / coding agents:** put the file in your project and say: "Run the playbook in `playbooks/01-meal-planner-grocery-list.md`."
4. Fill in the `{{INPUTS}}` when the agent asks, or edit them into the prompt before pasting.
5. Check the output. The agent will wait for your **approval** before doing anything that can't be undone.

## Safety principles

- **Human approval gate.** The agent never purchases, sends, cancels, or deletes without your explicit "yes".
- **Least data.** Share only what the task needs. Mask account numbers.
- **You stay responsible.** Check the agent's work, especially money and dates. See the [LICENSE](LICENSE). This kit comes with no warranty.

## Want more?

- **Pro Pack ($19–29, one-time):** 10+ more playbooks (travel planning, reservations, research digests, home maintenance, and more), video walkthroughs, MCP connector configs, and free updates. → `[PRO_PACK_LINK]`
- **Done-for-you setup ($99–249):** we install and configure the kit on your own accounts for you. → `[SETUP_SERVICE_LINK]`

## Support the project

If the kit saves you time, please ⭐ star the repo and consider [GitHub Sponsors](`[GITHUB_SPONSORS_LINK]`). Sponsorships pay for new free playbooks.

## Contributing

PRs with new playbooks are welcome. Follow the same structure: **Inputs → Prompt → Steps → Example output → Guardrails**.

## License

Apache 2.0. See [LICENSE](LICENSE).
