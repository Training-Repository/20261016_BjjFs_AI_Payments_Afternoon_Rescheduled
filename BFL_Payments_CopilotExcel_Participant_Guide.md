# Copilot in Excel — Participant Exercise Guide
### Formulas & Pivot Tables for Payments Operations
**Bajaj Finance Limited | M365 Copilot Training**
**File:** `BFL_Payments_Copilot_Demo.xlsx`
**Mode:** Copilot in Excel (Microsoft 365 Copilot licence). *Copilot Chat only? Use `BFL_Payments_Alt_Copilot_Chat_Participant_Guide.md` instead.*

---

## Before You Begin

- Open `BFL_Payments_Copilot_Demo.xlsx` from **OneDrive**. Copilot in Excel needs the file saved in OneDrive or SharePoint with AutoSave on.
- Click the **Copilot** button (top-right of the Home ribbon) and keep the pane open for every exercise.
- The sheet `Payment Exceptions` has **25 exceptions**. Headers are in **row 2**, data runs from **row 3 to row 27**, and the data is as of **30 Sep 2026**.
- Columns **N–Q are intentionally blank**. You will fill them using Copilot. Column M is a blank spacer.

| Column | Field | Column | Field |
|---|---|---|---|
| A | Exception ID | G | Resolved Date (blank if open) |
| B | Customer Name | H | Status (Resolved / Open) |
| C | Channel | I | Allowed TAT (days) |
| D | Amount (₹) | J | Owner |
| E | Exception Type | K | Partner |
| F | Reported Date | L | Customer Complaint |

---

## Exercise 1 — Formula Column: TAT Days (Column N)

Click cell **N3**, then type into the Copilot pane:

```
In column N, calculate TAT Days for each exception: the number of days from
the Reported Date (column F) to the Resolved Date (column G). If column G is
blank (case still open), count to 30 September 2026 instead. Apply it to all
25 rows.
```

**What Copilot will produce:**
```excel
=IF(G3="",DATE(2026,9,30)-F3,G3-F3)
```

✅ **Check:** Kunal Shah (row 9, open EMI refund) shows **28**. Aarav Kulkarni (row 3) shows **1**.

> **On live data:** use `TODAY()` in place of `DATE(2026,9,30)` so open cases keep ageing automatically. The fixed date is used here so everyone gets the same answer.

---

## Exercise 2 — Formula Column: TAT Status (Column O)

Click **O3**, then type:

```
In column O, show "Breach" if TAT Days (column N) is greater than the Allowed
TAT (column I), otherwise "Within TAT". Apply it to all 25 rows.
```

**What Copilot will produce:**
```excel
=IF(N3>I3,"Breach","Within TAT")
```

✅ **Check:** **12 Breach** and 13 Within TAT.

---

## Exercise 3 — Formula Column: Compensation Due (Column P)

Click **P3**, then type:

```
In column P, calculate the compensation due to the customer: ₹100 for every
day that TAT Days (column N) exceeds the Allowed TAT (column I). If it is
within TAT, show 0. Apply it to all 25 rows.
```

**What Copilot will produce:**
```excel
=MAX(0,N3-I3)*100
```

✅ **Check:** the column totals **₹6,900**. The largest single amount is Kunal Shah at **₹2,100** (28 days against an allowed 7).

> **Try this:** *"Total column P by Channel."* e-NACH accounts for ₹2,300 of it, and every one of its five exceptions is in breach.

---

## Exercise 4 — Formula Column: Ageing Bucket (Column Q)

Click **Q3**, then type:

```
In column Q, show an ageing bucket for open cases only. If Status (column H)
is "Open": "Over 7 days" if TAT Days (column N) is more than 7, "4–7 days" if
it is 4 to 7, otherwise "0–3 days". If the case is resolved, show "Closed".
Apply it to all 25 rows.
```

**What Copilot will produce:**
```excel
=IF(H3="Open",IF(N3>7,"Over 7 days",IF(N3>3,"4–7 days","0–3 days")),"Closed")
```

✅ **Check:**
- **3 Over 7 days:** Kunal Shah, Meera Iyer, Varun Kapoor.
- **3 at 4–7 days.**
- **1 at 0–3 days.**
- **18 Closed.**

---

## Exercise 5 — Ask Copilot to Explain a Formula

Click **Q3**, then type:

```
Explain this formula in simple terms. What does each part do, and in what
order does it check the conditions?
```

**What Copilot will explain:**
> *"It first checks whether the case is open. Resolved cases return Closed straight away. For open cases it checks the age from the top down: more than 7 days, then more than 3 days, otherwise 0–3 days."*

> **Try this:** *"What does this return for an open case at exactly 7 days, and exactly 3 days?"* Because the tests are `>7` and `>3`, 7 lands in **4–7 days** and 3 lands in **0–3 days**.

---

## Exercise 6 — Pivot Table: Amount by Channel and TAT Status

Click anywhere in the data, then type:

```
Create a pivot table on a new sheet that shows the total Amount for each
Channel, broken down by TAT Status (column O). I want to see which channels
carry the most value in breach.
```

**What Copilot will produce:**
- **Rows:** Channel
- **Columns:** TAT Status
- **Values:** Sum of Amount (₹)

✅ **Check:** Card (PG) carries the most value, **₹1,06,496**, of which **₹71,998** is in breach. e-NACH's full **₹26,300** is in breach.

---

## Exercise 7 — Pivot Table: Owner Workload by TAT Status

Type into the Copilot pane:

```
Now create another pivot table showing the count of exceptions for each Owner,
broken down by TAT Status. I want to see whose desk has the most breaches.
```

**What Copilot will produce:**
- **Rows:** Owner
- **Columns:** TAT Status
- **Values:** Count of Exception ID

✅ **Check:** **Arjun Mehta (e-NACH desk) has 5 of 5 in breach.** That points to a process issue on the mandate file, not to an individual. Neha Kulkarni has 2 breaches out of 8.

> **If Copilot can't use column O:** the blank spacer column M can block range detection. Type `Spacer` into **M2** and ask again.

---

## Copilot Prompts — Quick Reference

| Task | Prompt to use in the Copilot pane |
|------|-------------------------------|
| TAT Days | "In column N, days from Reported Date (F) to Resolved Date (G); if G is blank, to 30 Sep 2026." |
| TAT Status | "In column O, "Breach" if N > Allowed TAT (I), else "Within TAT"." |
| Compensation | "In column P, ₹100 per day that N exceeds I; 0 if within TAT." |
| Ageing Bucket | "In column Q, for Open cases: Over 7 days / 4–7 days / 0–3 days from N; else Closed." |
| Explain a formula | "Explain this formula in simple terms." |
| Pivot — value at risk | "Pivot: total Amount by Channel and TAT Status." |
| Pivot — desk workload | "Pivot: count of Exception ID by Owner and TAT Status." |
| Highlight | "Highlight rows where TAT Status is Breach and Status is Open in red." |
| Sort | "Sort by Compensation Due, highest first." |

---

*Bajaj Finance Limited | AI Academy — Payments Operations | Microsoft Copilot Training Programme*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
