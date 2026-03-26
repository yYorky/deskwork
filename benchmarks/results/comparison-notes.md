# Benchmark Comparison Notes

> Side-by-side qualitative analysis per task. Scored using the GDPval rubric for each task.
> Rubrics sourced from `benchmarks/tasks/*/rubric.md` — **NOT provided during execution** (data integrity preserved).

---

## Task 1: Fall Music Tour P&L

> Status: Complete. Both outputs scored.

### Task summary

Produce a profit and loss report for a client's 2024 Fall Music Tour, covering October 2024 revenue and costs. As-of date: December 31, 2024. Output is a formatted `.xlsx` workbook with a three-column layout (Tour Manager | Production Company | Total Combined). Revenue section shows 7 European tour stops line-by-line with foreign withholding tax applied per country. Expense section rolls up into 4 categories: Band and Crew, Other Tour Costs, Hotel & Restaurant, Other Travel Costs. Closes with Net Income summary. **Total possible: 89 points.**

---

### Rubric Scorecard

| # | Pts | Criterion | Claude Code | ChatGPT 5.4 |
|---|-----|-----------|:-----------:|:-----------:|
| 1 | +2 | Final deliverable is .xlsx format | ✅ | ✅ |
| 2 | +2 | Separate TM, PC, and Total Combined columns | ✅ | ✅ |
| 3 | +2 | Revenue table lists City and Country per tour stop | ✅ | ✅ |
| 4 | +2 | All revenue in USD; non-USD converted before summarization | ✅ | ✅ |
| 5 | +1 | Currency columns use USD formatting | ✅ | ✅ |
| 6 | +1 | No duplicate tour-stop rows | ✅ | ✅ |
| 7 | +2 | Show 1 — London, UK: Combined Gross = $230,754 | ✅ | ✅ |
| 8 | +2 | Show 2 — Paris, France: Combined Gross = $175,880 | ✅ | ✅ |
| 9 | +2 | Show 3 — Paris, France: Combined Gross = $168,432 | ✅ | ✅ |
| 10 | +2 | Show 4 — Barcelona, Spain: Combined Gross = $125,932 | ✅ | ✅ |
| 11 | +2 | Show 5 — Madrid, Spain: Combined Gross = $110,823 | ✅ | ✅ |
| 12 | +2 | Show 6 — Munich, Germany: Combined Gross = $99,117 | ✅ | ✅ |
| 13 | +2 | Show 7 — Berlin, Germany: Combined Gross = $132,812 | ✅ | ✅ |
| 14 | +2 | No revenue attributed to production company | ✅ | ✅ |
| 15 | +2 | WHT rates: UK 20%, France 15%, Spain 24%, Germany 15.825% | ✅ | ✅ |
| 16 | +2 | WHT Amount = rate × Combined Gross per row | ✅ | ✅ |
| 17 | +2 | Net Revenue = Combined Gross − WHT per row | ✅ | ✅ |
| 18 | +2 | Total Gross Revenue = $1,043,750 | ✅ | ✅ |
| 19 | +2 | Total WHT = $191,322 | ✅ | ✅ |
| 20 | +2 | Total Net Revenue = $852,428 | ✅ | ✅ |
| 21 | +1 | UK WHT total = $46,151 | ✅ | ❌ |
| 22 | +1 | France WHT total = $51,647 | ✅ | ❌ |
| 23 | +1 | Spain WHT total = $56,821 | ✅ | ❌ |
| 24 | +1 | Germany WHT total = $36,703 | ✅ | ❌ |
| 25 | +2 | Expense category: Band and Crew (Fees & Per Diem) | ✅ | ✅ |
| 26 | +2 | Expense category: Other Tour Costs | ✅ | ✅ |
| 27 | +2 | Expense category: Hotel & Restaurant | ✅ | ✅ |
| 28 | +2 | Expense category: Other Travel Costs | ✅ | ✅ |
| 29 | +1 | Band and Crew Combined = $106,160 | ✅ | ✅ |
| 30 | +1 | Band and Crew TM = $15,160 | ✅ | ✅ |
| 31 | +1 | Band and Crew PC = $91,000 | ✅ | ✅ |
| 32 | +1 | Other Tour Costs Combined = $136,837 | ❌ | ❌ |
| 33 | +1 | Other Tour Costs TM = $136,837 | ❌ | ❌ |
| 34 | +1 | Other Tour Costs PC = $0.00 | ❌ | ❌ |
| 35 | +1 | Hotel & Restaurant Combined = $126,298 | ✅ | ✅ |
| 36 | +1 | Hotel & Restaurant TM = $47,560 | ✅ | ✅ |
| 37 | +1 | Hotel & Restaurant PC = $78,738 | ✅ | ✅ |
| 38 | +1 | Other Travel Combined = $362,711 | ❌ | ❌ |
| 39 | +1 | Other Travel TM = $350,056 | ❌ | ❌ |
| 40 | +1 | Other Travel PC = $12,655 | ❌ | ❌ |
| 41 | +1 | Other Tour Costs: Agency Commission $114,813 + Insurance $22,024, TM | ✅ | ✅ |
| 42 | +1 | Hotel PC by city: London $14,232, Paris $22,296, Barcelona $8,168, Madrid $8,776, Munich $12,040, Berlin $13,226 | ✅ | ✅ |
| 43 | +1 | Hotel TM by city: London $8,388, Paris $15,653, Barcelona $5,445, Madrid $5,113, Munich $6,369, Berlin $6,592 | ✅ | ✅ |
| 44 | +1 | Other Travel TM: Private Jet $341,000, Transfer Cars $4,237, Other $4,819 | ❌ | ❌ |
| 45 | +1 | Other Travel PC: Petty Cash $8,000, Transfer Cards $2,976, Other $1,679 | ❌ | ❌ |
| 46 | +1 | Band and Crew: 10 members $91,000, PC | ✅ | ✅ |
| 47 | +1 | Band and Crew: Sound Technician $8,256, TM | ✅ | ✅ |
| 48 | +1 | Band and Crew: Tour Coordinator $6,904, TM | ✅ | ✅ |
| 49 | +2 | Total Combined Expenses = $732,006 | ✅ | ✅ |
| 50 | +1 | TM Total Expenses = $549,613 | ✅ | ✅ |
| 51 | +1 | PC Total Expenses = $182,393 | ✅ | ✅ |
| 52 | +2 | Net Income summary present (TM, PC, Total Combined) | ✅ | ✅ |
| 53 | +2 | Total Combined Net Income = $120,423 | ✅ | ✅ |
| 54 | +1 | TM Net Income = $302,816 | ✅ | ✅ |
| 55 | +1 | PC Net Income = −$182,393 (deficit) | ✅ | ✅ |
| 56 | +2 | NI = Total Net Revenue − Total Expenses | ✅ | ✅ |
| 57 | +1 | TM NI = TM Net Revenue − TM Expenses | ✅ | ✅ |
| 58 | +1 | PC NI = PC Net Revenue − PC Expenses | ✅ | ✅ |
| 59 | +5 | Overall formatting and style | ⚠️ 3/5 | ⚠️ 4/5 |

