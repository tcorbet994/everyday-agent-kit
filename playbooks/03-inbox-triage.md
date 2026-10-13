# Playbook 03: Inbox Triage

**Outcome:** your unread emails sorted into **Act now / Reply / Read later / Archive / Unsubscribe?**, with a one-line summary for each and draft replies ready to review. **Nothing gets sent.**
**Works with:** ChatGPT, Claude, Grok (paste emails in), or agents with email access (Cursor/Claude Code with an email MCP, Gmail connectors). **Time:** ~5 minutes.

## Inputs

| Input | Example |
|---|---|
| `{{EMAILS}}` | Paste up to ~30 emails (sender, subject, body), or let a connected agent read unread mail from the last 24h |
| `{{PRIORITIES}}` | Anything from my boss or my kid's school is urgent; invoices matter |
| `{{TONE}}` | Friendly and brief; sign off with "– Sam" |
| `{{VIPS}}` | boss@company.com, school.org |

## Prompt

```text
You are my inbox-triage agent. Help me get to inbox zero quickly and safely.

INPUTS
- Emails: {{EMAILS}}
- What matters to me: {{PRIORITIES}}
- VIP senders: {{VIPS}}
- Reply tone: {{TONE}}

STEPS
1. Put each email in exactly ONE bucket:
   🔴 Act now (deadline within 48h, or a VIP needs something)
   🟡 Reply (needs a response, but not urgent)
   🔵 Read later (newsletters or info worth reading)
   ⚪ Archive (receipts, notifications, FYI)
   🗑️ Unsubscribe? (bulk mail I never engage with)
2. For each email: the sender, the subject, a 1-line summary, any deadline, and the bucket.
3. For 🔴 and 🟡 emails, write a short draft reply in my tone. Mark it clearly as DRAFT.
4. List any action items, with due dates, as a checklist.
5. Be on the lookout for phishing. Flag urgent payment requests, mismatched sender domains, and requests for credentials with ⚠️ POSSIBLE PHISHING. Never draft a compliant reply to these.

RULES
- NEVER send, delete, archive, unsubscribe, or click links on my behalf without my explicit approval for each item.
- If you have mailbox access, only read and label. Save drafts as drafts.
- Do not include full sensitive data (passwords, account numbers) in summaries.
```

## Steps (what the agent does)
1. Reads and sorts each email into one bucket.
2. Summarizes each email and pulls out deadlines.
3. Drafts replies for the emails that need them.
4. Builds an action checklist.
5. Flags suspected phishing.

## Example output (abridged)

**🔴 Act now (2)**
- **boss@company.com** – "Q4 deck": needs slides by Thu 10/15 at 9am.
  > DRAFT: "Hi Jordan, on it. You'll have the deck by Wednesday evening. – Sam"
- **Lincoln Elementary** – "Permission slip": due Fri 10/16.

**🟡 Reply (1)** · **🔵 Read later (4)** · **⚪ Archive (9)** · **🗑️ Unsubscribe? (3):** DealBlast, PromoHub, …

⚠️ **POSSIBLE PHISHING:** "PayPaI Security" (sender domain paypai-support.co) asks you to "verify your account". Do not click the link.

**Action items**
- [ ] Q4 deck → Wed 10/14
- [ ] Sign the permission slip → Fri 10/16

## Guardrails
- Drafts only. You approve every send.
- No deletions, unsubscribes, or link clicks without your approval.
