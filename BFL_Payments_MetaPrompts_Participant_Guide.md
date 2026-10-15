# BFL Payments Operations — M365 Copilot Participant Guide
### Meta Prompts for Exception Handling, Mandate Health, Payments Reporting, Reconciliation, Chargebacks & Partner SLAs

**Programme:** Microsoft Copilot for Payments Operations (Non Sales)
**Organisation:** Bajaj Finance Limited
**Interface:** M365 Copilot Chat (m365.cloud.microsoft/chat or Teams)
**Dataset:** `BFL_Payments_Copilot_Dataset.xlsx` — data as of 30 Sep 2026 (synthetic)

---

## How Each Exercise Works — The 3-Step Rhythm

| Step | What You Do | What It Shows |
|------|-------------|----------------|
| **Step 1 — Meta Prompt** | Fill in the template and paste it into Copilot Chat | Copilot generates a tailored, role-specific working prompt |
| **Step 2 — Generated Prompt** | Review the prompt Copilot created | How your context shaped the output |
| **Step 3 — Live Apply** | Attach the file(s) using `/` and run the generated prompt | Copilot produces a real Payments insight or summary |

> 💡 BFL's Copilot allows **up to 3 file attachments per prompt**. Every exercise below stays within that limit. To work across more files at once, see `Copilot_Notebooks_Guide.md`.

---

## The Meta Prompt Template (used in every stage)

```
Act as a Microsoft Copilot prompt expert.

I am a [YOUR ROLE] at [COMPANY/CONTEXT].
I need to [WHAT YOU WANT TO DO].
My audience is [WHO WILL READ THE OUTPUT].

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

## RTCFT Quick Reference

| Element | What It Means | Example (Payments Context) |
|---------|---------------|-------------------------------|
| **R** — Role | Who are you? | "You are a Payments Operations executive at Bajaj Finance Limited" |
| **T** — Task | What do you need? | "List every exception past its allowed TAT, with compensation due" |
| **C** — Context | What is the situation? | "UPI reversals are due in T+1; card gateway reversals in T+5; ₹100 per day beyond TAT" |
| **F** — Format | How should it look? | "Table: Exception ID, Channel, TAT Days, Allowed, Days Over, Compensation" |
| **T** — Tone | What register? | "Factual, precise, ready for the team lead" |

---

## Your Files at a Glance

`BFL_Payments_Copilot_Dataset.xlsx` has six sheets. In every sheet the title is in row 1, the sub-title (period, targets) is in row 2, headers are in row 4 and data starts in row 5.

| Sheet | What it holds |
|---|---|
| Exception Log | 20 failed or disputed transactions logged 1–29 Sep 2026, with allowed TAT, TAT days, status and root cause |
| Mandate Register | 20 EMI mandates with mode, registration status, rejection reason and Jul–Sep bounces |
| Payments Performance | Monthly KPIs, Apr–Sep 2026, with targets in the sub-title row |
| Reconciliation Tracker | Partner-wise breaks for the 15 Sep and 30 Sep 2026 cycles |
| Chargeback Register | 12 chargeback cases (Visa, Mastercard, RuPay, UPI) with due dates and evidence status |
| Partner SLA Tracker | 5 payment partners (fictional names): uptime, settlement adherence, incidents, RCA status |

`Payments_Operations_Standard.pdf` is the rulebook for Stage 5. It is a **training sample**, not BFL policy or RBI text.

---

## Stage 1 — Failed Transaction Exception Handling

**Use case:** A daily view of exceptions, TAT breaches and compensation due.
**Sheet to use:** `Exception Log`

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Payments Operations Executive at Bajaj Finance Limited.
I need to review failed and disputed transactions — UPI, e-NACH, card gateway,
net banking, BBPS, wallet and EMI refunds — and report open cases, TAT breaches
and the compensation due to customers.
My audience is my Payments Ops team lead.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

*(Typical output. Yours will be worded differently.)*

```
You are a Payments Operations Executive at Bajaj Finance Limited preparing
the daily exception report.

Task: Review the exception log and report open cases, TAT breaches and
compensation due.

Context: Each exception has an allowed TAT in days. TAT Days is counted from
the Reported Date to the Resolved Date, or to the report date if still open.
Beyond the allowed TAT, the customer is due ₹100 per day of delay.

Output format:
1. Open cases, oldest first: ID, customer, channel, amount, TAT days
2. TAT breaches: ID, channel, TAT days, allowed, days over, compensation (₹)
3. Total compensation due
4. Root causes that repeat within a channel, with a suggested fix at source

Constraints: Use only the data provided. Do not estimate missing dates.
Tone: Factual, precise, ready for the team lead.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our Payments dataset. Use only the "Exception Log" sheet,
as of 30 Sep 2026.

