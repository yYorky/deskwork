# Example Builder Session — Fall Music Tour P&L

> This is an annotated walkthrough of what a full Deskwork builder session looks like.
> Use this as a reference before running your own session.
>
> **Task used**: Fall Music Tour P&L (from the GDPval benchmark)
> **Model used**: ChatGPT 5.4 Think Deeper
> **Reference file**: `Fall Music Tour Ref File.xlsx`

---

## Step 1 — Set up the chat

1. Open a new ChatGPT chat. Select **5.4 Think Deeper** as the model.
2. Paste the full contents of `builder-prompt.md` as your first message.
3. Upload `Fall Music Tour Ref File.xlsx`.
4. After the file upload, write your task brief (see below).

**Your task brief** (2–3 sentences is enough):

> I need to produce a profit and loss report for a client's 2024 Fall Music Tour. The report is for production company executives and covers October 2024 revenue and costs. As-of date is December 31, 2024.

---

## Step 2 — The LLM reads the files and asks clarifying questions

The LLM will scan the uploaded file, see what data is available, and ask only the questions it cannot already answer. A good response looks like this:

> **LLM**: I've reviewed the file. It contains three sheets: income and costs tracked by the Tour Manager, withholding tax assumptions by country, and costs tracked by the Production Company. I can see revenue data by city/country in USD and cost line items from both sources.
>
> A few things I need to confirm before writing the system prompt:
>
> 1. **Output structure**: The file separates Tour Manager and Production Company data. Should the P&L show these as separate columns (Tour Manager | Production Company | Total Combined), or should they be merged?
> 2. **Expense categories**: The costs include Band & Crew, Hotels, and several "Other" items (Agency Commission, Insurance, Private Jet, etc.). Should these be rolled up into broad categories (e.g. Band and Crew / Hotel & Restaurants / Other Tour Costs / Other Travel Costs), or shown as individual line items?
> 3. **Revenue presentation**: Should each tour stop be shown as a separate line item with its withholding tax breakdown visible, or just the net revenue per stop?
> 4. **File delivery**: Should the output be a downloadable `.xlsx` file?

> **You**: Separate columns for Tour Manager and Production Company with a Total Combined column. Roll up into the four broad categories you mentioned. Show each tour stop as a line item with withholding detail visible. Yes, downloadable `.xlsx`.

---

## Step 3 — The LLM generates the system_prompt.md

After your answers, the LLM produces the `system_prompt.md` in a fenced code block. Copy the content between the fences and save it as:
- `benchmarks/gpt-5/music-tour-pl/system_prompt.md`
- `deskwork-kit/examples/music-tour-pl/system_prompt.md`

A well-generated system prompt will have all five sections clearly populated — not generic placeholders, but specific details derived from the file (exact sheet names, the four expense categories, the withholding rates by country, the as-of date).

---

## Step 4 — What to check before using the system_prompt.md

Before moving to Chat 2 (the execution run), verify the generated system prompt:

- [ ] **Section 1 (Role)** names the correct task and audience (production company executives)
- [ ] **Section 2 (Output spec)** specifies `.xlsx`, the three-column layout, the four expense categories, "As of 12/31/2024" in the header
- [ ] **Section 3 (Reference file index)** names all three sheets and what each contains
- [ ] **Section 4 (Quality rubric)** includes: withholding rates per country (UK 20%, France 15%, Spain 24%, Germany 15.825%), currency in USD, foot check, cross check
- [ ] **Section 5 (Self-verification)** includes a file delivery check and at least one calculation reconciliation check

If any section is vague or missing a key detail, ask the LLM to revise that section before proceeding.

---

## Step 5 — Start Chat 2 (the execution run)

Once the system prompt looks right:

1. Open a **new** chat — do not continue Chat 1.
2. Paste the system prompt as the first message (or as the system prompt if the interface supports it).
3. Upload `Fall Music Tour Ref File.xlsx` again.
4. Send the task prompt verbatim from `benchmarks/tasks/music-tour-pl/prompt.md`.
5. The LLM should produce a downloadable `.xlsx` file. Download it and save to `benchmarks/gpt-5/music-tour-pl/output/`.

---

## Why the two-chat split matters

Chat 1 is noisy — it contains your brief, back-and-forth questions, and the generation of the system prompt. All of that context would distract the model in Chat 2 from just executing the task cleanly.

Starting Chat 2 fresh means the model sees only: a precise system prompt, the reference files, and the task. This is structurally equivalent to how Claude Code reads a SKILL.md before starting work — the workflow is defined separately from the execution.
