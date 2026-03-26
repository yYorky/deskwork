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

> Status: Complete. Both outputs scored.

### Task summary

Produce a prepaid amortization workbook for Aurisic covering January–April 2025. Source data: five PDFs — two GL trial balance reports (accounts 1250 and 1251) and three invoice PDFs. Output is a three-tab `.xlsx`: a Prepaid Summary tab with YTD figures and April 30 balances, plus two detail schedules (one per account) showing invoice-level straight-line amortization with monthly remaining balances. All balances must reconcile to the authoritative GL figures. **Total possible: 95 points.**

---

### Rubric Scorecard

| # | Pts | Criterion | Claude Code | ChatGPT 5.4 |
|---|-----|-----------|:-----------:|:-----------:|
| 1 | +2 | Delivers a single .xlsx workbook | ✅ | ✅ |
| 2 | +2 | Sheet titled "Prepaid Summary" | ✅ | ✅ |
| 3 | +2 | Sheet name includes account number 1250 | ✅ | ❌ |
| 4 | +2 | Sheet name includes account number 1251 | ✅ | ❌ |
| 5 | +1 | Prepaid Summary header includes company name Aurisic | ✅ | ✅ |
| 6 | +1 | Prepaid Summary states period up to April 30, 2025 | ✅ | ✅ |
| 7 | +2 | Summary totals linked by Excel formulas to detail tabs | ❌ | ⚠️ 1/2 |
| 8 | +2 | 1250 April GL balance = $559,377.61 | ✅ | ✅ |
| 9 | +2 | 1251 April GL balance = $369,976.70 | ✅ | ✅ |
| 10 | +2 | Total prepaid balance = $929,354.31 | ✅ | ⚠️ 1/2 |
| 11 | +2 | YTD amortization shown for each account | ✅ | ✅ |
| 12 | +1 | Description-and-amount layout in Summary | ✅ | ✅ |
| 13 | +2 | 1250 includes every invoice from all 4 PDF months | ✅ | ✅ |
| 14 | +2 | 1250 original amounts match source PDFs | ✅ | ✅ |
| 15 | +2 | 1250 amortization period = contract dates or 6-month default | ✅ | ✅ |
| 16 | +2 | 1250 monthly expense straight-line over documented term | ✅ | ✅ |
| 17 | +1 | 1250 schedule organized by vendor | ✅ | ✅ |
| 18 | +2 | 1250 includes: Original Amount, Amort Period, Monthly Expense, Remaining Balance | ✅ | ✅ |
| 19 | +1 | 1250 displays Jan, Feb, Mar, Apr 2025 monthly activity | ✅ | ✅ |
| 20 | +1 | 1250 amortization only in months within start–end period | ✅ | ✅ |
| 21 | +2 | 1250 Beg Balance + Adds − Amort = Ending Balance per line | ✅ | ✅ |
| 22 | +2 | 1250 totals: total amort = sum of line amort; total ending = sum of line balances | ✅ | ✅ |
| 23 | +2 | 1250 January ending balance = $518,934.86 | ✅ | ✅ |
| 24 | +2 | 1250 February ending balance = $426,673.13 | ✅ | ✅ |
| 25 | +2 | 1250 March ending balance = $473,655.55 | ✅ | ✅ |
| 26 | +2 | 1250 April ending balance = $559,377.61 | ✅ | ✅ |
| 27 | +1 | 1250 summary section shows monthly additions | ✅ | ✅ |
| 28 | +1 | 1250 summary section shows monthly amortization expense | ✅ | ✅ |
| 29 | +1 | 1250 summary section shows ending balances | ✅ | ✅ |
| 30 | +2 | 1250 GL Balance and Variance check; all variances = $0.00 | ✅ | ✅ |
| 31 | +1 | No negative amortization on 1250 | ✅ | ✅ |
| 32 | +1 | 1250 balance does not increase unless documented addition | ✅ | ✅ |
| 33 | +2 | 1251 includes every insurance invoice (no omissions) | ✅ | ✅ |
| 34 | +2 | 1251 original amounts match source PDF | ✅ | ✅ |
| 35 | +2 | 1251 amortization period = policy dates from PDF | ✅ | ✅ |
| 36 | +2 | 1251 Good Insurance: 1/1/2025–12/31/2025 straight-line | ✅ | ✅ |
| 37 | +2 | 1251 BCBS: monthly billing, amortization starts Feb 2025 | ✅ | ✅ |
| 38 | +1 | 1251 displays Jan, Feb, Mar, Apr 2025 monthly activity | ✅ | ✅ |
| 39 | +2 | 1251 Beg Balance + Adds − Amort = Ending Balance per line | ✅ | ✅ |
| 40 | +2 | 1251 totals reconcile per month | ✅ | ✅ |
| 41 | +2 | 1251 January ending balance = $506,657.98 | ✅ | ✅ |
| 42 | +2 | 1251 February ending balance = $461,097.55 | ✅ | ✅ |
| 43 | +2 | 1251 March ending balance = $415,537.13 | ✅ | ⚠️ 1/2 |
| 44 | +2 | 1251 April ending balance = $369,976.70 | ✅ | ⚠️ 1/2 |
| 45 | +1 | 1251 schedule organized by vendor | ✅ | ✅ |
| 46 | +2 | 1251 includes: Original Amount, Amort Period, Monthly Expense, Remaining Balance | ✅ | ✅ |
| 47 | +1 | 1251 summary section shows additions, amortization, and ending balances | ✅ | ✅ |
| 48 | +2 | 1251 GL Balance and Variance check; all variances = $0.00 | ✅ | ⚠️ 1/2 |
| 49 | +1 | No negative amortization on 1251 | ✅ | ✅ |
| 50 | +1 | 1251 balance does not increase unless documented addition | ✅ | ✅ |
| 51 | +1 | Expense classification uses COA account numbers | ✅ | ✅ |
| 52 | +2 | Schedules show Beg Balance, Additions, Amortization, Ending Balance each month | ✅ | ✅ |
| 53 | +1 | Currency formatted as dollars; dates in clear format | ✅ | ✅ |
| 54 | +1 | Comments column classifies nature of prepaid | ✅ | ✅ |
| 55 | +1 | Each detail tab has 17 columns or equivalent | ✅ | ✅ |
| 56 | +5 | Overall formatting and style | ⚠️ 3/5 | ⚠️ 4/5 |