Run the report as described above. Then answer:
- Which channel breached TAT on every one of its exceptions?
- What do its root causes have in common?
```

**What a good answer contains:**
- **Open cases (6), oldest first:**
  - Kunal Shah (EMI refund, 28 days)
  - Meera Iyer (Card PG, 11 days)
  - Varun Kapoor (e-NACH, 8 days)
  - Sneha Gokhale (UPI, 5 days)
  - Pallavi Chavan (e-NACH, 4 days)
  - Amol Patwardhan (UPI, 1 day, still within TAT)
- **TAT breaches:** 11 of 20, with total compensation due of **₹6,100**. The largest is Kunal Shah: 21 days over, ₹2,100.
- **Pattern:** **e-NACH** breached on all 4 of its exceptions. The root causes are mandate-file hygiene:
  - Revocations not applied (Ishita Rane, Varun Kapoor).
  - Files presented twice (Divya Menon, Pallavi Chavan).
  - The fix is at source, in the mandate file process, not case by case.

---

## Stage 2 — EMI Mandate Health Review

**Use case:** A weekly action list for the mandate desk.
**Sheet to use:** `Mandate Register` (and `Exception Log` for the cross-check)

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Mandate Management Executive in Payments Operations at Bajaj Finance Limited.
I need a weekly action list from our EMI mandate register — rejected mandates
to re-initiate, pending registrations to chase, mandates with repeated bounces
that need a service call, and revoked mandates to stop.
My audience is the mandate desk and customer service.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a Mandate Management Executive at Bajaj Finance Limited.

Task: Produce the weekly mandate action list.

Context: Modes are physical NACH, e-NACH (net banking, debit card, Aadhaar)
and UPI AutoPay. Rejected mandates should be re-initiated within 7 days,
preferably through a digital mode. A mandate with 2 or more bounces in 3
presentations needs a service call. No presentation may be made on a revoked
mandate.

Output format:
1. Rejected — customer, mode, reason, recommended re-initiation mode
2. Pending — customer, mode, next step
3. Service calls — customer, bounces / presentations, bounce rate
4. Revoked — customer, action
5. One line on which mode is causing most rejections

Tone: Clear and operational. These are service calls, not collection calls.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our Payments dataset. Use the "Mandate Register" sheet.

Produce the action list as described. Then check the "Exception Log" sheet:
is any customer with a revoked mandate also in the exception log? What does
that tell us?
```

**What a good answer contains:**
- **Rejected (5):**
  - 4 are **physical NACH**: Sneha Gokhale and Fatima Sheikh (signature mismatch), Prakash Jadhav (account closed), Yash Thakur (invalid account details).
  - 1 is UPI AutoPay: Sameer Khan (customer did not authorise).
  - Recommended route for the physical-NACH rejections: e-NACH or UPI AutoPay.
- **Pending (2):** Divya Menon (e-NACH Aadhaar) and Amol Patwardhan (physical NACH).
- **Service calls (4):** Kunal Shah (3 of 3 bounced), Ishita Rane, Nisha Agarwal and Meera Iyer (2 of 3 each).
- **Revoked:** Varun Kapoor. He **also** appears in the Exception Log with "Debit after mandate revoked" (open, 8 days). The revocation was received after the file cut-off and not removed from the next file.

---

## Stage 3 — Payments Performance Reporting

**Use case:** The monthly summary for the Head of Payments Operations.
**Sheet to use:** `Payments Performance`

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Payments MIS Analyst at Bajaj Finance Limited.
I need to prepare a monthly performance summary for April–September 2026 —
volumes, success rates, failed transactions, auto-reversal within TAT,
chargebacks, reconciliation and complaints — with October actions.
My audience is the Head of Payments Operations.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a Payments MIS Analyst at Bajaj Finance Limited preparing the monthly
management review.

Task: Analyse six months of Payments performance and write a management summary.

Context: Data covers April–September 2026. Targets: overall success rate 98.5%,
auto-reversal within TAT 98%, chargeback win rate 65%, complaints no more than
150 a month.

Output format:
1. Executive summary (200–250 words)
2. Comparison table for Jul / Aug / Sep on every metric, with the target alongside
3. Three key observations
4. Two recommended actions for October 2026

Tone: Professional, data-driven, ready for leadership.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our Payments dataset. Use the "Payments Performance" sheet.

Generate the full summary as described. Also:
- Name every metric that missed its target in September, with the target.
- Volume grew sharply in September. By how much versus August, and did the
  operation keep pace?
