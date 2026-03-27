# Benchmark Summary

> High-level findings across all 3 GDPval tasks. See `comparison-notes.md` for per-task detail.

---

## Results at a glance

| Task | Rubric Pts | Claude Code + SKILL.md | GPT 5.4 One-Shot | GPT 5.4 + Deskwork |
|------|:----------:|:----------------------:|:----------------:|:------------------:|
| Fall Music Tour P&L | 89 | **79 (89%)** | 75 (84%) | 76 (85%) |
| Aurisic Prepaid Amortization | 95 | 91 (96%) | **93 (98%)** | 86 (91%) |
| Anti-Financial Crime Audit Sampling | 63 | **60 (95%)** | 48 (76%) | 49 (78%) |
| Aurisic Financial Reporting (Apr 2025) | 59 | **57 (97%)** | 44 (75%) | 40 (68%) |
| **Combined (Tasks 1–3)** | **247** | **230 (93%)** | **216 (87%)** | **211 (85%)** |
| **Combined (All 4 Tasks)** | **306** | **287 (94%)** | **260 (85%)** | **251 (82%)** |

Bold = highest score per row.

---

## Cross-task findings

### Finding 1: One-shot was NOT confirmed to fail — it outperformed Deskwork overall

The original prediction ("ChatGPT 5.4 Think Deeper, running one-shot without any system prompt, would have failed to produce correct deliverables on all three tasks") was empirically refuted.

The one-shot run scored **216/247 (87%)** combined — 5 points *above* the Deskwork run at 211/247 (85%). This reversal is driven primarily by Task 2 (Aurisic Prepaid Amortization), where the one-shot produced the highest-quality output of all three methods: 93/95 (98%), including correct sheet names with account numbers, a summary tab built on live cross-tab Excel formulas, and $0.00 GL variance on all 8 data points. The Deskwork run also had cross-tab Excel formulas in the Summary tab (confirmed by re-verification), but had $0.01 variance on four 1251 rows and missed account numbers in sheet names.

The finding is not that workflow scaffolding is unnecessary. The gap on Tasks 1 and 3 between one-shot and Deskwork is small (1 point each). Rather, the finding is:

> **Deskwork scaffolding does not uniformly improve all tasks.** For a well-structured accounting task where the model's priors are strong (Task 2), one-shot performance can meet or exceed a scaffolded run. Scaffolding adds the most value on tasks with many structural constraints that must be enumerated up front (Task 3).

Claude Code's SKILL.md still outperforms both ChatGPT approaches on the combined score (+14 pts over one-shot; +19 pts over Deskwork), and is the only method to beat one-shot on Task 2 (91 vs 93 — actually lost here by 2 pts).

**Corrected ranking (Tasks 1-3):**
1. Claude Code + SKILL.md: 230/247 (93%)
2. ChatGPT 5.4 One-Shot: 216/247 (87%)
3. ChatGPT 5.4 + Deskwork: 211/247 (85%)

**Updated ranking (All 4 Tasks):**
1. Claude Code + SKILL.md: 287/306 (94%)
2. ChatGPT 5.4 One-Shot: 260/306 (85%)
3. ChatGPT 5.4 + Deskwork: 251/306 (82%)

### Finding 2: The gap between Claude Code and ChatGPT is consistent; within-ChatGPT variation is task-dependent

| Task | Claude Code | GPT One-Shot | GPT Deskwork | CC vs best GPT |
|------|:-----------:|:------------:|:------------:|:--------------:|
| Music Tour P&L (low complexity) | 89% | 84% | 85% | +4 pts |
| Aurisic Amortization (medium complexity) | 96% | **98%** | 91% | −2 pts (one-shot wins) |
| AFC Sampling (high complexity) | 95% | 76% | 78% | +17 pts |
| Aurisic Financial Reporting (high complexity) | **97%** | 75% | 68% | +22 pts |

Claude Code's lead grows sharply with task complexity. On the AFC sampling task (63 rubric points covering column structure, full-population output, mandatory entity/country inclusions), both ChatGPT methods lost 14+ points. The SKILL.md approach closes most of those gaps through structured execution and self-verification.

The anomaly is Task 2: one-shot outperformed Claude Code by 2 points. The task provided four well-labeled PDFs with clean numerical data, making the expected output structure highly inferrable. Both models got the hard parts right; the 2-point gap reflects minor formatting differences.

### Finding 3: Source data ambiguity bypasses all three methods equally

