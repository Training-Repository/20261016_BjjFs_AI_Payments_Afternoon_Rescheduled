# M365 Copilot Training — Payments Operations, Non Sales (Bajaj Finance Limited)

Training materials for a Microsoft 365 Copilot enablement session for the Bajaj Finance Limited (BFL) **Payments (Non Sales)** team, delivered by Technizer India under the **GenAI for Enterprise Teams** program.

The session covers prompt engineering (meta-prompting and the RTCFT framework), Copilot in Excel (formulas and pivot tables on a payments exception tracker), checking practice against a payments operations standard in PDF, the end-to-end flow from a raw data file to a leadership-ready deck, and using Copilot Notebooks to work across more files than the chat attachment limit allows.

> All data in this repository is **synthetic** and safe to use in training. Customer names, partner names and case numbers are fictional. `Payments_Operations_Standard.pdf` is a **training sample**. It is not BFL policy, and it is not RBI text.

## Contents

| File | Description |
|---|---|
| [`MetaPrompting_Guide_Payments.md`](MetaPrompting_Guide_Payments.md) | Introduces meta-prompting: asking Copilot to write your prompt for you. Includes six ready-to-use meta-prompts for Payments Operations work. |
| [`BFL_Payments_MetaPrompts_Participant_Guide.md`](BFL_Payments_MetaPrompts_Participant_Guide.md) | Main hands-on guide. Six stages, each following the Meta Prompt → Generated Prompt → Live Apply rhythm: failed-transaction exceptions, EMI mandate health, payments performance reporting, reconciliation breaks, chargebacks and partner SLAs, and a partner escalation email in Outlook. Each stage lists what a good answer contains. |
| [`BFL_Payments_CopilotExcel_Participant_Guide.md`](BFL_Payments_CopilotExcel_Participant_Guide.md) | Copilot in Excel exercises with formula columns for TAT days, TAT status, compensation due and ageing bucket. Also covers explaining a formula and building two pivot tables. |
| [`BFL_Payments_Alt_Copilot_Chat_Participant_Guide.md`](BFL_Payments_Alt_Copilot_Chat_Participant_Guide.md) | The same Excel exercises **without a Microsoft 365 Copilot licence**, for Copilot Chat users. You describe the sheet, Chat writes the formula, and you apply it. |
| [`Excel_To_PowerPoint.md`](Excel_To_PowerPoint.md) | "AI at Work" workbook describing a 9-step Copilot flow across three chats (Discovery, Execution, PowerPoint agent). Turns any file into an analysis, a Word document and a leadership deck, with a worked Payments example. |
| [`Copilot_Notebooks_Guide.md`](Copilot_Notebooks_Guide.md) | Using Copilot Notebooks as a persistent workspace. Covers tracing one customer across exceptions, mandates and chargebacks, and tracing one partner outage across SLAs, reconciliation, KPIs and the Standard, without re-attaching. |
| [`copilot-pdf-playbook.md`](copilot-pdf-playbook.md) | Repeatable process for turning a large document into a formatted PDF using Copilot and Word, with a partner incident report as the example. |
| [`Payments_Operations_Standard.pdf`](Payments_Operations_Standard.pdf) | Payments Operations standard (training sample) covering failed-transaction TAT and compensation, reconciliation, chargebacks, EMI mandates, partner SLAs, complaints and reporting. Used in Stage 5 and in the Notebooks exercises. |
| [`BFL_Payments_Copilot_Dataset.xlsx`](BFL_Payments_Copilot_Dataset.xlsx) | Practice dataset for the meta-prompt stages. Sheets: Exception Log, Mandate Register, Payments Performance, Reconciliation Tracker, Chargeback Register, Partner SLA Tracker. |
| [`BFL_Payments_Copilot_Demo.xlsx`](BFL_Payments_Copilot_Demo.xlsx) | Practice dataset for the Excel exercises: 25 payment exceptions as of 30 Sep 2026, with columns N–Q left blank for Copilot-generated formulas. |
| [`PDFs/`](PDFs) | PDF versions of the seven guides, for printing or offline use. |
| [`Contact.md`](Contact.md) | Trainer contact details. |

## How to use this material

1. Start with `MetaPrompting_Guide_Payments.md` to learn the meta-prompt formula and RTCFT.
2. Work through `BFL_Payments_MetaPrompts_Participant_Guide.md` using `BFL_Payments_Copilot_Dataset.xlsx`.
3. Move to `BFL_Payments_CopilotExcel_Participant_Guide.md` for the formula and pivot exercises on `BFL_Payments_Copilot_Demo.xlsx` (requires a Microsoft 365 Copilot licence).
   - **Copilot Chat only?** Use `BFL_Payments_Alt_Copilot_Chat_Participant_Guide.md` instead. The exercises are the same and no licence is required.
4. Practise the full 9-step flow in `Excel_To_PowerPoint.md`, from raw file to analysis, document and deck.
5. Use `Copilot_Notebooks_Guide.md` to bring everything into one Copilot Notebook, with no re-attaching and no 3-file limit.
6. Keep `copilot-pdf-playbook.md` for when a report needs to go out as a PDF.

## Requirements

- Microsoft 365 Copilot (Copilot Chat and Copilot in Excel and PowerPoint). Users with a basic licence can use Copilot Chat only, via `BFL_Payments_Alt_Copilot_Chat_Participant_Guide.md`.
- Access to Copilot Notebooks in the M365 Copilot app, for `Copilot_Notebooks_Guide.md`.
- The Excel files and the PDF uploaded to OneDrive, so they can be attached in Copilot Chat. BFL allows up to 3 attachments per prompt.

---

*Delivered by Technizer India | GenAI for Enterprise Teams*
