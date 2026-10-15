# AI at Work – Participant Workbook

**The 9-Step Copilot Flow — from a raw file to a leadership-ready deck**

**Course:** AI Enablement — Copilot for Reviews & Decks
**Tool:** Microsoft Copilot (+ PowerPoint agent)
**Companion data for today:** `BFL_Payments_Copilot_Dataset.xlsx` — sheet **Payments Performance** (Apr–Sep 2026), **Reconciliation Tracker** or **Partner SLA Tracker** (Sep 2026)

> **The one thing that changes is the file.**
> The same nine steps take *any* document — a report, a register, a tracker, a dataset — and turn it into an **analysis**, a **document** and a **leadership deck**. Learn the flow once; run it on your own Payments file the same afternoon.

---

## What you'll be able to do after this

Take any work file and turn it into a sound analysis, a Word document and a leadership deck, using a repeatable 9-step method you can run on your own data the same day.

## The method at a glance

The flow uses **three separate chats** on purpose. Keeping them separate is what keeps the output clean.

| | Chat | Steps | Why separate |
|---|---|---|---|
| **A** | Discovery | 1–4 | Exploring is messy. Let it be messy here. |
| **B** | Execution | 5–8 | Run the real work in a clean context. |
| **C** | PowerPoint agent | 9 | Deck generation is its own tool. |

Two steps are **adapted to the room**, **Step 3** and **Step 7**, because the same file makes a different meeting depending on who you are presenting to.

---

# CHAT A — Discovery & Framing

> You never produce the final deliverable here. This chat is for understanding and deciding.

## Step 1 — Read & validate comprehension

**Do:** Attach the file. Ask Copilot to tell you what's in it *before* you trust any analysis.

**Type this:**
> Read the attached file. Tell me exactly what it contains — the sheets, columns, time periods, key categories, and any targets or status fields. List anything that looks incomplete, ambiguous or inconsistent.

**Check:** Did Copilot pick up every sheet and column that matters, all the months, and the targets in the sub-title row (for example, Success Rate 98.5% and Auto-reversal within TAT 98%)? If it missed one, it will mis-analyse later. Fix its understanding now.

**Why this matters:** everything downstream inherits this reading. Ten seconds of validation saves a wrong analysis.

---

## Step 2 — Diverge: what analysis is possible?

**Do:** Ask for the full menu of analyses, both to cross-check your own idea and to find ones you hadn't thought of.

**Type this:**
> Based on this file, list every meaningful analysis or review someone in my role (Payments Operations) could run. For each, give a one-line description of what it would reveal. Include the obvious checks *and* any less obvious ones you can see in the data.

**Check:** Does the list include the analysis you already had in mind? That is validation. What's on the list that you *didn't* think of? That is the value.

> **Note:** if your file is a document rather than a table (a circular, a partner agreement, the Payments Operations Standard), "analysis" becomes *review or extraction* — a clause pull, a compliance check or a list of clarification questions.

---

## Step 3 — Prioritise for the room  ⟵ *adapt to your audience*

**Do:** Narrow it down to the 5 highest-impact analyses **for the specific person you're meeting.**

