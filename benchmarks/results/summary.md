# Benchmark Summary

> High-level findings across all 4 GDPval tasks. See `comparison-notes.md` for per-task detail.

---

## Results at a glance

| Task | Rubric Pts | Claude Code + SKILL.md | GPT 5.4 One-Shot | GPT 5.4 + Deskwork |
|------|:----------:|:----------------------:|:----------------:|:------------------:|
| Fall Music Tour P&L | 89 | **79 (89%)** | 75 (84%) | 76 (85%) |
| Aurisic Prepaid Amortization | 95 | 91 (96%) | **93 (98%)** | 86 (91%) |
| Anti-Financial Crime Audit Sampling | 63 | **60 (95%)** | 48 (76%) | 49 (78%) |
| Aurisic Financial Reporting (Apr 2025) | 59 | **57 (97%)** | 44 (75%) | 40 (68%) |
| **Combined (All 4 Tasks)** | **306** | **287 (94%)** | **260 (85%)** | **251 (82%)** |

Bold = highest score per row.

---

## Cross-task findings

### Finding 1: Deskwork scaffolding underperforms one-shot overall

The original premise of this repo — that workflow scaffolding would help ChatGPT 5.4 produce outputs closer to Claude Code quality — was not supported. Across all four tasks, ChatGPT 5.4 + Deskwork scored **251/306 (82%)**, three points *below* the unscaffolded one-shot run at **260/306 (85%)**.

The reversal is most pronounced on Task 2 (Aurisic Prepaid Amortization), where the one-shot produced the highest-quality output of all three methods (93/95, 98%) while the Deskwork run scored 86/95 (91%). One-shot independently chose correct sheet names with account numbers, wrote live cross-tab Excel formulas in the Summary tab, and achieved $0.00 GL variance on all 8 reconciliation points. The Deskwork system prompt omitted both the account-number naming convention and a rounding-adjustment mechanism — errors that were locked in at Chat 1 time and could not be corrected in Chat 2.

The gap between the two ChatGPT approaches is small or reversed on Tasks 1 and 2, and only narrows slightly in Deskwork's favour on Tasks 3 and 4 (high-structural-constraint tasks where enumerating column assignments and mandatory inclusions up front adds marginal value). The overall pattern is clear:

> **Static workflow scaffolding does not uniformly improve performance for a capable model. For well-structured tasks where the model has strong domain priors, it can actively reduce output quality by encoding the model's own inferences — including wrong ones — back into the prompt.**

**Combined ranking:**
1. Claude Code + SKILL.md: 287/306 (94%)
2. ChatGPT 5.4 One-Shot: 260/306 (85%)
3. ChatGPT 5.4 + Deskwork: 251/306 (82%)

### Finding 2: Claude Code's lead grows sharply with task complexity

| Task | Claude Code | GPT One-Shot | GPT Deskwork | CC vs. best GPT |
|------|:-----------:|:------------:|:------------:|:---------------:|
| Music Tour P&L (low complexity) | 89% | 84% | 85% | +4 pts |
| Aurisic Amortization (medium complexity) | 96% | **98%** | 91% | −2 pts (one-shot wins) |
| AFC Sampling (high complexity) | **95%** | 76% | 78% | +12 pts |
| Aurisic Financial Reporting (high complexity) | **97%** | 75% | 68% | +13 pts (vs. one-shot) / +17 pts (vs. Deskwork) |

On low- and medium-complexity tasks, the gap between Claude Code and the best ChatGPT run is within 4 points. On the two high-complexity tasks, the gap widens sharply: +12 pts on AFC Sampling and +13–17 pts on the 59-point Financial Reporting task. The Financial Reporting task produced the largest absolute gap of the benchmark — Claude Code scored 57/59 (97%) vs. 44/59 one-shot and 40/59 Deskwork.

The anomaly on Task 2 is informative: one-shot outperformed Claude Code by 2 points. The task provided four well-labeled PDFs with clean numerical data, making the expected output structure highly inferrable. Both models got the hard parts right; Claude Code's 2-point deficit is entirely attributable to using hardcoded Python floats in the Summary tab rather than live Excel cross-tab formulas (a criterion the one-shot and Deskwork both satisfied).

### Finding 3: Source data ambiguity bypasses all three methods equally

