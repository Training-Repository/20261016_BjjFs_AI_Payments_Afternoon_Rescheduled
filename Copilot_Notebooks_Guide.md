# Copilot Notebooks — Participant Guide
### One workspace, all your files, no re-attaching
**Bajaj Finance Limited | M365 Copilot Training — Payments Operations**
**Files used:** `BFL_Payments_Copilot_Demo.xlsx`, `BFL_Payments_Copilot_Dataset.xlsx`, `Payments_Operations_Standard.pdf`, and the guides in this repo

---

## Why Notebooks?

In a normal Copilot Chat, every new conversation starts from zero. You attach the file again, explain your role again and restate the format you want. You are also limited to **3 attachments per prompt**.

A **Copilot Notebook** is a saved workspace for one piece of work. You add your files to it once, as **references**, and write your standing instructions once. After that, every chat you start inside the notebook is grounded on those references, across sessions and days.

| | Regular Copilot Chat | Copilot Notebook |
|---|---|---|
| Files | Attached per prompt (max **3** in BFL) | Added once as **references**, then available to every chat in the notebook |
| Context | Lost when you open a new chat | Kept in the notebook across chats and days |
| Instructions (role, tone, format) | Re-typed in every prompt (the RTCFT block) | Set once in the notebook's **Copilot instructions** |
| Grounding | Your prompt + attachments (+ wider M365 / web, depending on settings) | **Only** the references you added, so answers stay focused on your files |
| Outputs | Chat replies | Chat replies, saved pages, and (where enabled) Word / PowerPoint drafts, mind maps, study guides |

> 💡 **Rule of thumb:** use one notebook per piece of work, such as the September partner review, the month-end reconciliation or the monthly Payments MIS pack. Don't create a new notebook for every question.

---

## ⭐ Going Beyond the 3-Attachment Limit

This is the most useful reason to use Notebooks at BFL.

- The 3-file limit applies to **attachments in a chat prompt**.
- Notebook **references** are added separately, through the notebook's *Add references* panel rather than the chat box. Copilot then grounds its answers on **all** of them together.
- According to Microsoft's documentation:
  - **Copilot Chat** users can add up to **50 references**, and all 50 are used for grounding.
  - **Microsoft 365 Copilot** (licensed) users can add more than 300 references. The first **300** are used for grounding.
- A **OneDrive or SharePoint folder** can be added as a single reference. Every file you put in that folder later becomes available to the notebook without any extra steps.

**In practice:** one question can draw on the exception log, the mandate register, the chargebacks, the partner SLAs and the Standard at once, with nothing attached to the prompt.

> ⚠️ **Check in your own tenant:** the 3-attachment cap is BFL's setting for chat. If notebook references also appear capped, tell your trainer or IT. Exercise 2 below is a simple way to test it.

---

## Before You Begin

- [ ] You can sign in to the **M365 Copilot** app (desktop or web) with your BFL work account, and you see **Notebooks** in the left navigation.
- [ ] You have copied the files from this repo to your **OneDrive**, in a folder such as `OneDrive › Copilot-Training-Payments`.
- [ ] You have made `.txt` copies of three Markdown guides. Notebooks accept `.docx, .pptx, .xlsx, .pdf, .loop, .page, .txt, .rtf` and OneNote pages, but **not `.md`**. Download the guides, then rename them:

| Original in repo | Rename to |
|---|---|
| `MetaPrompting_Guide_Payments.md` | `MetaPrompting_Guide_Payments.txt` |
| `BFL_Payments_MetaPrompts_Participant_Guide.md` | `BFL_Payments_MetaPrompts_Participant_Guide.txt` |
| `Excel_To_PowerPoint.md` | `Excel_To_PowerPoint.txt` |

`Payments_Operations_Standard.pdf` needs no renaming.

Your OneDrive folder should now contain **6 files**:

