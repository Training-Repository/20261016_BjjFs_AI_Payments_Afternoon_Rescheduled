# Meta-Prompting Guide — Payments Operations
**Microsoft Copilot Training | Bajaj Finance Limited**

---

## What Is Meta-Prompting?

Instead of writing a prompt yourself, you ask Copilot to write the prompt for you. You tell it your role, your task and who will read the output.

In effect, you are saying:

> *"You are a prompt expert. You know how to talk to AI. Write me a prompt I can use for my actual work."*

The output becomes your **reference prompt**: something you refine once and reuse across Payments workflows, from exception handling to reconciliation, chargebacks, mandates and partner reviews.

---

## The Core Meta-Prompt Formula

```
Act as a Microsoft Copilot prompt expert.
I am a [YOUR ROLE] at [COMPANY/CONTEXT].
I need to [WHAT YOU WANT TO DO].
My audience is [WHO WILL READ THE OUTPUT].
Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

## Meta-Prompts for Payments Operations — Bajaj Finance

Use these as your starting point. Copy, paste and run them in Copilot, then use the output as your working prompt for the exercises.

---

### 1. Failed Transaction Exception Handling

```
Act as a Microsoft Copilot prompt expert.
I am a Payments Operations Executive at Bajaj Finance Limited, an NBFC. I handle exceptions
where a customer's account is debited but the expected credit, confirmation or reversal has
not happened — across UPI, e-NACH, card payment gateway, net banking, BBPS, wallet and EMI
refunds. Each channel has an allowed turnaround time (TAT), and beyond it the customer is
compensated ₹100 per day.

My audience is my Payments Ops team lead, who reviews TAT breaches and compensation daily.

Write me a detailed, structured Copilot prompt I can use to review my exception log and
produce a daily exception report. The prompt should specify: my role, the task, the input I
will provide, the output format (open cases by ageing, TAT breaches with compensation due,
repeat root causes by channel), and a factual, precise tone.
```

---

### 2. EMI Mandate Health Review

```
Act as a Microsoft Copilot prompt expert.
I am a Mandate Management Executive in Payments Operations at Bajaj Finance Limited. I
maintain the register of EMI mandates — physical NACH, e-NACH (net banking, debit card,
Aadhaar) and UPI AutoPay — with registration status, rejection reasons, presentations and
bounces. I need a weekly action list: which rejected mandates to re-initiate and through
which mode, which pending registrations to chase, which mandates need a service call
because of repeated bounces, and which revoked mandates must be stopped.

My audience is the mandate desk and the customer service team who make the service calls.

Write me a Copilot prompt I can use to produce this action list. The prompt should specify
how to group the mandates, what to flag, and the tone (clear, operational, non-collection —
these are service calls, not collection calls).
```

---

### 3. Payments Performance Reporting

```
Act as a Microsoft Copilot prompt expert.
I am a Payments MIS Analyst at Bajaj Finance Limited. I maintain a monthly dashboard for
April to September 2026 — transaction volume and value, overall, UPI and NACH success rates,
failed transactions, auto-reversal within TAT, refund TAT, chargebacks and win rate,
reconciliation breaks, unreconciled value, complaints and compensation paid. I need a
management summary: the trend, a comparison of the last three months, and recommended
actions for October.

My audience is the Head of Payments Operations and the leadership team in their monthly review.

Write me a structured Copilot prompt that will produce this summary from my dashboard. The
prompt should specify the format (executive narrative + comparison table + action
recommendations), the tone (professional, data-driven, management-ready), and the signals to
surface (every metric against its target, the September festive-season stress, compensation
paid as a cost of TAT breaches).
```

---

### 4. Reconciliation Break Analysis

```
Act as a Microsoft Copilot prompt expert.
I am a Reconciliation Lead in Payments Operations at Bajaj Finance Limited. Each cycle I
reconcile our ledger against the files from our payment partners — the UPI switch, the card
payment gateway, the NACH sponsor service, the BBPS unit and the net banking aggregator. I
track breaks, break value, aged breaks and root causes. I need to identify which partners
need escalation, which root causes are recurring, and what to fix at source.

My audience is the Head of Payments Operations and the Finance Controller.

Write me a Copilot prompt that will produce this reconciliation analysis. The prompt should
specify the format (partner-wise break table + escalations against the ₹10 lakh limit +
recurring root causes + fixes with owners), the tone (precise, finance-ready), and what to
compare (this cycle vs the previous cycle).
```

---

### 5. Chargeback and Partner SLA Review

```
Act as a Microsoft Copilot prompt expert.
I am a Cards & Payment Gateway Lead at Bajaj Finance Limited. I manage chargebacks and
network disputes across Visa, Mastercard, RuPay and UPI, and I review our payment partners'
SLAs — uptime, settlement adherence, incidents and RCAs — against our Payments Operations
Standard.

My audience is the Head of Payments Operations, who decides on escalations and partner reviews.

Write me a Copilot prompt I can use to produce a weekly review. The prompt should specify the
format (chargeback cases due in the next 7 days with evidence status + won/lost summary +
partner SLA scorecard + breaches against named clauses + actions), the tone (factual, firm,
audit-ready), and what to flag (cases at risk of missing the evidence deadline, partners due
for review before renewal).
```

---

### 6. Partner Escalation or Customer Communication

```
Act as a Microsoft Copilot prompt expert.
I am a Payments Operations Lead at Bajaj Finance Limited. I need to draft emails of two kinds:
(a) an escalation to a payment partner after an outage, asking for a root-cause analysis and
a fix by a stated date, and (b) a customer message explaining a delayed reversal or refund,
with the reference number, the new date and the compensation being credited.

My audience is either the partner's service manager or the customer.

Write me a Copilot prompt I can reuse for both. The prompt should specify the format
(subject + context + facts + ask + date + sign-off), the tone (firm and specific for partners;
clear, apologetic without over-explaining for customers), and the details to personalise.
```

---

## Still Not Right? Run This.

If the prompt Copilot wrote doesn't feel right (too generic, wrong format, wrong tone), don't rewrite it yourself. Use this follow-up instead:

```
The prompt you wrote is a good start, but I need you to adjust it.
Here is what I want to change:

- [What felt off — e.g., "the format doesn't match our daily exception report"]
- [What's missing — e.g., "it doesn't calculate compensation beyond the allowed TAT"]
- [The tone issue — e.g., "it is too long for a partner escalation"]

Please rewrite the prompt with these corrections.
Keep the same structure (Role / Task / Context / Format / Tone) but fix the parts I've described.
```

---

## What to Do With the Output

Once Copilot gives you a well-structured prompt:

1. **Read it.** Does it reflect your actual Payments role and channels?
2. **Replace the placeholders** with your real partner, channel, cycle or case details.
3. **Run it** on the exercise dataset provided in this session.
4. **Save it.** This is your reusable reference prompt for that task.

---

*Bajaj Finance Limited | AI Academy — Payments Operations | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