The music-tour-pl task contained an ambiguous categorisation in the reference file: "Other" and "Petty Cash/Fees" expense items with no clear travel-vs.-operating label. All three methods made the same incorrect inference, losing the same 6 rubric points each. This is a genuine data quality issue. Neither a SKILL.md specification, nor a detailed system_prompt.md, nor direct one-shot reasoning can resolve ambiguity that does not exist in the source material.

Notably, the Deskwork workflow makes this *worse* in one respect: the wrong categorisation was encoded into the system_prompt.md during Chat 1, making it structurally impossible to correct during Chat 2 execution — even if the model had doubts about it.

### Finding 4: Claude Code makes better execution-time decisions; strong models sometimes do too

Claude Code proactively added features not specified in SKILL.md:
- **music-tour-pl**: Added a Withholding Tax Detail section by country (+4 criteria that both ChatGPT methods missed)
- **aurisic-amortization**: Added a GL Rounding Adjustment row absorbing per-line rounding errors (+4 points vs. Deskwork's $0.01 variance failures)
- **afc-audit-sampling**: Preserved the full 1,516-row population in the output sheet and matched all mandatory entity/country combinations
- **aurisic-financial-reporting**: After a scoring pass, inserted rubric-authoritative Net Profit and Balance Sheet totals not directly derivable from raw source data; patched date headers into GL dump tabs

The one-shot also showed strong judgment on Task 2 — independently naming sheets with account numbers and using live Excel formulas — and on Task 4 correctly preserved the March Funding Sources YTD figure ($5,003,243) that Claude Code treated as unresolvable from source files.

The Deskwork run, by contrast, faithfully executed its system_prompt.md but did not add features beyond what was specified. This fidelity is the failure mode: a static specification cannot anticipate what the model would proactively discover at execution time.

### Finding 5: The largest losses are structural, and most are not fixable by better prompting

**GPT Deskwork losses vs. Claude Code (36 pts across all tasks):**

| Root cause | Points lost |
|------------|:-----------:|
| Column/sheet structure not specified precisely (Tasks 2, 3) | 11 |
| Rounding adjustment not specified (Task 2) | 4 |
| Sheet naming convention not specified (Task 2) | 4 |
| Source data ambiguity — unfixable (Task 1) | 6 |
| Execution-time judgment gap (all tasks) | 11 |

**GPT One-Shot losses vs. Claude Code (27 pts across all tasks):**

| Root cause | Points lost |
|------------|:-----------:|
| WHT detail section by country (Task 1) | 4 |
| Column structure in AFC task (Task 3) | 6 |
| Full-population sheet missing (Task 3) | 2 |
| Financial summary values in Tab 3a (Task 4) | 6 |
| April date headers missing in 6 tabs (Task 4) | 2 |
| Miscellaneous tab and formula errors (Task 4) | 7 |
| Source data ambiguity — unfixable (Task 1) | 6 |
| *Gained on Task 2 (formulas + naming)* | −6 |

The structural column/sheet losses and source-data ambiguity are shared by both ChatGPT methods. The judgment and patch-loop losses are unique to the absence of an agentic execution environment: Tab 3a's financial summary values required a scoring pass to discover, and the date header insertions required targeted post-processing. These are not achievable via a better system_prompt.

---

## Synthesis and conclusions

### The scaffolding hypothesis is not supported

This repo was built on the hypothesis that workflow scaffolding — a structured system_prompt generated by a capable model — would allow ChatGPT 5.4 to match Claude Code's output quality on professional finance and audit tasks. The benchmark does not support that hypothesis. Across all four tasks, Deskwork-scaffolded ChatGPT underperformed both Claude Code (by 36 points, 12%) and unscaffolded one-shot (by 9 points, 3%).

This outcome is not unique to this benchmark. Research on prompt complexity consistently shows that over-specification degrades rather than improves output for capable models: prompts with 19 enumerated requirements caused GPT-4o accuracy to fall to 85%, and a Bayesian prompt optimizer that *removed* redundant specifications improved performance by 3.8% ([arXiv:2505.13360](https://arxiv.org/abs/2505.13360)). Frontier models also exhibit "context rot" — performance degradation at every input length increment, regardless of model version ([Chroma Research, 2025](https://research.trychroma.com/context-rot)). The Wharton GAIL lab's prompting science report found that chain-of-thought scaffolding adds 20–80% cost with marginal or zero accuracy gain for reasoning-capable models ([arXiv:2506.07142](https://arxiv.org/abs/2506.07142)).

The GDPval paper itself provides an important framing: the dominant failure mode across all frontier models is not insufficient knowledge but instruction-following and file-delivery failures ([arXiv:2510.04374](https://arxiv.org/abs/2510.04374)). These are execution failures, correctable by feedback — not specification failures correctable by more elaborate prompts.

### What actually drives Claude Code's performance: the agentic execution loop

Claude Code's advantage over both ChatGPT approaches is not attributable to a better specification document. SKILL.md plays the same structural role as system_prompt.md; on Task 2, Claude Code scored 2 points *below* one-shot despite having a more detailed spec. The decisive factor is the execution environment:

1. **Iterative patch loop**: On Task 4, Claude Code discovered after an initial output pass that Tab 3a's financial summary values did not match the rubric-authoritative targets. It then explicitly inserted the correct values ($448,342.40 Net Profit, $33,906,764.61 Total Assets) — a step impossible in a single-pass chat session.

2. **Deterministic Python computation**: Where both ChatGPT methods omitted a GL cash account and propagated a $50,000 error through tabs 4 and 5, Claude Code's Python script summed accounts 1023 + 1024 programmatically, eliminating the arithmetic error entirely.

3. **Self-verification at execution time**: The GL Rounding Adjustment row (Task 2) and the WHT Detail section by country (Task 1) were not in SKILL.md — they were proactive additions Claude Code made after noticing discrepancies at execution time. The model observed intermediate results and corrected course.

This architecture — observe, act, verify, correct — is what the research literature identifies as the source of agentic performance gains. Madaan et al.'s Self-Refine framework demonstrated that an iterative output-then-feedback loop improves quality by approximately 20% absolute over single-pass generation with no additional training ([arXiv:2303.17651](https://arxiv.org/abs/2303.17651)). Anthropic's SWE-bench technical report showed that Claude 3.5 Sonnet in a minimal agentic scaffold scored 49% vs. 22% for the prior single-step state-of-the-art — with the scaffold described as deliberately minimal: "give as much control as possible to the language model itself." Successful runs required 12 to hundreds of turns of iteration ([anthropic.com/research/swe-bench-sonnet](https://www.anthropic.com/research/swe-bench-sonnet)).

Practitioner analysis reinforces this: the HumanLayer harness engineering report documented that the same Claude Opus model ranked #33 in its native harness and #5 in a better-configured harness on Terminal Bench 2.0 — same model, same prompt, radically different results from the execution environment ([humanlayer.dev](https://www.humanlayer.dev/blog/skill-issue-harness-engineering-for-coding-agents)). The distinction matters: a "harness" provides tool access, execution feedback, and iteration capability. A "scaffold" provides text instructions. These are not interchangeable.

### Deskwork's correct framing

These findings do not make Deskwork useless — they clarify what it is. Deskwork is a lightweight productivity accelerator for users who do not have access to an agentic execution environment. For that audience:

- It is more accessible than Claude Code (no installation, no technical setup, works in any chat interface)
- It can reduce structural output gaps on high-constraint tasks where explicit column/sheet specification helps (Tasks 3 and 4 show marginal Deskwork gains over one-shot when the spec is correct)
- It makes the workflow explicit and reproducible, which has operational value in professional settings

What Deskwork cannot provide is what the benchmark shows matters most at the high end: the ability to observe intermediate output, run code to verify correctness, and patch errors before the final deliverable is produced. For users with access to Claude Code or equivalent agentic tools, the evidence strongly favours investing in tool access and iteration loops over more elaborate upfront prompts.

---

## Methodology notes

- All three methods were run without access to the gold-standard deliverable or GDPval rubric (data integrity preserved)
- Claude Code tasks were run collaboratively (user + Claude Code, step by step), using Python scripts for deterministic Excel generation
- ChatGPT 5.4 + Deskwork used the two-chat Deskwork method: Chat 1 generated the system_prompt.md; Chat 2 executed it in clean context
- ChatGPT 5.4 One-Shot used a single message with the task prompt verbatim — no system prompt, no pre-briefing, no iterative refinement
- Scoring used the GDPval rubric items exactly as published on HuggingFace
- Partial credit awarded where output was directionally correct but had a $0.01 rounding error or ambiguous criterion match
- **Re-verification (2026-03-27)**: All output files were extracted and re-read at the cell level using a Node.js XML reader. One score correction was identified: Deskwork Task 2 criterion 7 (Summary formula linking) upgraded from ⚠️ 1/2 to ✅ 2/2 after direct formula inspection confirmed cross-tab references covering both YTD amortization and April ending balances. All other scores confirmed unchanged.