### Final scores

| | Claude Code + SKILL.md | ChatGPT 5.4 Think Deeper + Deskwork |
|--|:---:|:---:|
| **Score** | **79 / 89** | **76 / 89** |
| **Pct** | **89%** | **85%** |

---

### Claude Code + SKILL.md

**Output**: `benchmarks/claude-code/music-tour-pl/output/Fall_Music_Tour_PL_2024.xlsx` (7,438 bytes)
**Sheet structure**: Single sheet "P&L Statement"

**What succeeded**:
- All revenue and expense figures correct; gross, WHT, and net totals reconcile exactly
- WHT applied at correct per-country rates with a dedicated **Withholding Tax Detail** section showing country-level subtotals (UK $46,150.80, France $51,646.80, Spain $56,821.20, Germany $36,702.76) — earning criteria 21–24
- All four expense categories present; Hotel & Restaurant line items by city match exactly
- Band and Crew line items correct
- Net Income formula correct for TM, PC, and Combined
- `$#,##0.00` currency formatting on all numeric cells

**Issues**:
- **Expense miscategorisation — 6 criteria lost (rows 32–34, 38–40, 44–45)**: TM "Other" ($4,819) placed in _Other Tour Costs_ instead of _Other Travel Costs_. PC "Petty Cash" ($8,000) and "Fees" ($1,679) placed in _Other Tour Costs_ instead of _Other Travel Costs_. The rubric expects these in the travel bucket, shifting both subtotals off target.
- **Formatting (3/5)**: `$#,##0.00` applied correctly but no section shading, no bold category rows, and title contains a Unicode encoding artefact ("▒" character).