### Final scores

| | Claude Code + SKILL.md | ChatGPT 5.4 Think Deeper + Deskwork |
|--|:---:|:---:|
| **Score** | **91 / 95** | **85 / 95** |
| **Pct** | **96%** | **89%** |

---

### Claude Code + SKILL.md

**Output**: `benchmarks/claude-code/aurisic-amortization/output/Aurisic_Prepaid_Amortization_Apr2025.xlsx` (3 tabs)
**Sheet structure**: Prepaid Summary · Prepaid Expenses #1250 · Prepaid Insurance #1251

**What succeeded**:
- All 8 GL reconciliation checks pass: 1250 and 1251 balances for all four months match targets exactly ($0.00 variance on every month)
- Rounding accumulation handled via a "GL Rounding Adjustment" row that absorbs the 1–5 cent per-month discrepancy that arises from individually rounding 40+ line balances
- All invoice data correctly extracted from 5 PDFs; 6-month default applied to all 1250 invoices (no contract dates on any PDF); BCBS monthly billing treatment correct (each Jan invoice covers Feb, etc.)
- Good Insurance 12-month straight-line applied correctly across 21 invoices
- Sheet names include account numbers 1250/1251 (criteria 3–4) — earned 4 points that ChatGPT lost
- Vendor grouping, monthly activity columns (Jan–Apr), summary section with GL reconciliation all present

**Issues**:
- **Formula linking (−2)**: Prepaid Summary totals are Python-computed floats written directly to cells — not Excel formulas referencing the detail tabs. The rubric requires live formula links.
- **Formatting (3/5)**: Professional dark-blue styling, color-coded GL variance rows. However: (a) no per-line monthly expense column in detail tabs (only remaining balance shown), limiting column count to 14 vs. 17; (b) Summary tab uses hardcoded values rather than cross-sheet formulas.

---

### ChatGPT 5.4 Think Deeper + Deskwork

**Output**: `benchmarks/gpt-5/aurisic-amortization/output/Aurisic_Prepaid_Amortization_Schedule_through_Apr_2025.xlsx` (3 tabs)
**Sheet structure**: Prepaid Summary · Prepaid Expenses · Prepaid Insurance