- Express compensation paid as a cost: how many times August's figure is it?
```

**What a good answer contains:**
- **Volume:** 188.7 lakh transactions in September, **+15.5%** on August (163.4 lakh), likely festive-season load. The operation did not keep pace.
- **Missed targets in September:**
  - Overall success rate: **98.1%** against 98.5%.
  - Auto-reversal within TAT: **94.6%** against 98%.
  - Chargeback win rate: **58%** against 65%.
  - Complaints: **214** against the limit of 150.
- **Other September stress points:**
  - UPI success fell from 99.3% to 98.4%, and NACH from 89.2% to 86.4%.
  - Failed transactions rose from 2,260 to 3,980.
  - Average refund TAT rose from 2.9 to 4.1 days.
  - Reconciliation breaks rose from 441 to 1,011, and unreconciled value at month-end from ₹6.9 lakh to ₹26.8 lakh.
- **Compensation:** ₹92,600 against ₹30,200 in August, about **3×**. This is the direct cost of the TAT misses.

---

## Stage 4 — Reconciliation Break Analysis

**Use case:** Which partners to escalate, and which root causes to fix at source.
**Sheet to use:** `Reconciliation Tracker`

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Reconciliation Lead in Payments Operations at Bajaj Finance Limited.
I need to analyse partner reconciliation breaks for the 15 Sep and 30 Sep 2026
cycles, decide what to escalate, and identify recurring root causes to fix.
My audience is the Head of Payments Operations and the Finance Controller.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a Reconciliation Lead at Bajaj Finance Limited.

Task: Analyse partner-wise reconciliation breaks and recommend escalations and fixes.

Context: Breaks = ledger transactions − matched transactions. Breaks older than
3 days must be reported daily. Unreconciled value above ₹10 lakh for one partner
in one cycle is escalated to the Finance Controller the same day.

Output format:
1. Table for the 30 Sep cycle: partner, breaks, value (₹ lakh), aged > 3 days,
   change vs 15 Sep
2. Partners above the ₹10 lakh limit
3. Root causes that appear in both cycles, with a fix at source and an owner
4. A 100-word note for the Finance Controller

Tone: Precise and finance-ready.
```

---

### Step 3 — Live Apply (attach the dataset via `/`)

```
I am attaching our Payments dataset. Use the "Reconciliation Tracker" sheet.

Run the analysis as described. Also total the breaks, value and aged breaks
for the 30 Sep cycle.
```

**What a good answer contains:**
- **30 Sep totals:** 804 breaks, **₹26.8 lakh**, 150 aged more than 3 days.
- **Above the limit:** **NovaPay UPI Switch**, with 582 breaks worth ₹14.6 lakh (96 aged), up from 70 breaks and ₹1.8 lakh on 15 Sep. The cause was the switch outage on 27–28 Sep and a late settlement file, so this needs escalation the same day.
- **Recurring:** **Sahyog Payment Gateway** shows "Refunds missing from settlement file" in both cycles, rising from ₹6.4 lakh to ₹9.8 lakh. It is just under the limit, but it is a process gap to fix with the gateway.
- **The other three partners** are below ₹1.5 lakh each.

---

## Stage 5 — Chargeback and Partner SLA Review

**Use case:** A weekly review against the Payments Operations Standard.
**Files to attach:** `BFL_Payments_Copilot_Dataset.xlsx` + `Payments_Operations_Standard.pdf` (2 attachments)

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Cards & Payment Gateway Lead at Bajaj Finance Limited.
I need a weekly review of chargeback cases due soon and of our payment partners'
SLAs, checked against our Payments Operations Standard.
My audience is the Head of Payments Operations.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, constraints, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are the Cards & Payment Gateway Lead at Bajaj Finance Limited.

Task: Review chargebacks and partner SLAs as of 30 Sep 2026 against the
Payments Operations Standard, and recommend actions.

Context: The Chargeback Register gives due dates and evidence status; the
Partner SLA Tracker gives uptime, settlement adherence, incidents and RCA status.
Relevant clauses: 5.1 and 5.2 (chargeback evidence deadlines), 5.3 (win-rate
review), 7.1 (SLA targets), 7.2 (outage reporting and RCA), 7.3 (partner review).

Output format:
1. Pending chargebacks due within 7 days: case, network, amount, days to due,
   evidence status, required action (quote the clause)
2. Won / lost summary and win rate on decided cases
3. Partner scorecard: uptime, settlement adherence, incidents, RCA, status
4. Breach table: partner | clause | what the data shows | action
5. The single most urgent item for this week

Tone: Factual, firm, audit-ready. Use only the two files.
```

---

### Step 3 — Live Apply (attach both files via `/`)

```
I am attaching our Payments dataset and the Payments Operations Standard.
Use the "Chargeback Register" and "Partner SLA Tracker" sheets, as of 30 Sep 2026.

