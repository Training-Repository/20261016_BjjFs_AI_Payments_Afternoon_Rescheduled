# Copilot Chat for Excel — Participant Exercise Guide
### Formulas & Pivot Tables for Payments Operations
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `BFL_Payments_Copilot_Demo.xlsx`
**Mode:** Copilot Chat (no Microsoft 365 Copilot licence required)

---

## Before You Begin

### What You Need
- **Excel** open with `BFL_Payments_Copilot_Demo.xlsx`
- **Copilot Chat** open in a second window — any of:
  - `https://m365.cloud.microsoft/chat` (M365 Copilot Chat, work account)
  - The **Copilot** button in Microsoft Edge
  - The Copilot app in Windows or Teams
- Both windows side by side (**Win + ←** and **Win + →**)

### How This Session Works
Copilot Chat is **not connected to your workbook.** It cannot insert formulas, build pivot tables or change anything in Excel. It can *write* all of it for you, and you paste it in.

| Step | Where | What You Do |
|------|-------|-------------|
| **1. Ask** | Copilot Chat | Paste the prompt; get the formula or the steps |
| **2. Apply** | Excel | Paste into the cell, press Enter, fill down |

> **Key habit:** because Chat cannot see your file, **you** must describe it. That is the core skill of this session.

**The sheet:** headers are in **row 2**, and data runs from **row 3 to row 27** (25 exceptions, as of 30 Sep 2026). Columns **N–Q are empty**, and you will fill them using Copilot Chat. *(Column M is a deliberate blank spacer. It matters in Exercise 7.)*

---

## Step 0 — Set the Context (do this once)

Paste this into Copilot Chat **first**:

```
I'm working in Excel on a payments exception tracker. You can't see the file,
so here is the layout:

Headers are in row 2. Data runs from row 3 to row 27 (25 rows).
The data is as of 30 September 2026.

A  Exception ID        (text, e.g. PEX-26091)
B  Customer Name       (text)
C  Channel             (UPI, e-NACH, Card (PG), Net Banking, BBPS, Wallet,
                        EMI Refund)
D  Amount (₹)          (number)
E  Exception Type      (text)
F  Reported Date       (date)
G  Resolved Date       (date; blank if the case is still open)
H  Status              (Resolved / Open)
I  Allowed TAT (days)  (number)
J  Owner               (text)
K  Partner             (text)
L  Customer Complaint  (Yes / No)
M  (blank spacer — ignore it)
N  TAT Days            (empty — I'll add this)
O  TAT Status          (empty — I'll add this)
P  Compensation Due    (empty — I'll add this)
Q  Ageing Bucket       (empty — I'll add this)

For the rest of this conversation: when I ask for a formula, give me the
formula for the FIRST data row (row 3), ready to paste and fill down.
Give the formula on its own line, then a one-line explanation. No long
preamble.
```

> 💡 **Keep this block handy.** Save it, and adapt it for any tracker you use at work.

---

## Exercise 1 — TAT Days (Column N)

### Step 1 — Ask

```
Write a formula for N3: days from the Reported Date (F3) to the Resolved Date
(G3). If G3 is blank, count to 30 September 2026 instead.
```

**Expected output:**
```excel
=IF(G3="",DATE(2026,9,30)-F3,G3-F3)
```

### Step 2 — Apply
1. Click **N3**, paste the formula and press Enter.
2. Double-click the fill handle (the small square at the bottom-right of N3) to fill down to **N27**.
3. If you see a date instead of a number, set the column format to **General**.

✅ **Check:** Kunal Shah (row 9) shows **28**.

> **On live data:** ask Chat to *"use TODAY() instead of a fixed date"*.

---

## Exercise 2 — TAT Status (Column O)

### Step 1 — Ask

```
Write a formula for O3 that returns "Breach" if N3 is greater than the Allowed
TAT in I3, otherwise "Within TAT".
```

**Expected output:**
```excel
=IF(N3>I3,"Breach","Within TAT")
```

### Step 2 — Apply
Paste into **O3**, press Enter, and fill down to **O27**.

✅ **Check:** 12 Breach and 13 Within TAT.

---

## Exercise 3 — Compensation Due (Column P)

### Step 1 — Ask

```
Write a formula for P3: ₹100 for every day N3 exceeds I3; 0 if it does not.
```

**Expected output:**
```excel
=MAX(0,N3-I3)*100
```

### Step 2 — Apply
Paste into **P3**, press Enter, and fill down to **P27**.

✅ **Check:** the column totals **₹6,900**. Select P3:P27 and read the Sum in Excel's status bar.

> **Bonus:** *"Rewrite this using IF instead of MAX."* Both work. Which one is easier for a colleague to read?

---

## Exercise 4 — Ageing Bucket (Column Q)

### Step 1 — Ask

```
Write a formula for Q3. If H3 is "Open": "Over 7 days" if N3 is more than 7,
"4–7 days" if it is 4 to 7, otherwise "0–3 days". If H3 is not "Open", return
"Closed".
```