```
Copilot-Training-Payments/
├── BFL_Payments_Copilot_Demo.xlsx              (25 exceptions, as of 30 Sep 2026)
├── BFL_Payments_Copilot_Dataset.xlsx           (Exception Log, Mandate Register, Payments Performance,
│                                                Reconciliation Tracker, Chargeback Register,
│                                                Partner SLA Tracker)
├── Payments_Operations_Standard.pdf            (TAT, reconciliation & dispute standard — training sample)
├── MetaPrompting_Guide_Payments.txt
├── BFL_Payments_MetaPrompts_Participant_Guide.txt
└── Excel_To_PowerPoint.txt
```

That is already **twice the 3-attachment limit**, which is intentional for these exercises.

---

# Exercise 1 — Create Your Notebook
**Time:** ~5 minutes

### Step 1 — Create it
1. In the M365 Copilot app, select **Notebooks** → **New notebook**.
2. Name it: `BFL Payments Ops — Sep 2026 Review`

### Step 2 — Add references
1. Select **Add references** (at the top of the content pane in the Copilot app, or the **+** next to *References* in OneNote).
2. Choose **one** method:
   - **Option A: files.** Select all 6 files from your OneDrive folder, or use **Upload** to add them from your computer.
   - **Option B: folder (recommended).** Select the `Copilot-Training-Payments` **folder** as a single reference.
3. Select **Add**.

> 💡 **Option B scales better.** When October's recon tracker or partner report lands in the folder, the notebook can use it without any extra step.

### Step 3 — Set the Copilot instructions (your RTCFT Role, Format and Tone, written once)
Open the notebook's **Copilot instructions** and paste:

```
I work in Payments Operations (non-sales) at Bajaj Finance Limited (an NBFC): exceptions, EMI mandates,
reconciliation, chargebacks and payment partner management.
Currency is ₹. Watch the units: Payments Performance uses ₹ Cr for value and ₹ lakh for unreconciled
value; the Reconciliation Tracker uses ₹ lakh. TAT is in calendar days. The data is as of 30 September 2026;
the performance sheet covers April–September 2026.
The rules are in Payments_Operations_Standard.pdf (a training sample).

When you answer:
- Use only the references in this notebook. Name the file and sheet (or the clause number, for the
  Standard) for every number or rule you quote.
- If something is not in the references, say "not in the data" — do not estimate.
- Matching customers across sheets by name is a lead, not proof. Say so when you do it.
- Lead with a 3-line summary, then a table, then recommendations with a suggested owner.
- Tone: factual, precise, audit-ready — suitable for the Head of Payments Operations.
- Use Red / Amber / Green where a target, limit or TAT exists.
```

### ✅ Check
Your notebook shows **6 references** (or 1 folder), and the instructions are saved.

---

# Exercise 2 — Validate the Notebook Can See Everything
**Time:** ~5 minutes

Start a chat **inside the notebook** and type:

```
List every reference in this notebook. For each one, give:
- the file name
- what it contains (sheets / sections, row counts, periods covered)
- one fact from it that proves you have read it
Then tell me if any file looks incomplete or could not be read.
```

### ✅ Check
- [ ] All **6 files** are listed. That is more than you could attach to one chat prompt.
- [ ] For `BFL_Payments_Copilot_Dataset.xlsx`, it names all **six** sheets.
- [ ] For `BFL_Payments_Copilot_Demo.xlsx`, it mentions 25 exceptions as of 30 Sep 2026.
- [ ] For the PDF, it identifies the Payments Operations Standard (ref PAY-OPS-STD-04) and notes that it is a training sample.

---

# Exercise 3 — Ask Across Files (the payoff)
**Time:** ~15 minutes

Neither question below could be answered in one regular chat prompt without re-attaching. In the notebook, you don't attach anything.

### 3a — One customer, every sheet

```
Some customers appear in more than one sheet of BFL_Payments_Copilot_Dataset.xlsx.
Find every customer who appears in the Chargeback Register AND in the Exception Log.
For each one, build a single view across the Exception Log, the Mandate Register and
the Chargeback Register: what happened, current status, any TAT breach or compensation,
and what is due next.
Then tell me what evidence from one sheet could help the chargeback in another,
and which clauses of the Standard apply.
```