**Type this** (swap in your audience):
> From that list, pick the top 5 highest-impact analyses for a review meeting with **[the person I'm meeting]**. Prioritise what drives their decision — approve, proceed, escalate or clarify. Explain in one line why each earns a place.

**Adapt — same file, different top 5.** Who are you walking in to see?

| If they're… | They mostly want… |
|---|---|
| **Head of Payments Operations** | The headline and the ask: targets missed, the cost of breaches, the one decision needed |
| **Finance / Controller** | Unreconciled value, ageing of breaks, compensation as a cost line |
| **Risk & Compliance / Audit** | TAT breaches against the Standard, complaint trend, chargeback losses |
| **Vendor / Partner Management** | Partner SLAs, outages, RCAs, renewals |
| **Desk leads (UPI, NACH, Cards & PG)** | Today's open cases, ageing, evidence deadlines |

**Your note — who am I meeting, and what do they care about?**
> _______________________________________________

---

## Step 4 — Meta-prompt: build the prompt for your chosen analysis

**Do:** Pick ONE analysis. Ask Copilot to *write the prompt* for it (the meta-prompt move).

**Type this:**
> Act as a prompt engineer. I want to run this analysis on my file: **"[your chosen analysis]."** Write me a precise Copilot prompt that will produce a reviewer's note with a flags table and a clear recommendation. Use a **Role–Task–Context–Format–Tone (RTCFT)** structure.

**Result:** Copilot gives you a polished prompt. Copy it. **You're done with Chat A.**

---

# CHAT B — Execution & Productising

> Open a **new chat.** Clean context gives clean output.

## Step 5 — Run the analysis

**Do:** Paste the prompt from Step 4 and attach the file again.

**Check that the output catches what you'd catch by hand.** Read it as the reviewer, not the operator. Are the flags the ones *you* would have raised? Is anything obvious missing, such as a target miss, a TAT breach, a limit breach or an adverse trend?

**If it misses one:** follow up plainly — *"You didn't flag [the specific thing] — check again against [the target / limit / clause]."*

---

## Step 6 — Create the document

**Do:** Turn the analysis into a Word document with **Export to Word** (or **Edit in Pages** to collaborate).

**Polish prompt (optional):**
> Reformat this as a one-page reviewer's note: heading, a flags table, and a recommendation line. Formal tone.

**You now hold deliverable #1 — the review document.**

---

## Step 7 — Plan the deck for your time slot  ⟵ *adapt to your audience*

**Do:** Ask how to fit this into your actual meeting length and audience.

**Type this** (swap both):
> I have **[X minutes]** with **[the person I'm meeting]** to walk through this review. How many slides should I use, and what should each cover? Keep it decision-focused.

**Adapt:** 5 minutes means 3 slides (headline and ask). 15 minutes means 5–6 slides with the flags table. A working session needs an appendix slide as well.

---

## Step 8 — Generate the slide-by-slide outline

**Do:** Ask for the full outline with suggested visuals.

**Type this:**
> Generate a slide-by-slide outline based on that plan. For each slide: title, 3–4 bullet points, and a suggested visual (chart, table or icon). Base it only on the analysis we produced — don't invent figures.

**You now hold deliverable #2 — the slide outline.**

---

# CHAT C — PowerPoint Agent

## Step 9 — Build the deck

**Do:** Paste the Step-8 outline into the **PowerPoint agent** (or **Copilot inside PowerPoint**) to generate the deck. Then check every figure against your Step-6 document before you present.

**You now hold deliverable #3 — the presentation.**

---

# Worked example — Payments Performance for the Head of Payments Operations

Use this to see the flow end to end on today's file before you try your own.

| Step | What you do | What to look for |
|---|---|---|
| 1 | Attach the dataset; ask what the **Payments Performance** sheet contains | Six months (Apr–Sep 2026), 14 metrics, the targets in row 2, and the units (₹ Cr vs ₹ lakh) |
| 2 | Ask for every possible analysis | Volume vs success rate, TAT and compensation, chargeback win rate, reconciliation, complaints |
| 3 | Prioritise for the **Head of Payments Operations** | The September targets missed; the cost of TAT breaches; which partner drove it |
| 4 | Meta-prompt for *"September performance review"* | An RTCFT prompt asking for a flags table and an October recommendation |
| 5 | Run it in Chat B | It should flag: volume **+15.5%**; success **98.1%** (target 98.5%); auto-reversal **94.6%** (target 98%); chargeback win **58%**; complaints **214**; compensation **₹92,600** |
| 6 | Export to Word | A one-page reviewer's note |
| 7 | *"I have 10 minutes with the Head of Payments Operations"* | About 4 slides |
| 8 | Outline with visuals | A success-rate trend line, a target-vs-actual table, an actions slide |
| 9 | PowerPoint agent | The deck; check every figure against the Word note |

> **Try a second room:** run Step 3 again for **Finance / the Controller**, using the **Reconciliation Tracker**. The top 5 changes completely, even though the dataset is the same.

---

# Applying the flow to documents (not just spreadsheets)

Many Payments files are Word or PDF, not Excel. The flow is the same, but **Step 2 changes meaning**: "analysis" becomes "review or extraction".

| Document type | Step 2 becomes… |
|---|---|
| Payments Operations Standard / RBI circular | Obligation and clause extraction + compliance flags |
| Partner agreement / SLA schedule | Commitments, penalties, renewal terms + gaps |
| Partner RCA after an outage | Timeline, root cause, fix, open questions to send back |
| Network chargeback notice | Reason code, deadline, evidence checklist |
| Customer complaint letter | Facts vs claims, the clause it touches, a draft reply |

Everything else stays the same: validate, prioritise for the room, meta-prompt, run in a clean chat, export to Word, then plan and build the deck.

---

# Your turn — run the 9 steps on your own file

Fill this in during the session, then reuse it at your desk.

| Step | Your entry |
|---|---|
| 1. File I'm reading | ____________________ |
| 2. Analyses/reviews possible | ____________________ |
| 3. Who I'm meeting + their priority | ____________________ |
| 3. My top 5 → the one I pick | ____________________ |
| 4. Meta-prompt gave me this prompt | ____________________ |
| 5. Key findings from the run | ____________________ |
| 6. Document created? (Y/N) | ____________________ |
| 7. Time slot + slide count | ____________________ |
| 8. Outline ready? (Y/N) | ____________________ |
| 9. Deck built + figures re-checked? | ____________________ |

---

## The one rule that never changes

Copilot **reads, analyses, drafts and builds.** You **validate every figure and own every decision.** Reversals, compensation, partner actions and what goes in front of leadership stay yours.

---

*AI at Work – Participant Workbook | Bajaj Finance Limited — Payments Operations*
*Training delivered by **Technizer India** | GenAI for Enterprise Teams*