**What succeeded**:
- All 1250 GL balances reconcile exactly: $518,934.86 / $426,673.13 / $473,655.55 / $559,377.61 ✓
- 1251 January and February balances reconcile exactly
- Both detail tabs have 19 columns including per-line monthly amortization expense AND remaining balance
- Vendor-alphabetical sort, complete summary sections, correct BCBS and Good Insurance treatment
- Strong formatting (4/5): clean executive layout, 19-column structure, assumption notes in each tab
- Summary tab values appear formula-linked to detail tabs (could not confirm without formula inspection, but awarded 1/2 credit)

**Issues**:
- **Sheet names missing account numbers (−4)**: Sheet names are "Prepaid Expenses" and "Prepaid Insurance" without "1250"/"1251" — fails criteria 3 and 4. The system_prompt.md specified sheet names but did not include the account numbers in the naming convention.
- **1251 rounding ($0.01 on Mar/Apr) (−4)**: Monthly expense rounding for Good Insurance accumulates a $0.01 discrepancy in March and April ending balances ($415,537.12 vs. $415,537.13; $369,976.69 vs. $369,976.70). This also causes a $0.01 non-zero GL variance in both months (−1 on criterion 48) and a $0.01 error in the April total balance.
- **Total balance shows $929,354.30 (−1)**: The schedule-computed total shows $929,354.30 while the GL column correctly shows $929,354.31 — rubric awards only 1/2 credit.

**Root cause of rounding issue**: ChatGPT applied the same individual-line rounding approach without a GL reconciliation adjustment row. Claude Code explicitly addressed this with a "GL Rounding Adjustment" row — proactively solving a problem that the Deskwork system_prompt did not specify.

---

### Key comparison

**Outcome**: Claude Code + SKILL.md scored higher (91 vs. 85). The margin is explained by two structural differences:

**Where Claude Code had an edge**:
- Sheet names include account numbers (criteria 3–4): +4 points vs. ChatGPT's 0
- GL rounding fix: all 8 variances exactly $0.00; ChatGPT had $0.01 in two 1251 months: +4 points
- Both advantages trace to execution decisions made during the run, not pre-specified in SKILL.md

**Where ChatGPT 5.4 had an edge**:
- Formula linking: partial credit (1/2) vs. Claude Code's 0/2 — ChatGPT likely used formulas; Claude Code used hardcoded Python values
- Better formatting (4/5 vs. 3/5): 19-column detail tab (expense + balance per month); assumption notes; cleaner column width and alignment
- Total: −3 points vs. Claude Code on items where ChatGPT scored better

**What this tells us**:
The Deskwork system_prompt.md guided ChatGPT to a well-structured output covering nearly all criteria. However, two omissions in the system_prompt propagated to the output: (1) sheet name format not specified to include account numbers; (2) no rounding-adjustment requirement. Both are domain-specific details that require knowing the rubric in advance — which neither method had. Claude Code made a better execution-time decision on rounding (proactively adding an adjustment row) and named sheets to include account numbers naturally.

---

## Task 3: Anti-Financial Crime Audit Sampling

> Status: Complete. Both outputs scored.

### Task summary

Produce an audit sampling workpaper for an Anti-Financial Crime review. Population: 1,516 KRI rows across 4 divisions and 13 sub-divisions. Apply attribute sampling at 90% confidence, 10% tolerable deviation, with finite population correction. Output is a two-tab `.xlsx` ("Sample" and "Sample Size Calculation") showing the full population with QoQ variance scores, sample flags, and mandatory coverage of specific entity/country combinations. **Total possible: 63 points.**

---

### Rubric Scorecard