**Root cause of miscategorisation**: The reference file labels these items ambiguously — "Other" and "Petty Cash / Fees" without a clear travel vs. operating designation. SKILL.md specified output categories but did not include a line-item-to-category mapping, leaving the decision to inference at execution time.

---

### ChatGPT 5.4 Think Deeper + Deskwork

**Output**: `benchmarks/gpt-5/music-tour-pl/output/2024_Fall_Music_Tour_PnL_Report_AsOf_2024-12-31.xlsx`
**Sheet structure**: 3 sheets — "P&L Summary", "Revenue Detail", "Expense Mapping"

**What succeeded**:
- Multi-sheet structure is well-organised: summary on one tab, per-stop revenue detail on another, full expense line-item mapping on a third
- All revenue and expense totals reconcile correctly; gross, WHT, and net match exactly
- WHT rates applied correctly by country
- Expense line items correctly mapped to categories (with the same categorisation error as Claude Code — see Issues)
- Hotel & Restaurant by city exact ✅; Band and Crew by member exact ✅
- Net Income section with TM/PC/Combined all correct
- Professional formatting: clean headers, `$#,##0.00` on all cells, executive-ready layout
- Notes section at the bottom explicitly documents WHT rates and category mapping assumptions

**Issues**:
- **Same expense miscategorisation — 6 criteria lost (rows 32–34, 38–40, 44–45)**: The `system_prompt.md` generated in Chat 1 explicitly mapped "Other", "Petty Cash", and "Fees" to _Other Tour Costs_. Chat 2 faithfully executed this — the wrong mapping was codified into the workflow artefact itself.
- **No country-level WHT detail — 4 criteria lost (rows 21–24)**: The P&L Summary shows only a single total WHT row; the Revenue Detail has per-stop WHT but no country subtotals. Claude Code proactively added a WHT Detail section; ChatGPT's system prompt did not specify this, so it was not produced.
- **Formatting (4/5)**: Clean, executive-ready, clear title. Multi-sheet structure is genuinely useful (scorer's note: the rubric appears written with a single-sheet layout in mind, but the extra sheets are an improvement in practice).

---

### Key comparison

**Outcome**: Claude Code + SKILL.md scored higher (79 vs. 76) on this task. The hypothesis — that the Deskwork system_prompt would fix the categorisation error — was **not confirmed**.

**Why the hypothesis failed**:
The same miscategorisation appeared in both outputs because the error originates in the reference file, not in the workflow. The reference file labels TM "Other" and PC "Petty Cash / Fees" without indicating which travel bucket they belong to. Chat 1 (the briefing session in ChatGPT) made an incorrect inference and encoded it into the system_prompt as a definitive mapping rule. Chat 2 then executed that rule faithfully. The Deskwork method is only as good as the Chat 1 system prompt — if an ambiguity in the source data is resolved incorrectly at the briefing stage, it propagates into the deliverable.

**Where Claude Code had an edge**:
- Claude Code proactively added a **Withholding Tax Detail** section by country, earning 4 criteria the ChatGPT output missed entirely. This was not in the SKILL.md spec — it was added as a good-practice decision during execution.

**Where ChatGPT 5.4 had an edge**:
- Better formatting and multi-sheet organisation (4/5 vs 3/5 on the style criterion)
- Explicit notes section documenting assumptions
- Cleaner title without encoding artefacts

**What this tells us**:
A well-structured workflow (system_prompt.md) is necessary but not sufficient. When the source data is ambiguous, the system prompt must contain an explicit, correct category mapping — and getting that right requires either domain knowledge or a gold-standard reference. The Deskwork kit improves structure and reduces omission errors, but it cannot resolve genuine data ambiguity automatically. To close the remaining gap on this task, SKILL.md (or system_prompt.md) would need to explicitly specify: _"Other" (TM) → Other Travel Costs; "Petty Cash" and "Fees" (PC) → Other Travel Costs_.

---

## Task 2: Aurisic Prepaid Amortization

> Status: Pending (Stage 9)

<!-- Populated in Stage 9 -->

---

## Task 3: Anti-Financial Crime Audit Sampling

> Status: Pending (Stage 9)

<!-- Populated in Stage 9 -->
