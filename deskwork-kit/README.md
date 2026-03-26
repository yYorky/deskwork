# Deskwork Kit

> Get Claude Code-level output quality on professional tasks — using any LLM, just file uploads and a structured prompt.

**Who this is for**: Finance professionals, auditors, consultants — anyone who produces structured deliverables (Excel models, workpapers, reports) from reference documents.

---

## How it works

The kit uses a two-chat method:

**Chat 1 — Briefing** (generates your workflow)
1. Open a new chat with any capable LLM (ChatGPT, Claude, Gemini, etc.)
2. Paste the contents of [`generate/builder-prompt.md`](generate/builder-prompt.md) as your first message
3. Upload your reference files and write a 2–3 sentence brief: what you need to produce
4. The LLM will ask a few targeted clarifying questions
5. It will generate a complete `system_prompt.md` tailored to your task

**Chat 2 — Execution** (produces your deliverable)
1. Open a **new chat** — clean context, no noise from Chat 1
2. Paste the generated `system_prompt.md` as your system prompt
3. Upload your reference files again
4. Ask for the deliverable
5. The LLM produces the file — already verified against your quality criteria

---

## Why two chats?

Chat 1 is the *briefing* — gathering context and generating the workflow. Chat 2 is the *execution* — clean context, just the task. This mirrors how Claude Code's SKILL.md works: the skill is defined separately from task execution.

---

## Examples

See the [`examples/`](examples/) folder for complete worked examples:
- [music-tour-pl](examples/music-tour-pl/) — Fall Music Tour P&L (Excel financial model)
- [afc-audit-sampling](examples/afc-audit-sampling/) — Anti-Financial Crime Audit Sampling (workpaper)