**Expected output:**
```excel
=IF(H3="Open",IF(N3>7,"Over 7 days",IF(N3>3,"4–7 days","0–3 days")),"Closed")
```

### Step 2 — Apply
Paste into **Q3**, press Enter, and fill down to **Q27**.

✅ **Check:** 3 Over 7 days (Kunal Shah, Meera Iyer, Varun Kapoor), 3 at 4–7 days, 1 at 0–3 days, 18 Closed.

---

## Exercise 5 — Ask Copilot Chat to Explain a Formula

Copy the formula from **Q3** and paste it into Copilot Chat with:

```
Explain this formula in simple terms. What does each part do, and in what
order does it evaluate?

=IF(H3="Open",IF(N3>7,"Over 7 days",IF(N3>3,"4–7 days","0–3 days")),"Closed")
```

> **This works on any formula.** Paste the most complex formula from your own MIS or reconciliation sheet and ask the same question.

---

## Exercise 6 — Pivot Table: Amount by Channel and TAT Status

Copilot Chat **cannot build the pivot for you.** It gives you the click-path, and you build it.

### Step 1 — Ask

```
Give me step-by-step instructions to build a PivotTable from A2:Q27 showing
the total Amount for each Channel, broken down by TAT Status (column O).
Column M is a blank spacer with no header. Tell me which field goes in which
area, and how to handle the blank column.
```

### Step 2 — Apply
1. Select **A2:Q27**.
2. **Insert → PivotTable → From Table/Range → New Worksheet** → OK.
3. **If Excel says *"The PivotTable field name is not valid"***, the cause is the blank header in column M. Type `Spacer` into **M2**, then insert the pivot again.
4. Drag the fields:
   - **Rows:** Channel
   - **Columns:** TAT Status
   - **Values:** Amount (₹), set to **Sum**

✅ **Check:** Card (PG) has the most value, ₹1,06,496, with ₹71,998 in breach.

### No-Pivot Alternative

```
Instead of a PivotTable, give me a SUMIFS formula that totals Amount for a
given Channel and TAT Status, so I can build a small summary grid.
```

You will get something like `=SUMIFS($D$3:$D$27,$C$3:$C$27,$S3,$O$3:$O$27,T$2)`.

---

## Exercise 7 — Pivot Table: Owner Workload by TAT Status

### Step 1 — Ask

```
Give me the steps for a second PivotTable from A2:Q27 showing the count of
exceptions for each Owner (column J), broken down by TAT Status (column O).
```

### Step 2 — Apply
1. Insert a PivotTable from **A2:Q27** on a new worksheet (with **M2** labelled as in Exercise 6).
2. Drag the fields:
   - **Rows:** Owner
   - **Columns:** TAT Status
   - **Values:** Exception ID *(Count)*

✅ **Check:** Arjun Mehta (e-NACH) has **5 of 5** in breach. That pattern points to the mandate-file process, not the person.

### No-Pivot Alternative
`=COUNTIFS($J$3:$J$27,$S3,$O$3:$O$27,T$2)` puts owners down the side and TAT Status across the top.

---

## ⚠️ Data Handling — Read This

This is a **synthetic training dataset**, so it is safe to describe and safe to paste. Live payments data is not:

- Use **Copilot Chat signed in with your BFL work account** (look for the enterprise data protection indicator).
- Never paste card numbers, account numbers, UPI IDs, UTR/RRN references or PAN.
- **De-identify first.** Replace names with Cust-1, Cust-2 and so on, and paste only the columns the question needs.

---

## What Changes When You Get a Copilot Licence

| | **Copilot Chat** *(today)* | **Copilot in Excel** *(licensed)* |
|---|---|---|
| Sees your workbook | ✗ — you describe it | ✓ — reads it directly |
| Writes formulas | ✓ | ✓ |
| **Inserts** formulas into cells | ✗ — you paste | ✓ automatic |
| Builds PivotTables | ✗ — gives you the steps | ✓ builds them |
| Formats, charts, highlights | ✗ | ✓ |
| Explains any formula | ✓ | ✓ |

---

## Quick Reference — Payments Prompts *(this session)*

| Task | Ask Copilot Chat |
|---|---|
| TAT Days (N) | *"Formula for N3: days from F3 to G3; if G3 is blank, to 30 Sep 2026."* |
| TAT Status (O) | *"Formula for O3: "Breach" if N3 > I3, else "Within TAT"."* |
| Compensation (P) | *"Formula for P3: ₹100 per day N3 exceeds I3; else 0."* |
| Ageing (Q) | *"Formula for Q3: for Open cases, Over 7 / 4–7 / 0–3 days from N3; else Closed."* |
| Explain a formula | *"Explain this formula in simple terms, part by part."* (then paste it) |
| Pivot — value at risk | *"Steps for a PivotTable from A2:Q27: Sum of Amount by Channel × TAT Status; M is a blank spacer."* |
| Pivot — desk workload | *"Steps for a PivotTable: count by Owner × TAT Status."* |
| Highlight | *"Steps to conditionally format rows where O = Breach and H = Open in red."* |

---

*Bajaj Finance Limited | AI Academy — Payments Operations | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