Produce the review as described.
```

**What a good answer contains:**
- **Chargebacks due within 3 days:**
  - **CB-7719** (Mastercard, ₹24,499): due in 1 day, evidence partial. It has already missed the 2-day submission point in clause 5.1, so escalate now under 5.2.
  - **CB-7715** (RuPay, ₹18,999): due in 2 days, evidence complete. Submit today, as clause 5.1 requires.
  - **CB-7726** (UPI, ₹2,000): due in 3 days, evidence not started. Escalate under clause 5.2.
- **Chargebacks due within 4–7 days:** CB-7712 (₹42,999, partial evidence) and CB-7747 (complete).
- **Outcomes:** 3 won and 2 lost on decided cases, a **60%** win rate, below the 65% in clause 5.3.
- **Partners:**
  - **NovaPay UPI Switch:** uptime 99.62% (clause 7.1). A 74-minute outage with **no RCA received** (clause 7.2). 2 breaches in the quarter, so a partner review is needed (clause 7.3).
  - **Sahyog Payment Gateway:** settlement adherence 97.8% (clause 7.1). 2 breaches in the quarter, so a review is due **before its 31 Dec 2026 renewal**.
  - **NetSettle Aggregator:** uptime 99.85%, 1 breach in the quarter.
- **ClearMandate:** its 86.4% success rate reflects customer-side NACH bounces, not a partner failure. Its SLA is met.

---

## Stage 6 — Bonus: Partner Escalation Email in Outlook

**Use case:** A firm, specific escalation to a partner after an outage.
**No file needed. Use Outlook → Draft with Copilot.**

---

### Step 1 — Fill in the Template

```
Act as a Microsoft Copilot prompt expert.

I am a Payments Operations Lead at Bajaj Finance Limited.
I need to draft an escalation email to a payment partner after an outage that
breached our SLA, asking for a root-cause analysis and a fix by a stated date.
My audience is the partner's service delivery manager.

Write me a detailed, structured Copilot prompt I can use to complete this task.
The prompt should specify: role, task, context, output format, and tone.
```

---

### Step 2 — Copilot Generates Your Working Prompt

```
You are a Payments Operations Lead at Bajaj Finance Limited writing to a
payment partner after an SLA breach.

Task: Draft an escalation email requesting an RCA and a corrective action plan.

Context: The outage exceeded the agreed reporting threshold, the RCA is overdue,
and the outage caused reconciliation breaks and customer reversal delays.

Output format:
- Subject line with the incident date
- Context: what happened, when, how long
- Impact: the facts, with numbers
- Ask: RCA and corrective plan by [date]; a review call
- Next step if unresolved: formal partner review under the contract
- Sign-off: Payments Operations, Bajaj Finance Limited

Tone: Firm, specific and professional. No emotional language.
```

---

### Step 3 — Live Apply (in Outlook → Draft with Copilot)

```
Draft an escalation email to the service delivery manager at NovaPay UPI Switch.

Facts: a 74-minute outage on 27–28 Sep 2026; September uptime 99.62% against
our 99.9% SLA; no RCA received yet (due within 3 working days); the 30 Sep
reconciliation cycle shows 582 breaks worth ₹14.6 lakh; this is the second SLA
breach this quarter.

Ask for the RCA and a corrective action plan by 6 October 2026 and a review
call that week. State that a second breach in the quarter triggers a formal
partner review.

Use the format and tone above. Include a subject line.
```

> ⚠️ Check every number in the draft against the tracker before sending. Copilot should not add figures you did not give it.

---

## All Exercises at a Glance

| Stage | Use Case | Sheet / Tool | Output |
|-------|----------|--------------|--------|
| 1 | Exception handling | Exception Log | Open cases, TAT breaches, compensation, root-cause pattern |
| 2 | Mandate health | Mandate Register (+ Exception Log) | Weekly mandate action list |
| 3 | Payments reporting | Payments Performance | Management summary |
| 4 | Reconciliation | Reconciliation Tracker | Escalations and fixes at source |
| 5 | Chargebacks & partner SLAs | Chargeback Register + Partner SLA Tracker + Standard PDF | Weekly review with clause references |
| 6 *(Bonus)* | Partner escalation | Outlook — no file | Escalation email |

---

## ⚠️ Data Handling

The dataset is **synthetic**, so it is safe to attach. Live payments data is not. On real data:

- Use Copilot signed in with your **BFL work account** (look for the enterprise data protection indicator).
- Never paste card numbers, full account numbers, UPI IDs, UTR/RRN references tied to named customers, or PAN into any tool outside BFL's approved Copilot.
- Attach only the sheets and columns the question needs.

---

*Bajaj Finance Limited | AI Academy — Payments Operations | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
