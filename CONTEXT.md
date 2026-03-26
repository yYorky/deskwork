# Deskwork — Project Context

> Read this file first. It contains everything needed to understand the project goal, structure, design decisions, and what to build next.

---

## What is Deskwork?

Deskwork is a **portable workflow kit** that enables any professional to get Claude Code / Claude Cowork-level output quality on office tasks — using any frontier LLM (e.g. GPT-5, Gemini) via a standard chat interface with file uploads.

The core insight: the dominant failure modes on real-world professional tasks are **workflow problems, not capability problems**. The GDPval benchmark paper (OpenAI, 2025) confirms this — models most often lose to human experts due to instruction-following gaps, failed file delivery, and lost context across multi-file inputs. Not because the model lacks intelligence.

Deskwork solves this by making the workflow layer explicit, portable, and model-agnostic.

---

## Origin & Motivation

This project was conceived as a portfolio piece to showcase Applied Technical + Business usecases. The approach:

1. Take specific tasks from the **GDPval benchmark** (OpenAI's real-world professional task evaluation dataset, 220 tasks open-sourced on HuggingFace)
2. Show that **Claude Code with SKILL.md** can solve tasks that one-shot models fail at
3. Show that the **Deskwork portable method** replicates comparable results on GPT-5.4 (or any LLM) without any native agentic tooling — just structured documents uploaded via chat

The key claim: it is a **workflow gap**, not a capability gap. Proper scaffolding closes most of the delta.

### Why it's well-timed
- No one has done this with Claude Cowork/Code specifically — existing leaderboards use agentic shell access, not desktop file workflows
- The GDPval paper explicitly names one-shot limitations as a gap it plans to fix in future versions
- The paper's own prompt-tuning experiments showed simple scaffolding improvements (self-checking, rendering files as images) boosted win rates by 5+ percentage points
- There is no equivalent to Claude's SKILL.md / Cowork architecture for OpenAI or other LLMs — Deskwork fills that gap

---

## The GDPval Paper — Key Facts

- **Full citation**: "GDPval: Evaluating AI Model Performance on Real-World Economically Valuable Tasks", Patwardhan et al., OpenAI, arXiv:2510.04374v1, Oct 2025
- **What it is**: A benchmark of 1,320 tasks (220 open-sourced) across 44 occupations and 9 US GDP sectors
- **Tasks are based on actual work product** from industry professionals averaging 14 years experience
- **Primary metric**: Head-to-head human expert pairwise comparison (win rate)
- **Best model**: Claude Opus 4.1 at 47.6% wins+ties vs human expert baseline
- **Key finding on failures**: Claude, Grok, and Gemini most often lost due to **instruction-following failures**. Gemini and Grok frequently promised but failed to deliver files, ignored reference data, or used wrong formats
- **Key finding on scaffolding**: Prompt-tuning GPT-5 to self-check deliverables, render files as images, and avoid formatting errors improved win rates by **5 percentage points**
- **One-shot limitation**: Tasks are precisely-specified and one-shot, not interactive. Paper acknowledges this as a gap to fix in future versions
- **File complexity**: Tasks require parsing up to 17 reference files in the gold subset (38 in full set)

### The three target tasks (all Accountants & Auditors, Professional/Scientific/Technical Services sector)

These were chosen to match a CA (Chartered Accountant) background and to specifically demonstrate workflow advantages:

| Task | Why it's a good test case |
|------|--------------------------|
| **Fall Music Tour P&L** | Model explicitly failed to produce the Excel file despite correct analysis. File delivery failure — directly fixed by Deskwork's output spec enforcement |
| **Aurisic Prepaid Amortization** | 6 reference files (PDFs + Excel), GL reconciliation across months. High context complexity — directly fixed by Deskwork's reference file index |
| **Anti-Financial Crime Audit Sampling** | 30+ rubric checkpoints. Demonstrates iterative self-verification hitting every criterion including edge cases one-shot models miss |

---

## Repo Structure

```
deskwork/
├── README.md                          # Project overview + benchmark results summary
├── CONTEXT.md                         # This file — full project context for Claude Code
│
├── benchmarks/                        # Section 1: Performance comparison (the proof)
│   ├── tasks/                         # Shared GDPval task inputs
│   │   ├── music-tour-pl/
│   │   │   ├── prompt.md              # Raw GDPval task prompt
│   │   │   └── reference-files/       # All reference files for the task
│   │   ├── aurisic-amortization/
│   │   │   ├── prompt.md
│   │   │   └── reference-files/
│   │   └── afc-audit-sampling/
│   │       ├── prompt.md
│   │       └── reference-files/
│   │
│   ├── claude-code/                   # Claude Code + SKILL.md method
│   │   ├── SKILL.md                   # The skill definition used
│   │   ├── music-tour-pl/
│   │   │   ├── instructions.md        # Exact prompt used
│   │   │   └── output/                # Resulting deliverable file(s)
│   │   ├── aurisic-amortization/
│   │   │   ├── instructions.md
│   │   │   └── output/
│   │   └── afc-audit-sampling/
│   │       ├── instructions.md
│   │       └── output/
│   │
│   ├── gpt-5/                         # GPT-5 + Deskwork portable method
│   │   ├── music-tour-pl/
│   │   │   ├── system_prompt.md       # The generated system prompt used
│   │   │   ├── instructions.md        # What was typed into the chat
│   │   │   └── output/                # Resulting deliverable file(s)
│   │   ├── aurisic-amortization/
│   │   │   ├── system_prompt.md
│   │   │   ├── instructions.md
│   │   │   └── output/
│   │   └── afc-audit-sampling/
│   │       ├── system_prompt.md
│   │       ├── instructions.md
│   │       └── output/
│   │
│   └── results/
│       ├── comparison-notes.md        # Side-by-side qualitative notes per task
│       └── summary.md                 # High-level findings (feeds into README)
│
└── deskwork-kit/                      # Section 2: The product (user-facing)
    ├── README.md                      # How to use the kit — user instructions
    ├── generate/
    │   ├── builder-prompt.md          # The prompt a user pastes to generate their system_prompt.md
    │   └── example-session.md         # Annotated example of a full generation session
    └── examples/
        ├── music-tour-pl/
        │   ├── system_prompt.md       # Example generated system prompt
        │   └── output/                # Example deliverable
        └── afc-audit-sampling/
            ├── system_prompt.md
            └── output/
```

---

## The Two Sections Explained

### Section 1 — Benchmarks (the proof)

This section exists to demonstrate the performance claim with reproducible evidence. A reader should be able to:
1. Read the task prompt and reference files
2. See exactly what was given to each method (instructions + system prompt)
3. See the resulting deliverable
4. Read the comparison notes explaining where each method succeeded or failed

**Claude Code method**: Uses a SKILL.md file that defines the output format, quality bar, and self-verification steps. Claude Code has native file creation and persistent file access — it can read all reference files, produce actual xlsx/pdf deliverables, and verify its own output.

**GPT-5 Deskwork method**: Uses the portable system_prompt.md (generated by the kit in Section 2). No native agentic tooling — just the system prompt, reference files uploaded as attachments, and GPT-5's code interpreter for file creation. The system_prompt.md encodes everything the SKILL.md does implicitly.

### Section 2 — Deskwork Kit (the product)

This is what a user actually uses. The flow is:

1. User opens a new chat with any capable LLM
2. User pastes the `builder-prompt.md` as their first message
3. User uploads their reference files and writes a short brief (2-3 sentences) describing what they need
4. LLM reads the files and asks clarifying questions — extracting: expected deliverable file type, required columns/sheets/structure, which reference file contains what, quality criteria specific to the task
5. LLM generates a complete `system_prompt.md` tailored to the user's task
6. User opens a **new chat**, pastes the system_prompt.md as system context, uploads the reference files again, and requests the deliverable
7. LLM produces the deliverable file

**Key design principle**: The two-chat split is intentional. Chat 1 is the *briefing* — gathering context and generating the workflow. Chat 2 is the *execution* — clean context, no noise, just the task. This mirrors how Claude's SKILL.md works: the skill is defined separately from the task execution.

---

## What the system_prompt.md Must Contain

This is the core artifact of the Deskwork method. Every generated system_prompt.md should include:

1. **Output spec** — exact file type, structure (sheet names, column headers, formatting conventions)
2. **Reference file index** — explicit map of which file contains what, and which rows/sections are relevant
3. **Quality rubric** — the specific checkpoints for this task type (e.g. for a P&L: revenue matches reference, all cost categories present, totals reconcile, formatting is professional)
4. **Self-verification protocol** — before marking complete, the model must: confirm the file exists and is not empty, check all rubric items are addressed, verify calculations reconcile, confirm no placeholder values remain
5. **File delivery instruction** — explicit instruction to use whatever file creation mechanism is available (code interpreter, canvas, artifact panel) and confirm the file is downloadable before finishing

The self-verification protocol is the single highest-leverage addition. The GDPval paper's prompt-tuning experiment recovered 5 points of win rate purely from adding self-checking steps.

---

## SKILL.md Design (for Claude Code section)

Claude Code's SKILL.md pattern works as follows:
- A markdown file placed in `/mnt/skills/` or referenced at the start of a session
- Defines: what the skill produces, the technical approach, quality standards, and verification steps
- Claude Code reads it at the start of the task and follows it throughout

For the benchmark section, we need a SKILL.md per task type (xlsx financial model, audit sampling workpaper) that defines:
- The expected output format in detail
- The reference file reading strategy (how to extract data from each file type)
- Task-specific quality checks
- The self-verification checklist

---

## Tone and Framing

- **Audience**: Finance professionals, auditors, consultants — people who do office work, not developers
- **Voice**: Practitioner-facing, clear, no jargon. "Upload your files and get a working deliverable" not "implement an agentic scaffold"
- **Claim**: Deskwork gives you Claude Code-level output quality on professional tasks, on any LLM, with just file uploads and a structured prompt
- **Not claiming**: That GPT-5 + Deskwork beats Claude Code. The claim is *comparable results* — good enough that the workflow gap is closed even without native tooling

---

## What to Build Next (suggested order)

1. **Set up the repo** with the folder structure above (empty folders + placeholder READMEs)
2. **Write the SKILL.md** for the xlsx financial task type (covers music-tour-pl and aurisic-amortization)
3. **Run the Claude Code benchmark** on music-tour-pl first (clearest failure mode, clearest fix)
4. **Write the builder-prompt.md** for the deskwork-kit generate flow
5. **Generate a system_prompt.md** for music-tour-pl using the builder
6. **Run the GPT-5 benchmark** on music-tour-pl using that system_prompt.md
7. **Write comparison-notes.md** for music-tour-pl
8. Repeat steps 3-7 for the remaining two tasks
9. **Write the README.md** summarising results and linking to the kit

---

## Reference Links

- GDPval paper: https://arxiv.org/abs/2510.04374
- GDPval HuggingFace dataset: https://huggingface.co/datasets/openai/gdpval
- GDPval automated grader: https://evals.openai.com
- Claude file creation announcement: https://www.anthropic.com/news/create-files

---

## Notes for Claude Code

- The `/benchmarks/tasks/` reference files will need to be sourced from the GDPval HuggingFace dataset — they are not included in this repo yet
- When running the Claude Code benchmark tasks, use the actual SKILL.md pattern (read the skill file first, then execute) — do not shortcut this, as the point is to demonstrate the method faithfully
- The GPT-5 benchmark results will be run manually (outside Claude Code) and outputs pasted/uploaded into the repo
- When writing the builder-prompt.md, the clarifying questions the LLM asks are the most important design decision — they should extract exactly what is needed to write a tight system_prompt.md, nothing more
- Keep all user-facing copy (deskwork-kit/README.md, builder-prompt.md) simple enough that a non-technical finance professional can follow it without help
