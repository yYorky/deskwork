# Deskwork Kit

> Get professional-quality deliverables from any LLM — using only file uploads and a structured prompt.

**Who this is for**: Finance professionals, auditors, and consultants who produce structured deliverables (Excel models, workpapers, reports) from reference documents — and want consistently correct output without needing to prompt-engineer every time.

---

## The problem

Frontier LLMs are capable enough to produce a correct P&L, amortization schedule, or audit workpaper. But left to their own devices, they:

- Miss columns or sheets specified in the task
- Calculate something correctly but forget to put it in the file
- Produce output that _looks_ right but doesn't reconcile to the source data
- Declare the task done without checking their own work

These are **workflow problems**, not intelligence problems. Deskwork fixes them.

---

## How it works

The kit uses a **two-chat method**. One chat to build the workflow. One chat to run it.

### Chat 1 — Build your workflow (5–10 minutes)

1. Open a new chat with any capable LLM (ChatGPT 5.4, Claude, Gemini, etc.)
2. Paste the full contents of [`generate/builder-prompt.md`](generate/builder-prompt.md) as your **first message**
3. Upload your reference files
4. Write 2–3 sentences describing what you need to produce (see example below)
5. Answer the LLM's clarifying questions — it will ask about structure, columns, and quality criteria
6. The LLM generates a complete `system_prompt.md` for your task
7. Save that file — it is your reusable workflow for this task type

> **Example brief**: "I need to produce a prepaid amortization schedule for our finance team covering January through April. I have PDF invoices for two GL accounts and a GL trial balance to reconcile against. Output should be a three-tab Excel file."

### Chat 2 — Run the task (let the LLM do the work)

1. Open a **new chat** — clean context, no history from Chat 1
2. Paste the `system_prompt.md` contents as your first message (or system prompt if your interface supports it)
3. Upload your reference files again
4. Ask for the deliverable in one sentence: "Please produce the deliverable as specified."
5. Download the output file

---

## Why two chats?

Chat 1 is the **briefing** — gathering context and building the workflow. Chat 2 is the **execution** — clean context, no noise, just the task.

This matters because:
- Chat 1 produces a workflow document (`system_prompt.md`) that is reusable. Next time you run the same task type, skip Chat 1.
- Chat 2 has no context pollution from the Q&A session. The model reads the spec cold and executes it — which is how professional processes work.
- The `system_prompt.md` can be shared with a colleague who runs the same task on different data.

---

## What the generated system_prompt.md contains

Every `system_prompt.md` produced by the builder includes five sections:

1. **Output specification** — exact file type, sheet names, column headers, formatting rules
2. **Reference file index** — which file contains what, which sections are relevant, how to read each one
3. **Quality rubric** — the specific checks for this task (e.g. totals reconcile to source, all categories present, no placeholder values)
4. **Self-verification protocol** — before declaring done, the model must check every rubric item and confirm the file is downloadable
5. **File delivery instruction** — explicit instruction to use code interpreter / canvas and confirm the file exists

The self-verification step is the single highest-leverage component. It is what prevents the model from skipping a column, using the wrong formula, or producing output that cannot be opened.

---

## Examples

See the [`examples/`](examples/) folder for complete worked examples:

| Example | Task | Output |
|---------|------|--------|
| [music-tour-pl](examples/music-tour-pl/) | Fall Music Tour P&L — 7 European tour stops, WHT by country, TM/PC split | `.xlsx` P&L statement |
| [afc-audit-sampling](examples/afc-audit-sampling/) | Anti-Financial Crime Audit Sampling — 1,516-row population, attribute sampling, mandatory coverage | `.xlsx` sample workpaper |

Each example includes the generated `system_prompt.md` and the output file.

---

## Tips

- **Reuse across periods**: Once you have a `system_prompt.md` for a task type, run Chat 2 again with updated reference files. The workflow is the same; only the data changes.
- **Tweak before Chat 2**: If Chat 1 got something slightly wrong (e.g. wrong sheet name), edit the `system_prompt.md` before pasting it into Chat 2. You control the workflow document.
- **Be specific in your brief**: The LLM will ask clarifying questions, but the more you say upfront about required structure and quality targets, the tighter the output spec.
- **Upload all reference files in both chats**: Chat 2 cannot access Chat 1's files. Always re-upload.
