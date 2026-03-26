# Deskwork

> A portable workflow kit that closes the gap between one-shot LLM chat and Claude Code-level output quality on professional office tasks.

**Status**: Work in progress. Benchmark results being compiled.

---

## What is Deskwork?

Deskwork demonstrates that the dominant failure modes on real-world professional tasks are **workflow problems, not capability problems**.

Using 3 tasks from the [GDPval benchmark](https://arxiv.org/abs/2510.04374) (OpenAI, 2025), this project shows:
1. Claude Code + SKILL.md solves tasks that one-shot models fail at
2. The Deskwork portable method replicates comparable results on ChatGPT 5.4 Think Deeper — no native agentic tooling required, just structured prompts and file uploads

---

## Repository Structure

```
deskwork/
├── benchmarks/          # Performance comparison (the proof)
│   ├── tasks/           # GDPval task inputs (prompts + reference files)
│   ├── claude-code/     # Claude Code + SKILL.md method outputs
│   ├── gpt-5/           # ChatGPT 5.4 Think Deeper + Deskwork method outputs
│   └── results/         # Side-by-side comparison notes and summary
│
└── deskwork-kit/        # The product (user-facing)
    ├── generate/        # Builder prompt to generate your own system_prompt.md
    └── examples/        # Example generated system prompts and outputs
```

---

## Architecture

<!-- Mermaid diagram added in Stage 10 -->
*Architecture diagram (Claude Cowork/Code + SKILL.md vs ChatGPT 5.4 + Deskwork) coming soon.*

---

## Benchmark Results

<!-- Results table added in Stage 10 -->
*Results summary coming soon.*

---

## The Deskwork Kit

See [deskwork-kit/README.md](deskwork-kit/README.md) for instructions on using the kit to generate a custom workflow for your own tasks.