**What a good answer contains:**
- **Meera Iyer**:
  - **Exception Log:** Card (PG) ₹42,999 open for 11 days against an allowed 5, so in breach with ₹600 compensation due (clause 3.8).
  - **Chargeback Register:** **CB-7712** (Visa, goods/services not received), due 4 Oct with **partial evidence**. It reaches the clause 5.2 escalation point (3 days before due) on 1 Oct.
  - **Mandate Register:** 2 of 3 presentations bounced, so a service call is due (clause 6.2).
  - **Note:** the open gateway exception and the chargeback relate to the same ₹42,999 purchase. Resolving one should feed the evidence for the other.
- **Sameer Khan**:
  - **Exception Log:** a ₹2,000 wallet refund, resolved within TAT on 25 Sep.
  - **Chargeback Register:** **CB-7726** (UPI, credit not processed, ₹2,000) has evidence **not started** and is due 3 Oct.
  - **Note:** the resolved refund is likely the evidence needed. This is a name-and-amount match, so verify it.
  - **Mandate Register:** his UPI AutoPay mandate was rejected, so re-initiate it within 7 days (clause 6.1).

### 3b — One incident, every source

```
NovaPay UPI Switch had an outage in late September. Trace its impact across every
reference:
- Partner SLA Tracker — uptime, incident, RCA status, breaches this quarter
- Reconciliation Tracker — 30 Sep cycle vs 15 Sep
- Payments Performance — what moved in September
- Exception Log — open UPI cases
- Payments_Operations_Standard.pdf — which clauses are triggered
Give me an incident summary, a clause-by-clause table (Clause | Requirement | What the
data shows | Met? | Action | Owner), and a 3-line note for the Head of Payments Operations.
```

**What a good answer contains:**
- **SLA:** uptime 99.62% against 99.9% (clause 7.1). The longest outage was **74 minutes**, more than 30, and **no RCA has been received** (clause 7.2). It is the second breach this quarter, so a partner review is required (clause 7.3).
- **Reconciliation:** breaks rose from 70 (₹1.8 lakh) to **582 (₹14.6 lakh)**, above the ₹10 lakh limit, so escalate to the Finance Controller (clause 4.3). **96** breaks are aged more than 3 days (clause 4.2).
- **Performance:** UPI success fell from 99.3% to **98.4%**, auto-reversal within TAT fell to **94.6%**, and compensation paid reached **₹92,600**.
- **Exceptions:** Sneha Gokhale's UPI case is open at 5 days against T+1 (clause 3.1), with the root cause "pending with PSP bank". Amol Patwardhan's case is open at 1 day and still within TAT.
- **Caution:** Copilot should link the exceptions to the outage only as a *likely* cause. The log does not say so.

### ✅ Check
- [ ] Every figure is quoted with its **file and sheet**, and every rule with its **clause number**.
- [ ] 3a uses three sheets; 3b uses four sheets **and** the PDF.
- [ ] Name matches and likely causes are presented as leads, not proof.
- [ ] You did **not** attach a single file.

---

# Exercise 4 — Re-run the Use Cases Without Re-attaching
**Time:** ~10 minutes

Pick any two and use these short versions. The notebook instructions already supply the role, tone and format.

| Stage | Prompt inside the notebook |
|---|---|
| 1 — Exceptions | `From Exception Log: open cases oldest first, TAT breaches with compensation, and the channel that breached on every case.` |
| 2 — Mandates | `From Mandate Register: rejected (with re-initiation mode), pending, service calls (2+ bounces) and revoked mandates.` |
| 3 — Performance | `From Payments Performance: every metric that missed its target in September, with Aug and Sep values.` |
| 4 — Reconciliation | `From Reconciliation Tracker: 30 Sep breaks by partner vs 15 Sep, partners above ₹10 lakh, recurring root causes.` |
| 5 — Chargebacks & SLAs | `From Chargeback Register, Partner SLA Tracker and the Standard: cases due in 7 days with required action by clause, and the partner scorecard.` |