| # | Pts | Criterion | Claude Code | ChatGPT 5.4 |
|---|-----|-----------|:-----------:|:-----------:|
| 1 | +2 | File basename is 'Sample' | ✅ | ✅ |
| 2 | +2 | Worksheet named exactly 'Sample Size Calculation' | ✅ | ✅ |
| 3 | +2 | SSC states confidence 90% and tolerable error 10% | ✅ | ✅ |
| 4 | +2 | Population size N = 1516 | ✅ | ✅ |
| 5 | +2 | z=1.645, p=0.5, e=0.10, FPC applied; R reported as integer (ceil) | ✅ | ✅ |
| 6 | +2 | First worksheet col A–H in Population order with identical headers | ✅ | ✅ |
| 7 | +2 | Values in A–H exactly match Population reference | ✅ | ✅ |
| 8 | +2 | G=Q3 2024, H=Q2 2024 consistent with Population column positions | ✅ | ✅ |
| 9 | +2 | Col I computes QoQ variance = (Q3−Q2)/Q2 for rows where Q2≠0 | ✅ | ❌ |
| 10 | +1 | Q2=0, Q3=0: col I = 0 (no change) | ✅ | ✅ |
| 11 | +1 | Q2=0, Q3≠0: col I avoids #DIV/0! errors | ✅ | ✅ |
| 12 | +1 | No Excel errors in col I | ✅ | ✅ |
| 13 | +2 | Col J exists; sampled rows flagged by numeric value 1 | ✅ | ❌ |
| 14 | +1 | Non-sampled rows in col J blank or 0 | ✅ | ❌ |
| 15 | +2 | Sample count S shown; S ≥ R | ✅ | ❌ |
| 16 | +2 | At least one row with \|variance\| ≥ 20% is sampled | ✅ | ✅ |
| 17 | +1 | If \|variance\| ≥ 100% rows exist, at least one is sampled | ✅ | ✅ |
| 18 | +2 | Sample: Corporate Banking + Corporate Loans + Italy | ✅ | ❌ |
| 19 | +2 | Sample: Corporate Banking + Correspondent Banking + Greece | ✅ | ✅ |
| 20 | +2 | Sample: Markets + Trading + Luxembourg | ✅ | ✅ |
| 21 | +2 | Sample: Corporate Banking + Marine Finance + Brazil | ✅ | ✅ |
| 22 | +2 | Sample: Retail Bank + EMEA + UAE | ✅ | ✅ |
| 23 | +2 | Sample includes Total Clients metric | ✅ | ✅ |
| 24 | +2 | Sample includes HR Clients metric | ✅ | ✅ |
| 25 | +1 | If Q2=0 and Q3=0 rows exist, at least one sampled | ✅ | ✅ |
| 26 | +1 | If Marine Finance rows exist, at least one sampled | ✅ | ✅ |
| 27 | +1 | If Correspondent Banking rows exist, at least one sampled | ✅ | ✅ |
| 28 | +1 | If Cayman Islands rows exist, at least one sampled | ✅ | ✅ |
| 29 | +1 | If Pakistan rows exist, at least one sampled | ✅ | ✅ |
| 30 | +1 | If UAE rows exist, at least one sampled | ✅ | ✅ |
| 31 | +2 | All distinct Divisions represented in sample | ✅ | ✅ |
| 32 | +2 | All distinct Sub-Divisions represented in sample | ✅ | ✅ |
| 33 | +1 | SSC shows arithmetic steps (z, p, e, FPC) reproducibly | ✅ | ✅ |
| 34 | +1 | First worksheet includes full population (1516 rows) | ✅ | ❌ |
| 35 | +1 | Col J header clearly indicates QoQ variance | ❌ | ✅ |
| 36 | +1 | Metrics with \|variance\| ≥ 100% easily identifiable | ❌ | ❌ |
| 37 | +1 | First worksheet named 'Sample' | ✅ | ❌ |
| 38 | +5 | Overall formatting and style | ⚠️ 4/5 | ⚠️ 3/5 |

### Final scores

| | Claude Code + SKILL.md | ChatGPT 5.4 Think Deeper + Deskwork |
|--|:---:|:---:|
| **Score** | **60 / 63** | **49 / 63** |
| **Pct** | **95%** | **78%** |

---

### Claude Code + SKILL.md

**Output**: `benchmarks/claude-code/afc-audit-sampling/output/Sample.xlsx` (2 tabs)
**Sheet structure**: Sample (1516 rows + header) · Sample Size Calculation