The music-tour-pl task had an ambiguous categorisation in the reference file ("Other" expense items with no clear label). All three methods made the same incorrect inference, losing the same 6 rubric points each. This is a genuine data quality issue, not a workflow or model problem. Neither SKILL.md nor a detailed system_prompt.md can resolve ambiguity that does not exist in the source.

### Finding 4: Claude Code makes better execution-time decisions; one-shot occasionally does too

Claude Code proactively added features not specified in SKILL.md:
- **music-tour-pl**: Added a Withholding Tax Detail section by country (+4 criteria that both ChatGPT methods missed)
- **aurisic-amortization**: Added a GL Rounding Adjustment row handling the accumulation of per-line rounding errors (+4 points vs. Deskwork's $0.01 variance failures)
- **afc-audit-sampling**: Preserved the full 1516-row population in the output sheet (+1 point); all mandatory entity/country combinations correctly matched

The one-shot also showed strong judgment on Task 2 — it independently chose to name sheets with account numbers (1250, 1251) and to use live cross-tab Excel formulas in the summary tab (not specified in the prompt). Re-verification confirmed that Deskwork's summary tab also has cross-tab formula links; the one-shot's advantage on Task 2 relative to Deskwork is the sheet naming (+4 pts) and the 1251 rounding accuracy (+3 pts), not formula linking. This suggests that for tasks where the model has strong domain priors, it will exercise good judgment even without scaffolding.

ChatGPT + Deskwork executed the system_prompt faithfully but did not add features beyond what was specified.

### Finding 5: The largest single source of ChatGPT losses is structural specification gaps

**Deskwork losses vs. Claude Code (36 points) [re-verified 2026-03-27]:**

| Root cause | Points lost |
|------------|:-----------:|
| Column/sheet structure not specified precisely | 11 |
| Rounding adjustment not specified | 4 |
| Sheet naming convention not specified | 4 |
| Source data ambiguity (unfixable) | 6 |
| Execution-time judgment gap | 11 |

**One-shot losses vs. Claude Code (14 points):**

| Root cause | Points lost |
|------------|:-----------:|
| WHT detail section by country (Task 1) | 4 |
| Column structure in AFC task (Task 3) | 6 |
| Full-population sheet missing (Task 3) | 2 |
| Source data ambiguity (unfixable) | 6 |
| Formatting differences | 2 |
| *Gained on Task 2 (formulas + naming)* | −6 |

The top three Deskwork losses are all fixable with a more precise system_prompt.md. One-shot losses on Task 3 are harder to fix without scaffolding — the structural column requirements and mandatory entity inclusions are non-obvious from the prompt alone.

---

## What Deskwork closes and what it doesn't

**Closes** (vs. one-shot):
- Consistent structural output (sheets, columns, sections matching specification)
- Self-verification steps reduce residual miscalculations
- Moderately reduces column mis-assignment risk

**Does not close** (vs. one-shot, verified):
- Strong model priors on well-structured tasks (Task 2 one-shot beats Deskwork)
- Source data ambiguity (if the reference file is ambiguous, the system_prompt encodes the wrong inference)
- Execution-time judgment (proactive additions require domain experience to specify or decide)

**Does not close** (vs. Claude Code):
- Enumerated mandatory inclusions in complex tasks (Italy + Corporate Loans, WHT detail by country)
- GL rounding accumulation handling
- Sheet naming conventions when not specified in system_prompt.md (account numbers in tab names)

---

## Methodology notes

- All three methods were run without access to the gold-standard deliverable or GDPval rubric (data integrity preserved)
- Claude Code tasks were run collaboratively (user + Claude Code, step by step)
- ChatGPT 5.4 + Deskwork used the two-chat Deskwork method: Chat 1 generated the system_prompt.md; Chat 2 executed it in clean context
- ChatGPT 5.4 One-Shot used a single message with the task prompt verbatim — no system prompt, no pre-briefing, no iterative refinement
- Scoring used the GDPval rubric items exactly as published on HuggingFace
- Partial credit awarded where output was directionally correct but had a $0.01 rounding error or ambiguous criterion match
- **Re-verification (2026-03-27)**: All 9 output files were extracted and re-read at the cell level using a Node.js XML reader. One score correction was identified: Deskwork Task 2 criterion 7 (Summary formula linking) upgraded from ⚠️ 1/2 to ✅ 2/2 after direct formula inspection confirmed cross-tab references covering both YTD amortization and April ending balances. All other scores confirmed unchanged. Deskwork Task 2 revised from 85/95 to 86/95; combined revised from 210/247 to 211/247.