**Quick checks:**
- **Stage 1:** e-NACH breached on all 4 of its logged cases. Total compensation is ₹6,100.
- **Stage 4:** NovaPay is above the limit at ₹14.6 lakh. Sahyog's "refunds missing from settlement file" recurs in both cycles.

---

# Exercise 5 — The 9-Step Flow, Inside One Notebook
**Time:** ~10 minutes

`Excel_To_PowerPoint.md` uses three separate chats and asks you to **attach the file again** in Chat B. In a notebook:

1. Start **Chat A** in the notebook and run Steps 1–4 on one sheet, for example **Payments Performance** or **Partner SLA Tracker**. Copy the Working Prompt from Step 4.
2. Start a new chat in the **same notebook** (Chat B) and paste the Working Prompt. The file is already there.
3. Save the useful output as a **page** in the notebook.
4. If your notebook shows **create options** (Word document / PowerPoint deck), generate the Step-6 document or the Step-9 deck from the notebook. Otherwise, continue with the PowerPoint agent as in the workbook.

---

## Optional Extras (if visible in your tenant)

| Feature | Try this |
|---|---|
| **Mind map** | Map how partners, recon breaks, exceptions and Standard clauses connect. |
| **Study guide** | Generate a quiz from `MetaPrompting_Guide_Payments` to test yourself on RTCFT. |
| **Word / PowerPoint from notebook** | Turn your Exercise 3b output into a Word incident note or a 5-slide partner review deck. |
| **Share the notebook** | Share with a colleague so they work from the same references and instructions. |

---

## Efficiency Rules — Quick Reference

| Do | Avoid |
|---|---|
| One notebook per piece of work (e.g. "Sep partner review", "Month-end recon") | One giant notebook for everything |
| Put role, period, units, tone and format in **Copilot instructions** | Re-typing the RTCFT block in every prompt |
| Add a **folder** reference when recon files and partner reports keep arriving | Re-uploading each new version by hand |
| Remove outdated references (last month's tracker, an old Standard) | Keeping several versions of the same file |
| Ask Copilot to **name file + sheet or clause** for every number or rule | Accepting figures you can't trace |
| Treat cross-sheet name matches as leads and verify them | Acting on a match as if it were proof |
| Save good outputs as **pages** | Leaving key results only in chat history |
| Start a **new chat in the same notebook** for each new task | One endless chat |

---

## Troubleshooting

| Problem | What to do |
|---|---|
| `.md` file can't be added | Rename it to `.txt`, or copy the content into a notebook page. |
| Copilot mixes ₹ Cr and ₹ lakh | Restate the units in your prompt: *"Recon values are in ₹ lakh."* |
| Copilot says it can't find a number | Check the file is in **References**. Ask: *"Which sheet contains X?"* |
| A clause or figure looks wrong | Open the source, check it yourself, then ask Copilot to quote the exact text. |
| Notebooks not in the left navigation | Your licence or tenant setting may not include Notebooks yet. Tell your trainer. |
| Folder reference returns partial results | Name the specific file in your prompt. |

---

## Further Reading

- [How Microsoft Copilot Notebooks works](https://support.microsoft.com/en-us/microsoft-365-copilot/how-microsoft-365-copilot-notebooks-works)
- [Add references to your Copilot Notebook](https://support.microsoft.com/en-us/microsoft-365-copilot/add-references-to-your-microsoft-365-copilot-notebook)
- [Microsoft 365 Copilot release notes](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes)

---

## 📝 Notes

**What I would put in a notebook at work:**

&nbsp;

**My standing Copilot instructions:**

&nbsp;

---

*Bajaj Finance Limited | M365 Copilot Training — Payments Operations*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