**What succeeded**:
- First sheet named "Sample" exactly; full 1516-row population preserved with original A–H columns ✓
- Col I = "QoQ Variance (Q3 vs Q2)" computing (Q3−Q2)/Q2 as decimal; zero-zero rows return 0; Q2=0,Q3≠0 returns "N/M" (no #DIV/0! errors) ✓
- Col J = "Selected" flag (1 = sampled, blank = not sampled); S=67 ≥ R=66 ✓
- All 5 mandatory entity/country combinations satisfied: Italy (Corporate Bank+Corporate Loans), Greece (Correspondent Banking), Luxembourg (Trading), Brazil (Marine Finance), UAE (Retail Bank+EMEA) ✓
- All 4 Divisions and all 13 Sub-Divisions represented in sample ✓
- All specific country criteria: Pakistan, Cayman Islands, UAE, Total Clients, HR Clients ✓
- Sample Size Calculation tab shows all inputs (z=1.645, p=0.5, e=0.10, N=1516), formula steps, and FPC application ✓

**Issues**:
- **Col J header (−1)**: Header is "Selected" — the rubric requires the column J header to indicate QoQ variance (e.g., "% Var Q3 vs Q2"). In our design, Col I is the variance and Col J is the sample flag, so the header naming is semantically correct but fails this specific rubric criterion.
- **|≥100%| not easily identifiable (−1)**: No conditional formatting or separate flag column marks rows with extreme variance. The script selects them (all are in the sample) but does not visually highlight them.
- **Formatting (4/5)**: Clean structure, but no conditional formatting.

---

### ChatGPT 5.4 Think Deeper + Deskwork

**Output**: `benchmarks/gpt-5/afc-audit-sampling/output/Sample.xlsx` (2 tabs)
**Sheet structure**: Selected sample (65 rows) · Sample Size Calculation

**What succeeded**:
- Sample Size Calculation tab complete: N=1516, z=1.645, p=0.5, e=0.10, FPC applied, R=65 ✓
- Greece + Correspondent Banking, Luxembourg + Trading, Brazil + Marine Finance, UAE + Retail Bank correctly sampled ✓
- Total Clients and HR Clients both sampled ✓
- All Divisions and Sub-Divisions covered ✓
- Cayman Islands, Pakistan, UAE, Marine Finance, Correspondent Banking all sampled ✓
- Col J header = "QoQ Variance %" — correctly labelled to indicate QoQ variance (earned criterion 35)
- Formatting (3/5): Selection rationale column (L) explains each row's inclusion reason; well-organized SSC tab with arithmetic steps

**Issues**:
- **Column assignment mismatch (−7)**: GPT-5 placed absolute variance (Q3−Q2) in col I and QoQ percentage variance in col J, with the sample flag in col K. The rubric expects: col I = QoQ%, col J = sample flag. This single structural error costs: criterion 9 (−2, col I is wrong formula), criterion 13 (−2, col J is not the flag), criterion 14 (−1, col J is not blank for non-sampled), criterion 15 (−2, S shown in col K not the expected location).
- **First sheet not named 'Sample' (−1)**: Sheet named "Selected sample" instead of "Sample".
- **First sheet contains only sample rows (−1)**: 65 rows only — rubric expects the full 1516-row population with flags.
- **Italy + Corporate Loans not sampled (−2)**: Mandatory criterion 18. GPT-5 sampled Corporate Bank + Fund Services + Italy instead. The Deskwork system_prompt listed the 5 mandatory combinations but the exact Sub-Division match was missed (Fund Services vs. Corporate Loans).
- **|≥100%| not easily identifiable (−1)**: Same gap as Claude Code.

**Root cause of column mismatch**: The system_prompt.md specified "add a QoQ variance column and a sample selection flag column" but did not specify which column letter each should occupy. GPT-5 inserted two columns before the flag, shifting col J to variance and col K to flag — a defensible interpretation but misaligned with the rubric's col J = flag assumption.

---

### Key comparison

**Outcome**: Claude Code + SKILL.md scored substantially higher (60 vs. 49, a 14-point gap on a 63-point rubric). This is the largest performance gap across all three tasks.

**Where Claude Code had an edge**:
- Correct column assignment (I = QoQ%, J = flag): +7 points (criteria 9, 13, 14, 15)
- First sheet named "Sample" with full 1516-row population: +2 points (criteria 34, 37)
- Italy + Corporate Loans correctly sampled: +2 points (criterion 18)
- Total gap from structural errors in GPT-5 output: **11 of the 14-point difference**

**Where ChatGPT 5.4 had an edge**:
- Col J header indicates QoQ variance (criterion 35): +1 point
- Formatting with selection rationale column: +0 net (3/5 vs. 4/5, net −1)

**What this tells us**:
The Deskwork system_prompt correctly specified the sampling methodology (z, p, e, FPC, mandatory inclusions, division/sub-division coverage) — all verified correct. The gap comes from two structural specification gaps: (1) exact column letter assignments for variance and flag columns not specified; (2) the instruction to include the full population vs. selected rows only not made explicit. These are workflow specification gaps that a more precise system_prompt.md would close. The mandatory inclusion for Italy+Corporate Loans was also slightly mis-executed (wrong Sub-Division matched), suggesting a need for more explicit matching instructions.
